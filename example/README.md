![Pub](https://img.shields.io/pub/v/serial_communication)
# Serial communication!
An Android Plugin for Serial Communication which allow you to read
and write the data through the available ports
The supported features are:
* Listing the available serial ports on the device, including USB to serial adapters
* Configuring serial ports (baud rate, stop bits, permission, ...)
* Providing standard InputStream and OutputStream
# Description
This PlugIn enables the communication with the
**USB**
**RS232**
**RS485**
**UART**


**Supported platforms:**
* Android

## Video tutorial
In order to completely understand you can view our sample video in which we are using an android Lcm module.
Click the image below to watch the video:

[//]: # ()
[//]: # ([![IMAGE ALT TEXT]&#40;https://i.postimg.cc/T1YCPsSH/Screenshot-2022-09-12-at-11-16-36-AM.png&#41;]&#40;https://www.youtube.com/watch?v=GeNuR-YH6ms"&#41;)

## Getting Started
Add a dependency to your pubspec.yaml
~~~
dependencies:
	flutter_serial: version number
~~~
include the usbserial package at the top of your dart file.
~~~
import  'package:flutter_serial/flutter_serial.dart';
~~~
## ❓ Usage
If you encounter any issues please refer to the API docs and the sample code in the  `example`  directory before opening a request on Github.

### Example app[](https://pub.dev/packages/flutter_local_notifications#example-app)

The  [`example`](https://github.com/mahad555/serialCommunication/blob/main/example/lib/main.dart)  directory has a sample application that demonstrates the features of this plugin.
***

## 🔧 Android Setup #



**Initialisation**  
The first step is to call the startSerial() method and subscribe the
StreamSubscription

## **Start Serial**

startSerial method  will open the transaction stream
~~~
FlutterSerial serialCommunication = FlutterSerial();

  @override
  void initState() {
    super.initState();
   serialCommunication.startSerial().listen(_updateConnectionStatus);
    getSerialList();
  }
  
 void  _updateConnectionStatus(SerialResponse? result) async {
logData = result!.logChannel ?? "";
receivedData = result.readChannel ?? "";
});
}
~~~
By calling the startSerial() it will provide  you with the SerialResponse in the form of stream data

**SerialResponse**
In Serial Response you will get the following type  
1)  Log Channel (type:String)  
2)  Read Channel  (type:String)

1) Log Channel:
   In the log channel you wll get the repsone when you open any port
   ,close any port , transmit data (TX).

2) Read Channel:
   In the Read channel you wll get the Recived data (RX)

## **Available Ports**

The getAvailablePorts() method  will return you all the  
available ports on a device
~~~
serialList = await  serialCommunication.getAvailablePorts();
~~~

## **Open**

openPort method  will open the serial communication
Its has 3 required parameter
{ **DataFormat** dataFormat, **String** serialPort, **int** baudRate }
~~~
serialCommunication.openPort(
dataFormat: DataFormat.ASCII,
serialPort: serialList.first,
baudRate: serialCommunication.baudRateList.first)
~~~

## **Close**

closePort method  will close the port if you have opened any port
~~~
serialCommunication.closePort();
~~~

## **Send Command**
sendCommand method  will send your message
Its has 1 required parameter  {**String**  message}
~~~
serialCommunication.sendCommand(message: "message");
~~~


## Clear

**clearLog** method  will clear the Log channel
**clearRead** method  will clear the Read channel

~~~
serialCommunication.clearLog();
serialCommunication.clearRead();
~~~

## Destroy
**destroy** method  will eliminate the resources
~~~
@override
void  dispose() {
serialCommunication.destroy();
super.dispose();
}
~~~

* * *
*  **Baud Rate**
   To get the Standard baud rates list
   call the `FlutterSerial().baudRateList`
   it will return the integer list of standard baud rate

*  **Data Format**
   The Data format is used to convert the data type
   To pass the data format in the open()  method parameter
   For ascii format
   call the `DataFormat.ASCII`

   For hex_String format
   call the `DataFormat.HEX_STRING`

# Contribution

Any help from the open-source community is always welcome and needed:

-   Found an issue?
    -   Please fill a bug report with details.
-   Wish a feature?
    -   Open a feature request with use cases.
-   Are you using and liking the project?
    -   Promote the project: create an article, do a post or make a donation.
-   Are you a developer?
    -   Fix a bug and send a pull request.
    -   Implement a new feature.
    -   Improve the Unit Tests.
-   Have you already helped in any way?
    -   **Many thanks from me, the contributors and everybody that uses this project!**
- [BJS MB Dev](https://github.com/bjs-mb-dev)
- [Zain Ul Abideen](https://github.com/zain4bjs) 
     







