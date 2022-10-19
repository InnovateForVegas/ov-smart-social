<!--
 Copyright (C) 2022 Code for Vegas Foundation
 
 This file is part of ov-smart-social.
 
 ov-smart-social is free software: you can redistribute it and/or modify
 it under the terms of the GNU General Public License as published by
 the Free Software Foundation, either version 3 of the License, or
 (at your option) any later version.
 
 ov-smart-social is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU General Public License for more details.
 
 You should have received a copy of the GNU General Public License
 along with ov-smart-social.  If not, see <http://www.gnu.org/licenses/>.
-->

# Smart Social Smart News

In the simplest sense, this is a news feed, which has become as staple across all social media platforms, from MySpace and its ilk, to Facebook and their development of OpenGraph meta tagging for connecting shared items in a feed, to Twitter and its microblog entries and novel reply scheme, to various forms of Chat and Forums that take on a chronological presentation that is exceedingly rare in the other cases, which are often driven by algorithms to maximize engagement and monetization. The base functionality of the Smart News component is intended to function more like a forum or RSS feed with entries ordered chronologically, but with more consumer control.

Initially the Smart News services will focus on textual content, though over time an image or general media feed is also a possibility, very similar to the way RSS feeds are used to distribute podcasts and other media, except that RSS suffers from legacy boredom. A publishing scheme to examine as a fundamental of this project component, is structuring Smart News feeds similarly to RSS feeds, but with content sourced as Schema.org annotated HTML 5. This approach has many potential advantages, including ease of authoring or automated generation (the content structure is often a subset of a normal web page), ease of display of that content, ease of integration of WAI-ARIA accessibility features directly, and substantial machine-readability with Schema.org data annotations. More detail about these advantages below.

It may be worth considering inclusion of a classic usenet news style peering service, enabling anyone to read news locally using classic, proven infrastructure and tools.

The Smart News component of Smart Social should function independently, but is intended to integrate nicely with other Smart Social components and external services.

## Highest Priority Considerations

News is a contentious thing in the modern era, especially if it includes so-called user-generated content, such as blog entries or twitter feeds or similar. It will be essential that content not be censored, but also not raise ire, eg publishing *adult content* such that minor children can access that content, is a problem. Generally speaking, there will be content on the input side, that should not make it to the output side, this is the way it is, and initially there will be items that get through which should not. Consideration of content filtering (not so much censoring, but controlled viewing with control left to the Consumer whenever possible, within Publisher-vs-Platform laws such as 47 U.S. Code § 230). (Note that the implementation need not enforce policy, but enabling a policy or policies to be implemented and enforced is essential)

## Specification Details

There are many ways to consume news and current information. The challenge here is connecting any one event to a series of events unfolding in a story arc, connecting events in or near a particular location over time, and tracking directly and indirectly-related pieces of information to help maintain an informed populace.

Case in point, at the time of the preparation of this overview, water levels at Lake Mead are continuing to decline, and while daily and even hourly weather reports are commonplace, this vital resource is report on as though it were a comet or cicada hatching. Connecting news updates about water levels to other related news events is a simple, yet highly appropriate example.

## External Reference Materials

[Cornell Law Library: 47 U.S. Code § 230](https://www.law.cornell.edu/uscode/text/47/230)

[RSS Specifications collection](http://www.rss-specifications.com/)

[ATOM RFC](https://datatracker.ietf.org/doc/html/rfc4287)

[Schema.org article about News Markup](https://schema.org/docs/news.html)

## User Stories

Individual stories may be converted into Issues, or consolidated or exploded as needed for development and implementation.

**Terms**:

- **Consumer**: an end user of Smart News content, may be a human or some automation.
- **ExtSource**: an external origin for Smart News content to capture, store, and possibly re-publish
- **IntSource**: an internal origin of Smart News content to publish.
- **Peer**: a special case Consumer or ExtSource.
- **Developer**: one who makes use of Smart News APIs or similar to build on the platform

### Typical Uses

- **Card**: As a Consumer, I need to know when my bus will arrive so that I can plan my arrival at the bus stop accordingly.
  - **Conversation**: Each Consumer of transit services has their own journey to make from their actual point of origin to the bus stop at which they will wait for the arrival of their bus.
  - **Confirmation**:
    - Consumer is able to determine estimated versus scheduled arrival time for any route at any stop, with statistical information presented in clear terms (% on time, etc)

---
