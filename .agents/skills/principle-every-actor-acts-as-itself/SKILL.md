---
name: principle-every-actor-acts-as-itself
description: "Apply when work involves identity, service accounts, automation or access. Users, groups, agents, systems and bots each act as themselves, with only the access the task needs."
---

# Every actor acts as itself

1. Distinct actors: user, group, agent, system, bot. Agents are principals with an owner. Automation
   runs as a service or bot identity, never as a person.
2. Every token carries an audience, and a service refuses tokens meant for another.
3. Internal user IDs map explicitly to identity-provider subjects; never key users on the raw `sub`.
4. People get access only to the one resource their task needs.
5. The organisation's account, never a person's, owns shared resources and accounts.
6. Invitations bind late, at claim time, to a verified identifier.

Why: clear principals keep authorization auditable, and identity that survives a provider change avoids
re-keying every user.
