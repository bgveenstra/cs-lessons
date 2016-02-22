---
title: How Computers Communicate
type: lesson
duration: "1:20"
creator:
    name: 
    city: SF
competencies: Computer Science
---


# How Computers Communicate

## Intro (5 minutes)
### Objectives
*After this lesson, students will be able to:*

- Explain how data is transmitted between computers.    
- Define "packets" and "sockets" and explain the significance of each.   
- Recognize and describe fundamental internet protocols and systems: HTTP, TCP, IP, and DNS. 

### Preparation
*Before this lesson, students should already be able to:*

- Explain the client-server model.   
- Identify HTTP verbs and their uses.   
- Programmatically make requests to servers.   

Today we'll look at how information is sent between computers across the internet.


### What is the internet? 


*cats and memes*   
<img src="http://www.mindthesciencegap.org/wp-content/uploads/2013/07/the-internet-1024x691.jpg" width=70% alt="cat astride a laser-eyed, fire-breathing unicorn">

*a "web" of routing paths*   
<img src="https://mountpeaks.files.wordpress.com/2012/03/1069646562-lgl-2d-4096x40962.png" width=70% alt="Visualization of the routing paths of the Internet in 2003, from Barrett Lyon's Opte project">


The internet is a global system of interconnected computers that communicate with each other by sending data packets according to a series of protocols. (A protocol is just a set of rules.)  

## Overview (10 minutes)

Computers act on 0s and 1s -- so how does complex data like an HTTP request get transferred from your computer to one that may be on the other side of the world -- and back?

Your computer tranlsates the data all the way to 0s and 1s, which are sent electronicly and reconstructed on the other side.  It's AWESOME.

Computer scientists often think of this process as happening in layers. The data we care about as application developers - flash messages, user data, site content - is at the top layer. Various protocols specify how that top-level information should be wrapped up and sent "down" until finally it's translated to 1s and 0s and sent out.  Each level the information goes "down," it's encapsulated in another layer of header and/or footer information.  Internet protocols also specify how that packaged data should be routed around the many computers in the internet -- it usually takes many hops for data to move from its source computer to its target.  As web developers, we usually don't have to worry about anything but the topmost layers. However, getting a basic idea of how the internet works should demystify some aspects of web development and help you prepare for hosting your own sites.



<img src="http://s.hswstatic.com/gif/internet-diagram.gif" alt="request-response cycle diagram" width=70%>


## Internet Architecture and the Internet Protocol Suite 

All those protocols that run the internet are considered part of the internet protocol suite. Internet architecture was originally described in a 1989 document by the Internet Engineering Task Force as having four layers, each with one or more protocols.  The layers are:

* Application Layer 
* Transport Layer 
* Internet Layer
* Link Layer

> Note: For the rest of the class, have a labeled diagram available on the board that students can look at for reference. Note labels and how information is "wrapped". 

> 
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/UDP_encapsulation.svg/800px-UDP_encapsulation.svg.png" alt="UDP encapsulation diagram" width=70%>

<!-- @TODO replace with TCPish version? -->

###Application Layer (5 minutes)

This layer is at the top of the internet protocol suite ("top" meaning nearest to what humans use and see). There are many protocols associated with the application layer, largely because different kinds of data are sent in different formats.  

These are common application layer protocols that provide services to users:

* HTTP - HyperText transfer protocol
* FTP - File transfer protocol
* SMTP - Simple mail transfer protocol (email!)

These are a few examples of application layer protocols that support system functions:

* SNMP - Simple network management protocol
* DNS Protocol - Domain name system protocol


This is the level web developers work on most, so we'll dive deeper into HTTP now and DNS a little later today.  HTTP is [the protocol every web developer should know](http://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)!  

#### Activity: Examine an HTTP request and response (10 minutes)

Open the Network tab of your chrome dev tools, and refresh the page you're looking at to prompt an HTTP request (what kind of request will this be?).   Click on one of the requests in the list of requests, and a new division should pop up to the side.  Check out the request and response headers. These tell you how data is wrapped by HTTP.  What do you think each header means?







###Transport Layer (5 minutes)

This layer recieves data from the application layer above and packages it with extra information for transport across the internet.

The two most common protocols used in the transport layer are:

* TCP - Transmission control protocol

TCP is used when transportation of data must be *reliable*. It is ideal for transfering files such as images, songs, or webpages.  It combines the application layer data with extra header information that allows it to check for errors, ensure the data is ordered correctly, and trigger retransmission if there was a problem. Once they've been wrapped up by TCP, these units of data are called "packets."

* UDP - User datagram protocol

UDP is used if it's more important that transportation of data be *fast* than that it be reliable. The side-effect is that data may become disordered or lost along the way. It is ideal for real-time media communication like video-conferencing.

