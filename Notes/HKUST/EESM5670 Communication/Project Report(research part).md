Group representative (i.e., the member with the smallest student ID) should submit the 20+ page project report (in .docx or .pdf) for their group here (other group members do not need to submit). Please name the file using the format **group no.-representative name-representative ID, e.g., 00-Xuanyu-12345678**. Please also remember to provide the name and student ID of your group members on the cover page of your report.

The submission deadline is **13th May at 11: 59 pm**.

```toc
```
# Cloud Computing
> XIE, Peihong
> WANG, Zongwei
> JIN, Bowen
## 1. Inrtoduction
### 1.1 Why data matters
If we look at the past and present of computers, we can see how quickly they have evolved, In 1981 Bill Gates said, "640K ought to be enough for anybody." Something unthinkable today. Today everyone produces far more data every day. Today, we're all surrounded by an infinite amount of data, and while the amount of data being created globally hasn't stopped, a Large Hadron Collider generates 40 TB data per second and Boeing Jet Engine creats 10TB operation information every 30 minutes, further, the search index data of google contains 100s billions webpages and is well over 100 petabytes in size.If we look into the whole Internet, it is predicted that the total volume of data or information created, captured, copied, adn consumed worldwide by 2025 will reach 181 zettabytes.
So how do we crunch the massive amount of data? By cloud datacenter
### 1.2 Datacenters
#### 1.2.1 Features:
- There are over 100 thousands os servers worldwide.
- Overall costs of cloud computing worldwide is about billions of dollars
- All the cloud datacenters are geographically distributed
It is estimated that over 94% global workloads was processed indatacenters in 2021
#### 1.2.2 Infrastructure
- The smallest computing unit is the server, and we put 20 - 40 servers together inside a rack, and all the servers inside the rack are connected to the cluster switch, usually the cluster switch are hierarchical, for example, it may consists of a lot of spine switch and leaf switch. so we can connect multiple rack together, then form a cell. And a data center may contains multiple cells. the reanson why we use multiple cell is to provide fault-torllerance in case of power-off.
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132114290.png)
<center style="color:#C0C0C0;text-decoration:underline">datacenter structure</center>
- typically, a cell may contain 2,000 machines, and a datacenter may contains 10,000 machines.
- And Network room is a important facility in datacenter. In many cases, communication is bottel neck. That’s why modern datacenter usually build high-performance datacenter network to connect all the server they have.
 ![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132119018.png)
 <center style="color:#C0C0C0;text-decoration:underline">Network room</center>
- Bsides all the computing hardware needed in a cloud datacenter, The power supply of the data center, the cooling facilities have to be carefully designed.
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132122410.png)
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132122778.png)
 <center style="color:#C0C0C0;text-decoration:underline">Cooling Infrastructure</center>
 
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132206926.png)

![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132123023.png)
 <center style="color:#C0C0C0;text-decoration:underline">Power Infrastructure</center>
 
 

 ###  1.3 What is a cloud
 
 #### 1.3.1 Definition
 A long definition: Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.
 In short, cloud computing is featured as:
 - On-demand computing
 - delivered as a service over the Internet
 - pay-as-you-go pricing


Cloud computing enables users to stop thinking of infrastructure as hardware,Instead, users should think of and use it as software

#### 1.3.2 utility computing
Nowdays, we often consider computing as the 5th utility after water, electricity, gas, and telephony). Because applications and computing resources are delivered as a service over the internet. and the service is not only easy to acquire, but also a metered service, which means how much you use, how much you pay.

### 1.4 Cloud deployment models
#### 1.4.1 Public Cloud
- Providers let clients access the cloud via Internet
- Made. available to the general public
- Such as: Amazon web services, linode, rackspace, windows azure

#### 1.4.2 Private Cloud
- The cloud is used solely by an organization, such as Facebook or HSBC
- May reside in-house or off-premise

private cloud is secure, dedicated infrastructure with the benefits of on-demand provisioning, and it is not burdened by network bandwidth and availability issues and security threats associated with public clouds. Comparing with public cloud, private cloud has greater control, and is more secyrity and resilience.

#### 1.4.3 Hybrid Cloud

- Composed of public clouds and private clouds that remain independent entities, but interoperate using standard or proprietary protocols
- Wildly used by banks, hospitals and goverment

