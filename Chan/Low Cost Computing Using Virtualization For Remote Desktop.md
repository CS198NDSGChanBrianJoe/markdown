#Low Cost Computing Using Virtualization For Remote Desktop#
##by Dhaval Manvar, Mayank Mishra, Anirudha Sahoo ##
###Introduction###
####Problem:
Given the fast growth of technology nowadays, more users or companies buy highend units that end up too powerful for a specific work but easily gets out of fashion because of the said growth.
####Solution:
Given the problem above, the proponent gave the suggestion of using the technology called Remote Desktp so that the company or institution won't need to buy higend units for every staff but to have a good quality server and thin clients instead. Another problem arise on given the remote desktop, most remote desktop technologies support only one user at a time and some would allow many users. For the case of the ones that allow many users, it would end up that everyone is working on the same operating system and has the same system directory. Having that said, once an error occured everyone is affected.
####Final Solution:####
The proponents though of having a remote dekstop environment which actually runs virtual machines for the users.  

---
###System Design
####Setup:
1. Xen Hypervisors
2. LTSP
3. Thin Client
####Components:
1. Manageement Server - the central entity whose main task is to perform user to VM mapping, create VM on one of the existing VAPMs and provision resources to user’s virtual desktop (running as VM) as per requirements. 
2. Virtualization Aware Physical Machine (VAPM)

---
###Challenges
1. User To VM mapping
2. Starting VM on user login
3. Provisioning of VM to Host Virtual Desktop
4. Enhancing System Efﬁciency