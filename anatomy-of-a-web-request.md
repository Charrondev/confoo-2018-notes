# Anatomy of a Web Request

_Rob Richardson_ **@rob_rich** https://robrich.org

Typically a when lookin at a web request you look at a server pipeline. This is not the contents of this talk.

## What happens I type an IP into a browser

- Opens a Socker.
- Sends data.
  - HTTP method
  - url
  - http headers
  - http body
  - accept header (content negotiation)
  - user agent
- Server replies.
  - status code
  - headers
  - body
  - content length
  - content type
- Browser renders that reply.



## Status Codes

**2xx**: it worked

**3xx**: go look over there

**4xx**: error, use client's fault

**5xx**: error, server's fault

**1xx**: not done yet, but still here



## OSI Model

7 - HTTP

6

5

4 - TCP

3 - IP

2

1 - Wires

## TCP Packet

Max packet is 64k

TCP packets are usually under 1500 bytes

Ethernet frames are 1500 bytes

## TCP connection handshake

SYN w/ cookie + data

SYN ACK - Ackknowledge SYN and data.

Server can send responses before receiving ACK.

ACK

## TCP slow start

- Purpose: avoid over-saturation the connection.
- Start by sending a few packets.
- Check latency if responses.
- Assumes lack of response is due to congestion.
- Send more packets next time.
- Infer how fast it can go.

**Result** - Connection starts slow and speeds up as you use it.

## Resolving URL

What happens when I type a URL?

- ***Resolve url to ip***
- opens a socket to ip
- sends http packer
- server replies
- browser renders response

## DNS

**NS** record: "That guy is responsible for domain".

**A** Record: "here's the IP".

**CNAME** record: "Go ask that guy".

**MX** record: mail server.

**TXT** record: overloaded and used for everything.

**SPF** record: Mostly used for spam.

other: **AAAA**, **SRV**, **PTR**, etc.



**TTL**: how long *should* DNS servers cache this.

### How does the browser resolve DNS

Multiple layers of caching all the way down to the root DNS server.

- Browser asks it's DNS server
- It asks it's DNS server
- recursively until some knows or ...
- until one of the 13 root name servers answers.

Local computer -> Router -> ISP -> … -> DNS Root

### DNS example

- Browser asks for foo.com to my DNS server
- My DNS server doesn't know
- asks it's DNS server
- that server answers CNAME: ask bar.com
- My DNS server caches the answer then passes it on
- browser caches the answer
- browser asks for bar.com
- my DNS server knows
- answer with A: 123.45.6.7.89
- browser opens socket to 123.45.6.7.89
- browser sends http packet to http://123.45.6.7.89
- includes http header "hostname: foo.com"

## SSL - Resolving URL

- Resolve url to ip
- opens a socket to ip
- ***security stuff***
- sends http packer
- server replies
- browser renders response

Much longer handshake. Diffie-Hellman key exchange.

### What's the prupose of https urls?

Encrypt data in transit

Client verifies server

Server doesn't verify client (**that's client certificates**)

### How does the client verify server?

Client download certificate.

Client walks the trust chain.

Client finds someone/something that it trusted already (**CA / Certificate Authority**).

### What is encrypted

Everything apart from the hostname is encrypted so a server hosting multiple domains can respond with teh correct certificate.

TLS extension called **S**erver **N**ame **I**ndicator or **SNI**

### HTTPS startup

- TCP slow start
- TLS handshake
- Certificate download (can be big)
- Including trust chain

### HTTPs startup best practices

- Minimize certificate size.
- 2048 bit, sha256 ssl certificate is fine.
- Don't include a lot of extra domains.

## What happens when I type a url in chrome

- ***Resolve google url to ip***
- ***opens a socket to google***
- ***sends is this a url or a query***
- ***Google answers and returns suggestions***
- opens a socket to ip
- security stuff
- sends http packer
- server replies
- browser renders response

## Client concerns

- Stops at `<script> <link> <style>`
- Downloads linked resource
- Parses resource
- Applies changes (re-flow page if necessary)
- … need to get the cascade order right