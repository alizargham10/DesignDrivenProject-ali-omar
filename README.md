## **1. Introduction**
The aim of this project is real-time monitoring of noise levels at a construction site for improved implementation of administrative control methods. The exposure to high noise level has short- and long-term effects on the physical and mental well-being of both the workers and the residents within the vicinity of construction sites, which is our problem statement in this project. The microphone of the smartphone has been used as a noise sensor, while its GPS is used to locate the workers exposed to the noise in-situ, and eventually Noise Perimeter Zone (NPZ) can be generated. The data is then streamed live on remotely accessible digital dashboard using the MQTT protocol. This noise data can be analysed to plan work activities in a way which will reduce the worker's frequent exposure to high noise levels. This IoT project shall provide noise real-time data with generated maps and automated notifications (SMS) to the user in such ease and economy yet with relatively adequate precision and reliability.

![Construction noise](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/csm_PR019-standard-construction-safety_843b927ee9.jpg)

Figure 1

## **2 Installations**
### **2.1 Pre-requisites**
---
#### The prerequisites to run this repository are as follows:
1. Node Sensor Free android app.
2. Node-Red Visual programming. 
---
### **2.1.1 Sensor Node Free App**
---
#### Node sensor free is an android app which allows to convert smartphone into a sensor node for wireless sensor network. Sensor node makes use of smartphone's amazing sensors and streams them to a personal computer in real time through MQTT protocol.
###  **Requirements**
 1. An android phone with android 5.0 or above.
 2. Access to location (GPS precise location), storage and microphone.
 3. Network connection.

 ![Node Sensor Free](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot_2022-01-27_114755.png)

 Figure 2.1
### **Step 1.**
#### Download Node Sensor Free app from google play store.
### **Step 2.**
####   Stream data using MQTT protocol.
---

 ### **2.1.2 Node-Red**
 ---
 #### Node-Red is free, JavaScript-based server and web GUI for wiring together hardware devices.
### **Requirements**
#### 1. Operating system i.e. Windows, macOS or Raspberry pi 3 or 4.
#### 2.Network connection.
### **Step 1. Install Node.js**
#### Download the latest 14.x LTS version of Node.js from the official [Node.js Home page](https://nodejs.org/en/)

Once installed, open a command prompt and run the following command to ensure Node.js and npm are installed correctly.

![You should receive output that looks similar to following image](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot_2022-01-27_122045.png)

Figure 2.2 

### **Step 2. Install Node-Red**
#### Installing Node-RED as a global module adds the command node-red to your system path. Execute the following at the command prompt:
npm install -g --unsafe-perm node-red

### **Step 3. Run Node-Red**
Once installed, the simple way to run Node-RED is to use the node-red command in a command prompt. If you have installed Node-RED as a global npm package, you can use the node-red command:
C:>node-red
### **Step 4. Manage Palette**
After running node-red go to the User Settings and choose Palette to install following nodes required to run this Repo:
#### 1. node-red-dashboard
#### 2. node-red-contrib-chart-image
#### 3. node-red-contrib-web-worldmap
#### 4. node-red-node-sqlite
#### 5. node-red-node-twilio


### **Step 5. Node-Red Dashboard**
GUI for real time monitoring can be accessed from the Dashboard

click on the triangle icon then click on the dashboard as shown in the image below

![Dasboard](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot_2022-02-06_202205.png)  

Figure 2.3

In dashboard window click on the arrow button as highlighted in the image below 

![GUI Icon](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot_2022-02-06_202508.png)

Figure 2.4
 
 A new tab will open in the browser. Now you can monitor the real-time noise data.
 
 Maps can be accessed from menu 
 1. Click on the menu icon at the top left corner of the screen 
 2. Click on the GPS Tracker 

