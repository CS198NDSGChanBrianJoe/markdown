#An Adaptive Desktop Transfer Protocol for Mobile Thin Client

##

##Authors

- Tomoharu Imai
- Kenichi Horio
- Takashi Ohno
- Kazuki Matsui

##Background
- Thin Client systems provide remote access to a desktop environment which has an Operating System and applications installed on a remote server.

- Since the remote server does all the work, thin clients do not need high computing power.

- Thin client systems can now be integrated on the mobile phone since smartphones have recently become available and wireless networks have become faster.

- The bandwidth of wireless networks as compared to a wired one is very limited and will have trouble with transferring the amount of data required by the thin client system. 

- There are two remote display techniques that have been developed in the past:
	- Screen Data Compression Technique - Compresses the screen data at the server before sending it to the thin client. This has the problem of scaling since high resolution of the screen will lead to consumption of more CPU Power.
	- Draw source data direct transmission mode - The server sends the code it uses to construct the screen directly to the thin client instead of sending the screen data itself. The main problem here is the dependency on the OS. 


##Problem
In the paper, the authors propose a new technique to overcome the problems of thin client systems on mobile networks and that is to detect high motion zones on the desktop and encode them into a video stream. This technique can work with limited bandwidth and is OS independent.

##Solution
1. Design
	- The authors considered two cases for testing the new approach:
		- Case of Watching a Video - This is further divided into web browser and video player application. This case is defined by the video being in a fixed position in the screen.
		- Case of Browsing Files and Websites - This is further divided into file access and web page browsing. This case is defined by a lot of drastic updates in the display since you are going from one page to a different page. Some parts of the screen may stay the same and some might not.
	- In the paper, the authors created a method for estimating the high motion zone and transferring the compressed display updates as a high frame rate only in the estimated area. This is done by:
		- Dividing the screen into rectangles.
		- Add the updates in each rectangle.
		- Evaluate the update count.
		- Bind together areas that have high motion and they are estimated to be the encoding region.
		- We want to implement a time limit and a threshold for finding the updates.
		- The encoding region is sent as a video stream and the other areas are sent as images.
		- This method trades off quality for speed. 
		- This method is called adaptive quality of service architecture based remote virtual environment computing or AQUA-RVEC.
	- There are generally two problems here:
		- When the encoding region is too small, the server has a problem with sending a lot of image data to the client.
		- When the encoding region cannot be estimated properly due to random updates on the screen, the server sends the image pixel by pixel.
	- These two cases can be fixed by first having a scene detection algorithm that detects one of the two cases above. That is, if the user is watching a video or browsing files and websites. From here, depending on the choice, there are separate processes for the two cases.

#

2. Implementation
	- The server was given functions such as finding updates, estimating the encoding region and sending the video stream to the client.
	- The client was given functions to play the video streams the server gives to it.
	- The authors used a Policing Node that connects between server and client to simulate different network bandwidth environments.
	- The authors tested both VNC, RVEC and AQUA-RVEC to show how they would rank against each other.

	
##Conclusion
In conclusion, AQUA-RVEC is better than both VNC and regular RVEC. From the implementation, VNC was completely outdone by AQUA-RVEC when it comes to limiting bandwidth usage. RVEC was also beaten in performance by AQUA-RVEC but by a smaller margin compared to VNC. The authors also confirmed that AQUA-RVEC can be effective under actual conditions.