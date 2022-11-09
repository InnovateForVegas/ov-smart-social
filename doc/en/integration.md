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

Integrations always place user information and credentials at risk, it is the name of the game whenever one leaves the walled garden we have control over.

By way of example, if a user of Smart Social uses a particular display name and connects to some other service one which they use a different display name, it may be possible for some third party to connect the two display names as the same user. At best this is an unintentional exposure, at worst this can *out* someone where they did not wanted to be outed (in whichever context that may apply).

Thus, it is imperative that user privacy and credential security be maintained while interacting with external services by way of any integrations with Smart Social platform components, to the extent it is possible.

## Specification Details

This specification is subject to continuous update over the life of the Smart Social project, as more integration considerations appear.

## Servicing Incoming Requests

As a content platform, Smart Social needs to at minimum respond using the standards of online content found in all modern platforms, and in some legacy platforms.

Any content on a Smart Social platform implementation should be available via a canonical URL, in these formats:

- **HTML5** - Human-readable and WAI-ARIA accessible, ideally including schema.org markup
- **JSON** - in a generalized rendering pipeline, the content used to generate an HTML view can be served without the HTML, also applicable to a GraphQL interface
- **XML** - this is a stretch, but the rendering pipeline should be able to output XML, *eg* XHTML which may be useful… for example, RSS/ATOM feeds

In simplest terms, an HTTP GET request to a Smart Social URL should return at least one of the above static document formats. This makes embedding, sharing, forwarding, and so on easier for external clients and integration into external applications. An appropriate default document format can be used for a particular context, while a document may also include a standard suffix to select a specific type.

For example, if one were to visit a url at /path/to/document it may yield one of the following:

- /path/to/document returns the default document for this path, eg HTML5
- /path/to/document.html returns HTML5 explicitly
- /path/to/document.json returns the document content in a JSON structure for downstream or external rendering, etc
- /path/to/document.xhtml returns an xhtml structured XML document
- /path/to/document.rss returns an RSS structured XML document
- /path/to/document.atom returns an ATOM structured XML document

and so on. This means the rendering pipeline responsible for the final view/document output should defer commitment to an output format until as late in the pipeline as possible.

In cases where the document endpoint is a summary or top-level index or similar, the use cases for this approach for feed aggregation, automations using IFTTT or Zapier or similar, or general interaction as a user or their client-side tools want to interact with Smart Social content become more interesting.

### Servicing Incoming API Requests

Accessing Smart Social content and services via the full range of HTTP verbs and other methods is a more complicated goal and will require attention paid to user authentication and authorization in order to accomplish any mutations or edits in general.

Each Smart Social component must implement an OpenAPI interface description to enable external API access to content and services, and must adhere to the overall Smart Social security policy and best practices.

## Making External Requests

Implementing access to third party services, or to other services related more closely to Smart Social (eg a mastodon instance, a matrix server) will require something like an adaptor infrastructure to enable services to make requests of endpoints without unnecessary dependencies on those endpoints. That is, API breakage, accessing similar services with incompatible APIs, and similar should be isolated to the adaptor, rather than making core code depend on external services and their interfaces.

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
