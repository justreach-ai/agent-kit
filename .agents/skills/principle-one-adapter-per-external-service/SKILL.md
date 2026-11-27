---
name: principle-one-adapter-per-external-service
description: "Apply when integrating several external services that do the same job. Give each service its own adapter behind one shared interface; never a bespoke command, flag or code path per connection."
---

# One adapter per external service

1. When a capability talks to several external services of one kind (issue trackers, chat tools,
   calendars, model providers), define the interface once and give each service its own adapter behind
   it, built on that service's public API.
2. Callers, commands and agent tools speak only the interface. Adding a service means adding an adapter,
   not a new command, flag or branch in the caller.
3. With a single service, don't add the interface yet (`principle-fewer-concepts`); add it when the second
   one arrives.
4. Prefer a standard interface for that kind of service, where one exists, over a new one
   (`principle-standards-before-bespoke`).

Why: per-connection commands grow with every service and teach agents a new verb each time; adapters keep
the surface the same size however many services are connected.