## **3 Methodology**
## **3.1 Introduction** 
When it comes to the methodology of how the project was implemented, it is rather convenient at this point to highlight the fact that all the work that has been done was a result of an intensive academic research on controlling construction noise. The reader of this Read Me file may refer to the References section at the end of this file

 
### **3.2 Technical Background**
The Laborers’ Health and Safety Fund of North America classifies solutions to construction noise into three main control methods. Engineering Control refers to the equipment or the work area to make it quieter. Examples of engineering controls are: substituting existing equipment with quieter equipment; retro-fitting existing equipment with damping materials, mufflers, or enclosures; erecting barriers; and maintenance. Personal Protective Equipment (PPE) is the second noise control solution. Earplugs are the typical PPE given to workers to reduce their exposure to noise. Earplugs are the control of last resort and should only be provided when other means of noise controls are infeasible. As a general rule, workers should be using earplugs whenever they are exposed to noise levels of 85 dB (A) or when they have to shout in order to communicate. Last but not least are the administrative control methods. These are management decisions on work activities, work rotation and work load to reduce workers’ exposure to high noise levels. Typical management decisions that reduce worker exposures to noise are: moving workers away from the noise source; restricting access to areas; rotating workers performing noisy tasks; and shutting down noisy equipment when not needed.
It is obvious that the traditional approach is to attack the source of the noise through redesign or modification of the machinery, equipment or surrounding work area. Engineering controls, when feasible and properly applied, is the approach of choice. However, the cost and implementation process are considerations. Therefore, integrating IoT concepts and automation advancements to the administrative control seems most convenient solution to the construction noise problem.

 ### **3.2.1 Plotting Decibel vs. Time Graph(s)**
Sound Level Meters (SLM) measures the sound level in an environment by calculating the frequency weighted pressure of the sound waves which travel through the air from its source. The units of the sound intensity calculated are called decibels. Electronic circuits within the sound meter amplify and filter the sound picked up from the microphone attached to it and produce accurate sound level readings. The sound intensity is calculated using a logarithm based algorithm. The sound intensity is represented by the power of 10 which is expressed as a multiple of the hearing intensity. The following is the standard equation (Eq. (1)) to calculate the sound intensity in decibels.

![Eq 1](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot%202022-02-07%20141755.png)

Figure 3.1

(Decibels equals log based 10 times 10,000 times initial intensity divided by initial intensity).
Noise data in decibels are then live-streamed by Noise Free Sensor App via MQTT protocol and can be imported to hivemq.com, which is a free public broker, by setting a connection and then a subscription with valid ID set by the user. An example is shown in figure 3.2 below:

![Fig 3.2](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/sound%20capture.PNG)

Figure 3.2: Public Broker HiveMQ used to stream data

    

Node-Red provides both an MQTT subscribe (input) and publish (output) node. The configuration for these nodes are almost identical as the main part of the configuration concerns the actual client connection. To connect to an MQTT broker or server we need to know the Broker IP address or name, and the port that it is using (default 1883). 

![Fig 3.3](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/5.png)

Figure 3.3: MQTT In Node.

By double clicking on the node and then adding the link for our mqtt broker and Topic relative to the Base Topic we set on Sensor Free Node App, we are now ready to import the data into NodeRed, as can be shown in Figures 3.3 and 3.4 below:

![Fig 3.4](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/1.png)

Figure 3.4: MQTT in node used to import live data into Node Red

![Fig 3.5](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/2.jpg)

 Figure 3.5 : Streaming live Data by MQTT on Node Sensor Free Mobile App

 A Node-RED graphing package contains a data source node which handles historical data and live data streams, and a hackable visualization application designed to connect to the data source nodes. By connecting “omarNodeRed2/noise/decibels”, which is the MQTT in we set earlier, to the “dB vs Time Phone 2”, we are now able to plot decibel vs. Time graphs. This process can be demonstrated in Figure 4.5. It is to be noted that we set the MQTT in node to import only decibel from the noise sensor, as can be observed by the reader.

 ![Fig 3.6](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/3.png)

 Figure 3.6: Configuration of Nodes in the flow for generating dB vs. Time graphs