### 1.5 Cloud Service Model
So, what services can a cloud provide? There are several service models including Iaas, Paas, Saas,and others. To explain it, let’s first take a look at cloud computing stack
#### 1.5.1 cloud computing stack
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132146313.png)
 <center style="color:#C0C0C0;text-decoration:underline">Cloud Computing Stack</center>
 

 -  When we want to build a cloud computing system, we need to concentrate on different layers, we call these layers a computing stack. 
- At the bottom is the hardware layer, you need to decide what kind of hardwares including servers and storage network  you want use 
- and on top of that, you may have a virtulization layer. Because you don’t want users to have direct access to the hardware, you only want to let cloud users to use some virtual resources, and There are multiple virtulization tech you can choose
- once the virtulization is done, you can build some software infrastructure on top of that, this can allow users to access the virtulized resources through some infrastructure services
- on top of the instructure, the developers can only get computing resources in the form of virtual machines or containers, over there, we can build some computing platforms , such as a tensorflow framework, java environment, so developers can work on and deploy their applications on the platform. 
- Finally, is cloud applications which is basically used everyday in our dailylife.

#### 1.5.2 cloud service model
##### 1.5.2.1 Infrastructure-as-a-Service(Iaas)
- Providers give you the computing infrastructure made available as a service. You get “bare-metal” machines.
- Providers manage a large pool of resources, and use virtualization to dynamically allocate
-  Customers “rent” these physical resources to customize their own infrastructure
-  Full control of OS, storage, applications, and some networking components (e.g., firewalls)
-  Use case: 
	-  Netflix rents thousands of servers, terabytes of storage from Amazon Web Services (AWS)
	-  Develop and deploy specialized software for transcoding, storage, streaming, analytics, etc. on top of it
	-  Is able to support tens of millions of connected devices, used by 40+ million users from 40+ countries

##### 1.5.2.2 Platform-as-a-Service (PaaS)
-  Providers give you a software platform, or middleware, where applications run
-  You develop and maintain and deploy your own software on top of the platform
-  The hardware needed for running the software is automatically managed by the platform. You can’t explicitly ask for resources.
-  You have automatic scalability, without having to respond to request load increase/decrease
-  No control of OS, storage, or network, but can control the deployed applications and host environment
-  Use case: Best for webapps, Language and API support, such as google app engine, microsoft azure and whatsapp

##### 1.5.2.3 Software-as-a-Service (SaaS)
- Providers give you a piece of software/application. They take care of updating, and maintaining it.
- You simply use the software through the Internet.
- Use case: office web apps, gmail, dropbox, github etc.


#### 1.5.3 Comparison
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132156458.png)
 <center style="color:#C0C0C0;text-decoration:underline">Separation of responsibilities</center>
As we can see from above, if we own a datacenter on-premises, ofcourse we can manage everything, but maintaining hardware is Tedias  Why people want to go to the cloud. If we use Iaas, what we get is nothing but a virtual machine, we need to manage the operatinf system, Middleware, runtion etc.
If we use Paas, we can create specific applications for the certain platform using proprietary APIs and make that application available to any  user. And we do not need to worry about other things, all the resources we need is automatically allocated by the platform. Last is Saas, you just run the application, you do nit need to be a computer science expert to use all these wonderful applications.

![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132202989.png)
 <center style="color:#C0C0C0;text-decoration:underline"> tradeoff between flexibility and customization </center>

 ##  2. Current development of cloud computing
Since the concept of cloud computing was first proposed in 2006, more than a decade of development has passed. After more than a decade of competition, the development of cloud computing has reached a relatively mature stage. At the same time, the market size of cloud computing is expanding year by year, and we have good reasons to believe that the market share of cloud computing will continue to grow in the future.
### 2.1 Cloud Computing Current Market Size
According to data statistics agency iiMedia Research, the global cloud computing (IAAS+PAAS+SAAS) market size reached $224.5 billion in 2020, up 19.22% from 2019, and is expected to reach $265.4 billion in 2021. iiMedia's data analysts believe that the global cloud computing market has huge space and long-term trend of stable growth.
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132207893.png)
SaaS holds the largest market share, with $126.9 billion in 2020. The smallest market share is PaaS, with a market share of only $43.5 billion in 2020. IaaS has a slightly larger market share than PaaS, with a market share of $54.1 billion in 2020.

  

According to the forecast, the global cloud computing industry market size is not only not affected by the Covid-19 epidemic, but also continues to maintain a very good upward trend, and the market size will continue to maintain rapid growth in the coming years. The market share of SaaS is growing particularly fast. IaaS and PaaS will also continue to grow very well, reaching $96.5 billion and $75.7 billion respectively by 2023, according to iiMedia.
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132207227.png)
The global cloud computing market reached a new high of $406 billion in 2021 and is forecast to reach $663 billion in 2024, which means that the global cloud computing market will be more than twice as large in 2024 as it was in 2020. Therefore, we have good reason to believe that the cloud computing market has not only reached a relatively mature stage, but also will remain dynamic in the future. 

  

