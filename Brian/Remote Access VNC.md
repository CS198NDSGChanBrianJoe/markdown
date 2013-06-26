#VNC ARCHITECTURE BASED REMOTE DESKTOP ACCESS THROUGH ANDROID MOBILE PHONES

##

##Authors

- Archana Jadhav
- Vipul Oswal
- Sagar Madane
- Harshal Zope
- Vishal Hatmode

##Background
- Mobile phones today have the processing power of old computers and is therefore a candidate to be a client for remotely accessing some server.

- Virtual Network Computing is a graphical desktop sharing system providing remote control via network. It supports a controlling functionality by usage of a graphical screen update from a controlled device and capturing a mouse and/or a keyboard.

- Virtual Network Computing is based on Remote Frame Buffer protocol which suggests that the way it transfers the screen from server to client is through giving the image of the screen itself pixel by pixel and the client will reassemble it for the user to see.

- VNC need two applications: A server application and a client application.

- Server side application is responsible for interpreting what the client sends and responding by updating the screen and sending back to the client.

- Client side application is responsible for providing the user with a view of the shared screen as well as allowing the user to control the server.

- Since VNC follows the remote frame buffer protocol, it is compatible with a lot of other operating systems. This is because a lot of operating systems recognize RFB protocol.

- Encoding refers to the format an image or part of an image is sent. There are 4 types of encoding discussed in this paper, namely:
	- RAW - Pixel by pixel sending of image data from server to client.
	- RRE (Rise and Run Length Encoding) - consists of grouping consecutive identical pixels in order to send only the information of one pixel and the number of replications of that pixel.
	- CopyRect Encoding - consists of using old frames to lessen the amount of pixels sent to the client.
	- Hextiles - divides the image into 16x16 tiles and sends them one by one and using any other type of encoding on each of those tiles. It is parallel to the divide and conquer technique.

- VNC supports multiple clients.

##Problem
The main problem in the paper is the implementation of remote access using VNC and an android phone. The only connection this needs to support is a Wi-Fi connection. There should be no operating system restriction. There should be functions that cater to the ease of navigation and viewing. 

##Solution
1. Design - There are six components that are needed for smooth navigation and viewing of the screen.

	- Desktop Sharing - This is a function where the server can be shared by multiple clients.
	- Panning and Zooming - Panning refers to the ability to move the focus of the screen in any direction. Zooming refers to the ability to move the screen nearer or farther away from the user.
	- Overviewing and Twin view - Overview refers to the ability to zoom out such that the whole screen fits in the phone. Twin view refers to the ability to display two parts of the screen side by side.
	- Inputting Text - The standard text input for the phone is used here.
	- Shortcut Assignment - Allowing some functions of the server to be accessed by pushing a combination of buttons.
	
2. RFB Implementation
    - ClientInit is the process where the client specifies if it is willing to share the server or if it wants exclusive access. 
    - ServerInit is the process where the server tells the client the frame buffer dimensions and the format it uses for sending the images.
    - After these steps, the server and client are now initialized and will continue to exchange information until the user closes the client application.

	
##Conclusion
There is merit to providing remote access capabilities to the phone. It is a portable device that has a lot of processing power for a client. Also, with VNC, it is possible to have a centralized server and a lot of clients requesting for files and uploading files to the server. 