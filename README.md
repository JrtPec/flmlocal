#FLM local visualizations
This is a native implementation of the [Justgage](http:/justgage.com) gauges, the [Flot](http://www.flotcharts.org/) charts and a plain panel to be used in the [Fluksometer's](http://flukso.net) AngularJS based user interface. It sits on top of the [Paho JavaScript client](https://eclipse.org/paho/clients/js/).<br/>
To utilize this implementation, copy the content of the [www/](www/) folder to your Fluksometer with firmware version >2.4.<br>
Use the linux/OSX command **scp** for this purpose; for windows use [WinSCP](http://winscp.net).

    scp -r * root@<FLM ip address>:/www/

You are prompted for the root's password, then all necessary files are transferred (recursively through option -r)

By that you gain direct access to a local gauge and panel visualization directly from the Fluksometer's landing page navigation when calling

    <flm ip address>

in your browser.

<img src="FLMlocalGauge.png" width=500px>

With a next version of the Fluksometer firmware there will be a dedicated topic on which the FLM's configuration is published; this adaptation is also available for an "old" fluksometer using the code provided in [/usr/sbin/fluksod.lua](/usr/sbin/fluksod.lua) - this enhances the flukso daemon by the corresponding functionality; use at own risk (after scp copy a reboot of the FLM is required).

##Show arbitrary sensors
Even though the primary purpose of this implementation is to visualize Fluksometer readings, it is capable to handle also other information passed to the FLM's MQTT broker. So, if you have, for example, an [Arduino Ethernet](https://github.com/gebhardm/energyhacks/tree/master/AVRNetIOduino/AVRNetIO_MQTT_DS_DHT) publishing sensor data (for example on temperature or humidity), this can be visulaized as well, if you address the FLM MQTT broker. The visualizer (gauge, graph and panel) take all sensor information formatted as (payload in either format)

    topic: /sensor/<sensor id>/gauge
    payload: <value> 
            [<value>] 
            [<value>, <unit>] 
            [<timestamp>, <value>, <unit>]

Note that here the `<sensor id>` is taken as name as long as you are not publishing any device configuration topic with id, name and if enabled (other parameters are currently not used, like "class" and "type", but may in the future).

    topic: /device/<device id>/config/sensor
    payload: { "<sensor enum>":{ "id":"<sensor id>", 
                                 "function":"<sensor name>", 
                                 "enable":"1" } }

<img src="FLMlocalPanel.png" width=500px>
 
##Credits
This code under [MIT license](LICENSE); all used libraries/includes with the respective license noted.

The gauge uses [JustGage](http://justgage.com/), the graph is built using [Flot](http://www.flotcharts.org/) and the panel utilizes [jQuery Sparkline](http://omnipotent.net/jquery.sparkline/).<br/>
Corresponding licenses are the [MIT license](http://opensource.org/licenses/mit-license.php) and the [New BSD license](http://opensource.org/licenses/BSD-3-Clause).

