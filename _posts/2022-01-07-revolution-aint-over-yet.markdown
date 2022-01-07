---
layout: post
title:  "The revolution ain't over yet"
date:   2022-01-07 15:02:11 -0800
categories: cloud-native kubernetes
---
As discussed in previous posts, some of the most rapid and exciting advances in software engineering have surely taken place within the cloud and cloud-native computing paradigms and yet, despite both having been around for many years now, the pace of change hasn't slowed down in the slightest.

#### **Standardized concepts? *\#ToDo***

However, despite a generally uniform, rapid progression in terms of the number and power of cloud-native tools and technologies available to us, the progress in terms of our arriving at well-defined, standardized concepts and a shared understanding of how to apply these has been much more differentiated. As an example, although the Cloud Native Computing Foundation (CNCF) itself was founded in 2015, they were still working out their own *v1.0* definition of the term "**cloud-native**" itself a whole three years later[^1]!

Confusion persists around other terms and concepts in the space as well, with some of the better-known examples relating to the lack of clarity around relevant roles or personas. For example, while many continue valiantly to insist that "DevOps is a culture not a role!"[^2], this claim is confronted with the reality of tens of thousands of job listings for open positions having the title "DevOps Engineer". And although the problem may be slightly better when it comes to the Site Reliability Engineering (SRE)[^3], Platform Engineering, or, more recently, Production Engineering[^4] roles, even here there is still a high degree of variation in what companies understand by the monikers, and especially little standardization around ***when*** (i.e. under which set of technical, organizational maturity, financial, etc. circumstances) companies should be doing the '*what*' of these various roles[^4].

Similarly in an area of central interest for myself, uncertainty persists around the concept of cloud-native *application delivery*. Comparing the results of the relevant Google search[^5] with the areas considered in-scope in the CNCF Application Delivery Technical Advisory Group's Charter[^6], it appears the implicit understanding contained in the latter hasn't yet become well-established in the industry. This state of affairs hasn't been helped by the unclear criteria used to determine tools' inclusion under the closely-related "*Application Definition and Development*" heading in the CNCF's landscape[^7] and indeed the Co-Chairs of the Application Delivery TAG have in the past themselves called for an update of the landscape in this area[^8].

Although the CNCF has made a great start in some of these areas with their nascent Cloud Native Glossary initiative[^9], its definitions for such ubiquitous-yet-overloaded terms as 'serverless'[^10] or 'service'[^11], or its missing definitions for many common terms (including some in frequent use by the CNCF itself, such as the names of some of the Technical Advisory Groups or several of the headings in the CNCF Landscape[^7]), show that there is still much room for contributions and improvements.

In the future, I would like to see the CNCF take an even more active, structured stance on moving the state of play forward here; for example, by using industry surveys or stakeholder interviews to arrive at more clarity around exactly *why*, *how*, *when*, and *which* companies are using these concepts and practices, and using the results of these to try to arrive at some useful standardizations.

#### **Beyond infrastructure-centricity**

Another area which appears overdue for re-evaluation has to do with what we conceive of as the actual underlying driver of change and innovation in the cloud/cloud-native space, the lion's share of which has been taking place in the ecosystem which has sprung up around Kubernetes.

As is sometimes the case when progress is made in an aspect of software engineering, an innovation in one, often lower-level, area of concern can become a launching-off point for further advancements in related, higher-level areas. In the case of Kubernetes, the early motivations of increased efficiency and decreased toil around managing and automating containerized workloads have over time been extended and enabled other, higher-level use-cases such as improved observability, reliability, dynamicity, security, et cetera.

Yet despite this evolution in the level of abstraction of the use-cases it is able to address, many still think of Kubernetes solely or primarily as a container orchestration platform. This narrow view misses the real reasons why Kubernetes has exploded in popularity. Rather than retread ground on this topic which has already been covered very well by others, though, I will simply refer to a few of them here. Kelsey Hightower himself was one of the first, pointing out several years ago that: "[*Kubernetes is a platform for building platforms*](https://twitter.com/kelseyhightower/status/935252923721793536?lang=en)". Others have convincingly made further, related points, for example by arguing that Kubernetes' true staying power comes from its well-defined, extensible API core[^12]<sup>,</sup>[^13], and from its potential for someday becoming a pure, universal control plane[^14]<sup>,</sup>[^15], fully-divorced from managing containers.

