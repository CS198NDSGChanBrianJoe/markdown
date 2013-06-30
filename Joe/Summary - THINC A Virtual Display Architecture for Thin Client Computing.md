#THINC: A Virtual Display Architecture for Thin Client Computing

##
##Authors
* Ricardo A. Baratto
* Leonard N. Kim
* Jason Nieh

##Background
- "Remote Display is a client/server architecture that decouples a computer from the devices used to interact with it, such as the monitor, keyboard, and mouse, and uses the network to provide a communication channel between these devices and the computer. Basically, a client transmits user input to
a server, and the server returns screen updates of the user
interface of the applications to the client." This is used interchangeably with Remote Desktop Protocol.

- Remote Display is used for ubiquitous access of a computing session, remote collaboration of multiple clients in a computing session,IT support and most especially, thin client set-ups/systems all of which give benefits like: easier backup of data,better data security, cheaper maintainance/upgrades of hardware/software,better distribution of computing resources,convenience,etc.

- "A thin client system moves all application processing and data to centralized servers and secure server rooms, and using a remote display protocol provides access to these servers from simple and stateless devices."

- There are many different thin client systems out there such as X,NX,VNC,GoToMyPc,Sun Ray, Microsoft RDP,etc. These use different kinds of remote display/desktop protocols under these general classifications:

	* System Architecture common to RDPs = Application <-->Window System <--> Device Driver <--> Frame Buffer 

		1. Intercepting high-level application display commands in the server and sending these commands to the client whose window system executes these commands. Synchronization between server and client is an issue here. Also clients must be able to do some processing.
	
		2. Intercepting low-level frame buffer display commands in the server and  compressing and sending these commands to the client wherein they are decompressed and represented as raw pixel. The issue here is the amount of data transmitted in the network as well as computation intensity on the server side due to compression.

  
	
##Problem
Even with the all the different Remote Display/Desktop protocols today, performance is still an issue, particularly in providing high fidelity visual and interactive experience for end users(displaying multimedia content).Most RDPs do not effectively support multimedia(e.g videos) and are not effecient in high latency environtments (e.g WAN)

##Solution
Thin-client Internet Computing, THINC, is a virtual display architechture/remote display/desktop protocol designed for thin client computing that provides high fidelity display and interactive performance in LAN and WAN environments.

* A virtual display driver(w/c takes the place of device driver in the system architecture mentioned above) intercepts drawing commands of the device driver, encodes these commands using the command's semantic information  nd THINC's low-level encoding protocol(COPY,SOLID FILL,TILE FILL,BITMAP FILL,RAW) for display updates and sends these to the client device to display.The client device easily displays the encoded commands because they mimic operations commonly found in client display hardware and represent a subset of operations accelerated by most graphics subsystems.

* Display updates are pushed from the server to the client immediately.For slow responding clients, updates are merged into new ones(deleting old/usesless updates) and sent to the client
 
* THINC uses Shortest-Job-First display command scheduling to improve response time.Display updates are queued and are flushed in increasing size.

* THINC also provides server-side screen scaling which minimizes display bandwidth and processing requirements for handheld devices.

THINC was then compared to existing RDPs regarding web browsing performance, and A/V playback quality in different situations: WAN,LAN,802.11 PDA, internet 2 sites around the world
 
##Conclusion
* "THINC’s unique mapping of application
level drawing commands to protocol primitives and
its command delivery mechanisms significantly improve the
overall performance of a thin-client system."

* "THINC provides superior web performance over other systems, with up to 4.5 times faster response time in WAN environments."

* "THINC’s audio/video support vastly outperforms existing systems."

