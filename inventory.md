---
layout: post
title: PDR
date: 2016-11-14 12:43:44 +0000
permalink: /PDR/
---

**This document still needs EXTENSIVE edits to be markdown presentable.**





Agricultural Multi-Sensor Nodal Network with Mesh Network Wireless Communication Topology


Client: T. Anthony Choi


PDR Document 


Presented by: 
Daniel Mackowski
Faisal Al-dhorgham
Pierre Balinda 


November 14th, 2016













Executive summary
Ideally, farmers would be able to survey their crops adequately for a low price. However, current satellite surveying methods widely used by farmers are very expensive. To provide a more cost efficient option, Dr. Anthony Choi of the Mercer University School of Engineering (MUSE) has contacted a team of MUSE students to design a multi-sensor nodal network to collect data on soil temperature along with soil moisture and pH levels. The platforms will send this information through a mesh network to the user who will then be able to make informed decisions to cut farm maintenance costs. The MUSE student engineering team is composed of Pierre Balinda, a Computer Engineer, Faisal Al-dhorgham, and Daniel Mackowski, both Electrical Engineers.
The scope of the project was restricted to a proof of concept stage in light of the complexity of design, time limit, and not having a Mechanical Engineer on the team. Focus was given to determining the best alternatives for a low-power microcontroller, wireless communication protocol chip, soil attribute sensors, user interface for data analysis and presentation, and adequate disposable, per-node power supply. The alternatives that met the feasibility criteria and proved to be the most meritorious alternative were the STM32 L4 microcontroller, ZigBee wireless communication protocol chip, Arduino’s Soil Moisture Sensor Hygrometer, SparkFun Electronics’ DS18B20 Waterproof Temperature Sensor, Luster Leaf’s Digital Soil pH Meter, a Web interface for data analysis and presentation, and 3 disposable AA alkaline batteries for a per-node power supply.
Based on the research on the alternatives, the total cost of this stage of the project is expected to be $350. MUSE will cover $300 of this budget. The client is willing to cover any remainder beyond the limit provided by MUSE. The team plans to perform tests to determine sensor reading accuracy, proper transmission of the data through the ZigBee wireless transmission protocol, and proper analysis and display of the data at the user interface. If the client, manager, and technical advisors find these decisions acceptable, the team would like to ask permission to move forward to the build and test phase of this proof of concept project.
Table of Contents
Executive summary	1
Table of Contents	2
List of Figures	3
List of Tables	3
Glossary	4
Introduction	4
Project description	5
Feasibility and merit criteria, specs	6
Microcontroller	7
Feasibility Criteria	7
Merit Criteria	7
Communication protocol chip	8
Feasibility Criteria	8
Merit Criteria	8
Sensors	9
Feasibility Criteria	9
Merit Criteria	9
User interface	9
Feasibility Criteria	9
Merit Criteria	9
Power supply	9
Feasibility Criteria	9
Merit Criteria	10
Design alternatives	10
Microcontroller	10
Communication protocol	11
Sensors	12
User interface	13
Evaluation, selection, and criteria	13
Microcontroller	13
Communication protocol	15
Sensors	16
User interface	18
Design work accomplished	18
Engineering design & analysis	20
Determining the power supply	20
Performance prediction	23
Project schedule	23
Budget	24
Proposed tests	24
Conclusion and Recommendation	25
Acknowledgment	25
References	26
Appendices and Annexes	30
Pseudo-code	30
Gantt chart	31
Bill of Materials	32
Team Resumes	33
List of Figures
Figure 1 STM32 L4 microcontroller
14
Figure 2 Raspberry Pi 3 Model B
14
Figure 3 Microchip Technology MRF24J40MAT-I/RM ZigBee transceiver
15
Figure 4 Arduino Soil Moisture Sensor Hygrometer
16
Figure 5 Sparkfun Electronics’ “DS18B20 Waterproof Temperature Sensor”
17
Figure 6 Luster Leaf’s “Digital Soil pH Meter”
18
Figure 7 Sensor node component general locations
19
Figure 8 Project test site layout
20
List of Tables
Microcontroller features
10
Table 2 Microcontroller feasibility analysis
13
Table 3 Microcontroller merit analysis
13
Table 4 Communication protocol feasibility analysis
15
Table 5 Communication protocol merit analysis
16
Table 6 Sensor node average current consumption calculations for one hour
22
Table 7 Typical alkaline battery life calculation values
22
Table 8 Bill of Materials
24
Glossary
µC: Microcontroller
1WTSSSP: Tempsensing.com’s “1-Wire Temperature Sensor with 1.2 inch Stainless Steel Probe”
A&P app: Analysis & Presentation application
Arduino Hygrometer: Arduino Soil Moisture Sensor Hygrometer
DS18B20: Sparkfun Electronics’ “DS18B20 Waterproof Temperature Sensor”
IC: Integrated Circuit
Luster Leaf: Luster Leaf’s “Digital Soil pH Meter”
Mega: Arduino Mega
MUSE: Mercer University School of Engineering
OS: Operating System
Pi: Raspberry Pi 3 Model B
SFESMS: SparkFun Electronics’ “Soil Moisture Sensor”
TCO:  Technical Communications
Introduction
Ideally, as the world population continues to grow past 7.4 billion, farmers all over the world would be able to keep up with the demand for more, high quality food at affordable prices. However, with the demand steadily increasing, farmers are turning to engineers and scientists for new methods and technologies capable of reducing costs and optimizing crop yield. One of the methods farmers are looking to use to increase the affordability and availability of their produce is by employing technology to ensure soil conditions are optimized for their crops in near real time. Dr. Anthony Choi of MUSE has contacted the MUSE student engineering team composed of Pierre Balinda, a Computer Engineer, Faisal Al-dhorgham, and Daniel Mackowski, both Electrical Engineers, to design a solution to this problem. The team has designed a proof of concept agricultural multi-sensor nodal network to survey and present collected data to farmers to advise them on how to optimize their land for maximum yield at minimum cost.
As the growing demand for affordable produce is nothing new to the agriculture industry, the team conducted research about similar projects on the market or currently in development and found four major smart garden sensors of interest. According to [1], they are the Edyn Garden Sensor, Koubachi Wi-Fi Plant Sensor, Parrot Flower Power, and Oso Technologies Plant Link. Each smart sensor has a plant database that allows them to give proper recommendations to the user about their specific plant’s needs. The team used these devices as models to kickstart the design process.
The Oso Technologies PlantLink costs $80, senses soil moisture, has 50,000 plants in its database, uses a Zigbee signal to transmit data and 2 AAA batteries to power it for over a year. It only has a web interface for the user. The Parrot Flower Power costs $60, senses soil moisture, temperature, sunlight, fertilizer and pesticide levels. It has 7000 plants in its database, uses a Bluetooth signal to transmit data and 1 AAA battery to power for 6 months. The Parrot only has an iOS app in as a user interface.
The Koubachi Wi-Fi Plant Sensor costs $100, senses soil moisture, temperature, and sunlight. It has 800 plants in its database. This sensor uses Wi-Fi to transmit its data and 2 AA batteries that can power it for over a year. The Koubachi sensor offers ample choices to its users when it comes to interfaces as it has an iOS, Android, and Web applications. The Edyn Garden Sensor costs $100, senses soil moisture, temperature, light, fertilizer, pesticide, and humidity levels. It has 5000 plants in its database, uses Wi-Fi to transmit data and a solar powered battery that can last 2.5 years. The Edyn sensor has an iOS and Android app that the user can use as an interface.
Project description
This project requires the design and construction of low-power, agricultural sensor nodes capable of mesh network communication and a software system to analyze and present the data collected from the sensors. The sensors will be selected according to the client’s specifications to measure three required soil attributes of moisture level, temperature, and pH level at three equally separated depths. The nodes will be stationary columns, two feet in length, designed to be driven into the ground. The microcontroller, wireless communicator, and the power supply will be the only above ground, surface level components of each node. The nodes will have housing to protect the circuitry of the sensors, microcontroller, wireless communicator, and power supply from damage. The nodes will be battery powered and will communicate information wirelessly from node to node to transmit soil attribute data packets back to a central station that will run the analysis software. The soil attribute data packets will be created by software in the node microcontrollers and will contain the environmental data along with the location, depth, and, time of the reading from each node. The software will collect these packets to construct graphical views of the data. This will provide the end user with a clear understanding of the data to expedite decision making for maintenance of networked regions. The pseudo code for the sensor node and A&P app software can be seen in Appendix A.
Feasibility and merit criteria, specs
The client gave the following set of specifications for the proof of concept design of the networked nodes:
Microcontroller: low-power
Minimum number of nodes: 3
Minimum number of sensor levels: 3
Minimum power supply duration: one season (six months or 180 days)
Minimum node depth: 2 feet
Node data:
Depth
Location
Time
Soil data: 
Moisture level
pH level
Temperature
Wireless communication protocol: mesh network capable 
The team decided that the following additional specifications were necessary to make engineering decisions for the proof of concept design:
Node spacing: 10m - 40m (33 ft - 130 ft)
Reading frequency: once per hour
The network needed a central station to collect the data from the other nodes and an A&P application for presenting the data to the end user in a clear and concise manner. The central station that will contain A&P application would need to communicate through a wifi communication protocol. The A&P app would need to present the collected information with daily line charts for data from each node and with separate current time graphic displays for each soil data type for the networked area to show the data values on a gradient scale at each of the 3 depths.
