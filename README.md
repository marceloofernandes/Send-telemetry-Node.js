# Send-telemetry-Node.js-
Quickstart: Send telemetry from a device to an IoT hub and read the telemetry from the hub with a back-end application (Node.js).   

This document presents the results of the following hands-on lab about ***Azure IoT from Microsoft*** and is available at https://docs.microsoft.com/en-us/azure/iot-hub/quickstart-send-telemetry-node.     


## Register a device
1. Run the following commands in Azure Cloud Shell to add the IoT Hub CLI extension and to create the device identity.

Note: replace `YourIoTHubName` by `barueri-test-hub`


az extension add --name azure-cli-iot-ext
az iot hub device-identity create --hub-name YourIoTHubName --device-id MyNodeDevice

```
az extension add --name azure-cli-iot-ext
az iot hub device-identity create --hub-name barueri-test-hub --device-id MyNodeDevice         
```


2. Run the following commands in Azure Cloud Shell to get the device connection string for the device you just registered:     

```
az iot hub device-identity show-connection-string --hub-name barueri-test-hub --device-id MyNodeDevice --output table     
```

Make a note of the device connection string, which looks like:       

```
HostName=barueri-test-hub.azure-devices.net;DeviceId=MyNodeDevice;SharedAccessKey=1DrstUh8tUnp8ndhobjaMYo4mbN4gYhm5pkdtzg2dms=
```

3. You also need a service connection string to enable the back-end application to connect to your IoT hub in order to retrieve the messages. The following command retrieves the service connection string for your IoT hub:     

```
az iot hub show-connection-string --hub-name barueri-test-hub --output table       
```

Make a note of the service connection string, which looks like:      

```
HostName=barueri-test-hub.azure-devices.net;SharedAccessKeyName=iothubowner;SharedAccessKey=6iwF5p2PNqZrBxejs3FZPNlfPkznrUton9Dlnp0Kz/Y=
```

## Send simulated telemetry
1. Open your local terminal window, navigate to the root folder of the sample Node.js project. Then navigate to the iot-hub\Quickstarts\simulated-device folder.    

