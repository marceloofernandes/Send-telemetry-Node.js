# Send-telemetry-Node.js-
Quickstart: Send telemetry from a device to an IoT hub and read the telemetry from the hub with a back-end application (Node.js).   

This document presents the results of the following hands-on lab about **Azure IoT from Microsoft** and is available at https://docs.microsoft.com/en-us/azure/iot-hub/quickstart-send-telemetry-node.     


## Register a device
1. Run the following commands in Azure Cloud Shell to add the IoT Hub CLI extension and to create the device identity.

Note: replace `YourIoTHubName` by `barueri-test-hub` which is the IoT Hub created for this experiment.


az extension add --name azure-cli-iot-ext
az iot hub device-identity create --hub-name YourIoTHubName --device-id MyNodeDevice

```
az extension add --name azure-cli-iot-ext
az iot hub device-identity create --hub-name barueri-test-hub --device-id MyNodeDevice         
```

![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2012.43.30.jpg)



2. Run the following commands in Azure Cloud Shell to get the device connection string for the device you just registered:     

```
az iot hub device-identity show-connection-string --hub-name barueri-test-hub --device-id MyNodeDevice --output table     
```
![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2012.54.29.jpg)

Make a note of the **device connection string**, which looks like:    


```
HostName=barueri-test-hub.azure-devices.net;DeviceId=MyNodeDevice;SharedAccessKey=1DrstUh8tUnp8ndhobjaMYo4mbN4gYhm5pkdtzg2dms=
```


3. You also need a service connection string to enable the back-end application to connect to your IoT hub in order to retrieve the messages. The following command retrieves the service connection string for your IoT hub:     

```
az iot hub show-connection-string --hub-name barueri-test-hub --output table       
```

![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2012.54.54.jpg)

Make a note of the **service connection string**, which looks like:      

```
HostName=barueri-test-hub.azure-devices.net;SharedAccessKeyName=iothubowner;SharedAccessKey=6iwF5p2PNqZrBxejs3FZPNlfPkznrUton9Dlnp0Kz/Y=
```

## Send simulated telemetry
1. Open your local terminal window, navigate to the root folder of the sample Node.js project. Then navigate to the iot-hub\Quickstarts\simulated-device folder.    

![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2013.12.56.jpg)


2. Open the **SimulatedDevice.js** file in a text editor of your choice.   

![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2013.20.55.jpg)


3. In the local terminal window, run the following commands to install the required libraries and run the simulated device application:   

```
npm install
node SimulatedDevice.js
```
![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2013.24.17.jpg)


The following screenshot shows the output as the simulated device application sends telemetry to your IoT hub:    

![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2013.24.52.jpg)


## Read the telemetry from your hub
1. Open another local terminal window, navigate to the root folder of the sample Node.js project. Then navigate to the **iot-hub\Quickstarts\read-d2c-messages** folder.

![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2013.44.29.jpg)


2. Open the **ReadDeviceToCloudMessages.js** file in a text editor of your choice.     


Replace the value of the `connectionString` variable with the **service connection string** you made a note of previously. Then save your changes to the ReadDeviceToCloudMessages.js file.  

![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2013.53.49.jpg)


3. In the local terminal window, run the following commands to install the required libraries and run the back-end application:

```
npm install
node ReadDeviceToCloudMessages.js
```

![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2013.55.43.jpg)  


The following screenshot shows the output as the back-end application receives telemetry sent by the simulated device to the hub:    

![alt text](https://github.com/marceloofernandes/Send-telemetry-Node.js-/blob/draft/Pictures/Screen%20Shot%202018-12-21%20at%2013.56.43.jpg)  


## Summary

The hands-on activity was successfully complete.

