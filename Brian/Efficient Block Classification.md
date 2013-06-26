#An Efficient Block Classification for Multimedia Service in Mobile Cloud Computing

##

##Authors

- Nguyen Thuy An
- Tien-Dung Nguyen
- Seungkon Ko
- Eui-Nam Huh

##Background
- Measures of a good system:
	- Network condition - Lowest latency and best performance for a certain bandwidth.
	- Hardware resource consumption - processing power is critical since the client has minimal hardware and the server has overhead consumption of resources.
	- User demands - speed and cross platform support.

- Despite the power of mobile phones, we need to give most of the computing to the server since there are limitations to phones like battery power and hardware.

- Compression is very important for heavy work like video streaming.

- There are two kinds of thin client protocols:
	- Low level image frame buffers - sends the image itself to the client and it is reconstructed there. VNC is an example of this.
	- High level API display function - sends the images as something else like a set of coordinates so as to dramatically decrease the time used for reconstruction. An example is RDP.

- Both have problems when playing videos so hybrid remote desktop protocols have been implemented to overcome this problem. 

- Classification of text and non-text blocks is also a technique for speeding up the process of reconstruction since if they are separated, we can create separate reconstruction functions for them and therefore specialize the processes for a specific block.

- Another way to reduce the computation time is to skip the parts of the screen that have not been updated. Only transmit the new parts of the screen to the client.

##Problem
The problem is to come up with a quick and accurate way to classify blocks into either text or non-text. So far, the best is the classification based on the Sobel operator edge detection. The goal is to surpass that method so that multimedia viewing on the phone will have a better quality.

##Solution
1. Method - Adaptive Sobel operator edge detection
	- Is an improvement upon the normal Sobel operator edge detection.
	- We need to set a threshold for the classification.
	- The Sobel operator edge detection will color the edges in the image white while leaving the rest black.
	- Text blocks will mostly have edges since very stroke of the letters are edges and pictures will have little to no edges since they are mostly color and do not have lines.
	- The next step is to get the percentage of white in the block. 
	- Depending on the threshold set earlier, the block can be classified as either text or non-text.
	- The core of Adaptive Sobel operator edge detection is in this step. When finished with classifying a certain block, we can reduce the computations for the neighboring blocks by determining their type beforehand. We can see that this is logical since normally, text and images come in big chunks so we can say that adjacent blocks will mostly have the same block classification. 
	- Group the blocks with the same classifications and pass them separately to the client so that the client can proceed to reconstruct them separately.
	
2. Experimental Results
    - The Adaptive Sobel operator edge detection is pitted against its non-adaptive counterpart as well as several other methods for separating the image to blocks.
    - The results state that Sobel beat Adaptive Sobel in terms of accuracy by about 5% which is significant but tolerable. Both methods beat all other methods that was tested in the paper.
    - Even if Adaptive Sobel lost in accuracy, it won in speed since it employs a reduction of the computations when blocks with the same classification are near each other. The speed of Adaptive Sobel is approximately 30% better than Sobel. This is a huge amount when we are talking about videos since we want a smooth flow of frames and this means a lot of frames should be processed in a short amount of time.

	
##Conclusion
The block classification that the authors presented is debatably a good alternative for the non-adaptive Sobel. It is a large boost in speed for the price of a small amount of accuracy. This is all the more true when it comes to multimedia since accuracy should only be second to speed in this case. However, there are some cases where we would want better accuracy rather than a faster way to reconstruct screens in the client device. What to use is something that we need to decide for ourselves depending on what we need and what we are willing to sacrifice. 