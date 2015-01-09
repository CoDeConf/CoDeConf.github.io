---
layout: post
title: Removing waste from pipeline
tags: [Continuous Delivery]
authors: [Michiel Sens]
---

## Continuous Delivery is about removing waste from the Software Delivery Pipeline

#### By Michiel Sens, Solution Architect, Xebia
{: sens}

#### Speak:[The implementation of Continuous Delivery at Ziggo (UPC-Liberty Global)](/program#cdziggo)

![Michael Sens](/images/speakers/msens.jpg){: .portrait} On October the 22nd I will be speaking at the Continuous Delivery and DevOps Conference in Copenhagen where I will share experiences on a very successful implementation of a new website serving about 20.000.000 page views a month.

Components and content for this site were developed by five(!) different vendors and for this project the customer took the initiative to work according to DevOps principles and implement a fully automated Software Delivery Process as they went along. This was a big win for the project, as development teams could now focus on delivering new software instead of fixing issues within the delivery process itself and I was the lucky one to implement this.

This blog is about visualizing the 'waste' we addressed within the project where you might find the diagrams handy when communicating Continuous Delivery principles within your own organization.

To enable yourself to work according to Continuous Delivery principles, an effective starting point is to remove waste from the Software Delivery Process. If you look at a traditional Software Delivery Process you'll find that there are probably many areas in your existing process that do not add any value for the customer at all.

These area's should be seen as pure waste, not adding any value to your customer, costing you either time or money (or both) over-and-over-and-over again. Each time new features are being developed and pushed to production, many people will perform a lot of costly manual work and run into the same issues over and over again. The diagram below provides an example of common area's where you might find waste in your existing Software Development Pipeline. Imagine this process to repeat every time a development team delivers new software. Within your conversation, you might want to an equal diagram to explain pain points within your current Software Delivery Process.

![A traditional software delivery process](/images/speakers/slog.jpg)

Automation  of the Software Delivery process within this project, was all about eliminating known waste as much as possible. This resulted in setting up an Agile project structure and start working according to DevOps principles, enabling the team to deliver software on a frequent basis. Next to that, we automated the central build with Jenkins CI, which checks out code from a Git Version Management System, compiles code using maven, stores components in Apache Archiva, kicks off static, unit and functional tests covering both the JEE and PHP codebase and creating Deployment Units for further processing down the line. Deployment Automation itself was implemented by introducing XL Deploy. By doing so, every time a developer pushed new JEE or PHP code into the Git Version Management System, freshly baked deployment units were instantly deployed to the target landscape, which in its turn was managed by Puppet. An abstract diagram of this approach and chosen tooling is provided below.

![Overview of tooling for automating the software delivery process](/images/speakers/slog2.jpg)

When paving the way for Continuous Delivery, I often like to refer to this as working on the six A's: Setting up Agile (Product Focused) Delivery teams, Automating the build, Automating tests, Automating Deployments, Automating the Provisioning Layer and clean, easy to handle Software Architectures. The A for Architecture is about making sure that the software that is being delivered actually supports automation of the Software Delivery Process itself and put's the customer in the position to work according to Continuous Delivery principles. This A is not visible in the diagram.

After automation of the Software Delivery Process, the customer's Software Development Process behaved like the optimized process below, providing the team the opportunity to push out a constant & fluent flow of new features to the end user. Within your conversation, you might want to use this diagram to explain advantages to your organization.

![An optimized software delivery process](/images/speakers/slog3.jpg)

As we automated the Software Delivery Pipeline for the customer we positioned this customer to go live at a press of a button. And on the go-live date, it was just that: a press of the button and 5 minutes later the site was completely live, making this the most boring go-live event I've ever experienced. The project itself was real good fun though! :)

Needless to say that subsequent updates are now moved into live state in a matter of minutes as the whole process just became very reliable. Deploying code just became a non-event. More details on how we made this project a complete success, how we implemented this environment, the project setting, the chosen tooling along with technical details I will happily share at the Continuous Delivery and DevOps Conference in Copenhagen. But of course you can also contact me directly. For now, I just hope to meet you there..
