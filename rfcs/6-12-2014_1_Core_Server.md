Core Server
=====

Explanation
-----------

The Core Server is the most fundamental building block of the **C Server**.
It acts as the connector between requests and the way they are handled.
Thus it is meant to be built waiting-free and multi-threaded.

C Server is meant to be running behind a reverse proxy, making it similar to
other web servers. This limitation also comes with less responsibilities, easing
the implementation as far less details need to be considered.

### 1. The Core Server

The Core Server itself manages incoming requests through a tcp socket. It then
uses its loaded modules to respond to the request. It does so by looking up its
own list of loaded modules. Each module has to be registered on load. This data
is then used to process the request. Modules are covered in their own section.

The basic component one needs for a request is a router. A router decides, based
on the request what should happen next. The simplest router could simply decide
to reject all requests.

### 2. Task Queue

Today the responsiveness of a webserver is limited by mostly two things, network
bandwidth, and IO Operations. **C Server** tries to mitigate the time waiting on
the latter by using a task queue. The basic premise is that if a thread is about
to block it defers this by putting the current task into the background, waiting
for the IO Operation to be done before allowing it to be handled again.

Possible Drawbacks
------------------

[ Explain what problems could be encountered by implementing this ]

To be done
----------

[ List what would have to change so that this functionality is implemented ]

Alternatives
------------

[ List alternatives that you know of as well as others might have pointed out
in the comments ]
