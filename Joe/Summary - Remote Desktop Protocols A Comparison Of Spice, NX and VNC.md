#Remote Desktop Protocols: A Comparison Of Spice, NX and VNC

##

##Author
Martin Hagström

##Background
- A Remote Desktop Protocol (RDP) is a protocol that allows users(clients) to access remote computers(servers) as if they were local desktop computers. 

- RDPs are generally used for telecommuting, virtual desktop environments and IT support. 

- Different RDPs focus on different features such as mutlimedia performance or operating system independence. This makes the overall performance and user experience of different RDPs vary depending on the environment setting especially when we take into account factors such as the kind of network(LAN,WAN,etc), network load, bandwidth,compression complexity,etc.

- A good performance indicator for RDPs is video playback because the remote desktop server has to encode a lot of frames quickly 

- RDPs generally differ in their means of sending data. There are 2 general types of RDPs:
	- Pixel-based RDP: RDPs classified as pixel-based send a copy of the server's frame buffer, which contains all pixel information of the current screen, to the client. This is easy to implement but is prone to sending large amounts of data (e.g. VNC) and is computationally intensive on the server side (compression,etc)
	
	- Object-based RDP: Object-based RDPs draw the screen image on the client by using application-level display commands sent by the server.This is harder to implement and maintain. (e.g. Spice, NX)

##Problem
Because end user experience is important in choosing the right RDP, an objective comparison needs to be made in order to give a system administrator the tools to make a good choice. This research aims to characterize, compare and contrast critical features of the ff RDPs: Spice,NX and VNC.

##Solution
1. Use slow-motion benchmarking.
	- Play a video in slow-motion to evaluate the quality of video and video data transfer. Slow-motion guarantees data is not discarded.
	
	- Video Quality = (((Data Transferred In Normal Video Speed/Playback Time in Normal Video Speed)/Ideal FPS)/(Data Transferred in Slo-Mo/Playback Time in Slo-Mo)/Ideal FPS in Slo-Mo))
	  
2. Test in cases like:
	- High Network Load, Medium Video bitrate
	- High Network Load, Low Video bitrate
	- No Network Load, Medium Video bitrate
	- No Network Load, Low Video bitrate  	
	
##Conclusion
Spice had the worst video quality and largest amount of data transferred in all test cases. NX seems to be the most stable protocol having more or less consistent performance in all teset cases. VNC has the best video quality and lowest data transferred in all test cases. 