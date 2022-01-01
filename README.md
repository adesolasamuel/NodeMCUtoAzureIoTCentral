# NodeMCUtoAzureIoTCentral
This is a detailed description of how to send data from NodeMCU or ESP8266 to Microsoft Azure IoT Central

How to send data to Microsoft Azure IoT central Using NodeMCU

Link to step by step Video: https://youtu.be/X1aBKd9nJs4 

IoT being an integral part of cloud computing, several cloud vendors make IoT part of the services they render. Also, with the emergence of IoT, there are different platform that makes IoT implementation available even to individuals. In this tutorial, I will be taking you through steps in sending data from NodeMCU, an IoT development platform to Azure IoT Central.
To ensure all necessary things are in place, you will have to set up your computer to communicate with NodeMCU or ESP8266 before you can follow along this tutorial.
In this tutorial, we will be using DHT 11 sensor to send Temperature and Humidity data to Azure IoT Central. 
Materials Needed
1.	NodeMCU or ESP8266
2.	DHT 11 sensor
3.	10K resistor
4.	Personal Computer
5.	Arduino IDE software
6.	Jumper Wires

Step 1: The very first step is to ensure that your PC has been configured to communicate with ESP 8266. If you haven’t did this already, now is the time. Once you have configured your PC, come right back to continue following this tutorial.
Step 2: Hardware Setup: Connect the NodeMCU and the DHT 11 to the breadboard, depending on your model of DHT 11, it can be a 3-pin ready made model or a 4-pin model, in this tutorial, I am using a 3-pin model. If you are using a 3-pin model, connect the VCC to 3V of the NodeMCU, GND of the DHT 11 to GND on the NodeMCU and connect the data pin to Pin 4 of the NodeMCU. If it is 4-pin model you are using, connect Pin 1 of the DHT11 to 3V of the NodeMCU, connect the 10K resistor between pin 1 and pin 2 of the DHT 11, leave pin 3 of the DHT 11 sensor unconnected and connect pin 4 of the DHT 11 to GND on the NodeMCU. Connect the NodeMCU via a USB cable to your computer and you are good to go.

![image](https://user-images.githubusercontent.com/55460620/147842004-aebcd437-7bda-453b-92ab-83779a577a41.png)

 
Step 3: Before writing the code, now is the time to set up Azure cloud platform. First, sign in to your Azure portal. We will be working on IoT central. What you want to do is to use the search bar to search for IoT Central applications, click on IoT Central applications. Here you will click on create new IoT Central application. At the prompts, fill in your application details, under the template section, select custom application. Once you are done filling in the details, click on create after which you can the click on go to resource. Once the IoT application resource opens us, click on the application URL, this will take you to another tab where you will be able to work on the IoT applications.  Every thing we need to do to communicate between our IoT device and the cloud will be done in this tab. If you check the side bar, you will see options like “Devices”, “Dashboard”, “Device Template”, etc.

![image](https://user-images.githubusercontent.com/55460620/147842040-3471fb2b-69c7-4630-bb96-bd7d289000c3.png)
![image](https://user-images.githubusercontent.com/55460620/147842063-c46e1433-3783-417d-bdf9-94b9d5d777c0.png)
![image](https://user-images.githubusercontent.com/55460620/147842064-10495a95-13c3-4088-9bf5-ef5e372eae46.png)
![image](https://user-images.githubusercontent.com/55460620/147842068-ae4fd9a5-148e-4ea6-8330-ed50e78f2cc5.png)
![image](https://user-images.githubusercontent.com/55460620/147842070-045a8878-42cd-4018-82d8-e935e56cfe63.png)


     
Step 4: Let me walk you through our main aim on this tab, we are to create a template or a blueprint for our device, the template will be structured according to the type of data we are expecting from our device. Therefore, what we need to set up first is the device template.

![image](https://user-images.githubusercontent.com/55460620/147842079-6cd26453-00e5-40c5-9747-5448d922a320.png)

 
Step 5: Setting up the device template: From the sidebar, click on “create a device template”, you will be presented will a lot of ready-made templates, feel free to check this out but what we will do in this tutorial is to create a new one. Click on “IoT Device”, give your template a name and select “custom model”. After this, we will “Add capability” to our template, since we are expecting only Temperature and Humidity from our DHT sensor, we will add these two capabilities: Temperature and Humidity, and select “Telemetry” as the Semantic type. After this, click on views and select “Default Views”. You will be presented with how your data will be presented. I will advice you change the Temperature and Humidity to “Last Known Value”. After this click on “Save” and you can go on to publish your template.

![image](https://user-images.githubusercontent.com/55460620/147842089-069b7323-0e42-4d62-8823-b880b05409da.png)
![image](https://user-images.githubusercontent.com/55460620/147842091-397c7a01-e399-4399-ad0a-c9a133d34bc5.png)
![image](https://user-images.githubusercontent.com/55460620/147842093-d7c66a23-dc63-469f-a6a2-e48da4190048.png)
![image](https://user-images.githubusercontent.com/55460620/147842095-c4d48d46-1f7f-430c-8591-f8b657d958da.png)
![image](https://user-images.githubusercontent.com/55460620/147842096-21ef12fe-37ba-456e-81ce-798e44a20913.png)
![image](https://user-images.githubusercontent.com/55460620/147842098-b88a2e8b-8829-4a16-80b4-7a79749157dc.png)
![image](https://user-images.githubusercontent.com/55460620/147842099-b4777a1c-839b-43f6-9289-f77684d535ab.png)

       
Step 6: Setting up the Device: After creating a blueprint for our device through the Device template, our next task is to configure the device. Select the “Devices” option and click on “Create a device”, give your device a name and an ID and select the Device template you just created as the device template. Once this is done, click on the device you just create and click on “Connect” on the left top corner, you will be presented will information you need to connect your NodeMCU to the cloud like the DeviceID, Name, Primary Key and Public Key. Now is the time to write the code.

![image](https://user-images.githubusercontent.com/55460620/147842105-fffa7c2e-9aa7-4f97-bd4c-8338f141a7af.png)
![image](https://user-images.githubusercontent.com/55460620/147842106-21dffb15-d149-4b75-8f54-03161e4df531.png)
![image](https://user-images.githubusercontent.com/55460620/147842107-250a416e-cd25-4e91-8859-97793911a4c1.png)
![image](https://user-images.githubusercontent.com/55460620/147842109-ba5520bd-fadc-4377-8498-2e75abeedbd1.png)

    
Step 7: Writing the Code: I made the link to the code available. Download the code and feel free to edit it to your taste. You will need to provide your network SSID and Password.  You will also see where to insert all your device information, this can be copy and pasted directly into your code. The code can also be edited to send different data depending on your choice.

![image](https://user-images.githubusercontent.com/55460620/147842114-d8fe43e8-becd-43d6-b9ff-5f6a02df858a.png)
![image](https://user-images.githubusercontent.com/55460620/147842115-662597fd-23ac-4752-bff1-a92b59e1f183.png)
![image](https://user-images.githubusercontent.com/55460620/147842116-182857ca-cee2-42db-b80a-0d799b68f733.png)

   
Step 8: Once you are done setting up the code and Azure IoT central, upload the code to the NodeMCU and with a little bit of luck, you will see your Temperature and Humidity displayed in IoT Central. You can also monitor the connection via the Serial Monitor.

![image](https://user-images.githubusercontent.com/55460620/147842124-0ba24d10-5833-479e-a59f-42618ee4a5a0.png)


link to Detailed Video guide:
https://youtu.be/X1aBKd9nJs4


 

