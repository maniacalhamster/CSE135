# Server-Side Programming

## Web Server Roles

- File Servers
  - static assets
  - web pages
- Application
  - run code
  - serve results

Running apps requires
- Understanding program triggers
  - Route/url
  - File extension
- How data is sent in
  - Query String
  - Message Body/Payload
  - Headers
- How data is returned
  - Formatting
  - MIME

## Simple Programming Flow

1. Read some data
2. Perform some processing on the data
3. Output some results

Though rudimentary, most all code can be reduced to this

## HTTP Law of Three

```
GET / HTTP/1.1          # Request/Response Type
                        # [Method] [Path] [Standard]

Host: example.com       # Headers
User-Agent: Chrome      # Key: Values
Accept-Language: en
/n/n


<Data payload or empty>
```

> When it comes to adopting tools,
> 1. understand what it is/what it does
> 2. "walk the property"

Submitting Forms
- GET: query strings
- POST: payload

![](images/2023-04-18-09-55-31.png)

On ChatGPT:
- LLM. 
- There are common beliefs + pop sciency explanations

## The Program

Treat HTTP request as `stdin` and your `stdout` gets piped back out to browser

Any program, in a sense, can be a web program as long as it understands what it is reading and writing

## Getting Data Back to Client

Set appropriate type value of data returned
- `Content-Type`
- MIME

Relying on MIME sniffer is a security issue
- MIME smuggling: renaming file ext ("I'm not a virus")

## Redux-3 Server-side Programming Models

### Mastering the basics: CGI

> AWS Lambda is just a glorified CGI-BIN

Common Gateway Interface (CGI)

Defines a way for external programs to be run on Web Servers
- the way data is read by external programs 
- the expected return

Prof's "Hamburger" model, while others have some "onion" model

#### Pairing Problem: CGI and Perl

Associations
- Python and Data Science
- JavaScript and Web Dev

Why the association?
- Perl commonly found on UNIX --> first Web Servers
- Perl common used by sysadmins
- Good string maniulations --> main tasks when writing web program
- Pretty easy to hack around with
- Interpreted language --> to blame for CGI speed problems
  - Soln: use mod_perl
  - Best Soln: recompile as C program

```perl
print "Content-type: text/html\n\n";
print "<html><head><title>Hello!</titl>";
print "</head><body bgcolor='yellow'>\n";
print "<h1>Hello from CGI w/ Perl</hw>\n";
print "</body?\n</html>";
```

- Notice the Content-typ header... That's 50% of the CGI's "magic"
- in this case, we use a pl extension though you might want to use .cgi or even better something else or even nothing
- Prob placed code in `cgi-bin` dir
  - Good practice in some ways, but again change the name
  - organization
  - security: apply perms to the bin dir

> Note: we should prob use the `~!/usr/bin/perl -wT` to invoke Perl. 
> - `w` flag shows warnings 
> - `T` flag turns on taint checking which checks incoming data a little more carefully.

```c
#include <stdio.h>
main()
{
    printf("Content-Type: txt/html \n\n");
    print ("<html><head><title>Hello!</titl>");
    print ("</head><body bgcolor='yellow'>\n");
    print ("<h1>Hello from CGI w/ Perl</hw>\n");
    print ("</body?\n</html>");
}
```

#### Don't Re-invent the Wheel

There isn't much to do in CGI (nor really in server-side env)
- main task: read user submitted data --> write HTML + headers
- real programming is outpu

Plenty of room to screw-up

Utilize a library
- diff from React coz you actually have to KNOW the wheel first

#### Environment Variables

vars unique to the request/time/etc.

HTTP_: request headers

SERVER_: response headers

1. Easier to think about what to do --> figure out syntax NEEDED
   - Mastery of syntax is overrated. Much more efficient to look up what you need than know what you don't

2. Query for what you know and expect. Never just trust a whole packet submitted

3. If you receive unexpected data or data type --> just reject it

#### CGI Troubles

- Insecurity issues
  - Often programs set to run at higher perms than they should be
  - sometimes people use shell
    - some people run things as root too!
  - again devs trust input way too much
    - XSS
    - code injection
    - etc.

- Speed issues