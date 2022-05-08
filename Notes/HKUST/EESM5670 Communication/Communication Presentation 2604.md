Communication Presentation 26/04

# Page2: data

- Nowdays, we all surrounded by countless  amout of data, and even though, the volume of data created worldwide are not stopping,  
- SLIDES

- Also it is predicted that by the end of 2025, there will be 181 zetabytes(10<sup>21</sup> bytes ) data worldwide.

- How do we crunch so much data?

# Page 4: cloud datacenters 

- First, let’s take a look inside the datacenter. The smallest computing unit is the server, and we put 20 - 40 servers together inside a rack, and all the servers inside the rack are connected to the cluster switch, usually the cluster switch are hierarchical, for example, it may consists of a lot of spine switch and leaf switch. so we can connect multiple rack together, then form a cell. And a data center may contains multiple cells. the reanson why we use multiple cell is to provide fault-torllerance in case of power-off.
- ~~typically, A cell may contain 2,000 machines, and a datacenter may contains 10,000 machines.~~

# Page5 : Network room 

- And Network room is a important facility in datacenter. In many cases, communication is bottel neck. That’s why modern datacenter usually build high-performance datacenter network to connect all the server they have.

# Page 6: What is a cloud?

- with all these  powerful computing resources, lets’ see what is cloud all about

- SLIDES
- Nowdays, we often consider computing as the 5th utility after water, electricity, gas, and telephony). Because applications and computing resources are delivered as a service over the internet. and the service is not only easy to acquire, but also a metered service, which means how much you use, how much you pay.

# Page 7: cloud service models

- So, what services can a cloud provide? There are several service models including Iaas, Paas, Saas,and others. To explain it, let’s first take a look at cloud computing stack

# Page8: cloud computing stack

- When we want to build a cloud computing system, we need to concentrate on different layers, we call these layers a computing stack. 
- At the bottom is the hardware layer, you need to decide what kind of hardwares including servers and storage network  you want use 
- and on top of that, you may have a virtulization layer. Because you don’t want users to have direct access to the hardware, you only want to let cloud users to use some virtual resources, and There are multiple virtulization tech you can choose
- once the virtulization is done, you can build some software infrastructure on top of that, this can allow users to access the virtulized resources through some infrastructure services
- on top of the instructure, the developers can only get computing resources in the form of virtual machines or containers, over there, we can build some computing platforms , such as a tensorflow framework, java environment, so developers can work on and deploy their applications on the platform. 
- Finally, is cloud applications

# Page 9: Iaas 

- SLIDES
- Netflix rents thousands of servers, terabytes of storage from Amazon Web Services (AWS)
- Develop and deploy specialized software for transcoding, storage, streaming, analytics, etc. on top of it
- Is able to support tens of millions of connected devices, used by 40+ million users from 40+ countries

# Page 10: Paas

- SLIDES
- Developers can create specific applications for the Facebook platform using proprietary APIs and make that application available to any Facebook user.

# Page 12: Seperation

- maintaining hardware is Tedias  Why people want to go to the cloud
- tradeoff between flexibility and customization 