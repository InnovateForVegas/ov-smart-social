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

# Smart Social Smart Messaging

The modern era is all about messaging, this component will attempt to make a privacy-aware implementation available to connect our Smarter Smart City, with Smart Messaging.

This module is not intended to be yet another Discord or Slack or Teams platform. However, with chat rooms as a standard feature of the likely existing messaging platform, Matrix, the comparison will be made. The key difference with the use of Matrix, is the possibility for a single user, or groups of users, to have accounts on their own self-hosted Matrix servers, and then communicate with other Matrix servers in a decentralized, self-hosted messaging network. This is not a feature of Smart Messaging, but rather an essential piece of existing technology to build upon for the Smart Messaging collection of services.

As well, an existing piece of software, Mailman, is quite capable of handling mailing lists (a modern email listserv). The classic mailing list is one of those things that nobody really thinks about, but which keeps people informed with newsletters, digests, and reminders, not to mention alerts and other higher-priority messages. Integration of a city-scale mailing list service is essential though likely undervalued initially. Individual, single-recipient email alerts are also essential, especially if encrypted email is used.

The Smart Messaging component of Smart Social should function independently, but is intended to integrate nicely with other Smart Social components and external services.

## Highest Priority Considerations

As with most things in the modern era prone to abuse, any form of chat between individuals or group chat rooms, or emailing, is all subject to misuse at best, and actual crime at worst. It is essential that private messaging between adults and minors be disallowed or highly regulated. Any occurrence count greater than zero, of scenarios where anyone is injured as a result of coercion or bullying or any other acceptable use cases, is completely unacceptable. (Note that the implementation need not enforce policy, but enabling a policy or policies to be implemented and enforced is essential)

General spam is also a concern across messaging methods and is also a priority, but nowhere near as high a priority to plan defensively for than potential injury to users of the Smart Messaging services.

## Specification Details

## External References

[Matrix.org Decentralized Communication](https://www.matrix.org/)

[GNU Mailman](https://list.org/)

[Public Key Infrastructure (start at Wikipedia)](https://en.wikipedia.org/wiki/Public_key_infrastructure)

## User Stories

Individual stories may be converted into Issues, or consolidated or exploded as needed for development and implementation.

**Terms**:

- **Consumer**: an end user of Smart Messaging, may be a human or some automation.
- **ExtSource**: an external origin for Smart Messaging to receive, store, and possibly re-transmit
- **IntSource**: an internal origin of Smart Messages to store and transmit.
- **Peer**: a special case Consumer or ExtSource.
- **Developer**: one who makes use of Smart Messaging APIs or similar to build on the platform

### Typical Uses

- **Card**: As a Consumer, I need to know when my bus will arrive so that I can plan my arrival at the bus stop accordingly.
  - **Conversation**: Each Consumer of transit services has their own journey to make from their actual point of origin to the bus stop at which they will wait for the arrival of their bus.
  - **Confirmation**:
    - Consumer is able to determine estimated versus scheduled arrival time for any route at any stop, with statistical information presented in clear terms (% on time, etc)

---
