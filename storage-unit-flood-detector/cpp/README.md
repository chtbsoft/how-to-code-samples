﻿# Storage unit flood detector in C++

This storage unit flood detector application is part of a series of how-tos for Intel's Internet of Things (IoT) code sample exercises using the Intel® IoT Developer Kit, Intel® Edison board, Intel® IoT Gateway, cloud platforms, APIs, and other technologies.

From this exercise, developers will learn how to:

- Connect the Intel® Edison board or Intel® IoT Gateway, computing platforms designed for prototyping and producing IoT and wearable computing products.
- Interface with the Intel® Edison board or Arduino 101\* (branded Genuino 101\* outside the U.S.) board IO and sensor repository using MRAA and UPM from the Intel® IoT Developer Kit, a complete hardware and software solution to help developers explore the IoT and implement innovative projects.
- Run these code samples in the Intel® System Studio IoT Edition (Eclipse IDE for C/C++ and Java\* development) for creating applications that interact with sensors and actuators, enabling a quick start for developing software for the Intel® Edison board or the Intel® Galileo board.
- Store water detection data using Azure Redis Cache\* from Microsoft, Redis Store\* from IBM Bluemix\*, or ElastiCache\* using Redis\* from Amazon Web Services (AWS)\*, different cloud services for connecting IoT solutions including data analysis, machine learning, and a variety of productivity tools to simplify the process of connecting your sensors to the cloud and getting your IoT project up and running quickly.
- Set up a MQTT-based server using Microsoft Azure\* IoT Hub, IoT from IBM Bluemix\*, or IoT from Amazon Web Services (AWS)\*, different cloud machine to machine messaging services based on the industry standard MQTT protocol.

## What it is

Using an Intel® Edison board or Intel® IoT Gateway, this project lets you create a storage unit flood detector that:

- continuously checks the moisture sensor.
- sounds an audible warning when it looks like flooding.
- stores a record of each time moisture is detected, using cloud-based data storage.

## How it works

This storage unit flood detector uses the sensor to constantly make sure your stored belongings are not destroyed by water.

If moisture level crosses a predefined threshold, it makes a sound to indicate a warning.

Optionally, all data can be stored using the Intel® IoT Examples Datastore or an MQTT server running in your own Microsoft Azure\*, IBM Bluemix\*, or AWS\* account.

## Hardware requirements

Grove\* Home Automation Kit containing:

