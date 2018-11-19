---
title: Legal Entities
layout: default
root: ../
---

There are two types of entity: companies and individuals.

The government is implemented as a special kind of company with some restrictions
on the permissions that are available to non-moderator players.


## Company

### Basic Concepts

A player belongs to zero, one, or more companies.
A player can act on behalf of only one company at
a time - this is their active company. The active company can be obtained using the following function:

```lua
local comp = company.get_active(name)
```

### Actions and Permissions

Actions include:

* Setting up craft networks and factories (`CREATE_FACTORY`, `EDIT_FACTORY`)
* Making deals (`NEGOTIATE_TRADE`)
* Making acquisitions (`NEGOTIATE_STOCK`)
* Edit land (`EDIT_LAND`)

These actions are subject to having the appropriate permission:

```lua
if not comp:check_perm(name, perm_name, meta) then
	error("can't do this!")
end
```

Permissions can be granted by the CEO of a company to other
players at any time. This is done as part of the player tab
in the inventory formspec.

### Scripting

One interesting idea is the ability for company owners to provide Lua scripts
to manage permissions. This, of course, needs to be properly managed to avoid
DDoSes.

### Government Restrictions

All permissions in the government default to false.
The Government cannot own factories, buy companies, or sell shares.
The only grantable permission is the ability to edit public areas in cities.

Members of the government can, instead, vote on bills to affect tax and other
legislation. Note that this feature will only be available in later releases
of the game.
