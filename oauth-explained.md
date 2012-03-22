# OAuth Explained

## Introduction

OAuth 1.0 (and later 2.0) was created to give a standard way to access data as an **authentified** user from one service (or API) to another without giving away your password to the other service. Some service would require you to give them your username and password to import data from a third pary service. One exemple would be importing your contacts email addresses from your GMail to find "friends" on another web service. This is aptly called the [password anti-pattern] (http://adactio.com/journal/1357/), you can read a bit more on the rationale of why OAuth was invented. One metaphor commonly used to explain OAUth is the _valet key_: you can give limited access to your car with this key, but not complete access.  

## Notes

* OAuth 2.0 is not backward compatible with OAuth 1.0, it's a new protocol.
* Most OAuth 2.0 services requires SSL connections.
* It has the same concepts but some key differences (mostly around cryptographic **signatures** requirements that are optional in 2.0).
* If you are serious about OAuth I recommend that you buy a copy of * [Getting started with OAuth 2.0 book by Ryan Boyd] (http://shop.oreilly.com/product/0636920021810.do). It describes in greater details all the concepts we summarize here (and more). This primer is partly based on this book and other web ressources (see the _reference_ section at the end of this document).

## Terminology

Understanding OAuth requires naming concepts and understanding them. In this primer, all terminology is in **bold** to help you grasp the most important concepts.

OAuth define **flows*, typical use cases (or patterns) of **authentication** and **authorization**.

**Authentication** is verifying the identity of a user. With most internet services this typically done by requesting a username and a password.

**Authorization** is usually done after **authentication**. Once a user is **authenticated** the service can apply rules that would give access (or not) to specific data or features.

**Delegated Authorization** is the main reason _why_ OAuth was created. At it's core is the _passing_ of your **authorization** to another service, without requiring your password. This **delegated autorization** is often to access your data or pose an action on your behalf, for exemple sending a message on Twitter from a website where you are commenting to your Twitter timeline. Often on services where many applications use **delegated authorization** you can find a trace of the service that did an action on your behalf, the "via" information under a tweet is a good exemple.

## Roles

Since OAuth is used to define the actions of multiple parties in a specific **flow**, you need to understand what are the actors and what **roles** they can play.

The **ressource server** is the actor hosting the data or actions that requires OAuth to access. Think of it as the _source_ of the information that will be passed to the requesting service.

The **ressource owner** is the user of an application or a service, the actor that needs to give permission before the third party service can get access.

The application making the request to access a user **ressources** is called the **client**. This **client** will act on the user's behalf once the user has **delegated authorization**. The **client** is also sometimes called the _consumer_ in some services ()

The last actor is the *authorization server**, the maestro of the OAuth symphony, managing the *authorization* from the user (ressource owner), issuing **access tokens** to the *client* application so that it can request data or act on behalf of the user from the **ressource server**.

Let's recap this with a simple schema to understand all the actors involved in a **user-agent flow** (more on **flows** later)


[**client**] --(requests)----> (access to ressource) ----> [**authorization server**]

[**authorization server**] ----> (prompts) --> [**ressource owner**] ----> (accept/deny)

[**authorization server**] ----> (emits **tokens**) --> [**client**] ----> (access to ressources granted)

[**client**] -- (requests on behalf of **owner**, with **tokens**) ----> (ressource) ----> [**ressource server**]

[**ressource server**] -- (validates tokens) -- (grants access to ressource) ----> [**client**]

It's not _that simple_ but I hope you get the gist of it!

## Registration

OAuth requires a registration with the **authorization server** prior to sending requests from a **client**. For most APIs and services, this has to be done via a web form for developers, usually in conjonction with requesting an API key and giving a little bit of information about your intended use of the service. Once registered, you will get your **client** credentials to **authenticate** all the requests sent to the **authorization server**.

## Flows

### Web Server (or Server Side) Flow (Ruby, Python, PHP, etc.)

### Client Side (or User Agent) Flow (Usually with Javascript)

### Mobile Flow

### Desktop Flow

### Limited Device Flow

## Concepts not covered in this primer

* **Federated Authentication**
* Username and Password Flow
* Client Credential Flow
* Assertion Flow

## References

* [OAuth 2.0 specification] (http://oauth.net/2/)
* [Introduction to OAtuh 2.0] (http://hueniverse.com/2010/05/introducing-oauth-2-0/)
* [Getting started with OAuth 2.0 book by Ryan Boyd] (http://shop.oreilly.com/product/0636920021810.do)