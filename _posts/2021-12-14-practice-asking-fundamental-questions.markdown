---
layout: post
title:  "Practice asking fundamental questions"
date:   2021-12-14 15:12:31 -0800
categories: engineering-practices
---
After the [previous post]({{ page.previous.url }}) argued that many advancements in our software engineering practice are important because they are, in some sense, advancements in *engineering with intention*, some might wonder about the reverse: "engineering *without* intention". Surely, that's not a thing. Right?

Right.

Well, mostly. It clearly doesn't make much sense to speak of engineering *wholly* without intention, and the post (title notwithstanding) indeed discusses things in relative rather than binary terms. Beyond obvious generalizations, though, the reality is that there are a number of avenues for engineering with intention which many software engineering organizations may be missing out on.

This post will therefore go over some questions which software engineering organizations can ask themselves in order to discover where their practices may not be aligned with their intention.

#### **Clarifying fundamentals**

Sometimes the most seemingly "settled" questions on a project can be the source of the most confusion and heartache.

On a previous project I worked on for a mid-sized government contractor, the decision was made early on to take a system-of-systems[^1] approach to designing and delivering a distributed, microservice-based software solution. Far from merely being a design-level decision to aid in structuring our work, though, the code of the system was quite literally composed of a nested hierarchy of separate component systems, extending from a single metacomponent at the root-level representing the entire software solution all the way down to the individual, actually deployable components (i.e. the microservices themselves).

This early design decision had far-reaching consequences, not just for the technical implementation of the solution but also for the types of teams which became necessary within the project.

For example, due to the fact that development work began at the "bottom" (individual microservice) level, before a solution had been found for how to integrate and deploy the system at higher levels in a standardized way, confusion and frustration later arose about the role and work of the team working on said uniform solution. The latter team's members thought the necessity of their work was obvious when, for the teams who had been developing and deploying their individual microservices and occasionally their isolated subsystems for months, it was anything but. Had the implications of the chosen architecture been discussed early on, or better-yet, regularly during development, a great deal of heartache could have been avoided.

After broadly similar experiences at various other points in my career, I no longer think these were rare, freak occurrences. Even though it may occasionally feel silly, we shouldn't take even the most basic questions for granted: What *exactly* are we building? What does that imply about who we need doing what? What *exactly* do we each mean when we use specialized terms? How do we want to work together? The gulf between the upsides and the downsides are simply too great to leave such things to resolve themselves "organically" in the course of a project's development.

#### **Questioning our practices**

Below are some examples of additional questions software engineering organizations can use to revisit their practices and see whether any of them are poorly aligned with how they would actually like to work:

- Do we treat software development as a commodity? Or as a craft?[^2]<sup>,</sup>[^3]
- Do we practice egoless programming and co-working?[^4]<sup>,</sup>[^5]
- Do we have the right mix of roles (or personas)?[^6]<sup>,</sup>[^7]
- Are we enabling self-service teams?[^8]
- Have we questioned our team topologies?[^9]<sup>,</sup>[^10]
- What phase of organizational reliability are we in?[^11]

Posing and working out answers to these and other questions are opportunities to make our practice of software engineering more intentional and less "organic", which is to say, less accidental. Further, building up a library of such questions to pose at regular intervals could form the basis for a set of organizational patterns to help keep software engineering organizations on track.

Rather than belabor the point about the fundamental connection between our practices, good or bad, and our intentions, in future posts I will skip this extra step and assume the reasons to and value in regularly scrutinizing our practices is understood.

#### References:
[^1]: [System of systems](https://en.wikipedia.org/wiki/System_of_systems)
[^2]: [The Principles of Craftsmanship](https://blog.cleancoder.com/uncle-bob/2013/02/10/ThePrinciplesOfCraftsmanship.html) (Martin 2013)
[^3]: [The Software Craftsman: Professionalism, Pragmatism, Pride](https://www.pearson.com/store/p/software-craftsman-the-professionalism-pragmatism-pride/P100002142776/9780134052502) (Mancuso 2014)
[^4]: [The Ten Commandments of Egoless Programming](https://blog.codinghorror.com/the-ten-commandments-of-egoless-programming/) (Atwood 2006)
[^5]: [The Psychology of Computer Programming](https://geraldmweinberg.com/Site/Programming_Psychology.html) (Weinberg 1971)
[^6]: [App Operator: The Hidden Persona, KubeCon China 2019](https://www.youtube.com/watch?v=U9a6jOiNY5c) (Bhatia, Huruli 2019)
[^7]: [Improving Developer Happiness on Kubernetes, But First: Who Does Configuration?](https://thenewstack.io/improving-developer-happiness-on-kubernetes-but-first-who-does-configuration/) (Williams 2020)
[^8]: [Pattern: Self Service](https://www.cnpatterns.org/infrastructure-cloud/self-service) (cnpatterns.org authors 2020)
[^9]: [Team Topologies](https://itrevolution.com/team-topologies/) (Skelton, Pais 2019)
[^10]: [DevOps Topologies](https://web.devopstopologies.com/) (Skelton, Pais 2020)
[^11]: [The Five Phases of Organizational Reliability](https://cloud.google.com/blog/products/devops-sre/the-five-phases-of-organizational-reliability) (Google, 2021)
