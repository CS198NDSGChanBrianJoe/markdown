#Virtualized Remote Web Desktop 
---
###Authors:
* Amina Sultana
* Bittu Daimary
* Mahesh Chettri
* Joby Joseph


---
###Introduction:
On the paper, it first discussed the basic features of a operating system such as as follow:  

* Software and hardware management
* Constant API
* Execution of Programs and Applications
* Interruptions
* Managing Memory
* Networking
* Security   
 
Another part of the introduction discusses the paradigms behind cloud itself and the types of cloud development models available nowadays such as as follows:

* Public Cloud
* Private Cloud
* Hybrid Cloud
* Community Cloud

And also defined available cloud services in town which were as follows:

* Infrastructures as A Service:  The consumer does not manage or control the underlying cloud infrastructure but has control over operating systems, storage, and deployed applications; and possibly limited control of select networking components.
* Platform as A Service: The consumer does not manage or control the underlying cloud infrastructure including network, servers, operating systems, or storage, but has control over the deployed applications and possibly configuration settings for the application-hosting environment.
* Software As A Service: The consumer does not manage or control the underlying cloud infrastructure including network, servers, operating systems, storage, or even individual application capabilities, with the possible exception of limited user-specific application configuration settings.

On the paper, it also discussed the Cloud Operating system which can be treated as a Platform As A Service. On this type of service, one can place any operating system on the cloud and be able to access the operating system on a local machine having the feel of running the operating system on the machine.  On the current implementation of the said system, it captures the activities of users on the client side and sends it to the cloud where the operating system resides. Then the server processes the activity sent by the client then sends the result back to the user. 

---
###Proposed System
On the paper, the proponents created a model for a cloud-based system which they named as "Virtual Remote Web Desktop".
####Components:
1. Browser: The browser is the component of the proposed system which acts as the user interface of the users to cloud where the operating system resides.
2. Web Client OS: It is a client-side component which is responsible on creating messages and defining the display seen by the user though the browser. The Web Client OS is purely written on Javascript. On its create message feature, it captures activities such as key pressed and mouse pressed and then sends it to the cloud through either http or https. Messages are described as either a Client Message (used for  sending event triggered information to the Server) and a Server Message (A command which corresponding data that wll fulfill the command its proper execution). On the other hand, the Create Display feature, the Web Client OS receives data from the server which is either a reply for the message sent or another event due to an activity on the cloud.
3. Web Request Handler: An application running on top of the operating system with three basic features known as Request Interceptor (intercepts the message sent by the client and extracts al the information relaed to the event.), Trigger Event (It triggers event in the Operating System residing in the Cloud for a particular application specified in Client Message.) and Web Window (It is the replacement of the GUI creation component present in the actual OS in the cloud. Web Window component uses the generalized set of commands and performs the necessary functioning corresponding to the commands invoked.)
4. The operating system

---
###Conclusion:
Given this idea, it allows not-so-powerful units such as thin clients to be able to access data from a cloud server. It allow many users to be able to access the operating system. Considering the client-side, having such technology would require lesser processing that could lead to beter performance.