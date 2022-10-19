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

# Smart Social Integration

The Smart Social platform is built of several modules that are intended to function on their own, but also together.

This document will specify integration methods and strategies, as well as User Stories with specific integration use cases. Ideally the collection of integration use cases will be large and interesting, as will the Smart Social platform be.

As well, the Smart Social platform must integrate into the larger Internet, making use of OpenAPIs using modern methods (REST, GraphQL, gRPC, etc) and even legacy methods (RSS/ATOM, per module but also as a general integrated feature).

## Highest Priority Considerations

## Specification Details

## External Reference Materials

## User Stories

Individual stories may be converted into Issues, or consolidated or exploded as needed for development and implementation.

**Terms**:

- **Consumer**: an end user of Smart Social, may be a human or some automation.
- **ExtSource**: an external origin for any content to capture, store, and possibly re-publish
- **IntSource**: an internal origin of content to store and publish; this is presumed to be a Smart Social module.
- **Peer**: a special case ExtSource or IntSource. Likely another, separate instance of Smart Social modules.
- **Developer**: one who makes use of Smart Social APIs to build on the platform

### Typical Uses

- **Card**: As a Consumer, I would like to receive Smart News items via my Smart Messaging contact channels.
  - **Conversation**: Smart Messaging with email digests and end-to-end chat with notifications are both possibilities to share news items directly to a Consumer as they like. This is a classic push-to-Consumer approach, as opposed to publication on a web page for Consumer-pull, which is also to be supported.
  - **Confirmation**:
    - Consumer is able to receive Smart News items via email, chat, or other supported Smart Messaging channels under their control.

---
