# HA
home assistant configs



#labcom.cloud.json
node-red flow for getting the measurements for one accountid(currently) and adding the measurements as sensors to home assistant. Depends on 
- node-red-contrib-graphql
- node-red-contrib-home-assistant-websocket

The auth token will need to be generated for your account, see https://labcom.cloud/pages/user-setting. Place the token in customHeaders.Authorization node in the flow.

#Pool Enzo
Esphome for the Atlas Scientific Wifi Pool Kit, including 2 Ezo-pmp for Acid and Chlorine pumping
The code does not allow for pumping acid at the same time as chorine due to health risks.

#Brilix Heat Pump
Does not use the wifi interface of the screen(if you have wifi), instead it replaces the screen for more reliable setup.
