---
label: "Manager | Member"
icon: book
order: 1400
---

# ASC-Factions Documentation

## Overview

The `ASC-Factions` module provides a set of functions for managing factions within the `alt-server` environment. This includes creating, updating, and deleting factions, as well as managing faction members and ranks.

## Import the FactionAPI

```javascript
const FactionsAPI = useApi().getAsync("ascended-factions-api");

FactionsAPI.member.someFunction();
```

## Functions

### `inviteMember(factionName: string, memberId: number, rankName: string, isLeader = false)`

Invites a member to a faction with the specified rank.

#### Usage:

```javascript
await inviteMember("FactionName", 12345, "NewRank", false);
```

#### Behavior:

- Checks if the faction exists.
- Checks if the rank exists in the faction.
- Adds the member to the faction if not already a member.
- Logs the invitation status.

### `kickMember(memberId: number)`

Kicks a member from their faction.

#### Usage:

```javascript
await kickMember(12345);
```

#### Behavior:

- Finds the member in the factions.
- Removes the member from the faction.
- Logs the removal status.

### `promoteMember(factionName: string, memberId: number)`

Promotes a member to the next rank in their faction.

#### Usage:

```javascript
await promoteMember("FactionName", 12345);
```

#### Behavior:

- Checks if the faction exists.
- Promotes the member to the next rank.
- Logs the promotion status.

### `demoteMember(factionName: string, memberId: number)`

Demotes a member to the previous rank in their faction.

#### Usage:

```javascript
await demoteMember("FactionName", 12345);
```

#### Behavior:

- Checks if the faction exists.
- Demotes the member to the previous rank.
- Logs the demotion status.

## Database Initialization

Ensure the factions collection is created:

```javascript
await Database.createCollection(FactionsConfig.dbCollection);
```

## Logging

The module uses `alt.logWarning` to log various statuses and errors throughout the operations.

## Summary

This module provides comprehensive functionality for managing factions in `alt-server`, including creation, updating, and deletion of factions, as well as member and rank management. It leverages a caching mechanism to optimize performance and ensure efficient data retrieval.
