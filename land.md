---
title: Land
layout: default
root: ../
---

Land areas can be owned by a company, an individual, or the government.
The area protection is implemented using a modified version of
`areas` by ShadowNinja with more callbacks, and a `land` mod.

<h2 class="mt-4">Exclusive Subareas</h2>

Unlike with vanilla `areas`, owners of parent area cannot modify a subarea unless
they are also own that area. This is done to protect, for example, a company
subletting from a property company which has created a mall.

Note that owner is used vaguely to mean an employee of
the company with correct permissions, the owning individual, or a member of the
government if government-owned.

<h2 class="mt-4">Structure</h2>

The world is protected by an arbitrary tree of area protections.
The government should own root areas (ie: areas with no parents),
and sublet areas to private persons and companies.

It is suggest to create an area for each city, then to subarea into zones
and individual lots.
These city areas can be maintained by members of the Land department.

The city then contains subareas for each district, with rentable lots on each.

    City A
    ├── City Centre (C)
    │   ├── Shop 1 (C)
    │   ├── Shop 2 (C)
    │   ├── Mall (C)
    │   |   ├── Shop 4 (C)
    │   |   └── Shop 5 (C)
    │   └── Offices 1 (I)
    └── Industrial (I)
        ├── Factory 1 (I)
        ├── Factory 2 (I)
        ├── Factory 3 (I)
        ├── Factory 4 (I)
        ├── Offices 2 (I)
        ├── Offices 3 (I)
        └── Offices 4 (I)
    City B
    └── City Centre (C)
        └── Shop 1 (C)

## Eviction

When renting, tenants can be evicted by the parent owner with a month's notice
(a week IRL), or immediately by an admin.

Owners of a property can only be evicted by the admin.

Anything left by the tenant on eviction will be automatically packed up and
stored by the government. The remaining content can be obtained for free until
6 months time (6 weeks), at which point it is sold by the government.
