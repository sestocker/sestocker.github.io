---
layout: post
title: Sitecore Infrastructure in Multiple Regions
---

{{ page.title }}
================

<p class="meta">30 June 2022</p>

_This blog post originally appeared on Perficient's blog and was removed during a redesign. This post is pretty old at this point but still applies to non-headless multiple region Sitecore setups._

Sitecore is capable of serving traffic from multiple regions from your cloud provider of choice. Why bother though? It’s a good question because Sitecore in multiple regions is more complex, more expensive to host and more work to maintain. If your organization is using Sitecore XP to its fullest (although there are other options today), you can’t cache HTML at the edge using a CDN. Even when Sitecore output caching is used, every request is still served by a content delivery server to enable personalization and multivariant testing. If your infrastructure is only in a single region, many of the website users are going to end up far from the Sitecore content delivery server, resulting in a slower overall experience.

## How do you setup multiple regions for Sitecore in Azure?

What does it mean to set Sitecore up in multiple regions? Set up the primary region in the standard way for Sitecore XP – a single content management app service and instance, a content delivery app service with the number of instances that make sense for your traffic and then xConnect and related app services. Of course, Kubernetes can be used instead of app services but the point remains the same – in the primary region, not much is going to be different from a standard Sitecore setup.

Only content delivery servers and their dependencies are needed in the secondary or “content delivery only clusters”. xConnect is a dependency of running full XP. Decide whether to setup xConnect in each region or rely on the primary region’s xConnect service. A single xConnect in the primary region will cause some slight latency on the first request. Other dependencies include SQL, Solr and Redis for each content delivery cluster. Those supporting services should be setup in the same region as your content delivery servers to maximize speed. Also consider setting up a separate indexer in the CD-only regions so that the actual CD’s that are serving traffic do not need to perform any of the indexing operations.

## Challenges

The biggest challenge setting up regional content delivery clusters will be the web database where published content lives. There are 3 viable setups, each with their own unique set of pros and cons.

1. Database replication – in this setup there is a single publishing target setup in the primary region. The web database will then be replicated across regions. This setup avoids the pitfalls of publishing across regions but processing publishing events against a read-only replica is challenging and comes with its own setup intricacies. During deployments, be careful not to publish changes that break functionality in regions where the latest deployment artifacts aren’t deployed.
2. Separate publishing targets – in this setup, there is a separate target for each region. Because the database is not replicated, event processing can happen against the database as usual. Publishing across regions is incredibly slow though so consider using the Sitecore Publishing Service. This setup also allows different content published to different regions if there’s a business requirement for varying content.
3. A third option would be using a combination of the tactics. Use separate publishing targets but those databases would reside within the primary region SQL Server. Then, those databases would be replicated out to your other regions. This approach allows for separate content per region while retaining fast publishing. The primary drawback is the complexity of the approach.

## Additional Benefits

Performance is a big benefit for setting up Sitecore in multiple regions. There are some other benefits to this approach which may sway you to strongly consider this setup.

1. Disaster Recovery – While not a full DR plan, serving traffic from multiple regions in an active/active configuration can act as disaster recovery. If a region goes down, end users will not be affected. The other regions will continue to serve traffic. Serving from multiple regions mitigates much of the downtime risk associated with an outage. Full DR plans are still necessary in the event that CM is down or a region will be offline for an extended period.
2. Blue/Green deployment – Azure supports blue/green natively via deployment slots. When serving from multiple regions, the deployment slots aren’t needed. To achieve glue/green, turn the region being deploying to off completely in Front Door. End users continue to be served by the other regions. Internal users and testers can access the region that has the latest code via an internal url. This allows for extended testing if necessary.
3. Setting up Sitecore in multiple regions has huge benefits and isn’t too difficult to achieve. From an infrastructure perspective, it’s something to consider to increase your site’s performance and resiliency. The future is starting to look like personalization and multivariant testing will be pushed client side. In that model, HTML will be cached at the edge. If the front end is calling Sitecore API’s on the CD server, however,  consider Sitecore in multiple regions to get the API response time as low as possible.