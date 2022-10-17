ELECTRICAL DESIGN AND FABRICATION
LORA MESH CLOUD FOR ANALOG SENSORS
ATMEGA 328P TQFP

It is based on ATMega328 tqfp microprocessor. ICSP programming is need to load the bootloader and software to the tqfp chip.
 ![image](https://user-images.githubusercontent.com/46260701/196164576-82d13a04-0416-456a-9f12-3150f9867421.png)


 V-USB is used for software-only implementation of a low-speed USB device for Atmel’s AVR® microcontrollers, making it possible to build USB hardware with almost any AVR® microcontroller, not requiring any additional chip. Operating the AVR at higher voltages exceeds the common mode range of many USB chips. Therefore, a voltage regulator from 5v to 3v is needed. If there’s need to run the AVR at 5 V, add 3.6 V zener diodes at D+ and D- to limit the voltage.
 Advantages over Microcontrollers with USB Hardware
o	Standard AVR controllers are usually easier to obtain.
o	Most of the controllers with USB support are only available in SMD, which is almost impossible to handle for hobbyists.
o	V-USB comes with a free shared Vendor- / Product-ID pair.
o	A good free ANSI-C compiler (GNU gcc) and a free development system for Windows (WinAVR) are available for AVR.
o	AVR controllers are faster than most of the controllers with integrated USB and cost less.
o	Stand-alone operation: Some of the USB controllers download their firmware from the host computer into RAM. They don’t work without connection to the host.
o	AVR controllers have on-chip EEPROM.
Advantages over separate USB Peripheral
o	No additional cost.
o	No additional hardware complexity: simpler PCB, less failures.
o	No additional power consumption when USB is disconnected. This may be relevant for battery powered devices.
o	More freedom in the choice of USB descriptors.
o	V-USB comes with a free shared Vendor- / Product-ID pair.
o	Little hardware resources used: only two to three I/O pins.
Advantages over other Firmware-Only Implementations
o	All customizable code written in ANSI-C and thus easier to maintain.
o	Modular concept: easier to integrate into existing designs.
o	Slightly smaller code size in spite of high level language modules.
o	Faster: All encoding/decoding (USB requires NRZI coding and bit stuffing) is done in real-time, not in the main loop after storing away the raw data stream.
o	More endpoints, USB descriptors can be better customized.
o	V-USB comes with a free shared Vendor- / Product-ID pair.
o	The level of standards conformance is documented (description of limitations and potential problems).
o	Licensed under the terms of the GNU General Public License or alternatively under a commercial license.
 
![image](https://user-images.githubusercontent.com/46260701/196164668-2f0eab95-0634-46b0-89b6-404eacf8b213.png)

RFM95W LORA MODULE
LoRa (“long range”) radio technology. It is intended for reliable communication of small amounts of data over long distances (several kilometers). It’s also geared toward low power applications.
Mesh networking of LoRa nodes. Mesh networking is a network topology where nodes communicate with one another either directly (if they are in range) or indirectly via intermediate nodes. For example, if node 1 wants to send a message to node 2, but is too far away from node 2, the message will automatically be routed via an intermediate node that is in range, say Node 3. 
The discovery of the route from 1 to 2 is handled by a mesh networking layer — your application code doesn’t need to know anything about the routing. With mesh networking, LoRa nodes can be spread out across a further distance but can still communicate with one another as long as there is some connectivity between nodes in the mesh. Every node can talk to every other node, even though the network is only partially connected.
The Radiohead library will be used in this project, because it includes an implementation of mesh networking.
Using test network #3 which is defined in the library, that is, nodes 1 and 4 cannot communicate with one another directly, and nodes 2 and 3 cannot communicate with one another directly.
Each node attempts to communicate with every other node in the network, and in the process it keeps track of a routing table that describes which nodes it can talk to directly and which nodes that messages get routed through when there is no direct connection available. It also keeps track of the signal strength that it “hears” from a node when it communicates with it directly. The result is that each node has a data structure with this info.
Example of routing table (expressed in JSON) for node 2:
{"2": [{"n":1,"r”: -68}, {"n":255,"r":0}, {"n":1,"r":0}, {"n":0,"r":0}]}
The data has an array of 4 records, one for each node in the network. The 4 records above represent the routing info for this node (2) communicating with nodes 1, 2, 3, and 4 respectively. Each record has two properties. Property “n” is the identity of the node that node 2 must talk to in order to communicate with the node in this position of the table. Record number 1 {"n":1,"r”: -68} means that node 2 can talk to node 1 via node 1. That is, it has successfully communicated directly with node 1 and the signal strength indicated by the “r” property is -68 dBm.

Record 2 {"n":255,"r":0} has an “n” value of 255 which means “self”, so we can ignore this record. Record 3 {"n":1,"r":0} means that node 2 must communicate with node 3 via node 1 because there is no direct communication (which is why the RSSI value is 0). Record 4 {"n":0,"r":0} has a “n” property of 0 which means that node 2 has not yet discovered a way to talk to node 4. This may because it has not tried yet, or perhaps node 4 has dropped out of the network and nobody can find it.
In order to display the network in a web page, we need to get all the routing information from each node. One of the LoRa nodes in my network (node 1) is connected to the Internet
 ![image](https://user-images.githubusercontent.com/46260701/196164752-52224102-f3c7-4668-b56b-a2b41c687aae.png)

There is transistor as switch if you want to regulate work of LoRa module (RFM95W) with it. When you give signal from digital pin, it will turn on or off
Real Time Clock DS3232
RTC is based on DS3231 chip and can be used for setting alarm for wakeup time of board. It is connected to D2 pin so you can interrupt microprocessor. It is great if you want change wake up intervals from distance. It is possible with downlink messages from TTN server.
 ![image](https://user-images.githubusercontent.com/46260701/196164786-590e3b08-2d87-4550-aba4-a7a3583fc1be.png)

ESP32 WROOM 32D
The NodeMCU is great for connecting cloud and will be used to send mqtt messages to a TTN server. On nodemcu side we need to receive the messages sent by Arduino over serial. It is powered by 3V.
Arduino will send the messages in JSON format
A 3.3V to 5V logic level shifter with 3.3V for the node MCU board and 5V for the atmega 328p allows for the software serial communication between the two IC’s
 ![image](https://user-images.githubusercontent.com/46260701/196164856-84c65567-ade0-40c6-a031-259319b83d3c.png)

 
 
 
