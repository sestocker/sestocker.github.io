---
layout: post
title: Sitecore Symposium 2019: Reinventing a Modern Intranet
---

{{ page.title }}
================

<p class="meta">5 Nov 2019</p>

_This blog post originally appeared on Perficient's blog and was removed during a redesign. This post is pretty old at this point but many of the strategies are still applicable. Sitecore AI (XM Cloud) publishing content to EXperience Edge while not technically "public" would probably not meet the security requirements for an intranet for most organizations._

Sitecore has been ranked as one of the leading Enterprise Web CMS products for years. Sitecore’s robust personalization features paired with top of the line analytics and marketing automation capabilities make Sitecore a top choice for public-facing websites. But, Sitecore features that are useful for public sites can also be used to improve internal processes and engagement. Have you considered the benefits of improving your intranet with Sitecore? At Sitecore Symposium 2019, I gave a talk with Scott Mortenson, Knowledge Architect at Orrick, titled “Reinventing a modern intranet” where we took a look at building Orrick’s intranet on the Sitecore platform.

![Screenshot of Orrick intranet homepage](/images/homepage-600x348.jpg)

As you can see, the user experience for Orrick’s intranet is top-notch. Perficient Digital worked extensively with Orrick users and leadership to come up with a modern, clean design that matched Orrick’s brand. It also met the experience objectives for the new intranet. The site is completely responsive and works really well on both mobile and tablet. The main driver of the user experience was ease of access to information and speed. One of the key objectives of the new intranet was to make information that attorneys need fast and easy to find. Perficient Digital was able to achieve a site design and user interaction flow that resulted in fewer clicks to find the most important information for all users.

## Content, content, content

Sitecore isn’t a perfect choice for every type of intranet but it’s a great choice if the primary function of the intranet is communication to an internal audience. Orrick has a robust library of content they publish on their public website orrick.com. We wanted to pull this extensive content library into Orrick’s intranet where the content can live forever, instead of the lifespan they have on the public site. This was made easy by the fact that orrick.com was also built on Sitecore. Using Sitecore Powershell Extensions, we pulled content from orrick.com and transformed that data as needed. For example, we mapped external division names to internal ones.

## Personalization

The biggest differentiator for developing an Intranet vs. public-facing website on Sitecore is what we know about site visitors.  With Intranets, companies have the unique capability to know an immense amount about every person who visits. For instance, Sitecore knows a person’s job title, their department or practice group, and anything else that is tracked in Orrick’s HR or IT databases. For Orrick’s intranet, we were able to put users in four “big bucket” roles: partners, associates, secretaries, and staff. Throughout the site, content is delivered to best match the needs of those four different roles. One such feature is the intranet’s “quick links” section where the list of links is different for each of the roles.

We accomplished this level of personalization for Orrick’s intranet was through Windows authentication. By forcing an authentication process (which is seamless to the user – they don’t actually have to enter a username or password), we are able to capture the user’s HR information. As part of the login process, we save that information to a Sitecore user and assign appropriate roles. This was later used for personalization. 

## Integrations

Orrick’s intranet also contains many interactive pages that pull from line of business systems. Examples of this are a user’s “Your Page” which displays clients and matters they are currently engaged with client pages and matter pages. These pages contain a ton of data you wouldn’t expect to be stored as traditional content inside a web CMS such as Sitecore. We determined Sitecore would be a poor way to store this data because of the relational nature of the data and the fact that near real-time data was a requirement. As part of the project, a custom .NET Core API was developed for the data needed for line of business systems. Sitecore encouraged componentization of the interactive pages which allowed for parallel development and for the API to have many small, isolated functions. We used a javascript framework called Knockout to help us manage these client-side interactions. Because a vast majority of the API calls happen client-side, the site loads extremely fast, which was one of the key objectives for the rebuild. Highcharts was used to construct interactive charts and graphs which helped the data to be more easily consumed by users of the application.

## Search

Another key to Orrick’s intranet was Search. At the same time that the intranet was being built on Sitecore, Orrick was undertaking a massive enterprise search project. We were able to seamlessly integrate Orrick’s enterprise search solution, BA Insight’s SmartHub technology, into the intranet so that user’s had a “one-stop-shop” for all of their internal information needs. The new interface allows users to see results from repositories together or separately, with very little friction between the two. A nice side benefit of improving search is that it is one of the best ways to increase adoption and trust in the end product, aka the intranet.

## Lessons Learned
1. Bite off what you can chew / Launch with less –  We started with a Minimum Viable Product, our MVP, and went live with a hybrid Intranet of both old and new pages in order to meet a launch deadline.
2. Put a diverse team on the project –  There will inevitably be major challenges.  We were lucky to have a project and development team of about 10 people (both Perficient and Orrick), each with varying skill sets. This helped us navigate the challenges better.
3. Lead with what they need – By now, you know what actions your employees need to perform on the Intranet and what things they expect to find.  The things they need it for should be in their face and the nice-to-haves should be behind menus or be less prominent.  Use personalization to surface important information and tasks to the people that need them.
4. Ease of use helps adoption – Create an Intranet that doesn’t require training.  If users find value in it, they will come. We sent out coming soon emails pre-launch but offered no training options – we took the position that if it required training, we built it wrong.
5. Sitecore can be a fantastic platform for an intranet!