1. Intel® Edison board with an Arduino\* breakout board
2. Grove Base Shield V2
3. [Grove Moisture Sensor](http://iotdk.intel.com/docs/master/upm/node/classes/grovemoisture.html)
4. [Grove Speaker](http://iotdk.intel.com/docs/master/upm/node/classes/grovespeaker.html)

DFRobot\* Starter Kit for Intel® Edison platform, containing:

1. Intel® Edison module with an Arduino\* breakout board
2. [Moisture Sensor](http://www.dfrobot.com/index.php?route=product/product&product_id=599)
3. [Buzzer](http://www.dfrobot.com/index.php?route=product/product&product_id=84)
4. [I/O Expansion Shield](http://www.dfrobot.com/index.php?route=product/product&product_id=1009)

## Software requirements

1. [Intel® System Studio (Eclipse IDE for C/C++ and Java\* development)](https://software.intel.com/en-us/node/672439)
2. Microsoft Azure\*, IBM Bluemix\*, or AWS\* account (optional)

### How to set up

This sample is already one of the IoT examples included in Intel® System Studio. To start using it, follow these steps:

1. From the main menu, select **Intel® IoT > Import IoT Examples**.<br>
![](./../../images/cpp/import-iot-examples.png)
2. Expand the tree view for **C++ > How To Code Samples > Storage Unit Flood Detector** and click **Import Example**.<br>
![](./../../images/cpp/click-how-to-code-samples.png)
3. Select your developer board from the selection window then select **Next**.<br>
![](./../../images/cpp/select-board.png)
4. Select **Intel® IoT C/C++ project** from the Select a project type window then click **Next**.<br>
![](./../../images/cpp/select-project-type.png)
5. Select **Yocto** from the Selct target OS dropdown menu then click **Next**.<br>
![](./../../images/cpp/select-os.png)
6. The next tab will ask for connection name and target name. If you do not know these click **Search Target**.<br>
![](./../../images/cpp/search-target.png)
7. Select your Edison from the dropdown list. Select **OK**.<br>
![](./../../images/cpp/click-how-to-code-samples.png)
8. Your connection name and target name should be filled in. Select **Finish**.<br>
![](./../../images/cpp/finish-target.png)
9. A new window will open for you and you will need to choose a name for your project and click **Next**.<br>
![](./../../images/cpp/enter-project-name.png)
10. Your project source files will now be available on the on the upper left of your IDE by default.<br>
![](./../../images/cpp/project-src-imported.png)

### Connecting the Grove\* sensors

You need to have a Grove\* Base Shield V2 connected to an Arduino\* compatible breakout board to plug all the Grove devices into the Grove Base Shield V2. Make sure you have the tiny VCC switch on the Grove Base Shield V2 set to **5V**.

1. Plug one end of a Grove cable into the Grove Moisture Sensor, and connect the other end to the A0 port on the Grove Base Shield V2.<br>
![](./../../images/js/flood-detect.jpg)
2. Plug one end of a Grove cable into the Grove\* Speaker, and connect the other end to the D5 port on the Grove\* Base Shield V2.

### Connecting the DFRobot\* sensors

![](./../../images/js/flood-detect-dfrobot.jpg)

You need to have a I/O Expansion Shield connected to an Arduino\* compatible breakout board to plug all the DFRobot\* devices into the I/O Expansion Shield.

1. Plug one end of a DFRobot\* cable into the Moisture Sensor, and connect the other end to the A3 port on the I/O Expansion Shield.

2. Plug one end of a DFRobot\* cable into the Buzzer, and connect the other end to the A1 port on the I/O Expansion Shield.

### Intel® Edison board setup

This example uses the **restclient-cpp** library to perform REST calls to the remote data server. The code can be found in the **lib** directory. The **restclient-cpp** library requires the **libcurl** package, which is already installed on the Intel® Edison board by default.

### Data store server setup

Optionally, you can store the data generated by this sample program in a back-end database deployed using Microsoft Azure\*, IBM Bluemix\*, or IBM, along with Node.js\*, and a Redis\* data store.

For information on how to set up your own cloud data server, go to:

[https://github.com/intel-iot-devkit/intel-iot-examples-datastore](https://github.com/intel-iot-devkit/intel-iot-examples-datastore)

### MQTT server setup

You can also optionally store the data generated by this sample program using [MQTT](http://mqtt.org/), a Machine To Machine messaging server. You can use MQTT to connect to Microsoft Azure\*, IBM Bluemix\*, or AWS\*.

For information on how to connect to your own cloud MQTT messaging server, go to:

[https://github.com/intel-iot-devkit/intel-iot-examples-mqtt](https://github.com/intel-iot-devkit/intel-iot-examples-mqtt)

## Configuring the example for your hardware kit

To configure the example for the specific hardware kit that you are using, either Grove\* or DFRobot\*:

1. From the main menu, select **Project > Properties** dialog box is displayed.
![](./../../images/cpp/click-project-properties.png)
2. Expand the section **C/C++ General**. <br>Click on the **Paths and Symbols** sub-section, and click on the **Symbols** tab.
![](./../../images/cpp/click-gen-path-symbols.png)
3. Now click on **GNU C++**, and click on the **Add** button.
![](./../../images/cpp/click-gnupp-add.png)
4. In the **Name** field, enter "INTEL_IOT_KIT". In the **Value** field, enter either "GROVEKIT" (this is the default) or "DFROBOTKIT", depending on which hardware kit you wish to use.
![](./../../images/cpp/add-name-and-var.png)
5. Your new name symbol and value will now be displayed. Click **OK**.
![](./../../images/cpp/name-var-ok.png)
6. Another dialog box will appear asking to rebuild project. Click **OK**.
![](./../../images/cpp/path-symbol-rebuild-ok.png)

### Connecting your Intel® Edison board or Intel® IoT Gateway to Intel® System Studio

1. On the **Target SSH Connections** tab, right-click your device and select **Connect**.<br>
![](./../../images/cpp/cpp-connection-eclipse-ide-win4.png)

If prompted for the username and password, the username is **root** and the password is whatever you specified when configuring the Intel® Edison board.

### Intel® IoT Gateway setup

You can run this example using an Intel® IoT Gateway connected to an Arduino 101\* (branded Genuino 101\* outside the U.S.).

Make sure your Intel® IoT Gateway is setup using Intel® IoT Gateway Software Suite, by following the directions on the web site here:

https://software.intel.com/en-us/getting-started-with-intel-iot-gateways-and-iotdk

The Arduino 101\* (branded Genuino 101\* outside the U.S.) needs to have the Firmata\* firmware installed. If you have IMRAA installed on your gateway, this will be done automatically. Otherwise, install the StandardFirmata or ConfigurableFirmata sketch manually onto your Arduino 101\* (branded Genuino 101\* outside the U.S.).

### Running the example with the cloud server

To run the example with the optional backend data store, you need to set the `SERVER` and `AUTH_TOKEN` environment variables. You can do this in Intel® System Studio
 as follows:

1. From the **Run** menu, select **Run Configurations**.<br> The **Run Configurations** dialog box is displayed.
2. Under **C/C++ Remote Application**, click **doorbell**.<br> This displays the information for the application.
3. In the **Commands to execute before application** field, add the following environment variables, except use the server and authentication token that correspond to your own setup:<br>

        chmod 755 /tmp/flood-detect;export API_KEY="YOURKEY"; export SERVER="http://intel-examples.azurewebsites.net/counter/logger/flood-detect"; export AUTH_TOKEN="YOURTOKEN"

4. Click **Apply** to save your new environment variables.

Now when you run your program using the **Run** button, it should be able to call your server to save the data right from the Intel® Edison board or Intel® IoT Gateway.

### Running the code on the Intel® Edison board or Intel® IoT Gateway

When you're ready to run the example, click **Run** at the top menu bar in Intel® System Studio
.<br>
![](./../../images/cpp/cpp-run-eclipse.png)

This compiles the program using the Cross G++ Compiler, links it using the Cross G++ Linker, transfers the binary to the Intel® Edison board or Intel® IoT Gateway, and then executes it on the board or Intel® IoT Gateway itself.

After running the program, you should see output similar to the one in the image below.<br>
![](./../../images/cpp/cpp-run-eclipse-successful-build.png)

Then you get output from the sensor in the console telling you if it is dry, moist, or wet.

When the sensor detects enough moisture, it sends a signal to the server; the console output informs you of this.

IMPORTANT NOTICE: This software is sample software. It is not designed or intended for use in any medical, life-saving or life-sustaining systems, transportation systems, nuclear systems, or for any other mission-critical application in which the failure of the system could lead to critical injury or death. The software may not be fully tested and may contain bugs or errors; it may not be intended or suitable for commercial release. No regulatory approvals for the software have been obtained, and therefore software may not be certified for use in certain countries or environments.
