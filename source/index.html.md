---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
 - python
 - java


includes:
  - errors

search: true
---

# Introduction

Welcome to the Connectavo API and Endpoint documentation

# Sensor

## Publish Sensor Data 

###MQTT

```python
import paho.mqtt.client as mqtt
import time

assetuid = "assetuid"
deviceuid = "deviceuid"
companyid = "companyid"
username = "companyname"
password = "apikey"
host="mqtt.connectavo.com"
port = 1883
topic = "company/"+companyid+"/asset/"+assetuid+"."+deviceuid+"/data/sensor"
value = 4440
client = mqtt.Client()
client.username_pw_set(username, password=password)


client.connect(host, port,  keepalive=10000)
data = "{
    \"deviceUid\":\""+deviceuid+"\",
    \"timestamp\":"+time.time()+",
    \"data\": {
		\"reading\":\""+value+"\", 
		}
    }"

client.publish(topic, data, retain=1, qos=2)
```

```java
 
```

```json
    {
    "id":null,
    "deviceUid":"deviceuid",
    "timestamp":1451281363,
    "data":
        {"reading":"4440", assetUid:"assetuid"}
    }
```


### HTTP Request

`POST https://api.connectavo.com/sensordata`

### Headers

Header| Default  
--------- | ------- 
Content-Type| application/json
Authorization| md5(companyid:apikey)



