---
layout: post
title:  "Enabling cloud-native application delivery"
date:   2022-01-30 16:25:37 -0800
categories: cloud-native application-delivery
---
In the [last post]({{ page.previous.url }}), I discussed a few aspects of the cloud-native revolution which I believe have yet to reach their full potential. One of these was the topic of cloud-native application management and, more specifically, one of its central sub-topics ***application delivery***.

The reason I find cloud-native application management in general, and the *application delivery* aspect of it in particular, so important is down to the potential, when done successfully, to deliver a huge amount of value to development teams in a *scalable* manner, that is also *sustainable* in the face of expanding requirements, while at the same time significantly improving developers' experience by hiding the *'accidental complexity'*[^1] inherent in platform/infrastructure details.

*(For more background information on the motivations and challenges of cloud-native application management, the ["Declarative application management in Kubernetes"](https://github.com/kubernetes/community/blob/c936aad7abe58e62bfe21beff4807bf7e3149e16/contributors/design-proposals/architecture/declarative-application-management.md) article by Brian Grant provides an excellent overview.)*

As argued in the [previous post]({{ page.previous.url }}), the majority of the tools and technologies currently being used in the area of application delivery have not really moved beyond the *infrastructure-centricity* at the root of the cloud/cloud-native revolution.

To do so would require, among other things, elevating the concept of the ***application*** itself to a *prime consideration* when taking engineering decisions, as well as finding the right manner of accurately defining or representing it, as opposed to the present state of affairs where 'the application' is typically a sort of *non-concept* which can at most be said to "emerge" after some set of cumulative actions but doesn't otherwise exist in any meaningful *technical* sense.

In this post, I will therefore explore the idea and implications of taking an ***application-first*** approach to delivering cloud-native applications into Kubernetes-based environments by examining the three concepts of ***workflows***, ***developer platforms***, and ***application models***.

#### **Workflows**
One of the hallmarks of reaching the later stages of cloud-native adoption in software engineering organizations is the recognition of the importance of enabling of ***autonomous development teams***[^2]. In other words, there is an understanding that development teams should not have to wait for another team to perform some work on its behalf so that they can proceed with their own work; we should always be striving to enable ***self-service workflows***[^3].

Despite their near-ubiquitous adoption in cloud-native teams, several popular tools and technologies in the space don't do a very good job of enabling *self-service workflows* and autonomous teams.

One example of a widespread workflow technology which is holding many teams back is actually the everyday, mild-mannered CI/CD pipeline! The fact is that many CI/CD pipelines are brittle, as well as hard to maintain, version, and 'package'/re-use, ultimately hampering many developers' experience of using them for delivering software. Although the approach taken by GitHub Actions[^4] addresses some of these complaints, and the drive towards GitOps[^5] being spearheaded by tools like ArgoCD[^6] and Flux[^7] may help reduce the overall number of pipelines we need in the first place, others (like those behind the keptn[^8] project) are re-thinking the idea of transitioning through software delivery stages in a more radical way and arriving at a fundamentally different approach to application lifecycle orchestration[^9].

Beyond pipelines, other popular current-generation tools are similarly keeping teams from achieving more autonomy.

For example, although Helm[^10] represents a great step forward in terms of reducing boilerplate YAML, and addresses the common use-cases of dependency management, as well as packaging and templating to facilitate re-use, the fact that its usage is generally restricted to installation, upgrade, and deletion of Kubernetes manifests, with no inherent support for higher-level concepts or for managing infrastructure elements makes it ill-suited for an *application-first* approach to cloud-native application delivery.

Conversely, while Terraform[^11] is currently still near-omnipresent when it comes to *infrastructure management*, it too does not have native support for *application-layer* concepts and its approach to solving the problem remains a *tool-based* one rather than an *API/control plane-based* one, which limits its ability to enable truly *self-service workflows*.

Next, the Waypoint[^12] project from Hashicorp claims to represent an application-centric approach to application delivery. However, its conception of application-centric delivery is a fairly narrow one which, like CI/CD pipelines, focuses mainly on the concept of *stages* inherent to the process. And while it manages to avoid a few of the drawbacks of traditional pipelines, its imposition of Hashicorp's own configuration language (HCL) renders it vulnerable to the same criticisms with respect to difficulty of re-use and unmanageable sprawl which are often levied at Terraform in complex application scenarios.

In addition to the previously mentioned flaws to the aforementioned tools or technologies—and which, in some combination, generally also apply to most other projects[^13] in the space—, the more fundamental gap which none of them addresses is that of giving developers a more *powerful*, *flexible*, and *intuitive* way to **define** their cloud-native application in the first place. A technical representation of the application in this manner is naturally a critical prerequisite to any ***application-first** delivery workflow*.

Taken together, these drawbacks to current-gen technologies effectively preclude them—indispensable though they still may be for various other functions—from truly enabling *self-service workflows* as well as from forming the cornerstone of an *internal developer platform* (IDP), both of which, as previously mentioned, are seen as key differentiating factors of high-performing, autonomous development teams[^2].

#### **Developer platforms**

The concept of ***internal developer platforms***[^14] has been around for many years but has experienced renewed interest recently as a result of the increasing difficulty in managing the sheer number of components making up modern cloud-native software systems and the recognition of new possibilities being opened up by the standardization around Kubernetes as a base platform.

What exactly are *internal developer platforms*, though, and how do they differ from Platforms as a Service (PaaS) like Heroku, CloudFoundry, or Google App Engine?

In addition to the previously referenced article, *["What I Talk About When I Talk About Platforms"](https://martinfowler.com/articles/talk-about-platforms.html)*,  by Evan Bottcher[^14], and the following one by Kaspar von Grünberg (CEO at proprietary IDP vendor Humanitec): *["What Is an Internal Developer Platform?"](https://humanitec.com/blog/what-is-an-internal-developer-platform)*, the *[internaldeveloperplatform.org](https://internaldeveloperplatform.org)* website also provides a useful resource here (with the important addition of calling out *application configuration* as an often-forgotten source of complexity).

Essentially, an *internal developer platform* can be thought of as a "PaaS done *your* way". That is, an IDP at minimum shares the usual PaaS features of having a focus on enabling self-service developer teams, a well-defined API for building and deploying application containers, and some level of infrastructure management, but unlike a PaaS doesn't require developer teams to force their application to fit the platform's view of the world.

The same features that initially drove Kubernetes' takeover of the container orchestration market—its endlessly-extensiblility and weak-opinionation compared to other options—later prompted some astute observers to remark that Kubernetes is, in fact, *not* (just) about containers but is rather a "***platform for building platforms***"[^15], a statement which *internal developer platforms* could end up being the ideal example of.

So if Kubernetes is seemingly the de-facto the answer to any and all questions of platform at the moment, what are we *still* missing?

As alluded to in the previous section, a more *natural*, *all-encompassing* way to represent *applications* is still missing; Kubernetes, with its weakly-opinionated and minimal built-in API (again, generally a good thing!), doesn't let us represent *application-layer* concepts in any powerful, meaningful way out of the box.

The good news, though, is that with the basic building block of *Custom Resources*[^16] we have everything we need in order to *extend* a Kubernetes-based platform with such application-modeling capabilities. The benefits, in terms of the improved user experience of working at the level of abstraction most *intuitive* to application developers (as the *primary customers* of any *internal developer platform*), are significant.


#### **Application models**

There are other, more tangible benefits to supporting application-layer concepts than just developers' user experience, though.

Firstly, having abstractions at a higher-than-infrastructure level can help achieve platform-agnosticism, avoiding vendor lock-in and potentially having cost-saving (*FinOps*) implications. Secondly, having application-layer concepts helps promote clear separation of concerns and supports a team topology which many software engineering organizations may find useful (Infrastructure/Platform Engineering vs. Application Operations vs. Application Development). Additionally, having an application-first *internal developer platform* can have security and reliability benefits as the guardrails typically present in such platforms can prevent common misconfiguration issues.

So, do any existing Kubernetes-based projects already support the ability to *intuitively* represent applications?

Thus far, I am aware of at least two projects taking different approaches which are still active and which have managed to gain a a certain amount of traction in the open-source, cloud-native community: the Open Application Model[^17] (and its current KubeVela[^18] implementation), and the Crossplane[^19] project.

The Open Application Model (OAM), announced as a collaboration between Microsoft and Alibaba in 2019[^20], is a spec-based approach which contains a literal *Application* concept, consisting of *Components* as well as associated *Traits* and *Scopes*.

The purely spec-driven nature of the OAM project has the advantage that it can clearly point to platform agnosticism as one of its main goals. In order to actually provide value, though, every spec still needs a real world implementation, which is the role of the related Kubernetes-based project, KubeVela.

*(As an interesting aside, Microsoft contributed a previous Kubernetes implementation of OAM called Rudr[^21], and the developers behind Crossplane were themselves involved in a set of libraries for building Kubernetes OAM implementations[^22], both of which were eventually phased out in support of the KubeVela[^18] project.)*

The Crossplane[^19] project, though, takes a different approach to enable representing applications, despite having originally been focused on offering a Kubernetes-native approach to infrastructure management, rather than explicitly focusing on applications.

Interestingly, as a result of Crossplane typically being associated with infrastructure management as well as the previous close involvement of Crossplane developers with OAM, use of the two projects in concert is sometimes proposed, with OAM/KubeVela for application management and Crossplane for infrastructure management[^23]<sup>,</sup>[^24].

However, one of the powerful and unique features of the Crossplane project, *Composite Resources* and *Compositions*[^25], allows it to potentially be used for modeling and managing not just infrastructure, but entire applications. The reason for this is that, from the high-level point of view of the Crossplane control plane, there is no inherent difference between handling a *Composite Resource* which represents some infrastructure component(s) and one which represents some *application-layer* component(s). Clearly, after a certain point (i.e. once an action needs to be taken by a Kubernetes controller) the difference does become relevant, but from the point of view of the *users* of a Crossplane-based *internal developer platform* they essentially get the power and flexibility of the *Composite design pattern*[^26] implemented via the Kubernetes API! Where such an approach could truly shine would be in building large-scale, complex systems-of-systems[^27], where the ability to compose multiple, smaller sub-systems into the final target application would be a massive boon to managing complexity.

So, does the power of composability in Crossplane make up for the lack of built-in support for *traits* and *scopes* which OAM/KubeVela provides? To me the answer isn't yet clear.

Regardless of whether one approach will eventually win out over the other, though, or whether both approaches will continue to synergize well with each other, or whether something entirely different emerges, I believe we all stand to benefit greatly from a continued drive toward ***application-first*** in *cloud-native application delivery*!

#### References:
[^1]: [No Silver Bullet](https://en.wikipedia.org/wiki/No_Silver_Bullet) (Brooks 1986)
[^2]: [2020 State of DevOps Report](https://circleci.com/landing-pages/assets/Puppet-State-of-DevOps-Report-2020.pdf) (Brown, Kersten, Stahnke 2020)
[^3]: [What Do Developers Really Need (And How Can Ops Help)?](https://www.youtube.com/watch?v=xx8EM08ihs) (Farcic 2021)
[^4]: [GitHub Actions](https://docs.github.com/en/actions)
[^5]: [OpenGitOps](https://opengitops.dev)
[^6]: [ArgoCD](https://argoproj.github.io/cd/)
[^7]: [Flux](https://fluxcd.io/)
[^8]: [Keptn](https://keptn.sh)
[^9]: [We've Been Building Pipelines Wrong. Here's How to Fix Them!](https://agardner.net/keptn-pipelines/) (Gardner 2021)
[^10]: [Helm](https://helm.sh)
[^11]: [Terraform](https://www.terraform.io)
[^12]: [Waypoint](https://www.waypointproject.io)
[^13]: [Kubernetes application management tools](https://github.com/kubernetes/community/blob/c936aad7abe58e62bfe21beff4807bf7e3149e16/contributors/design-proposals/architecture/declarative-application-management.md?plain=1#L127)
[^14]: [What I Talk About When I Talk About Platforms](https://martinfowler.com/articles/talk-about-platforms.html) (Bottcher 2018)
[^15]: [https://twitter.com/kelseyhightower/status/935252923721793536](https://twitter.com/kelseyhightower/status/935252923721793536)
[^16]: [Custom Resources](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)
[^17]: [Open Application Model](https://oam.dev/)
[^18]: [KubeVela](https://kubevela.io/)
[^19]: [Crossplane](https://crossplane.io/)
[^20]: [Announcing the Open Application Model](https://cloudblogs.microsoft.com/opensource/2019/10/16/announcing-open-application-model/)
[^21]: [Rudr](https://github.com/oam-dev/rudr)
[^22]: [OAM Kubernetes Runtime](https://github.com/crossplane/oam-kubernetes-runtime)
[^23]: [OAM and Crossplane: The Next Stage for Building Modern Application](https://www.alibabacloud.com/blog/oam-and-crossplane-the-next-stage-for-building-modern-application_596240)
[^24]: [Combining Argo CD (GitOps), Crossplane (Control Plane), And KubeVela (OAM)](https://www.youtube.com/watch?v=eEcgn_gU3SM) (Farcic 2021)
[^25]: [Composite Resources](https://crossplane.io/docs/v1.6/concepts/composition.html)
[^26]: [Composite pattern](https://en.wikipedia.org/wiki/Composite_pattern)
[^27]: [System of systems](https://en.wikipedia.org/wiki/System_of_systems)