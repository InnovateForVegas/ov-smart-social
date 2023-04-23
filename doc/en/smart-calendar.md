<!--
 Copyright (C) 2022 Innovate for Vegas Foundation
 
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

# Smart Social Smart Calendar

The challenge is discovery and Las Vegas is not an environment easy to navigate as we attempt to find out what is going on and where.

Since a calendar is a familiar tool used by many people today (most if not all mobile phones incorporate a Google or Apple calendar for examples, not to mention day-to-day use in workplaces, schools, and so on), it is a functional, but familiar way to introduce the Smart Social platform, and so it is aimed to be the first component rolled out.

A Familiar Surprise.

The Smart Calendar component of Smart Social should function independently, but is intended to integrate nicely with other Smart Social components and external services.

## Highest Priority Considerations

## Specification Details

The proposed strategy here is a base introduction to the notion that a Smart City is not necessarily enabled by using Slack or Discord or Meetup or Eventbrite or... the list goes on. Beginning with standard calendars, iCalendar and iCalendar Streams, organizer-owned RSVPs, calendar sharing and status broadcast (in the event of reschedule, cancellation, etc).

By making use of standard map and location data structures and protocols, it is also a small matter to connect a date and time with a place, and to provide additional useful information such as parking and transit data, not to mention weather and other appropriate, useful information.

This specification is subject to continuous update over the life of the Smart Social project (and Smart Calendar Service as a part of it). Calendaring is a complicated, yet vital and ubiquitous service useful for so many things, this part of the Smart Social platform represents high-utility service to deploy and maintain.

### Standard CalDAV sharing

Services in use today from Google, Microsoft Outlook, and many others make use of CalDAV, or Calendar Distributed Authoring and Versioning to share calendar event and related information via iCalendar streams accessible at a published url, for periodic updates. As well, it is possible to provide an iCalendar stream file (a file with a suffix *.ics*) via email, QR Code, and other means, for a user calendar client to incorporate into an existing calendar.

A typical use case for CalDAV calendars, is to subscribe to a calendar with a personal calendar service, and from that point forward the event entries for the subscribed calendar will appear in the user calendar, often with color or other decoration to differentiate these subscribed events from the other user-originated events in the calendar. There are use cases accessible today wherein some central server, often an event website such as Meetup.com similar, will capture user-entered event information and make that information available as an iCalendar stream, accessible via CalDAV protocol.

In the simplest case, a user calendar service may subscribe to an iCalendar stream from a public event website with a CalDAV server, and the user calendar service will periodically download the current calendar stream and update the user calendar, which the user will interact with in any number of ways (a common example is a mobile calendar application on a phone or tablet, or a web-based calendar client in a web browser, or a calendar client built into an email or productivity application such as Microsoft Outlook):

```mermaid
flowchart LR
    M[Public Event Site] -->|CalDAV| U[User Calendar Service]
    U <--> C[Consumer Client]
```

As a user subscribed to multiple external calendars, they are able to see these external events appear in their familiar calendar interface, while they interact with their calendar as they normally would.

```mermaid
flowchart LR
    M[Public Event Site] -->|CalDAV| U[User Calendar Service]
    N[Public Event Site] -->|CalDAV| U[User Calendar Service]
    U <--> C[User Consumer Client]
```

The shortcoming in this mode of use, is the typical placement of the external calendar event information in the public event site server, which can often remove or otherwise leave out the notions of organizer and RSVP sharing. This makes the event (the VEVENT in fact) stored in each of the Public Event Sites as dangling members of calendar collections local, or owned, by each of the event sites as illustrated.

Using standard CalDAV sharing and subscription updating methodologies, transporting iCalendar streams with current information, it is possible to not only subscribe to calendars from public event sites, but to share events *to* public servers, so that a public calendar can be stored and presented based on the synchronizing of multiple individual calendar events.

```mermaid
flowchart LR
    S0[Smart Calendar Server] <-->|CalDAV| U[User Calendar Service]
    U <--> C[User Consumer Client]
```

In this case the user may be using a Google or Outlook calendar service, they have subscribed to one or more calendar streams published by a Smart Calendar services, and they not only receive iCalendar stream updates from the external service, but they share their public calendar with the external service (this is optional but illustrative).