Eventually the graph for Decibels vs. Time can be plotted as shown in Figure 3.7 Below:


 ![Fig 3.7](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/9.jpg)

### **3.2.2 Plotting Intensity vs. Time Graph(s)**

The range of energy from the lowest sound that can be heard to a sound so loud that is produces pain rather than the sensation of hearing is so large that an exponential scale is used. The lowest possible sound that can be heard is called the threshold of hearing. The sound level at the threshold of hearing is:
![Threshold of hearing](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot%202022-02-07%20142227.png)

Combining Equation (2) into Equation (1) and solving for Intensity, we obtain;

![Eq 2](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot%202022-02-07%20145033.png)

To get the value of intensity we used the formula given in eq.2, The obtained values were very small and it was very difficult to plot them on a graph. Another function used to take the logarithm of the value obtained from eq.2. With this technique we successfully plotted the intensity vs time graph.

Graph for Intensity vs. Time can then be plotted as shown in figure 3.8 below:

![Fig 3.8](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot%202022-02-07%20181332.png)

### **3.2.3 Plotting Voltage Ratio Vs. Time Graph(s)**
The microphone changes the sound waves from your voice into electrical signals that are sent to the audio amplifier of the radio components. A sound pressure increases with increased loudness. In Europe the output voltage is directly classified as microphone’s sensitivity and its unit is mV/Pa (milli-volt per pascal). The sensitivity changes with input voltage. Voltage ratio also known as gain factor can be calculate using the formula 


![Voltage ratio formula](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot%202022-02-07%20150141.png)

![Voltage ratio vs time graph](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot%202022-02-07%20181429.png)

Figure 3.9: Voltage Ratio vs. Time Graphs

### **3.2.4 GPS Noise Tracking**
Today’s noise measurements are mainly carried out by designated officers that collect data in a location of interest for successive analysis and storage, using a sound level meter or similar device. This manual collection method using expensive equipment does not scale as the demand for higher granularity of noise measurements in both time and space increases. Therefore, in this project we rather not install thousands of fixed sensors out in to the environment, but can find out the nature of spatial and temporal variation by using a small and affordable tracked mobile sensors. It is believed that that pervasive computing can ultimately engage people in mass participation environmental campaigns, raising awareness of environmental issues, supporting education, activism and democracy, and delivering environmental data on a scale never before possible. Mobile computing has the potential to allow both experts and the public to collect and understand environmental data such as air pollutants in urban areas with an accuracy and cost-efficiency that current noise assessment procedures cannot afford.
It is then the settled a need to generate interactive maps which can allow the user to track the construction noise at its source. The use of smart phone will also allow to get the real time position of the noise source by using GPS. The GPS can give the location with the precision of 10 m. This will it make very easy to pin point the noise source since on construction site different machines are being used at the same time. By the acquisition of real time location data, noise management will become very efficient. Different nodes such as dashboard, contrib-chart-image, contrib-web-worldmap, Sqlite and Twilio helped to get GPS location in Node Red. In the GUI of Node Red phone location can be easily scene on the map.
The GPS Tracking flow was a progress made by “nygma2004” and was published the NodeRed Flows Library. This GPS tracking solution was developed mainly to work with a custom Android app which sends GSP data over email. This flow reads GPS tracks from the attachment of the email and stores it in SQL database and displays it in a map in the Dashboard. The user can store logs for multiple users, display data based on date, split the logs to different tracks.
However, since we imported our live data by means of MQTT streaming protocol, this flow wouldn’t work to our purpose. It is then become necessary to change the code so as to import our Latitude and Longitude data via MQTT Broker and not by Gmail which was intended originally by the Flow’s developer.

We then made a short development in the code to flow.get “lat” and “lon”, refering to latitude and longitude, respectively. Moreover line 4 gets the values for decibels and displays them on the map when the user right clicks on the circle denoting the source of noise’s location. This circle was set in line 5 with designated radius and colour as shown below:

