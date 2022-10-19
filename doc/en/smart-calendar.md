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

A Famliar Surprise.

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

- **Consumer**: a user of Smart Calendar services in general, usually a person but possibly automation tools.
- **Organizer**: a user or service which owns calendars and calendar objects, sends invites and updates, and receives RSVP messages from Consumers.
- **Developer**: a user of Smart Calendar services who is creating tools or services making use of Smart Calendar APIs and data.
- **Company**: a transit company, commission, or other agency overseeing transit services

### Typical Uses

- **Card**: As a Consumer, I need to know when my bus will arrive so that I can plan my arrival at the bus stop accordingly.
  - **Conversation**: Each Consumer of transit services has their own journey to make from their actual point of origin to the bus stop at which they will wait for the arrival of their bus.
  - **Confirmation**:
    - Consumer is able to determine estimated versus scheduled arrival time for any route at any stop, with statistical information presented in clear terms (% on time, etc)

- **Card**: As a Organizer, I need to know when my guess are going to arrive and when the reservation starts.
  - **Conversation**: The Organizer has a dynamic list of the number of guests attending and keep track of time.
  - **Confirmation**:
    - Organizer is able to see who rsvped and when their event ends

---
