#FLM local visualizations
This is a jQuery based implementation of a [Fluksometer](http://flukso.net) local visualization utilizing MQTT subscriptions with the [Paho JavaScript client](https://eclipse.org/paho/clients/js/).<br/>
To get the capability to show a gauge, graph and panel
from your [Fluksometer](http://flukso.net) directly (within the LAN, no internet access required), copy the content of the [www/](www/) folder to your FLM with firmware version >2.4.<br>
Use the linux/OSX command **scp** for this purpose; for windows use WinSCP.

`scp -r * root@<FLM ip address>:/www/`

You are prompted for the root's password, then all necessary files are transferred (option -r)

By that you gain direct access to a local gauge, graph, and panel visualization directly from the FLM's landing page navigation when calling

`<flm ip address>`

in your browser.

<img src="FLM_navigation.png" width=500px> 

<img src="FLM_local_panel.png" width=500px>

Note: The used library of the MQTT websockets connector *mqttws31.js* tends to lose connection; for the moment by a built-in reconnect you should not experience any script stops; if you do, just refresh your browser window to reset the websocket. Nevertheless the browser console will show (from time to time) following error message.

<img src="mqttws31_error.png" width=500px>

This code under [MIT license](LICENSE); all used libraries/includes with the respective license noted (see below). 

##Credits
The gauge uses [JustGage](http://justgage.com/), the graph is built using [Flot](http://www.flotcharts.org/) and the panel utilizes [jQuery Sparkline](http://omnipotent.net/jquery.sparkline/).<br/>
Corresponding licenses are the [MIT license](http://opensource.org/licenses/mit-license.php) and the [New BSD license](http://opensource.org/licenses/BSD-3-Clause).<br/>
All visualizations sit on top the [Paho JavaScript client](https://eclipse.org/paho/clients/js/) under [Eclipse Public License](http://www.eclipse.org/legal/epl-v10.html).