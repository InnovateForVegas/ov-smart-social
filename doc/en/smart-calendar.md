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

# Smart Social Smart Calendar

The challenge is discovery and Las Vegas is not an environment easy to navigate as we attempt to find out what is going on and where.

Since a calendar is a familiar tool used by many people today (most if not all mobile phones incorporate a Google or Apple calendar for examples, not to mention day-to-day use in workplaces, schools, and so on), it is a functional, but familiar way to introduce the Smart Social platform, and so it is aimed to be the first component rolled out.

A Familiar Surprise.

The Smart Calendar component of Smart Social should function independently, but is intended to integrate nicely with other Smart Social components and external services.

## Highest Priority Considerations

## Specification Details

The proposed strategy here is a base introduction to the notion that a Smart City is not necessarily enabled by using Slack or Discord or Meetup or Eventbrite or... the list goes on. Beginning with standard calendars, iCalendar and iCalendar Streams, organizer-owned RSVPs, calendar sharing and status broadcast (in the event of reschedule, cancellation, etc).

By making use of standard map and location data structures and protocols, it is also a small matter to connect a date and time with a place, and to provide additional useful information such as parking and transit data, not to mention weather and other appropriate, useful information.

A useful resource for general calendar technologies is at [CalConnect](https://devguide.calconnect.org/) also included in References below.

## External Reference Materials

[vCalendar RFC](https://datatracker.ietf.org/doc/html/rfc5545)

[CalConnect.org Dev Guide (visit the wiki)](https://devguide.calconnect.org/)

[Schema.org Event type](https://schema.org/Event)

[iCalendar.org](https://icalendar.org/)

## User Stories

Individual stories may be converted into Issues, or consolidated or exploded as needed for development and implementation.

**Terms**:

- **Consumer**: an end user of Smart Calendars, may be a human or some automation.
- **Organizer**: an end user of Smart Calendars, either as Publisher or Source
- **ExtSource**: an external origin for Calendar content to capture, store, and possibly re-publish
- **IntSource**: an internal origin of Calendar content to store and publish.
- **Peer**: a special case ExtSource or IntSource.
- **Developer**: one who makes use of Smart Calendar APIs (or CalDAV) or similar to build on the platform

### Typical Uses

- **Card**: As a Consumer, I would like to subscribe to a central source of Calendar event information using my normal Calendar tools.
  - **Conversation**: With mobile device use nearly ubiquitous, the casual Consumer has access to CalDAV Calendar services from Google, Microsoft/Outlook, and other services. The ability to discover and subscribe to calendars from a central location will make it easier to find events of interest and follow them in a standard way.
  - **Confirmation**:
    - Consumer is able to discover and subscribe to Calendar events using their standard Calendar tools such as Google Calendar, Microsoft Outlook, Apple iCalendar, and similar, to integrate events into their daily schedule.

---

- **Card**: As a Consumer, I would like to RSVP to an Event on a Calendar to which I am subscribed or which I am following on the Smart Calendar server(s).
  - **Conversation**: The RSVP Fanout problem is real. As Organizers publish Events to various different platforms and services, the RSVP process can lead to multiple RSVPs from one Consumer across platforms, or the lack of useful RSVP capture at all for a given platform. The goal here is to enable a Consumer to RSVP to an Event (assuming it is a public event open to RSVPs without invitations) and thus follow that Event for updates.
  - **Confirmation**:
    - Consumer is able to RSVP to an Event and later receive updates to the Event made by Organizer and disseminated via email (at least).

---

- **Card**: As a Consumer, I would like to receive update notifications when Calendars to which I am subscribed change with new or updated Events.
  - **Conversation**: Calendar servers are generally email-centric for managing organizers and subscribers (that is, anyone who has a Calendar usually has an email address associated with it), and so notifications are typically sent via email to those invited to or attending Events within a particular Calendar. Here, it is useful to notify those interested in new events a notification regardless of their attendee status for a particular event. This is not typical behavior, but will have utility for event discovery.
  - **Confirmation**:
    - Consumer subscribed to or otherwise following a Calendar receives notifications via email (at least) when a new Event is added to Calendar, or if an existing Event is updated, regardless of their attendee status for a given Event.

---

- **Card**: As an Organizer, I would like to maintain my own calendar, and publish it to a central server to share with others, but maintain control of my calendar events.
  - **Conversation**: The CalDAV protocol and workflow enables an origin Calendar maintained by an Organizer, to publisher their calendar for public visibility, and for synchronizing with other CalDAV servers. A central Smart Calendar server can capture Calendars and make them more easily discoverable and visible, while enabling the Organizer to update or even cancel an Event on their origin Calendar, which propagates to the Peering Smart Calendar server(s).
  - **Confirmation**:
    - Organizer is able to share a public calendar with Smart Calendar server, and publish events in their Origin Calendar that are captured by the Smart Calendar server, and update or cancel those Events, with the changes also propagating to the Smart Calendar server(s).

---

- **Card**: As an Organizer, I would like receive RSVP information from Consumers regardless of where my Calendar Event is published.
  - **Conversation**: RSVP Propagation from shared calendars is supported in CalDAV. If a Consumer is viewing an Event shared via a Smart Calendar server, and RSVPs to that Event, the RSVP must propagate to the Organizer (specifically to their origin ExtSource). For example, an Event published on Organizers Google Calendar, shared to Smart Calendar, receives an RSVP from Consumer, that RSVP must propagate to the Organizer’s Google Calendar by way of the Smart Calendar Server.
  - **Confirmation**:
    - Organizer receives RSVP user information propagated from Smart Calendar servers to their origin Calendar Server.

---