According to T4AI, while SaaS still dominates the cloud computing market, private clouds are also growing at a very fast pace from 2018 to 2021. While private clouds held a market share of just 32 billion dollars in 2018, this figure has grown rapidly to 10 billion dollars in 2021, making it the second largest market component after SaaS. According to forecasts, the private cloud market share will continue to grow at a much higher rate than other market components in the future. By 2024, the private cloud will reach a market share of $18.6 billion, officially overtaking SaaS as a major part of the cloud computing market.
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132208202.png)
With the global cloud computing market at record highs, the market penetration rate of the cloud computing market has also been increasing. According to iiMedia Research, the global penetration rate of global SaaS applications is 36%, up 12% from 2019. iiMedia analysts believe that the emergence and continuation of the new crown pneumonia epidemic has shortened the market SaaS application cycle, increased the penetration rate of SaaS applications in areas such as telecommuting and online education, and accelerated SaaS development.
![](https://cdn.jsdelivr.net/gh/Bennie13/Notes-Images@main/Images/202205132208181.png)
From the perspective of global enterprise cloud strategy distribution, hybrid cloud has become the mainstream within the cloud computing industry. 2020, global enterprises are more focused on the layout of the hybrid cloud field, the layout of enterprises up to 87%; enterprises no longer layout the private cloud field, the layout of enterprises only 1%. According to the analysts of Ai Media Consulting, the business boundaries of traditional enterprises and Internet enterprises are broken at the same time, the close relationship between traditional enterprises and private clouds, Internet enterprises and public clouds is also broken, and hybrid clouds have become a major trend. Traditional enterprises, in the process of exploring innovative businesses such as "Internet+", need public clouds to carry their business development. Therefore, while traditional enterprises use private clouds, they also need to use public clouds to develop new businesses. On the other hand, Internet enterprises use public cloud resources to cope with peak load business and also use private clouds to maintain a continuous workload.
### 2.2 Industry chain promotes cloud computing development
According to the whole industry chain of cloud computing industry, all parts can be divided into industry upstream, industry midstream and industry downstream. The upstream of cloud computing industry is divided into chip suppliers and infrastructure equipment suppliers. Chip vendors include the common Intel, Nvidia and other well-known chip vendors. And the infrastructure equipment suppliers include Huawei, Cisco and other communication equipment suppliers. In the domestic cloud computing industry, FiberHome and ZTE are also very important infrastructure equipment suppliers.

In the midstream of the cloud computing industry, there are various market-facing cloud service providers. For example, there are four cloud service providers that offer IaaS globally: AWS, Ali Cloud, Google and Microsoft. Many vendors that provide SaaS services are also an important part of the midstream chain, such as Adobe, which provides SaaS services that are very popular worldwide.

In addition to the IaaS, PaaS and SaaS mentioned above, IDC is also an important part of the midstream cloud computing industry. For example, IDC service providers such as Universal Data and DataPort also have a significant market share globally.

  

Cloud computing has a high demand for using the Internet to access physical data resources and virtual resources located in data centers. Therefore, with the technological development of infrastructure providers, such as the practical application of 5G technology, the network environment between the individual terminals to the servers in the data center is optimized, which can also facilitate the development of the cloud computing industry to a certain extent. At the same time, 5G technology provides more bandwidth, and with the development of the Internet of Things, the devices connected through the network will not only be mobile devices and computers, but also all furniture and public facilities will be connected through the network, which means that the amount of data generated by different devices will be far more than the previous amount of data. This means that the amount of data generated by different devices is far greater than before. All of this data cannot be processed locally on the device, so as 5G technology drives the development of IoT, the market share of cloud computing will also increase.

The advantages of cloud computing technology itself are also highly compatible with the needs of various different users downstream of the cloud computing industry chain. The back end of cloud computing has a very large and reliable cloud computing center, and for cloud computing users, they can get a high user experience at a small cost. More specifically, cloud computing has the following six major characteristics.

Internet-centric. Cloud computing platform operators take the Internet as the center and distribute storage and computing power among the nodes connected to the network, thus weakening the computing power of the terminal and making the computing architecture of the Internet evolve from "server + client" to "cloud service platform + client". " evolution. This means a major change in the Internet, the Internet will be more powerful, and even trigger a change in the general mode of existing enterprise information technology.

Flexibility. Enables users to quickly and inexpensively utilize technical infrastructure resources. The mechanisms for implementing services are transparent to users, who do not need to understand the specific mechanisms of cloud computing in order to access the services they need. Because of the ability to access the system using a web browser, users can then access the information they need and obtain the services they need from any location, using the device they are using, such as a personal computer or cell phone, via the Internet.

Economical. Costs are greatly reduced, and capital expenditures are converted to operational expenses. The infrastructure for cloud computing is usually the third party provided, which eliminates the need for users to purchase expensive equipment for one-time or non-recurring computing tasks. Billing on the basis of computing volume also reduces the customer's requirement for equipment knowledge.

Reliability. Cloud computing systems consist of a large number of commercial computers in a fleet to provide data processing services to users, utilizing a variety of hardware and software redundancy mechanisms, which makes it suitable for business continuity and disaster recovery. The security of cloud computing is improved due to centralized data management, which is due to the ability of the provider to dedicate resources to conducting security audits and resolving security issues, whereas the average customer has limited capacity or funding.

Scalability. Nowadays, most of the software and hardware have some support for virtualization, and various Ding resources, software, and hardware are virtualized and placed in the cloud computing platform for unified management, and the purpose of scaling the above applications is achieved by dynamically extending the virtualization hierarchy.

Sustainability. Since computers and related infrastructure are the main source of energy consumption, suppliers will consider all aspects to reduce overall energy consumption by improving resource utilization and building more efficient systems.

  

It is worth noting that many potential customers of cloud computing services have accelerated their move to the cloud due to the impact of the covid-19 outbreak. For example，Affected by COVID-19, many businesses have been unable to operate normally over the past few years. As a result, many companies, including traditional manufacturing, are facing digital transformation. At the same time, the policies of various countries also promote the use of cloud services by more and more enterprises.

## 3. Commercial application of cloud computing
In addition to the three modes of IaaS, PaaS and SaaS mentioned in the previous article, there are also many business applications for individuals that use cloud computing technology to enhance the user experience.

  

The most widely used industry for cloud computing is the online storage industry, with Google, Microsoft and Apple all launching their own cloud storage services. The most iconic of these is iCloud cloud storage, which allows users to access and edit data stored in the cloud through the network by logging into a local client with an Apple account. iCloud has data centers around the world, ensuring fast access to iCloud services around the world. The best-known cloud storage solution for enterprises is the OATOS cloud storage suite, which provides an innovative solution for meeting enterprise network storage needs. First, OATOS enterprise cloud storage solution allows data to flow instantly, so that data can be easily accessed anywhere, anytime, as long as there is network access; second, OATOS enterprise network storage has bank-level security: Https transmission, original data encryption algorithm, and role permission management for data security.

In addition to the cloud storage industry, personal communication services also make extensive use of cloud computing technology. For example, Google's mail service uses its own cloud computing service support. Google mail service takes Gmail mailbox service as the basic function, and Google has added a lot of cloud communication functions in the web page. For example, if users sign in to their Gmail account in the webpage, they can sign in to Gtalk and immediately use various powerful functions in the webpage, such as instant messaging, voice calling, video calling, document transfer and so on. Many business applications for multi-person online meetings also make extensive use of cloud computing services, such as Cisco Webex, the communications hardware giant Cisco spent $3.2 billion to acquire Webex back in 2007, and it has become the world's number one web conferencing provider. Users need to read the Webex program remotely by way of a Java Applet, and once completed, they can start a powerful multimedia teleconference in the familiar web format.

Cloud Input is also an emerging cloud computing application. The most important feature of cloud input is that it does not need to be installed, it can be used as long as you are connected to the Internet, and it is more compatible and easy to use. Unlike normal input methods that install the lexicon in the local computer, Cloud Input's lexicon is placed in a powerful dedicated server, which theoretically has an infinite lexicon and language model library, so the accuracy rate is higher. In addition, it can remember users' input habits. Google Cloud Input Method is currently the leader in the industry. With Google Cloud Input Method, you can input Chinese directly in the input box of the website without opening the client input method first every time. No matter where you are, you can use the online Chinese Pinyin input method by selecting Chinese from the language drop-down menu on the far left. In addition, you can also use the Chinese cloud input method in Google Translate, by selecting "Chinese" as the source language and checking "Allow input of Latin characters in Pinyin" below the input box, you can easily input Chinese Pinyin through phonetic translation and convert it to your own needs through Google You can easily input Chinese pinyin through phonetic translation and convert it into your desired language through the powerful function of Google Translate.
## 4. Obstacles and Measures for Cloud Computing
In this section, we list a number of obstacles to the development of cloud computing. With every obstacle comes an opportunity -- our ideas on how to overcome them, from direct product development to major research projects.
### 4.1 Security
The security of cloud computing has always been a hot topic. The users may worry about that is it possible their private data are obtained by attackers. It is certain that with the development of cloud computing, its advantages of flexibility, speed and high cost performance are further amplified, thus attracting more users. On the other hand, these advantages also make it become the target of super hackers, network illegal organizations and APT attacks. Once a cloud computing platform leaks users' data privacy, or a large amount of data is lost due to device failure in the process of cloud storage, or data is tampered arbitrarily by other users in the process of transmission, the adverse effects caused by such consequences are inestimable[].

The three dimensions of data are important criteria in security, which are availability, integrity and privacy. Data availability is the factor that prevents data from being unusable due to hacker attacks and physical device failures. In cloud computing, the measure to ensure data availability is redundancy backup, and the parallel model of the system is used to improve system reliability. Data integrity refers to the elements that ensure that data cannot be tampered with by unauthorized users or can be quickly discovered by the system during data transmission and storage. Digital signature is a common method to ensure data integrity, which ensure that data is not modified or changed during transmission, and confirm the identity of the sender and receiver of data transmission. Data privacy is the element to protect users' personal data and information in every link of mass data transmission, storage and processing. Cloud computing applications mainly protect data privacy through three methods: authentication based on shared key, biological characteristics and encryption algorithm based on public key.

In addition to the above information, it is also important and useful to build a closed loop network for cloud data protection. There are six parts in the loop, including data generation, data migration, data using, data sharing, data storage and data destruction.

In cloud computing, there is no absolute security, security is only relative. According to the current situation, cloud storage is more secure than local storage based on good, stable and secure software technology, hardware technology, and equipment room environment.
### 4.2 Data Lock-in
The software stack improves interoperability among platforms, but cloud computing API itself remains proprietary in nature, or at least have not yet been the subject of active standardization. Therefore, customers cannot easily extract data from one site and run programs on another. Users' data will be greatly influenced by external factors that cloud service providers are exposed to.

For example, The Linkup,an online storage service, has lost about 45% of customers’ data, and then it shut down on August8, 2008[]. The Linkup stored customers’ data in another online storage service Nirvanix in turn, and they both thought that the other should be responsible for it. However, almost 20000 users of The Linkup had to store their data in another site, which has brought great inconvenience to the operation of the users’ company. To solve this situation, it might be useful to standardize the APIs, so that SaaS developer could provide service and process the data across multiple cloud computing providers, and then a single company’s failure would not cause whole data be lost. 

Another situation is that cloud service companies suffer unforeseen accidents. For example, OVH is Europe's largest cloud and web hosting service operator, and a fire broke out its data center that located in Strasbourg, France, on March 10, 2021[]. OVH has more than 1 million customers and more than 300 hosting sites, and services cover 138 countries and four continents. The incident resulted in severe damage to sbG-2, which is one of the four facilities in the data center, and another three facilities also affected to varying degrees. It shows that disaster recovery backup is really important to minimize the damage caused by this situation.
### 4.3 Data Confidentiality and Auditability
Most cloud services are public (rather than private) networks in nature, exposing systems to more attacks. Every public cloud provider claims that its services are secure in all aspects, especially data management However, for enterprises, especially large enterprises, business-related data is their lifeline and cannot be threatened in any way. Therefore, in the short term, large enterprises will not put their Mission-critical applications to run on the public cloud. Then they can choose to use private cloud services, because the services are almost built behind a firewall or deployed in a secure hosting location. It is built for a single customer, thus providing the most effective control over data, security, and quality of service, the customers do not need to worry about data confidentiality. 

As to auditability, many countries have laws that require SaaS providers to keep customer data and copyrighted material within their own borders. Some enterprises do not hope their data being obtained by other regions’ governments, such that a European company would concern the United States government gets their data through a branch in the United States. To solve this, cloud computing may give SaaS providers and users more freedom to place their storage to varieties of locations.
### 4.4 Reputation Sharing
One customer’s bad behavior may affect the reputation of the whole cloud. And the cloud computing providers may want legal liability to remain with the customers, rather than share it with their customers. 

There is an example: the first infringement case of cloud server provider in China, on June21, 2019[]. Locojoy discovered that one of its games was copied from a server rented by AliYun. Subsequently, Locojoy sent a letter requesting AliYun to remove the alleged infringing content and provide details of the server tenant, but AliYun did not actively cooperate. Locojoy believes that Aliyun's actions are suspected of joint infringement. However, the trial result tells us that legal liability is not shared, and it might not be afraid.

## 5. Conclusion and Trends in Cloud Computing
Cloud computing is an important development direction of the IT industry in recent years. Its rise has brought great changes to the IT industry. It can make software services faster and more efficient, and also make IT more attractive. It allows more developers to deploy hardware without having to invest in hardware, and it also reduces the labor cost of operations. The flexibility of the resources offered by cloud computing services eliminates the need for customers to pay a massive premium. Although cloud computing providers may encounter various obstacles, in the long run, providers will successfully address these challenges and reap rich benefits from them.

In addition, Cloud computing is an important cornerstone of enterprise digital transformation. The future development of cloud computing will focus on technology, which is an important support for the development of cloud computing. The future trend of cloud computing is mainly reflected in the following aspects.
### 5.1 Hybrid Cloud
Hybrid cloud refers to the use and management of private cloud and public cloud to meet more business requirements of enterprises. As a single cloud service cannot meet the cloud requirements of enterprises, cloud computing service providers should change their solutions to provide hybrid cloud services based on user requirements.
### 5.2  Disaster Recovery
The importance of disaster recovery has already been mentioned. Disaster recovery refers to the process of restoring the data hardware and software equipment of information systems to normal business operations after a natural or man-made disaster. Nowadays, Coping with network attacks, information outages and outages is an important part of maintaining the normal operation of enterprises.

Cloud services offer lower costs and greater flexibility, but they are not without risk. Disaster recovery is that a service means more deployment and flexibility testing, but it also means more uncertainty. Disaster recovery raises a host of thorny questions: its systems are expensive, the configuration of disaster recovery systems are difficult, and most disaster recovery tests can only be performed during non-business hours. Because of its importance and difficulties, disaster recovery will be an important part of cloud computing's evolution.
### 5.3 Security
Security is a major challenge to the traditional information technology infrastructure, and it is a problem faced by many enterprises. In order to improve the security of cloud computing services, we can consider from the aspects of network, database, storage, operation and maintenance, etc.

- **network security and protection:** Providing a better firewall, intrusion detection and improved traffic cleaning rules.

- **Database security Protection:** The goal is high availability and reliability.

- **Storage security protection:** Providing large capacity and access control.

- **Security Operation Center:** Data is also confidential to operation and maintenance, requiring process assurance; A constantly updated virus library.
### 5.4 Edge computing
Edge computing is Edge computing is a technology that enhances the distributed computing network framework by collecting and processing information at the edge of an enterprise's network, and the edge is close to the source of information. Distributed computing allows more computers to process information faster and communicate with each other more efficiently.

Edge computing brings computing and processing power closer to the end user, and achieve reducing latency, saving bandwidth, and potentially improving privacy and security. Nowadays, when moving IT operations to the cloud, enterprises can move computing power to edge devices such as laptops or mobile phones to reduce stress on their primary systems and reduce latency and bandwidth for end users. 

Eventually, edge computing can be understood as a further extension of cloud computing center. If this distributed computing technology is combined with reasonable resource scheduling, the computing power and storage resources of edge computing nodes can be fully utilized. With the unified management of cloud center, a very efficient cloud computing platform can be generated
## 6. Reference
1. Xiaoxin Liu, Influence of cloud computing on traditional information security field and countermeasures[J]. Academy, 2015(34):2.
2. BRODKIN, J. Loss of customer data spurs closure of online storage service ’The Linkup’. Network World (August 2008).
3. Chunyang Xu,OVH Fire Incident - Data Center Pain Point, Sohu, 海峰看科技,2021/03/18.
4. Xu Zong, Fei Xu, 国内首例云服务器提供商侵权案：二审改判阿里云不承担法律责任,Daily Economic News, 2019/6/21.
5. L. Barroso et al., “The datacenter as a computer: An introduction to the design of warehouse-scale machines.”  
6. By Nick Barcet, “What is Ubuntu Cloud”, Nov 2009
7. National Institute of Standards and Technology (NIST), U.S. Department of Commerce，definition of cloud computing
8. K. Remde, “SaaS, PaaS, and IaaS.. Oh my!” TechNet Blog, 2011