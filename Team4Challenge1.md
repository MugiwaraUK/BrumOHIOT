az iot hub create --name iotHubTeam4 --resource-group OpenHack-IoT-Data-Team004-RG --sku S1

az iot hub device-identity create --hub-name iotHubTeam4 --device-id Hacker6Device
{
  "authentication": {
    "symmetricKey": {
      "primaryKey": "wxP3IRia60YFR+T44+/tkjefQVvPqLaUoLY7dLQar5Q=",
      "secondaryKey": "I+ilir7MKh6Vu1ko0/R6PffIqq/tSoyXkfNNAq0+vDo="
    },
    "type": "sas",
    "x509Thumbprint": {
      "primaryThumbprint": null,
      "secondaryThumbprint": null
    }
  },
  "capabilities": {
    "iotEdge": false
  },
  "cloudToDeviceMessageCount": 0,
  "connectionState": "Disconnected",
  "connectionStateUpdatedTime": "0001-01-01T00:00:00",
  "deviceId": "Hacker6Device",
  "etag": "MTU1Mzc2MzQ3",
  "generationId": "636801257635755319",
  "lastActivityTime": "0001-01-01T00:00:00",
  "status": "enabled",
  "statusReason": null,
  "statusUpdatedTime": "0001-01-01T00:00:00"
}





#show connection string 
az iot hub device-identity show-connection-string --device-id Hacker6Device --hub-name iotHubTeam4 --resource-group OpenHack-IoT-Data-Team004-RG


{
  "cs": "HostName=iotHubTeam4.azure-devices.net;DeviceId=Hacker6Device;SharedAccessKey=wxP3IRia60YFR+T44+/tkjefQVvPqLaUoLY7dLQar5Q="
}

####generate SAS token: 
az iot hub generate-sas-token --device-id Hacker6Device --hub-name iotHubTeam4

Sample output : 
{
  "sas": "SharedAccessSignature sr=iotHubTeam4.azure-devices.net%2Fdevices%2FHacker6Device&sig=z9reo02SA0AIcqdELbSnsTyIBi%2BxFQmgT%2BGFc1fFzBk%3D&se=1544533746"
}



az iot hub show --query properties.eventHubEndpoints.events.endpoint --name iotHubTeam4

"sb://iothub-ns-iothubteam-1063841-9c12ea224b.servicebus.windows.net/"

az iot hub show --query properties.eventHubEndpoints.events.path --name iotHubTeam4
iothubteam4

az iot hub policy show --name iothubowner --query primaryKey --hub-name iotHubTeam4
"5KI7ix7zs7T6H/KXaBhyl6J0OlTECXRAkI8qPEs6nkA="

# Monitoring event via Azure CLI 
az iot hub monitor-events --device-id Hacker6Device --hub-name iotHubTeam4

Useful links : 

https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-devguide-identity-registry

https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-devguide-security