Still, taking a step back could yield further insights about another likely direction of future developments. In spite of the aforementioned progression in lower-level, original motivations later enabling the addressing of higher-level concerns, the origins of Kubernetes and another similarly-ubiquitous tool in the space, Terraform, in managing ***low-level infrastructure*** is still apparent in their relatively complicated and unfriendly developer experience. The relevant rhetorical question to apply here is, *why are we doing any of this in the first place again?*

Except for a small number of companies actually selling infrastructure management services, the answer is generally **not** *'for its own sake'*, but usually something along the lines of, *in order to **deliver** some software **application** to our customers*. Yet despite this apparently obvious answer, and despite consideration of application management concerns in Kubernetes dating back many years[^16], no tool or technology has thus far managed to find an approach to declarative application management which is at once powerful, flexible, intuitive (i.e. for development teams expressing *their* application), and Kubernetes-native. Part of the reason for this 'gap' in the landscape may be that the benefits of such an *application-first* approach to cloud-native application management aren't yet widely-understood.

In a future post, I will explore the state of the art around a central aspect of application management, ***application delivery***, what I consider to be weaknesses in current tools and technologies in the space, as well as discuss some recent approaches which I believe hold promise.

#### References:
[^1]: [CNCF Cloud Native Definition v1.0](https://github.com/cncf/toc/blob/1b3bc9302b4ff440caf9b8f22ed070723cdfb4c9/DEFINITION.md)
[^2]: [Google search: "DevOps is a culture not a role"](https://www.google.com/search?q=devops+is+a+culture+not+a+role)
[^3]: [Google - Site Reliability Engineering](https://sre.google/)
[^4]: [The Continuously Evolving Nature of SRE](https://medium.com/@sumbry/the-continuously-evolving-nature-of-sre-a0b053e00aaa) (Sumbry 2020)
[^5]: [Google search: "Cloud-native application delivery](https://www.google.com/search?q=cloud-native+application+delivery)
[^6]: [CNCF App Delivery TAG Charter - Areas considered in Scope](https://github.com/cncf/toc/blob/main/tags/app-delivery.md#areas-considered-in-scope) (CNCF App Delivery TAG Charter Authors 2022)
[^7]: [CNCF landscape](https://landscape.cncf.io/)
[^8]: [Cloud-Native Application Delivery Landscape Update (Deep-Dive) (see: 0m00s - 3m16s and 20m56s - 22m17s)](https://www.youtube.com/watch?v=Mez0xvIvIHE) (Reitbauer, Zhang 2020)
[^9]: [Cloud Native Glossary](https://glossary.cncf.io) (Cloud Native Glossary Authors 2022)
[^10]: [Cloud Native Glossary - Serverless](https://glossary.cncf.io/serverless/) (Cloud Native Glossary Authors 2022)
[^11]: [Cloud Native Glossary - Service](https://glossary.cncf.io/service/) (Cloud Native Glossary Authors 2022)
[^12]: [Kubernetes Is Not Just About Containers — It’s About the API](https://thenewstack.io/kubernetes-is-not-just-about-containers-its-about-the-api/) (Farcic 2021)
[^13]: [Kubernetes isn't about containers](https://joshgav.github.io/2021/12/16/kubernetes-isnt-about-containers.html) (Gavant 2021)
[^14]: [Kubernetes’ True Superpower is its Control Plane](https://containerjournal.com/kubeconcnc/kubernetes-true-superpower-is-its-control-plane/) (Tabbara 2021)
[^15]: [The Power of Control Planes and the Kubernetes Resource Management Model](https://youtube.com/clip/Ugkxn64n20PiOgI4b3BONnQqk1a7UiVb_Gh-) (Tabbara, Hightower, Burns, Beda, Grant 2021)
[^16]: [Declarative application management in Kubernetes](https://docs.google.com/document/d/1cLPGweVEYrVqQvBLJg6sxV-TrE5Rm2MNOBA_cxZP2WU/view#) (Grant 2017)
