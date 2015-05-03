Indigo MySensors plugin
=======================
The Indigo MySensors plugin adds interaction with [MySensors](http://www.mysensors.org) to [Indigo](http://www.perceptiveautomation.com).

This plugin (and Readme) is a work in progress, based on MySensors 1.4b...

Unless you don't mind that not all sensors have been tested and you don't mind using beta software you can use the plugin. If you decide to do so please report issues through Github.

### Installation instructions
1. Download the (zip archive of the) plugin [here](https://github.com/IT2BE/indigo-mysensors/releases)
2. Follow the [plugin installation instructions](http://wiki.indigodomo.com/doku.php?id=indigo_6_documentation:getting_started#installing_plugins_and_configuring_plugin_settings_pro_only_feature)

When you have Indigo installed the folder will show as a single file (a so called package).
When you doubleclick on the file you will automatically open Indigo (or bring it to the front) and you will be asked if you want to install and enable it.

### Attach the Gateway
Next thing should be simple. Create a Gateway from the sample sketch that you most likely already downloaded [here](https://github.com/mysensors/Arduino). You need the SerialGateway.ino sketch.
After uploading the sketch to your Arduino board you can attach it to your Mac.
You now go to the configuration menu of the plugin (plugins > MySensors > configure) and select the correct serial port.
When you arrived at this point you are ready to add your devices.

### Include devices
New devices/boards are always recognised. Also when inclusion mode is not activated.
The only thing you really need to do is to (re-)activate a device. You can do so by using the push button or by plugging in a power source. The device has to be within reach of the MySensors network. This will make the gateway/plugin aware of the device and will try to add a node id to the device.

Now watch your event log to see what is going on and wait until the device starts sending out details about its sensor. When the device and its sensors are known (have an id) you can start adding the device to Indigo so you can start using it.

Click the 'New' button, select the device type 'MySensors', select the device and, when you selected the correct one click the 'Add Device' button. Notice that you actually selected a board and that the sensors are included after clicking the 'Add Device' button. It does not matter how many sensors the board has, they should all appear as long as they are known to the plugin.

Word of advice: It is ok when the board already has a node id but this will make that you are in charge of handing out the id's instead of the plugin and you should really beware of not using a node id twice (and certainly stay away from 0 because this is used for the Gateway by default).

### Battery operated devices
When a device uses batteries you can set the device up so that it sends its battery level to the gateway.
The gateway will forward this message (like any other message) to Indigo.
Indigo now 'recognizes' that this is a battery operated device and will automatically start showing support for the battery level.

### Using triggers, actions etc.
When you are at this point the device behaves similar to what you are used to in Indigo so I am not going to spend many more words than necessary here. Triggers, actions etc. are defined based on what is available for a sensor in MySensors. So this is pretty standard stuff. When you miss something that is available in MySensors but not in the plugin you can either let me know or fork the master and add it yourself (and commit the changes so that I can review and add them).

### Menu Items
The following menu items are available:

###### Toggle Debugging
This works like any other plugin in Indigo.
It toggles debugging output on and off.
And, like with all plugins you should use it with care and/or when you are asked to use it because it can give you an overload of output and slow down your system.

###### Start Inclusion Mode
Basically obsolete but this will trigger inclusion mode on the Gateway. Right now, as described above, the only thing it does is activate inclusion mode on your Gateway. The plugin ignores it.

###### Reload Devices
This will delete all board/sensor metadate stored and used by the plugin.
It does not delete/remove the devices setup within Indigo.
Although the plugin will try to reconnect and recreate your board and sensor metadata you should use it with care.
Three words of advice here:
* Don't do this unless you are asked to when you are unsure.
* Use it when you want to reset the system but you should (in this order): remove devices, reload devices, clear node id's on the board and upload new sketches and start 'fresh'.
* When you use it you should always (re-)activate a board to make it know to the Gateway again or you will end up with a mess.

### FreeBSD License
Copyright (c) 2014, Marcel Trapman
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR
ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

The views and conclusions contained in the software and documentation are those
of the authors and should not be interpreted as representing official policies,
either expressed or implied, of the FreeBSD Project.