![function node](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/4.png)

Then we made it possible to generate a Map on Node Red and to track multiple users in the same time with such ease and clarity.

![Map](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot%202022-02-04%20124212.png)

Figure 3.10

### **3.3 Construction Noise Management**
## **3.3.1 Introduction**
Despite the extensive work done in the 1970s and 1980s, Noise Induced Hearing Loss is still a pervasive problem (Federal Register, 1996). Therefore, MSHA has published new Health Standards for Occupational Noise Exposure (Federal Register, 1999). The new noise standard became effective Sept. 13, 2000. One of the changes was the adoption of a provision similar to OSHA’s Hearing Conservation Amendment, where a miner must be enrolled in a hearing-conservation program (HCP) if his full-shift noise exposure is at or above the action level of 85 dBA TWA8 or 50% dose.
This project’s approach along with an understanding of implementation procedures and evaluation methods will hopefully lead to increased acceptance and implementation of administrative controls and, consequently, a reduction of worker noise exposure.

### **3.3.2 Implementation and Evaluation Method**

The implementation and evaluation of an administrative control requires a lot of quality data to understand how the workers are exposed to high noise, what are the tasks which can exposed workers to high noise levels since their exposures to these levels will be very harmful for their health. To accurately identify the workers who are exposed to dangerous noise levels very precise data is required. The use of smart phone as a noise sensor can provide this data in real-time which will help in taking the decisions efficiently.  Noise levels exposures can be calculated by using the formula:

![Dose formula](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/Screenshot%202022-02-07%20151717.png)

Where,
D is the noise dose (%).

Cn is the exposure time at a particular sound level (hours).

Tn is the reference duration of exposure at the measured sound level (hours).

This formula was added inside a function node, while corresponding change nodes were added and explained in the below figure.

![Fig 3.11](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/7.png)

Figure 3.11

In the function node 'db' variable is created as an array. The values have been assigned to it as db.1, db.2, and db.3. To assign values to these numbers we are calling 'flow.get' method because get method is used to return the value of variable name.

'Flow.set' method is called and 'db' variable is passed as a parameter because set method is used to take a parameter and assigns to it the name of variable.

'msg.payload' is created and initial value of '0' has been assigned to it. Meanwhile 'for' loop is used to calculate the value of an array

The value of 'msg.payload' increments each time to calculate three values, loop will end after calculating these values. The final value is being calculated in the percentage using a string. 




![Function dose](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/8.png)

### **3.4 Functionality**

The project’s aim is unique due to the fact that not only the sound level within the perimeter of construction site environment is measured but also provides the sound level of the neighbouring environment to the user. The accessibility to the monitoring display where the user can easily access the data along with respective graphs, charts, and map serves to facilitate the noise control process with such ease and more precise results than other traditional methods. The phone in this case serves as a portable sensor station that yields precise measurements as a function of the worker’s distance from the source of noise. Furthermore, it has not been implemented before an automated accurate calculation for the dose of exposure formula with regards to the Implementation and Evaluation method in accordance with the OSHA’s prescriptions. This allows the user to easily target each worker and monitor their exposure and thus work rotations and scheduling can be done accordingly with no need to calculate the dose for each worker every time. 

### **3.5 Method of Testing**
Throughout the development process, the system was improved in an iterative manner. Users were asked to use the system in a variety of locations. One user was asked to stand beside a Front-End Loader while hauling earth materials and was given a name phone 12 while the other was at a distance further and was called phone 11. Data for noise in decibels were then collected and plotted in the below graph.


![db vs time graph](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/co-relation.png)

Figure 3.12

