#RVEC: Remote Virtual Environment Computing

##

##Authors
* Shinichi Sazawa
* Masayoshi Hashima
* Yuichi Sato
* Kenichi Horio
* Kazuki Matsui

##Background
* Cloud computing (CC) services where applications are centralized on a server allowing remote users ubiquitous access using remote desktop software/protocol/technology is becoming more prevalent because of its economic, practical, security, and efficiency benifits.

* Basically remote desktop software/protocols (RDPs) generally operate in 2 steps:
	1. Detect updates of the display by comparing the current frame buffer with the previous one.
	2. Compress the image of the updated area and transfer it to the client.

* The 2 general types of methods different RDPs use to perform the 2 steps mentioned above are:
	1. Screen-transfer method: Server sends screen changes to client through draw-commands or still image data(raw pixels). This is not very good if display updates frequently.
	2. Video-transfer method: Server sends entire desktop to client in video format. The disadvantage of this is that it imposes high processing load on the server also affecting performance,latency,response time,etc.


* 30 FPS generally provides smooth operation for a user when running an application locally. A reduction of frame rate will lead to lower data transfer, longer screen update intervals and a deterioration of response time. What is desired is that data transfer rate is lowered without compromising frame rate too much. Thus effective compression techniques are necessary.
 
* Compression Ratio = Uncompressed Size/ Compressed Size. Higher Compression Ratio is usually associated with fast compression speed but lower quality.

* Compression level is a parameter in the Deflate lossless compression algorithm used by Zlib compression software. This ranges from 1-9.A low compression level means faster compression speed. Low compression levels are used because long compression time results to long latency.

* Existing remote desktop technologies find it difficult to satisfy the requirements of compression ratios and compression speed simultaneously.

##Problem
Though cloud computing services can effectively deliver lightweight applications, current cloud technology has not been able to meet the growing need for high-end graphical applications (e.g. CAD) because of complex images having multiple slant lines,meshes and frequent display updates making it difficult to compress at desirable speeds without compromising quality/fidelity.
##Solution
RVEC solves the problem above by using a hybrid system that converts a region within the screen having frequent updates into video format which is 'lossly'  compressed (adapted movie compression) while sending less updated regions as still images 'losslessly' compressed (graphics compression). The reason behind this is because when an region is updating frequently, for instance, during a rotation operation in CAD, loss of visual details is to an extent, indescernible.

* To decide whether to convert a region to video or still-image format, RVEC first divides the desktop into meshes and counts the history of update occurrence in each mesh at fixed time intervals.

* For video conversion/compression, MPEG-4 is used because it requires less workload in encoding and decoding.

* For still-image conversion, a modified hextile compression technique is used which approximates a sequence of unicolored rectangles in a certain direction as a vector to be matched with pixel data.This is partnered with Wyle encoding to reduce the difference between the vector data and actual pixel data.This compression method maintains hextile's fast compression speed but is lossless.

RVEC was then evaluated in 2 ways:  
	(1) By comparing graphics compression performance with Zlib and the original Hextile in the ff instances:  2D CAD & 3D CAD (both using different modes: standard mode,flat mode,mesh mode, shading mode),Text image, Natural image.   
	(2) By comparing response time of RVEC with other RDPs (VNC,RDP,RGS) by monitoring transmitted packets.
 

##Conclusion
* RVEC achieves significant bandwidth reduction without deteriorating the visual quality with the use of its hybrid compression system.
* The response time of other systems cannot reach that of RVEC
either due to slow compression speed or poor compression ratio