Note: HTTPS is a secure version of the HTTP protocol; it uses a transport layer security protocol called Transport Layer Security (TLS) or on its predecessor, Secure Sockets Layer (SSL).  Many sites prefer HTTPS; you'll notice that all github and facebook urls start with "https."

###Internet Layer (5 minutes)

This layer is responsible for internet addressing and for forwarding data from one router to the next. The main internet layer protocol is IP, the Internet Protocol. IP receives information from the transport layer and wraps it up again, adding an IP header. So IP is the lower-level protocol that controls routing of TCP packets (or sometimes UDP datagrams) around the internet. IP also defines the structure of IP addresses. IP routers forward data based on IP addresses in the header and based on internet traffic information. Every time a message arrives at an IP router, it checks the IP address in the header, as well as some traffic information, to decide where to send that data next. (The "extra resources" video [A packet's journey](https://www.youtube.com/watch?v=ewrBalT_eBM) goes into this further.)

TCP and IP were developed by the United States Department of Defense. We usually lump these protocols together as TCP/IP, but they are two separate sets of rules.  "Sockets" are the software that provide access to TCP/IP on most operating systems.

Another protocol, the Internet Control Message Protocol (ICMP), deals with low-level messages related to IP datagram handling. It's used for the `ping` command, which you can use to check if your computer can reach another IP address.  (Try `ping 127.0.0.1` in your terminal to see an example!)

###Link layer (5 minutes)

There are billions of internet-connected devices, but they aren't all actually *directly* connected to the internet. They're connected together in smaller networks like Local Area Networks (LANs) or the wireless version, WLANs. The internet is actually a network of these smaller networks. 

The link layer is the lowest layer of the internet protocol suite, and it structures communication within these networks.  It's used for computers in the network to communicate with one another, with electric pulses that represent the data being transfered in binary.  Only one computer or "host" in each small network needs to be able to send packets through the internet; it will be connected to the internet through a modem.


Common protocols include:

* Ethernet
* ADSL


<!--Some poeple consider physical transmission (moving bits along wires) part of the link layer's job, but others say TCP/IP is hardware independent and doesn't specify anything about how bits should be transferred at the lowest level .-->


## A Closer Look at Addressing: URLs, IP addresses, and DNS (10 minutes)

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

![DNS resolution graphic](https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/An_example_of_theoretical_DNS_recursion.svg/563px-An_example_of_theoretical_DNS_recursion.svg.png)

Domain name resolution invovles connecting to a Domain Name Server and asking whether that server knows the IP address for the URL you want to visit.  If that server knows the IP address, you're done.  More often, the first domain name server will refer the requested URL to another domain name server. Generally, the process starts with at a root domain name server, which directs the request to a domain name server that knows lookup information for the correct top-level domain (.org, .com).  This server then directs the request to a domain name server that knows lookup information for the correct domain (craigslist.org).  If the IP address for the URL isn't there, the request will be sent to a machine with lookup information for the subdomains (www.craigslist.org).  If the URL can't be resolved into an IP address at all, you can see an error in your browser saying "DNS lookup failed!"

If you are part of a local area network, every computer on that network will have the same public IP address. The LAN will also assign each device a private, internal address. While the shared public IP address acts like a house's address, the private IP address for each computer acts like the name of one person living in that house.  

## Independent Practice (10 mins)

What happens when you go to https://www.generalassemb.ly?

This classic interview question captures the idea that web developers should know how the web works.  In groups of 3 or 4, discuss what happens when you open your browser, type in a url (you can use generalassemb.ly), and hit enter. One person should take notes. Try to be as detailed about the process as you can.

> Did you think of server-client architecture? Mention events that might fire on the front end for the enter key? Talk about a get request being made to the server?  

## Conclusion (15 mins)

Let's create a class version of our answers for "what happens when you go to generalassemb.ly"!

##Further Resources

* Video: [IPv4 vs IPv6](https://www.youtube.com/watch?v=aor29pGhlFE)
* Video: [A packet's journey](https://www.youtube.com/watch?v=ewrBalT_eBM)
* [The Internet: Bitesize  (BBC)](http://www.bbc.co.uk/education/guides/zp9jpv4/revision/1)
* [How Does the Internet Work? (Stanford)](http://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper.htm)
* [TCP/IP Fundamentals](http://www.thegeekstuff.com/2011/11/tcp-ip-fundamentals/)
* [The Internet Protocol Suite (Wikipedia)](https://en.wikipedia.org/wiki/Internet_protocol_suite)
* [HTTP Intro](https://dev.opera.com/articles/http-basic-introduction/)
* For fun: [The Mystery of the 500 Mile Email](http://www.ibiblio.org/harris/500milemail.html)
