#Efficient Remote Data Access in a Mobile Computing Environment

##

##Authors

- Laura Bright
- Louiqa Raschid 

##Background
- The growing presence of mobile computing and wire-less communication has increased the number of clients that access data remotely. The growing presence of mobile computing and wire-less communication has increased the number of clients that access data remotely.

- In mobile computing environments, there is typically a set of servers on a fixed network that provide data to a set of mobile clients.

- A base station is a fixed server with a wireless interface to communicate with mobile clients.

- Communication go like this:
	- First, the Mobile Client requests from the base station an object that the remote server has. 
	- Then, the base station acquires/downloads that object from the remote server.
	- Finally, the base station transmits the object to the requesting client.

- A drawback in this environment is that remote data access is slow due to network delays or server workloads.

- Maintaining a cache at the base station can improve the above situation since having a copy of the object the client requires will no doubt skip the second step of the communication process completely.

- The challenge here is to keep the cache as updated as possible given the preference of the user concerning the recency of the objects.

- A possible solution is called the asynchronous approach which continuously updates the cache every time a request is made. 
	- This speeds up the communication process since the client does not have to request anymore.
	- It wastes bandwidth since not every update will be used due to the speed the objects are changed in the remote server.
	- Objects may be updated at any time so the cache is never really completely updated.

- The results are applicable to any enviroment where time or bandwidth constraints make it impractical to access all requested data remotely.

##Problem
Given a set of requested objects (of varying sizes), a set of client recency requirements for each object, a cache containing a possibly less recent copy of each object, and a limit on the amount of data that can be downloaded, we 
need to decide which objects to access remotely, and which to read from the cache.

A second problem is to determine an upper bound on the amount of data that 
should be downloaded to answer a set of requests. 

##Solution
An on-demand approach is proposed in the paper. Reading some data from the cache reduces the amount of time that the wireless downlink bandwidth may be idle while the base station waits for data to arrive from remote servers. It also consumes less bandwidth on the fixed network than accessing all requested objects remotely.

After acquiring the demand for objects, the on-demand approach will get either from the remote server or from the cache. This is done via a computation using the client's preferred recency, the recency of the different objects in the cache and the amount of requests for the objects. 

Of course, we can never tell how the new approach will work without pitting it against another approach. In the paper, this approach was squared off against the asynchronous approach. With regard to the amount of data downloaded, the on-demand approach wins since the amount that the asynchronous approach downloads is an upper bound to the amount that can be downloaded. The on-demand approach however is very good with few requests and only approaches the upperbound when the number of requests reaches a high enough number.

Recency of data is very important for the clients since we always want the most updated version of the object in question. So, the two approaches were also compared by the average recency of the objects that were given to the clients. For the asynchronous approach, after imposing a limit in amount of downloads, it would indiscriminately pick the first items corresponding to the limit and download them from the server while the rest were read from the cache. The on-demand approach computed for the recency of the objects in the cache and the oldest among them were downloaded from the remote server. Again, on-demand approach wins due to getting the best case scenario for any input as opposed to asynchronous which will only be random. 

There are three things that dictate how the on-demand approach will behave. The first one is the number of requests for a specific object. The second is the size of the object while the third is how recent the object is in the cache. What we need to know here is what would happen if the number of requests for each object is uniform or skewed. For this, there is a need to define average score which is the average recency of objects across all clients. Depending on how the three factors are related, we can map them to a curve representing their scores ddepending on the download limit. From there, we can tell if small objects or large objects can dramatically affect the average score or not.
	
##Conclusion
Overall, the on-demand approach clearly beat the asynchronous one. The draw backs of asynchronous approach were all countered by the on-demand approach. For one, there is no unnecessary use of bandwidth and you can be sure that what you get via the on-demand approach is the best you can get factoring in the download limit. And the authors also tested their setup on different scenarios that can and will happen in the implementation. This is a characterization of the behavior of the on-demand approach depending on some factors.