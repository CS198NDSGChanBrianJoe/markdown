#Remote Collaboration Screen Control Using Mobile Multi Touch Interface
###Authors:
* 이문수
* 김민정
* 김순중
* 성조기

---
###Introduction
Nowadays, the trend of computing is quickly moving from desktop-centric computing to mobile computing because increasing number of smartphones available in the market and the cost of mobile computing is definitely cheaper as compared to desktop computing / pc-based computing for normal users.  
Another thing making work easier nowadays is the increasing support and services based on the web specifically services using HTML5 and Javascript. And since things are going from local storage into web storage and applications that can be done before only on desktop has move towards mobile. Given the number of services provided by the web, it also makes things easier for the device thus need for powerful computing devices such as work units (desktops or laptops). APIs of the devices are now also available for the developers making the applications be able to access natives of the phone. Thus, services are moving from client-based to server-based.  
Another wonderful technology existing nowadays are softwares that provided the capability of working on multiple screens to users since the amount of devices that can connect over a network that a user has is also increasing and the users also like to have the capability of using data and applications on cetain devices that they have even on different places. Given this capability, multi-touch interface is also a tool that could definitely make things alot more easier for the user.  
On this paper, the proponents propose a novel remote control scheme to perform inter-user collaboration using a web-based content/service which utilizes the multi-touch capability of phones.

---
###Review on Related Literature and Related Studies
On the article, the proponents mentioned five different methods that are previously developed that could possibly be a big help on the progress of the project. First was the technology called Virtual Network Computing (VNC) which is a widely used desktop sharing tool. Second was an application that makes the smartphone able to access a television receiver over the local network. The second application was really simple that it even looks like a normal tv remote control. The third application that was introduced was the TouchInteract which is basically an application which allows a user to do whatever a normal mouse allows to do on the pc such as cursor positioning and capturing the activity and executing it. The fourth method was a method made for interaction developed for large displays by capturing phone movements. And the last method presents dual interaction for collaboration for multiple users.

---
###Implementation
The collaboration system proposed on this paper is designed for exchange of web contents (exchange of data via a service available over the web)
####Setup
The collaboration system is designed and structured based on a client-server model.   

* Display: A display on a office workspace which can allow and has the capability of managing multiple clients.
* Client: Mobile units.
* Server: A light weight server which does the role of being the connection manager, the gateway and the unit which forwards the messages through all connected clients.

####Software Architecture
The software has a core framework which allows the communication among the collaborating units. The framework can identify and slect contents on a normal websites access using the application. It also sends and receives contents on an inter-client manner. Given the said framework on different client, the software developed has different implementation dependent on the type of client defined below:  

* Mobile Collaboration Client (MCC): an Android application used for sharing contents through the framework and controlling the web content shown on the large display.
* Collaboration Screen Client (CSC): an Chrome extension developed which receives the changes committed by the mobile collaboration clients, manage the multiple contents and layout their positions on the screen.

####Experimentation and Workflow
The MCC utilizes the touch interface to generate the input from the user. On the mobile device's screen an image of the display scrren is shown allowing the user to know the boundaries of the workspace. As on the input, the user is able to access and manipulate data onscreen which manipulates the HTML and CSS of the object without actually editing the code.
#####Interaction between MCC and CSC
1. MCC connects to a CSC which manages the large display via a collaboration server using web socket connection.
2. MCC gets a snapshot of the screen and executes an image recognition algorithm to compute for the bounds of the workspace.
3. MCC calculates the real position of objects on the collaboration using mapping.
4. User selects and moves an object on the capture image using the touch interface.
5. MCC computes the real positions of the object and sends it to the CSC.
6. CSC executes the alter and shows it to the display.

---
###Conclusion
####Pros:
1. Minimize the amount of transmitted data
2. Provides a more intuitive interface gives the user the feel that to user is actually manipulating contents of the large display on the large display itself.

####Cons:
1. Users can't make any action while detecting the boundaries of the workspace.