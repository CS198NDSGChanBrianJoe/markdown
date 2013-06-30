#pTHINC: A Thin-Client Architechture for Mobile	

##

##Authors
* Joeng Kim, 
* Ricardo A. Baratto
* Jason Nieh

##Background 
* "A thin-client computing system(TcCS) consists of a server and a client that communicate over a network using a remote display protocol (RDP)."
* A RDP in general, enables graphical displays to be virtualized and served across a network to a client device(w/c gives input messages(keyboard/mouse) to the server), while application logic is executed on the server(w/c translates the input  messages passed). 

* There are many different RDPs which differ in their means of transferring data but all follow the general concept of a RDP. (see "THINC" summary paper 'Background' part for more background information)

* Though TcCS has a lot of potential, currently, only few are support mobile handheld devices.
	- Form factor issues
	- Heterogeneous displays

##Problem
* Personal Digital Assistants/Mobile Devices(smart phones) are used a lot to access web content through native web browsers which deliver subpar performance/smaller feature/limited functionality than their desktop counter-parts.
	- The desktop application market is larger and more mature, most development effort generally ends up being spent on desktop applications, resulting in greater functionality and performance than their PDA counterparts.
	- PDAs/Mobile devices have a more resource constrained environment than traditional desktop computers to provide a smaller form factor and longer battery life.
##Solution
 * Extend the THINC rdp to support mobile handheld devices (see "THINC" summary paper 'Solution' part for more information about THINC's protocol)
  - Landscape/Portrait displaying (server side)
  - Heterogeneous display(zoom-in/out) / resolution support
  - Persistent session model
  - Support for mobile buttons/input mechanisms(e.g. stylus)


* Test pTHINC web browsing against native mobile web browsers and RDPs which support mobile remote desktop (ICA,VNC,Microsoft RDP)
	- 1024x768 and 640x480 resolution tests
	- Landscape view (if available) tests
	- Packet monitoring(network traffic)
	- Browsing web pages scenario
	- Video Playback scenario
##Conclusion
* "pTHINC transparently supports traditional desktop browsers and their helper applications on PDA devices and desktop machines, providing mobile users with ubiquitous access to a consistent, personalized, and full-featured web environment across heterogeneous devices."
* "pTHINC delivers web browsing performance up to 80 times better than existing
thin-client systems, and 8 times better than a native PDA browser."
* "pTHINC is the only PDA thin client that transparently provides full-screen, full frame rate video playback, making web sites with multimedia content accessible to mobile web users."
