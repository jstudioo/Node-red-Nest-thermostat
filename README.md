# NEST style thermostat Dashboard widget for Node-red

If you have made heating or cooling controls on Node-red you will need nice thermostat widget to display and control your device via Node-red dashboard.

![Nest html widget](https://www.ajso.lt/wp-content/uploads/2016/12/nest-html5-widget-1.png)

Fully responsive design. Touch enabled set-point makes it even more cool. Press and hold finger over and it will activate set point sliding function.

Also it has several display modes like heating, cooling and away. It makes it more intractable and user intuitive. For more ECO friendly there is possible to turn on and off that little green leaf.

![Nest html widget](https://www.ajso.lt/wp-content/uploads/2016/12/nest-html5-widget-1.png)
![Nest html widget](https://www.ajso.lt/wp-content/uploads/2016/12/nest-html5-widget-1.png) ![Nest html widget](https://www.ajso.lt/wp-content/uploads/2016/12/nest-html5-widget-1.png)


Let’s try to port this in Node-red. Data exchange is based on topics. You can can push separate payloads with specific topic. If you change the set-point in the web browser it will trigger back payload to node-red with topic `target_temperature` and a value.

ambient_temperature, target_temperature are numeric (21.5) payloads.
hvac_state is string (off, heating, cooling) payload.
has_leave, away are boolean (true, false) payloads.
If you familiar with CSS and JAVA there are more stuff to customize, colors, ranges etc.

Some options in JAVA script:

`options = {
 diameter: options.diameter || 400,
 minValue: options.minValue || 10, //Minimum value for target temperature
 maxValue: options.maxValue || 30, //Maximum value for target temperature
 numTicks: options.numTicks || 200, //Number of tick lines to display around the dial
 onSetTargetTemperature: options.onSetTargetTemperature || function() {}, // Function called when new target temperature set by the dial
};`

Widget can be rendered anywhere in the page. You just have to include div with thermostat ID.

`<div id="Mythermostat"></div>`

`var nest = new thermostatDial(document.getElementById('Mythermostat')`

IF you have more than one thermostat widget make sure they have unique names to avoid  rendering wrong data to wrong divs.
