# HTTP Overview

Protocol used by browsers to interact with web servers

## Pro tip: Web Dev is all about network

- Know the in/out of HTTP
  - network problems = your/users problems
  - much more problems than you are aware of
- State of the Industry: majority of devs don't know it as well as they should
  - Massive perf/security problems
    - URLs
    - GET vs POST
    - Cookies
  - "Layer 8"  Error Correction aka the "meat layer" 
    - humans/manual error correction

## Hyper Text Transer Protocol
- **application layer protocls** (e.g. SMTP, IMAP, NNTP, FTP, etc.)
  - defines standard way 
    - clients request data from servers 
    - servers respond to requests
  - typically running on top of TCP/IP

- 3 versions intially used (0.9 1.0 1.1) w/ 1.1 commonly used today
  - RFC 1945 HTTP 1.0 (1996)
  - RFC 2616 HTTP 1.1 (1999)

> IETF issue RFCs, this is a NETWORK protocol. It's not handled by W3C (html, css, etc.) or ECMA (ecmascript javascript)

## HTTP and TCP/IP

HTTP sits on top of the TCP/IP Protocol Stack
- Application Layer: HTTP
- Transport Layer: TCP
- Network Layer: IP
- Data Link: Network Interface

## Lower Layers affect Upper Layers

- many small individual objects together compose a web page
- v1.1 + varioud ev best practices try to help address poor perf    bundling

## Basic HTTP Req/Resp Cycle

- Web Client ("User Agent")
  - sends: request (opt encrypted w/ SSL)
  - receives: response

- Network
  - DMZ
    - Proxy
    - Local DNS
  - Internet
    - Transparent Proxies
    - DNS
      - External
      - Root
  - Reverse Proxy
  - Hosting Provider Network
    - Firewall
    - HTTP Server

- Web Server
  > TODO: fill from slides
  - Databases

> Storytime: Angry client about picture quality. Server is serving properly, accelerated proxies (cheaper) 
>
> Educating client on the reason (America Online)
>
> Remember to think "maybe my data didn't get through as intended"

## Mind your Proxies

Proxies are HTTP Intermediaries
- all act as both clients and servers
- friend and foe to WEb Devs --> you should ackowledge them

> TODO: revisit slides
 
1. Security
2. Performance
3. Content Filtering

## The Law of Three Redux

- 3 pieces to form of HTTP request/responses
  - server-side prog understand only get data from those 3 pieces
    - consider input and watch carefully
  - Can only output 3 pieces of response (mostly message)

```
1. Req/Resp line
2. Headers
\n\n
3. Message Body / Payload
```

Ways to debug
1. cmdline tools
   - curl, wget, Invoke-WebRequest, Invoke-RestMethod
2. HTTP/REST debug tool
   - Postman, paw
3. Proxy
   - Fiddler
4. Dev Tools
   - Console, Network, Sources, Elements

## Headers

### Aside: Detecting Bots
- IP/fingerprint --> proxies, vpn, botnets
- Usage metrics --> randomization
- "throw a Captcha at your ass" --> try to train AIs
  - redirect them to humans, have solve them for you 
    "get access to service in exchange for solving this Captcha"

> Captcha ==> Killing ants with atomic bombs. Do not do overkill

Content-Type: tells browser how to render/execute resource
- MIME sniffing

> Tradeoffs: security vs convenience

Most frameworks by default will issue NOT FOUND with 200 statuses
- web crawlers and search engine bots will index these pages since they rely on the response status

Option to "Use POST/GET only"
- wrapper for other methods, specifying within headers the "X-real-http-method" for example
- workaround for proxies that might not allow those methods

## Jargon time

**safe**: does not modify server

**Idempotent**: repeatable w/ same effect and server stays in the same state

> TODO: revisit slides

## HTTP Response

1. HTTP Version SP
2. Status Code SP
3. "Reason Phrase" CRLF

```
1xx: informational
2xx: success code
3xx: alt resource locations (redirects)
4xx: invalid
```

> TODO: revisit slides

