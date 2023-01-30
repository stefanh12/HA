# HA
home assistant configs



#labcom.cloud.json
node-red flow for getting the measurements for one accountid(currently) and adding the measurements as sensors to home assistant. Depends on 
- node-red-contrib-graphql
- node-red-contrib-home-assistant-websocket

The auth token will need to be generated for your account, see https://labcom.cloud/pages/user-setting. Place the token in customHeaders.Authorization node in the flow.
