---
title: Microservices Sharing Is Caring
theme: solarized
highlightTheme: rainbow
revealOptions:
    slideNumber: 'c/t'
    
---

# Microservices: Sharing Is Caring

#### @rachelcdavies @tes_engineering
![Tes Logo](./images/tes_logo.jpg)

Notes:  
Maintaining shared micro-services is a pragmatic approach to building resilient products.
At Tes, we have a dozen teams building products that use common shared micro-services for basic services, such as sending emails and authentication/authorization. Although the idea sounds simple, in practice sharing code between teams can be challenging. Shared services risk becoming polluted with product-specific details or turning into no-go areas that engineers fear to change. Come to this talk to hear about how we overcome these challenges at Tes and hear our tips for how to maintain a healthy set of shared micro-services.


---

## A bit about me

* Software engineer
* Work remotely from home
* XP/Agile fan since 2000

Notes: 
I've been working in software development since 1987. 
I worked in one of the first teams to practice Extreme Programming in London back in 2000. 
I became fascinated with the world of Agile software development and spent a decade avidly reading Agile books and participating in Agile conferences. 
I'm now a senior software engineer developing JavaScript micro-services at Tes.

---

## A bit about Tes

* Digital education company
* 200+ Javascript micro-services Node/React 
* 50+ full-stack engineers
* Remote-first culture

Notes: 
Who's heard of the Times Educational Supplement? 
We are more than a publication, we provide services that help schools recruit teachers and for teachers to share teaching resources. We support and connect teachers and schools worldwide, helping them to improve children's lives through education. 
A few years ago, our CTO Clifton Cunningham and VP of Engineering David Morgantini led a transition to a micro-services architecture building up product teams with ThoughtWorks alumni. I wasn't working at the company at the time so can't share much detail on how our remote-first got started but Martin Fowler was writing about remote-first at the time. Over the past few years we've established some ways of working that help us sustain remote working and I'll be sharing some more practical details of how Hack Days and Knowledge Sharing sessions underpin our remote working practice.

---

![Tes mission](images/tes-mission.jpg)

---

## About you?

![Hands](images/hands.jpg)

Notes: 
Add some questions here       


---

# Sharing?

![Care Bears](images/care-bears.jpg)


Notes: 
Why do we share?
* using existing services saves time
* reduce duplication

---

# Microservices?

![Snowflakes](images/snowflakes.png)

---

## Homogenous Services

* JS React/Node services
* REST / RabbitMQ 

Notes:
Built from ex-TWers about 5 years old
Stagnation vs Innovation

---

## People Architecture 

![Engineering Week](images/engineering-week.png)

Notes:
Remote workers so Slack channels
Conversations in the open vs provate channels
No architects
Federate everything?

---

## Organisation structure

* Cross-functional product teams for verticals
* Platform team responsible for infrastructure
* Data team for pipeline
* Security team support product teams

Notes:
* _New_ DX "group" 


---

## Distributed Leadership

![TesTeamRoles](images/TesTeamRoles.png)

Notes: 
The Principal Engineer at Tes is responsible for looking after 1 - 3 teams and ensuring that there are clear communication channels with other Principal Engineers (and thus the teams they were responsible for).
Small teams
---

## Package for consumption

![SharingFood](images/MenuSharing_web_hero.jpg)

---

## Sharing: Front-end 

![TesDesignSystem](images/TDS.png)
* Styled components (buttons, checkboxes)
* Styles (typography, colours)

Notes: 
Monthly front-end days.
Engineers who are interested.
Starts with a stand-up
https://www.tes.com/styleguide/elements/button

---

## Sharing: Backend Utilities

* Generating PDF documents
* Sending emails
* Sending SMS messages

Notes:
See Rouan blog post
https://techbeacon.com/app-dev-testing/4-ways-stop-your-shared-microservices-falling-apart
Some are open-source.

---

## Example

![ServiceExample](images/service-amqp2pdf.png)

---

## Sharing: Generic Tools

![Open Source](images/OpenSource.png)

Notes:
https://www.npmjs.com/~tesglobaladmin

---

# Reasons for change?

* Ecosystem moves on
* Security holes
* New features

---

## Challenges

* Fear of touching old code
* Lack of tests / docs
* Preventing domain logic creeping in

Notes: 
retention

---

![Time](images/time.jpg)

---

## Time to Maintain

* Front-end days, 1 per month
* Hack days, 2 per month
* Tech debt days, _coming soon_
* _New_ DX "group" 
 
Notes: 
Every last thursday of the month, the folks interested in the Frontend at tes topic (so, not app-specific frontend tasks) meet up and hack together on general/broad frontend related tasks. The day before (so, wed) there is a sort of quick "kick off" where we decide who is gonna work on what, and the morning after (so, fri) there is gonna be a sort of quick "retro" to see what has been done. If you want to participate just drop an email/message to the current frontend champion
More like Spotify guilds
No dedicated components guardians

---

## Navigation

* Naming conventions
* Engineering guide
* Tech Standards
* Ask on Slack

Notes: 

---

## Engineering Guide

![Engineering Guide](images/EngineeringGuide.png)

---

## Tes Culture

* Post-mortems on outages
* Champions
* Helping others 
* Mentoring
* Knowledge sharing

Notes: 
https://internal.tes.com/engineering/docs/how-to/have-a-post-mortem.html

---

![Sponge Bob](images/sharing-is-caring.jpg)

---

## Improving DX

* Culture reflects in code quality
* Taking responsibility to improve
* Caring about consumers and maintainers

---

## Summing Up

* Hire crafts people who care
* Technical oversight (Principal/Systems Engineers)
* Open communications (Slack)
* Culture **inextricably** linked to Architecture

Notes: 
Summing up ^^

---

## Thank You
#### @rachelcdavies @tes_engineering
![Tes Logo](images/tes-career-hero.png)

Notes: We're hiring :-)

