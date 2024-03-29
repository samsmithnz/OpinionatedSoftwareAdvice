# Architecture

> "Whenever a developer thinks they are being clever, they commit an atrocity"

![image](https://user-images.githubusercontent.com/8389039/201220906-95a21029-89ec-4a2a-a2a2-f43c7ed9a19b.png)

- Every project needs an architecture. An architecture is not just an infrastructure diagram!
- **The hardest part of architecture**: naming things. 

## The curse of Microservices and SOA
Is your project strategic or is it a line of business application? Does it a major revenue generator for your company? Does your project have ten's of thousands to millions of users? With the rise of Microservices, it's becoming a more common strategy - but more often than not, it will fail. Why?
1. Microservices require dedicated teams. If the team is balancing multiple applications, chances are they don't have the right allocation/bandwidth to make the microservice successful.
2. There is no point creating a microservice for a single instance application. If it doesn't need scale or require 5 nines uptime, it doesn't need resilency at this level. 
3. You should never start a project with a design that requires many microservices. Instead, the recommendation is to start building your monolith (which isn't always a negative thing to have), and as you need to have pieces that need scale and independence, break off these pieces and turn them into a microservice.

## The curse of Middleware
Many projects are overly-complicated and contain middleware that is unnecessary. There are a number of reasons this happens - some of it is the culture in our industry, where many feel they need to prove they are smart to their collegues with their complex system. But the reality is the best system is a simple maintainable one. A good system is one that is easy to maintain, scalable, and runs at a high performance. A poor system is a complex one that is difficult to maintain and teams are scared to make and deploy those changes.

When you add middleware, really ask the question: What problem does this solve? Is the problem it solves one I have today - or a perceived problem in the future? Am I installing this because I need it? Or because some guy on Twitter told me that I should...

## Maintenance, and the usage of RegEx/Linq
Ever looked at code someone else wrote, and thought "what were they thinking?" Ever looked at code you wrote some time ago (years, months, last week), and thought "What was I thinking?" This is common - but highlights why writing simple, maintainable code is so important. Comments matter too.

Some developers feel they need to look or prove to others they are smart, and that putting a vast amount of logic on one line with Linq and RegEx is something to be proud of. It isn't, these are actually some of the worst developers, as very few people can look at that logic when there is a bug or change later, and understand it. More often or not, they have to rewrite it (note - this is where unit tests are critical). It's been proven that a for loop is just as efficent as a linq query - if the code looks too complicated - it is. Use a simple loop(s) and if statement(s) instead - everyone who edits your code later with thank you.

## Using VM's
It's 2021. If you are using VM's, you aren't cloud native and you are maintaining a legacy product. If you start a new project with VM's, you are doing it wrong. 

## Open source software

Open source software is incredibly important and a huge timesaver, however, make sure you use software that is well maintained and has a good community, essentially, managing risk. For example, look at the number of stars on GitHub, compare it to competitors. Look at the number of contributors - over time. Some big repos have hundreds of contributors, but when you look into the details, you discover that most have contributed bugs/issues, fixed one bug, or updated the docs, and there is one contributor who has contributed 99% of the work. This is a risk - what happens when that one person gives up on the project or is hit by the big red bus tomorrow? Will your project have to take on maintaining that software or spend significant time looking for a replacement?

![Blockchain](assets/opensourcesoftware.jpg)
