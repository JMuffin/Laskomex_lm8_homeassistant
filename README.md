# Laskomex_lm8_homeassistant
Laskomex LM8 Home Assistant integration with PCB

Integration is based on ESP8266 using Wemos D1 mini.
Wemos with PCB sits in a custom printed holder (ESP-holder.stl).
All connections are made through 3 SPDT relays.

ESPHome (Domofon.yaml) sends the status to Home Assistant. Then Node-RED automations (flows.json) take care of all notifications and opening schema.

Incoming chime is based on optoisolator and voltage comparator to eliminate all insufficient signals.
Than, based on signal duration, divided to 3 options: Door open, Wrong code, Ringing.

Functions:
- Remote door opening 
- Automatic door opening
- "Do not disturb" mode (mute)
- Phone notifications for incoming calls
- retaining classic functionality - manual answering and opening.

It's not possible to directly utilize the L+ and L- lines for full communication using ESP8266 due to signal delays. 
For this purpose, a separate microcontroller based on Arduino should be used - such projects can be found elsewhere on the internet.

Relays should be connected to the locations indicated on the schematic (Podlaczenie.jpg), 
remembering to remove the measuring resistor in the volume control circuit - marked on the schematic as "X". 
This connection allows us to use the handset even when the MUTE function is enabled - we retain full functionality of the intercom regardless of the Home Assistant settings.