As can be seen from the two graphs above, we can build a correlation between the two graphs where the former (phone 12) represents neighbourhood ambient noise exposure on a citizen while the latter (phone 11) represents noise exposure of a worker who is operating the machine. 
Overall, we can divide both graphs into 3 main time intervals: region 1 which denotes arbitrary traffic noise, region 2 which denotes ambient measurement when there is no use of heavy noisy construction machineries, and region 3 which denotes when the loader started generating noise.
During region 2, the ambient noise reading for the neighbourhood was at a much lower average than when the machine started operating between the times 17:07:31 and 17:07:46 in region 2. This disturbance can be seen from the area above the yellow line and thus correlation is built between the two graphs.
Furthermore, the value reading we obtained for the loader (approximately 85 Decibels from graph for phone 11) is very close to the value range for a Front-End Loader as per given in the table below. This proves how precise our algorithm works and achieves better results. This was made possible after we tuned the parameters and algorithmic logic by means of mathematical models to improve its accuracy, rather than just relying on the values obtained by Node Sensor Application.

[Coherence obtained between obtained value and literature](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/reference%20picture.png)

Figure 3.13 shows coherence between the value we obtained and the one in the literature

## **4. References**

### **4.1 Figures**

[Figure 1:](https://www.ajg.com/uk/news-and-insights/2018/june/counterfeit-personal-protective-equipment-in-the-construction-sector/)

[Figure: 2.1](https://play.google.com/store/apps/details?id=com.mscino.sensornode&hl=en&gl=US)

[Figure 2.2](https://nodered.org/docs/getting-started/windows)

[Figure 3.2](http://www.hivemq.com/demos/websocket-client/)

### **4.2 Research papers**

[A Short Review of Constructing Noise Map
using Crowdsensing Technology](https://www.researchgate.net/publication/327864920_A_Short_Review_of_Constructing_Noise_Map_Using_Crowdsensing_Technology_13th_International_Conference_CollaborateCom_2017_Edinburgh_UK_December_11-13_2017_Proceedings)

[Construction Noise and Vibration
Management Plan](https://consult.environment-agency.gov.uk/engagement/bostonbarriertwao/results/appendix-1---max-forni_s-proof-of-evidence--construction-noise-and-vibration-management-plan-.pdf)

[Controlling Noise on Construction Sites](https://www.lhsfna.org/LHSFNA/assets/File/bpguide%202014.pdf)

[Administrative controls for reducing
worker noise exposures](https://www.cdc.gov/niosh/mining/UserFiles/works/pdfs/acfrw.pdf)


[NoiseSPY: A Real-Time Mobile Phone Platform for Urban Noise Monitoring and Mapping](https://www.researchgate.net/publication/220134386_NoiseSPY_A_Real-Time_Mobile_Phone_Platform_for_Urban_Noise_Monitoring_and_Mapping)

[Sound decibels levels](https://www.internet4classrooms.com/sound_decibel.htm)

[Noise Exposure Calculator](https://www.noisemeters.com/apps/exposure-calculator/)

[Intensity and the Decibel Scale](https://www.physicsclassroom.com/class/sound/Lesson-2/Intensity-and-the-Decibel-Scale)

[DEVELOPMENT OF WIRELESS SENSORNETWORKUSINGBLUETOOTH LOW ENERGY (BLE) FORCONSTRUCTIONNOISE MONITORING](https://cdt.sensors.cam.ac.uk/system/files/documents/s2is-hughes-2015.pdf)

[DEVELOPMENT OF WIRELESS SENSORNETWORKUSINGBLUETOOTH LOW ENERGY (BLE) FORCONSTRUCTIONNOISE MONITORING](https://cdt.sensors.cam.ac.uk/system/files/documents/s2is-hughes-2015.pdf)

[Technical Guide for: Noise Control – Engineering Controls, Work Practices, & Administrative Controls](https://oshainfo.gatech.edu/wp-content/uploads/2019/03/Technical%20Guide%20for%20Noise%20Controls.pdf)


[Noise -Frequently](https://www.hsa.ie/eng/Topics/Physical_Agents/Noise/Noise_-_Frequently_Asked_Questions/#high)

---
### **Credits**
Ali Zargham   ali.kazmi@rwth-aachen.de

Omar Aldohami omar.aldohami@rwth-aachen.de