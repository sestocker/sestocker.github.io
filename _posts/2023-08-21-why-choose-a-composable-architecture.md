---
layout: post
title: Why Choose a Composable Architecture
---

{{ page.title }}
================

<p class="meta">21 Aug 2023</p>

_This blog post originally appeared on Perficient's blog and was removed during a redesign. This post is pretty old at this point but applies to XM Cloud )Sitecore AI) and Sitecore headless in general._

If you’ve been following Sitecore’s architectural movement over the last few years, a lot has changed. Instead of the “all-in-one” approach of Sitecore XP, XM Cloud, and Headless encourage a composable architecture – one where Sitecore itself offers 11 SaaS products categorized into three clouds: Content Cloud, Engagement Cloud, and Commerce Cloud. However, with a composable architecture, your organization can easily utilize another enterprise product in place of Sitecore’s offering, and this kind of flexibility is integrated into the very nature of a composable architecture. For example, use Marketo for your email marketing campaigns instead of Sitecore Send. Let’s take a look at what composable architecture means and why it’s a good idea to choose this approach.

## What is a Composable Architecture?
Composable architecture’s textbook definition is “an approach in software design where complex systems are built by combining smaller, self-contained components or modules.” Each component or module is responsible for a specific functionality and can interact with the other modules through well-defined interfaces (in modern web development, these interfaces tend to be either a REST or GraphQL API). This approach allows each module to be iterated on individually with little to no dependencies on the other modules. We see a great example of this today with the near-weekly releases for XM Cloud, something that is not possible for traditional Sitecore releases that are self-hosted.

Integrating data from multiple sources is a crucial aspect of composable architecture. In today’s digital landscape, applications often need to gather and process data from various external services, databases, APIs, and other sources. A composable architecture is the best approach in today’s modern web, including the Enterprise CMS space.

## Why Use a Composable Architecture

### Functional Independence
In a composable architecture, each module is designed to handle a specific function or feature. This independence also encourages flexibility where for example, in the context of Sitecore, many modules included in the Sitecore SaaS suite are optional and not required when utilizing XM Cloud or Content Hub for your content.

### Reusability
By designing modules as independent, they can be reused across different parts of the system. For instance, if you have a module that interacts with a third-party API to retrieve some sort of data, you can reuse this module in various applications that require that information. Thinking of developing headless applications, a good architectural approach would be to develop an API layer for your custom data needs that can then be reused across multiple applications. For example, a provider search API for a healthcare provider can be used by the organization’s main website and also targeted microsites.

### Maintenance, Upgrades, and Releases
Applications often need to adapt to changes in data sources, APIs, or external services. When these sources evolve, having a modular approach makes it easier to update the relevant modules without affecting the rest of the application. This makes maintenance and upgrades more manageable, reducing the risk of unintended side effects. Using the previous example of a provider search API layer, if that layer is abstracting a third-party API, changes in that third party will not affect the consuming applications of your API – only the provider search microservice would be affected by the third-party change. Software releases too are independent – meaning that the updates needed to your provider search API can be made without needing to release any other module (since the provider search API contracts didn’t change, no need to change anything about your headless application).

### Scalability
Composable architecture allows you to scale specific parts of the system independently, which can be optimized for performance, scalability, and cost. The nature of headless development in Sitecore lends itself nicely to a Vercel or Netlify rendering host but it’s possible depending on your needs that a simple Azure app service could serve your initial needs.

### Testing and Debugging
Isolating data integration logic into separate modules simplifies testing and debugging. You can create focused unit tests for each integration module and this targeted testing approach improves overall system reliability.

### Flexibility and Agility
Composable architecture encourages flexibility and agility in adapting to changing business needs. Perhaps the biggest change regarding sites developed using Sitecore is the flexibility that a composable architecture gives you. Changing rendering hosts, updates to third-party API’s and upgrades to your commerce engine now feel much easier to deal with because of the isolation, testability, and independence.

Composable architecture and headless development is the future direction for Sitecore. When done correctly, it will allow organizations to use “best of breed” tools and to have a level of agility and innovation not possible before. The decoupled headless architecture will prove to be more performant, flexible, and secure.