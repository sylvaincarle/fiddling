# OAuth Explained

## Introduction

OAuth 1.0 (and later 2.0) was created to give a standard way to access data as an **authentified** user from one service (or API) to another without giving away your password to the other service. Some service would require you to give them your username and password to import data from a third pary service. One exemple would be importing your contacts email addresses from your GMail to find "friends" on another web service. This is aptly called the [password anti-pattern] (http://adactio.com/journal/1357/), you can read a bit more on the rationale of why OAuth was invented. One metaphor commonly used to explain OAUth is the _valet key_: you can give limited access to your car with this key, but not complete access.  

## Notes

* OAuth 2.0 is not backward compatible with OAuth 1.0, it's a new protocol.
* It has the same concepts but some key differences (mostly around cryptographic **signatures** requirements).
* If you are serious about OAuth I recommend that you buy a copy of * [Getting started with OAuth 2.0 book by Ryan Boyd] (http://shop.oreilly.com/product/0636920021810.do). It describes in greater details all the concepts we summarize here (and more). This primer is partly based on this book and other web ressources (see the _reference_ section at the end of this document).

## Terminology

Understanding OAuth requires naming concepts and understanding them. In this primer, all terminology is in **bold** to help you grasp the most important concepts.

OAuth define **flows*, typical use cases (or patterns) of **authentication** and **authorization**.

**Authentication** is verifying the identity of a user. With most internet services this typically done by requesting a username and a password.

**Authorization** is usually done after **authentication**. Once a user is **authenticated** the service can apply rules that would give access (or not) to specific data or features.

**Delegated Authorization** is the main reason _why_ OAuth was created. At it's core is the "passing" of your **authorization** to another service, without requiring your password. This **delegated autorization** is often to access your data or pose an action on your behalf, for exemple sending a message on Twitter from a website where you are commenting to your Twitter timeline. Often on services where many applications use **delegated authorization** you can find a trace of the service that did an action on your behalf, the "via" information under a tweet is a good exemple.

## Roles

Since OAuth is used to define the actions of multiple parties in a specific **flow**, you need to understand what are the actors and what **roles** they can play.




## Concepts not covered in this primer

* Federated Aythentication


## References

* [OAuth 2.0 specification] (http://oauth.net/2/)
* [Introduction to OAtuh 2.0] (http://hueniverse.com/2010/05/introducing-oauth-2-0/)
* [Getting started with OAuth 2.0 book by Ryan Boyd] (http://shop.oreilly.com/product/0636920021810.do)