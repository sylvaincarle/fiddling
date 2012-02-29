# HTTP made even easier.

## A simple tutorial, providing code and context.

Writing a _simple_ tutorial explaining HTTP is nothing but _simple_.

To achieve this goal, some material has to be omitted. We will focus on the basic functionnality of th HyperText Transfert Protocol.

This howto is written with web developers in mind. It is not for programmers interested in developping HTTP librairies. We will assume a certain level of abstraction that is provided by most modern http-aware programming languages.

### Some assumptions

* You searched the internet for "http tutorial" and found the document at [http://www.jmarshall.com/easy/http/]. Altought you could follow along a bit, you don't want to have anything to do with sockets or CGI...

* You have a basic understanding of the web. You know your **browser** _calls_ a **server** to get a _page_ (there is much more to it, but at least you get that part).

* You know that if you wanted to read the HTTP 1.1 specification, you could go to [http://www.w3.org/Protocols/rfc2616/rfc2616.html] (or you don't and even if you did, it would not help you much).

* You are ready to learn more (duh)!

### Overview of the main the main concepts

Quoting from "HTTP Made Really Easy" :

> Like most network protocols, HTTP uses the client-server model: An HTTP **client** opens a **connection** and sends a **request** message to an HTTP **server**; the **server** then returns a **response** message, usually containing the **resource** that was requested. After delivering the **response**, the server closes the **connection** _(making HTTP a stateless protocol, i.e. not maintaining any connection information between transactions)._

Let's recap this with a simple schema, the initial **request** then the **response**:

    [client] --(connection)----> (request) ----> [server]

    [server] ----> (response) --(ressource)----> [client]

The last important bit of information is that the format of the **request** and **response** message are the same. You have the main content of the message, also know as the **body** preceded by **headers**. These **headers** could be seen as the information someone would write on an enveloppe when sending a letter via the good old postal system. **Headers** are meta-information, information about the information in the **body** and also special instructions or _questions_ passed from the **client** to the **server** and vice-versa.

Let's look at a simple example, getting a the document of the HTTP 1.1 specification from the World Wide Web Consortium server, calling this specific **URL** (also called a *URI*, more on that later):

    GET http://www.w3.org/Protocols/rfc2616/rfc2616.html HTTP/1.1

* GET is the **method**. It is the instruction, the **request** the **client** is sending to the **server**. GET me the _rfc2616.html_ file (**ressource**) that can be found in the _Protocols/rfc2616/_ folder on the **server** that answers sent to the address _www.w3.org_ using the **HTTP* **protocol** _http://_ using the version _HTTP/1.1_ of this communication **protocol**.

The **server** will first reply with a **status** message:

    HTTP/1.1 200 OK

* This **status** has three parts, the version _HTTP/1.1_ (same as the one requested), a **response status code** _200_ (this means in http parlance: everything is fine) and a short, human readable version of the **status code**: _OK_ (that one was easy).

There is a whole bunch of **status codes**, there is a good list at [http://en.wikipedia.org/wiki/List_of_HTTP_header_fields] and the definitive ressource for all header fields codes and name (not just for HTTP) can be found at [http://www.iana.org/assignments/message-headers/perm-headers.html].

There is also a useful (if dated) list at [http://www.cs.tut.fi/~jkorpela/http.html].

It gives a pretty good idea of the usefulness of the different headers available. They are used to define what type of content can be accepted (_Accept: text/plain, text/html_), the language (English, French, etc) and a bunch of information about the specific browser requesting the information, where the **request** comes from (**referer**, note the historical mispelling still in use today) and other meta information, such as the length of the content, the compression method, the modification date (**If-Modified-Since**)... There can be many, many **headers** sent before the **body**.

### A simple example to follow along

* Using Firebug

* Details ToDo

### Understanding what is happening, some tools to help you

* Live HTTP headers for Firefox - https://addons.mozilla.org/en-US/firefox/addon/live-http-headers/
* Firebug - http://getfirebug.com/network
* Using the "network" tab in the developer tools - https://chrome.google.com/webstore/detail/mgekankhbggjkjpcbhacjgflbacnpljm
* HTTP Headers for Chrome - https://chrome.google.com/webstore/detail/hplfkkmefamockhligfdcfgfnbcdddbg
* HTTP Response Browser - https://chrome.google.com/webstore/detail/mgekankhbggjkjpcbhacjgflbacnpljm
* Ressource page from the W3C (list several options) - http://www.w3.org/International/questions/qa-headers-charset
* Using CURL - http://curl.haxx.se/docs/httpscripting.html
* Charles, web debugging proxy application - http://www.charlesproxy.com/

### What is OAuth, how does it work with HTTP headers?

* See [this other tutorial] (http://not.done.yet/oauth) 

### How to "unstuck" yourself

* a few tips for debugging your headers

### Some other ressources (pun intended)

* [How does the Internet work?] (http://tldp.org/HOWTO/Unix-and-Internet-Fundamentals-HOWTO/internet.html)
* [How the web works: HTTP (and CGI) explained] (http://www.garshol.priv.no/download/text/http-tut.html)
* [HTTP Made Really Easy] (http://www.jmarshall.com/easy/http/)
* [http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol]
* [The **canocical** reference at W3C] (http://www.w3.org/Protocols/rfc2616/rfc2616.html)