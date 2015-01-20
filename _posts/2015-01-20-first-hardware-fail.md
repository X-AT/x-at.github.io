---
layout: post
title:  "X-AT first hardware: fail"
date:   2015-01-20 09:56:00
categories: xat
---

Unfortunately the first iteration of the hardware was too bad.
Motor power is low (need worm gear), threaded studs too curves.

![old hardware](/images/hardware-v1/dscn0334.jpg)

I think gather [SatNOGS hardware][satnogs-hw].
Their turntable larger, but works and electronics is hidden inside the body.
And use with my own electronics and software.

I done with USB-HID stepper controller and LCM-motor daemon (`xat_rotd`).
Also i decided to use LUA for scripting (widely adopted in OpenWRT).


Example moveto script
---------------------
{% highlight lua %}
#!/usr/bin/env lua

local lcm = require('lcm')

-- this might be necessary depending on platform and LUA_PATH
package.path = './?/init.lua;' .. package.path

local xat_msgs = require('xat_msgs')
local lc = lcm.lcm.new()

local msg = xat_msgs.joint_goal_t:new()

-- XXX: find how to produce right header (seq+stamp)
msg.header = xat_msgs.header_t:new()
msg.azimuth_angle = arg[1]
msg.elevation_angle = arg[2]

lc:publish("xat/rot_goal", msg:encode())
{% endhighlight %}


[satnogs-hw]: https://satnogs.org/hardware.html