In a larger-scale deployment scenario, there may be multiple public Smart Calendar Servers publishing multiple calendars, and synchronizing between themselves in some cases. The user can share their calendar, or not, in the bi-directional synchronization model, and they may also subscribe to public calendars that are synchronizing amongst themselves.

```mermaid
flowchart LR
    subgraph cal_cluster
    S0[Smart Calendar Server]<-->S1[Smart Calendar Server]
    end
    cal_cluster -->|CalDAV| U[User Calendar Service]
    S2[Smart Calendar Server] <-->|CalDAV| U[User Calendar Service]
    U <--> C[User Consumer Client]
```

Peer-to-peer synchronized sharing across Smart Calendar Servers (and CalDAV servers which conform to the necessary parts of the CalDAV protocol) will be used to publish and share particular calendar collections for decentralized availability. Each peer in the server sync scheme can select individual calendars to synchronize, and the user server can synchronize or ignore particular calendar collections as the user chooses.

The user server can synchronize its events and updates to peer servers when the peer has accepted a subscription to the user calendar. The Smart Calendar Server can accept a public calendar URL for synchronizing, and may confirm the subscription via email to the calendar owner, or the server can optionally accept a calendar anonymously (this is a risk to be analyzed).

### SmartCal API

Modern applications are written with RESTful and GraphQL API access in mind. The Smart Calendar Server is intended to service well-establish legacy CalDAV transactions, but also service applications locally and remotely to make use of calendar services in a variety of ways.

The core services will be analogs to CalDAV services, with the data payloads matching, at least, the expectations of the CalDAV protocol and iCalendar steam transport. The data is returned in JSON format in the core implementation of a RESTful API, with RFC 7465 as a guide.

The basic API service must accept a calendar component (eg a VEVENT) input from an authenticated and authorized user, via an HTML form submission or similar RESTful POST or PUT. Where CalDAV synchronization is server pull, this interaction will be user or client push, making user authentication and authorization for a specific calendar collection (or calendar component) essential.

Unlike the CalDAV peer synchronization relationships, the initial major version of the SmartCal API is intended to be called specifically by some client or server for a particular interaction. In the RESTful case, this would be multiple REST POST or PUT transactions, in the case of a GraphQL interface this would be multiple mutations occurring individually. The CalDAV synchronization protocol is fairly simply, the source server is always correct, with a check of sequence numbers per component where appropriate. Similarly, the SmartCal API assumes component-level granularity in its initial major version, and does not account for merges.

The SmartCal API will be published with OpenAPI documentation to enable code generation for callers and to make visible the features implemented along the development timeline. Aside from the CalDAV analogs, there is substantial latitude to create sensible interfaces to calendar data and service the Smart Calendar Server implements, either on its own or in conjunction with other Smart Social services. This will be noteworthy when implementing external integrations, which may be bi-directional. For example, integration with Meetup.com APIs may include a Meetup.com adaptor to the Smart Social APIs so that a client written for Meetup.com endpoints might work with Smart Social. This is by no means a high priority feature but this would make adoption by third party application developers that much easier.

## External Reference Materials

[vCalendar RFC](https://datatracker.ietf.org/doc/html/rfc5545)

[CalConnect.org Dev Guide (visit the wiki)](https://devguide.calconnect.org/)

[Schema.org Event type](https://schema.org/Event)

[iCalendar.org](https://icalendar.org/)

[iCalendar in JSON format](https://www.rfc-editor.org/rfc/rfc7265.html)

## User Stories

**Terms**:

- **Consumer**: an end user of Smart Calendars, may be a human or some automation.
- **Organizer**: an end user of Smart Calendars, either as Publisher or Source
- **ExtSource**: an external origin for Calendar content to capture, store, and possibly re-publish
- **IntSource**: an internal origin of Calendar content to store and publish.
- **Peer**: a special case ExtSource or IntSource.
- **Developer**: one who makes use of Smart Calendar APIs (or CalDAV) or similar to build on the platform

User Stories are implemented as [GitHub Story Issues in the Overview Repository](https://github.com/InnovateForVegas/ov-smart-social/issues)
