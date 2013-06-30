#THINCing Together

##

##Authors
* Dave Coulthart
* Sudip Das
* Leo Kim
##Background
* See "THINC" summary paper 'Background' part for more background information
* Thin-client computing has become an enticing alternative to desktop computing because of its benefits (also mentioned in previous summary papers about THINC)
* Since colloboration software are commonly intertwined with RDPs and basic screen sharing, some RDPs/thin-client systems have already begun incorporating collaborative features.
* Kinds of collaboration:
	- Asynchronous(paper specific definition): "support for multiple users to run their own remote THINC sessions on the same machine." 
	- Synchronous: allow multiple users to share the same remote THINC session in a cooperative manner"
* The usual issue in synchronous collaborative features is "floor control" mechanisms which allow organized control over a mutli-user session.
	- Unmanaged control: Anyone can gain control at any point in time in the session. This can lead to numerous problems such as a congestion of updates as well as ineeffective collaboration
	- Managed control: This means assigning a client among other clients, control for a certain amount of time in a session and being able to relinquish/pass control when needed. This is harder to implement.

##Problem
Most RDPs which support collaboration (asynchronous/synchronous) fail to answer at least one the ff problems: floor control management, minimal change to original protocol, dependence on other applications for collaborative features.

##Solution
* Extend THINC rdp and provide solutions to the problems stated above
	- 'THINCing Together' allows different levels of screen-sharing:
		1. Single User Mode
		2. Unmanaged Mode
		3. Managed Mode
	- 'THINCing Together' allows switching from hardware cursor to software cursor (e.g. like using VirtualBox and alt-tabbing out to get to main desktop)
	- 'THINCing Together' is application-independent regarding collaborative functions

* Test 'THINCing Together' with other RDPs which support collaboration
	- Slow-motion video benchmarking
	- Cursor updating/drawing
	- Web benchmark

## Conclusion
*  "THINC protocol design was flexible enough to allow for synchronous sessions"
*  "THINCing Together has a negligible impact on performance over a version of the THINC system without multi-user functionality, and compares favorably to Collaborative VNC"