---
layout: post
title:  "Engineering with intention"
date:   2021-11-21 14:36:09 -0800
categories: engineering-practices
---
One way to think about the evolution of software engineering is as a constant game of cat and mouse, with the cat—as the state of our profession—never fully managing to catch the mouse representing the challenge of ever-complexer software systems.

But despite the fact that this mouse can never be caught once-and-for-all, great progress can and has been made in keeping up with it across a number of fronts, whether in hardware advances, modern programming languages, more powerful tooling, or more abstractly in the evolving culture, roles, and practices embodied by software engineering organizations.

Some of the most dramatic improvements have no doubt taken place as part of the adoption of cloud computing and, more recently, cloud-native thinking and practices. Some examples of the underlying advancements driving these improvements include the abstraction and commodification of compute/network/storage hardware via containerization and virtualization, the widespread use of declarative languages for managing system automation (i.e. Infrastructure-as-Code, GitOps), the exploding CNCF landscape[^1] in the area of tooling, and the emergence of DevOps/SRE in the realm of culture, roles, and practices.

Each of these advancements, on the one hand, represents an evolution in some particular aspect of software engineering. But their emergence and popularity can also be explained from a more universal perspective by considering that, in some way or other, they all enable engineers to narrow the gap between their *practices* and their actual *intention*. In other words, they represent an improvement in the ability of engineers to focus more of their efforts on *domain problems*.

Two closely-related ways in which the technical approaches discussed above accomplish this are by providing more *"appropriate levels of abstraction"*[^2] and better separation of *"accidental and essential complexity"*[^3]<sup>,</sup>[^4]. Experienced engineers will recognize intuitively the ever-present challenge posed by complexity and the difficulty in wielding abstraction skillfully in order to manage it.

On the non-technical side of things, the DevOps/SRE approaches to culture, roles, and practices invite software engineering organizations to explore what other changes they might make to better realize their intentions. To give one example: in order for product-focused engineers to concentrate on their domain problems, organizations discover that entirely new roles or personas (DevOps, SRE, Platforms, etc.) with their own, potentially derived yet equally valid, domain problems may be needed.

As mentioned earlier, these advancements, taken individually or together, cannot be a panacea in addressing the challenges of software engineering, but each nonetheless represents both a necessary and welcome step forward—not least because improving the alignment of our practices with our intentions not only results in better outcomes but also in deeper satisfaction[^5] on the part of us "cats"!

In future posts on this site, I plan to revisit each these topics and reflect on what their impact has been on my own work and thinking as well as on the state of software engineering practice more broadly.

#### References:
[^1]: [CNCF landscape](https://landscape.cncf.io/)
[^2]: [Appropriate Levels of Abstraction](https://web.archive.org/web/20171019085651/http://www.intentsoft.com/appropriate_lev-2/) (Simonyi 2015)
[^3]: [Is Software Development Difficult?](https://www.youtube.com/watch?v=S0fnvGCl73I) (Farley 2021)
[^4]: [No Silver Bullet](https://en.wikipedia.org/wiki/No_Silver_Bullet) (Brooks 1986)
[^5]: [Accelerate: State of DevOps 2018](https://services.google.com/fh/files/misc/state-of-devops-2018.pdf) (Forsgren, Humble, Kim 2018)