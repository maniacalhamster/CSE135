# L2 - Web Mental Models

## 5 Pillar Model

Applied to Design:
- Purpose: Content & Function
- Structure: Architecture
- Execution: Coding
- Distribution: Hosting
- Form: Visuals & Layout
    - ultimately, this is what matters

Better than fixating on specific success stories:
- Google: simple
- Amazon: not so simple - conflict

Environment & Sub-system specific
- Domain-driven design in web

## 3 Participant Groups

> Humans are not deterministic

Maintain a balance of Needs & Wants b/w:
- Devs & Designers
- Site/App owners
- End Users

## The Vast Web Medium

- Client Side
  - HTML, Browser, Scripting, etc.
  > Fundamentally out of your control
- Server Side
  - Web Server
  - connecting CGI Program
  - Backend database
  - Server API programs (ISAPI, NSAPI)
  - Server side scripting pages (Active Server Pages, etc.)
  > Language Neutral. Prof says PHP is the easiest for setting things up
- Connecting Network
  - Very hard to control

> Spouting stacks w/o problem analysis is Solutionism

## Medium in Context

Question: Chart generation. Where should it happen?

Server-Side Argument
- beefier in terms of computation power
- required resources are close at hand
- BUT would have to send generated chart as an img or something. NOT interactive

Client-Side Argument
- allows interactivity 
- variable computational power - at the mercy of the user device (laptop, tablet, phone, headless server, etc.)

Both:
- prio server side 
- optional client sid for interactivty 

## Toolbox Overflows

- Software Tools
- Acronyms and Concepts
- Ideas/Models
- Standards
- Ideologies

> Recently, AI is a very doomsday-style FOMO

## Dimensions

- Execution: server vs client side
- Network: public vs private
  - Code complexity/effort (simple/easy <-> complex/hard)
- Performance (lower <-> higher)
  - Often related to complexity
- Platform Specificity (Specific <-> General)
  - AKA Portability
- Coupling (Tight <-> Loose)
  - Often related to Platform Specificity

> HTML is foundation, like concrete. You can't really

## Web Programming Toolbox 2.0

- Client Side
  - Browser Extensions
- Server Side
  - Server API Programs
- Java Applets
  - Client-Side Scripting
- Java Servlets
  - Server-Side Scripting
- Helper Applications
  - Scripted vs Compiled
- CGI Programs

> There are no golden hammers. Things are rarely as direct as "this is the best" trade-offs abound!

 "As C is to Unix, Javascript is to Web"

## Maturity Safety Matrix

```
Usage     

High    | M $$  S $
        | 
Low     | D ??  D $$$
        +-----------
          New   Old
          Maturity
```

> End User doesn't care about implementation details

Avoid Scapegoating
- e.g. blame tech, process, least liked person, etc.
- only avoids accountability

Once you get old enough, you hate all things equally

## Super Simple View - Data Collection

Client Side
- lots to collect
- will eventually have to transmit collected
- ACTIVE

Server Side
- only collect from incoming request
- PASSIVE

Network
- proxy/sniffer could collect
- also only collect from requests 
  - but OTHER requests too

> More data $\ne$ Better. 
> Massive volume takes 

WikiPedia is REFINED
- can fit it into your drive
- takes up 2 rows of shelves in Geisel 

## Simple Fetch

Do we know URLs that well?
- Case Sensitivity: Y
- Max Length: depends on software/protocols carrying the packets + hardware that handles them 
- do we need wwws?
- trailing slashes?
- Port numbers?

> "I can train skill but I can't train attention and attitude"

## URLs Aside

- Uniform Resource Locator 
  - https://url.spec.whatwg.org/
  - https://datatracker.ietf.org/doc/html/rfc3986

- History
  - Uniform Resource Identifier:
  - Uniform Resource Name
  - Uniform Resource Characteristics: various \<meta\> data approaches

- Think abstractly about a "space" of information, "Book Space"
  - Instance of a book?
    - Finding it
    - Multiple copies
    - "canonical version"?
  - Unique identifier (ISPN?)

> Information Theory isn't specific to the web

Dirty URLs: not human-readable

Good URLs
- Short
- understandable
- permanent
- avoiding revealing implementation details or other "wiring" if possible (aka Dirty) as opposed to clean and simple

## Data URLs

`data: [media MIME type] [; encoding ], < data >`


> **The localhost effect**. Remember to test your implementation on VARIOUS device and environment emutations (e.g. slow networks)

Sampling Bias. If people don't stick around long enough to experience the rest of your site.

## Live Demo: UCSD site

Fast 3G loadup: ~30s

Non-visual changes, optimizing w/ bundling etc.: 4.2s

Industry prefers the "quick and dirty" methods. AI will recc what's popular, not what's efficient.

> Online purchases "for the love of god, don't press the back button" --> indication of bad web design. 
> State of industry: Instead of doing design properly, just cover up big red buttons :

Vestigial historical tendencies: sending individual files instead of bundling
- olden days: modem-based slow network speeds --> loading a single large file would take forever
- copy-cat/monkey see monkey do --> still hanging onto old practices

> Conditionally: some companies adapt, e.g. google w/ new QUIC protocol

Golden rules of Performance
- Less Data: compression, reduction, etc.
- Less Often: caching
- From nearby: CDNs / installing on browser
- Only when needed: lazy-loading, etc.

> Most of you don't need AWS. It's a premature optimization. 
> Break out of the "don't know" and sheeping cycle w/ Data Analytics

-- StackOverflow is monolithic but runs on a few servers, not hosted on cloud infrastructure or anything.

> For use to measure, we need to inherintly understand how the underlying mechanisms work.

Simple Metrics won't work
- 58 resources loaded = 58 hits. For just that one page view.
- just page view doesn't work either. Some site will milk the user to load in more pages for the views.