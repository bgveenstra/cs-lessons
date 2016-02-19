---
title: How Computers Communicate
type: lesson
duration: "1:15"
creator:
    name: 
    city: SF
competencies: Computer Science
---


# How Computers Communicate

### Objectives
*After this lesson, students will be able to:*

- Explain how data is transmitted between computers.    
- Define "packets" and "sockets" and explain the significance of each.   
- Recognize and describe fundamental internet protocols and systems: TCP, IP, and DNS. 

### Preparation
*Before this lesson, students should already be able to:*

- Explain the client-server model.   
- Identify HTTP verbs and their uses.   
- Programmatically make requests to servers.   

Today we'll look at how information is sent between computers across the internet.


## What is the internet?


*cats and memes*   
<img src="http://www.mindthesciencegap.org/wp-content/uploads/2013/07/the-internet-1024x691.jpg" width=70% alt="cat astride a laser-eyed, fire-breathing unicorn">

*a "web" of routing paths*   
<img src="https://mountpeaks.files.wordpress.com/2012/03/1069646562-lgl-2d-4096x40962.png" width=70% alt="Visualization of the routing paths of the Internet in 2003, from Barrett Lyon's Opte project">


The internet is a bunch of computers connected together, communicating with each other according to some protocols. A protocol is just a set of rules.

## Communication 

Computers act on 0s and 1s -- so how does complex data like an HTTP request get transferred from your computer to one that may be on the other side of the world -- and back?

Your computer tranlsates the data all the way to 0s and 1s, which are sent electronicly and reconstructed on the other side.  It's AWESOME.

Computer scientists often think of this process as happening in layers. The data we care about as application developers - flash messages, user data, site content - is at the top layer. Various protocols specify how that top-level information should be wrapped up and sent "down" until finally it's translated to 1s and 0s and sent out.  Each level the information goes "down," it's encapsulated in another layer of header and/or footer information.  Internet protocols also specify how that packaged data should be routed around the many computers in the internet -- it usually takes many hops for data to move from its source computer to its target.  As web developers, we usually don't have to worry about anything but the topmost layers. However, getting a basic idea of how the internet works should demystify some aspects of web development and help you prepare for hosting your own sites.


<img src="http://s.hswstatic.com/gif/internet-diagram.gif" alt="request-response cycle diagram" width=70%>

## The Internet Protocol Suite

Since the internet works across many layers, it's built up of many protocols. These get lumped together in the phrase "the internet protocol suite." Its main responsibilities are addressing and routing. 

### Addressing: URLs, IP addresses, and DNS

Humans like to interact with websites through URLs or URIs because these tend to look like words and are convenient for people. Computers use IP addresses. You've probably heard of an "IP address" if you've set up a printer or had to deal with network issues.  There are two kinds of IP addresses. The older version, IPv4, uses 32 bits to specify an address. IPv6 uses 128 bits, which means there are a lot more possible unique addresses.

General Assembly as a physical address and some GPS coordinates:

```
General Assembly
225 Bush St. 5th Floor
San Francisco, CA

Lat: 37.790834
Lng: -122.401572
```

General Assembly could have a hypothetical URL and IP address:
```
http://sf.california.us/streets/bush/buildings/225?floor=5

38.140.30.202
```

| Protocol | Host (subdomain, domain, top-level domain) | Path | Query String, with Parameter "query" that has value "one bedroom" |
| :---------- | :---------- | :---------- | :---------- |
| https:// | sfbay.craigslist.org | /search/apa | ?query=one+bedroom |


The system that helps translate URLs to IP addresses is called the Domain Name System, or DNS. Physically, the Domain Name System is made up of Domain Name Servers, servers that store large lists of urls and the corresponding IPs. When you send data (like an HTTP GET request) to a url, your computer starts by looking at a list of stored IP addresses it keeps. If you visit google.com frequently, your computer probably caches its IP address so that you can connect to it very quickly. When your computer doesn't know the IP address for the URL, it begins a process of domain name resolution. 

[DNS resolution graphic](https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/An_example_of_theoretical_DNS_recursion.svg/563px-An_example_of_theoretical_DNS_recursion.svg.png)

Domain name resolution invovles connecting to a Domain Name Server and asking whether that server knows the IP address for the URL you want to visit.  If that server knows the IP address, you're done.  More often, the first domain name server will refer the requested URL to another domain name server. Generally, the process starts with at a root domain name server, which directs the request to a domain name server that knows lookup information for the correct top-level domain (.org, .com).  This server then directs teh request to a domain name server that knows lookup information for the correct domain (craigslist.org).  If the IP address for the URL isn't there, the request will be sent to a machine with lookup information for the subdomains (www.craigslist.org).  If the URL can't be resolved into an IP address at all, you can see an error in your browser saying "DNS lookup failed!"


### Routing: TCP/IP (Transmission Control Protocol/Internet Protocol)

TCP and IP were developed by the United States Department of Defense. We usually lump these protocols together as TCP/IP, but they're two separate sets of rules. 

IP, the Internet Protocol, controls how data is packaged into "packets" that are sent across the internet.  IP forwards the packets based on IP addresses in the header of each packet. It also defines the structure of IP addresses. IP is the lower-level protocol that controls routing of these packets around the internet. Every time a message arrives at an IP router, it decides where to send that packet next. It usually makes the decision 

TCP is higher-level than IP (it wraps up data before sending it down to the IP layer). With the information it adds, it makes sure data sent over IP is transmitted reliably.  This information is used to check for errors and make sure data arrives complete and in order.  If a problem is detected, TCP triggers retransmission. 

Sockets are the software that provide access to TCP/IP on most systems.


## Independent Practice (15 mins)

What happens when you go to https://www.generalassemb.ly?


This classic interview question captures the idea that web developers should know how the web works.  In groups of 3 or 4, discuss what happens when you open your browser, type in a url (you can use generalassemb.ly), and hit enter. One person should take notes. Try to fill in as much information as you can.

We'll come back together in 15 minutes and create our class picture of what happens when you go to a url.

> Did you think of server-client architecture? Mention events that might fire on the front end for the enter key? Talk about a get request being made to the server?  

## Conclusion

Let's create a class version of our answers for "what happens when you go to generalassemb.ly"!


## Further Resources

[IPv4 vs IPv6](https://www.youtube.com/watch?v=aor29pGhlFE) - short video on all this

[The Mystery of the 500 Mile Email](http://www.ibiblio.org/harris/500milemail.html) - fun reading
