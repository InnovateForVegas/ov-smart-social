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

# Smart Social Smart Contacts

This is the age of the QR Code, used often to share URLs for websites and sign-in forms and whatnot, but perhaps more so to share contact information. Contact information across platforms, across devices, across language barriers, across any divide, is a constant requirement every day, and it can be made more useful with some creative application of existing standards and offline device features.

The Smart Contacts component of Smart Social should function independently, but is intended to integrate nicely with other Smart Social components and external services.

## Highest Priority Considerations

It is often the case that a person would like to share one contact configuration in one context, and some other configuration in another. For examples (see User Stories section for more detail), a user may want to have contact information to share for one job or role, another set for a completely different job or role, and yet another configuraton for personal use without reference to any job or role. It is critical that the user always has control over which information is shared in which context, if at all.

An extremely unlikely circumstance, wherein some user creates and publishes Smart Contact information for some other person, without permission, could be considered a violation of a person’s privacy. While this is difficult to check, it is something to be aware of, and it may come to pass that user verification is required, via email, phone number check, or similar. Verifying an email address seems like an easy first pass, though this requires that a user share this personal information where they not want to share their email address in general. It is something to ponder sooner rather than later.

## Specification Details

If a Smart City relies on Twitter and Nextdoor to inform its population of important updates, there is something missing. That is Smart Contacts.

Maintaining a locale-based anonymous communication channel is reasonably simple with modern technology and enables one-way broadcast based on location, and two-way conversation regarding service requests and other lower-priority discussion (this would not be intended to take the place of emergency services contacts such as 9-1-1 and similar).

## External Reference Materials

[vCard RFC](https://datatracker.ietf.org/doc/html/rfc6350)

[CardDAV RFC](https://datatracker.ietf.org/doc/html/rfc6352)

[Lightweight Directory Access Protocol](https://ldap.com/)

[Schema.org Person type](https://schema.org/Person)

## User Stories

Individual stories may be converted into Issues, or consolidated or exploded as needed for development and implementation.

**Terms**:

- **Consumer**: an end user of Smart Contacts, may be a human or some automation.
- **ExtSource**: an external origin for contacts to capture, store, and possibly re-publish
- **IntSource**: an internal origin of contacts to store and publish.
- **Peer**: a special case Consumer or ExtSource, often both.
- **Developer**: one who makes use of Smart Contacts APIs (or CardDAV) or similar to build on the platform

### Typical Uses

- **Card**: As a Consumer, I need to know when my bus will arrive so that I can plan my arrival at the bus stop accordingly.
  - **Conversation**: Each Consumer of transit services has their own journey to make from their actual point of origin to the bus stop at which they will wait for the arrival of their bus.
  - **Confirmation**:
    - Consumer is able to determine estimated versus scheduled arrival time for any route at any stop, with statistical information presented in clear terms (% on time, etc)

---
