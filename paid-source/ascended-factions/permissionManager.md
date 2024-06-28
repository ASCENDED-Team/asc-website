---
label: "Manager | Permission"
icon: book
order: 1300
---

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

FactionsAPI.permission.someFunction();
```

## Functions

### `addRankPermission(factionName: string, rankName: string, permission: string)`

Adds a permission to a rank within a faction.

#### Usage:

```javascript
await addRankPermission("FactionName", "RankName", "Permission");
```

#### Behavior:

- Checks if the faction exists.
- Checks if the rank exists within the faction.
- Adds the permission to the rank if not already present.
- Updates the database with the new permission.
- Logs the addition status.
- Updates member permissions.

### `removeRankPermission(factionName: string, rankName: string, permission: string)`

Removes a permission from a rank within a faction.

#### Usage:

```javascript
await removeRankPermission("FactionName", "RankName", "Permission");
```

#### Behavior:

- Checks if the faction exists.
- Checks if the rank exists within the faction.
- Removes the permission from the rank if present.
- Updates the database with the removed permission.
- Logs the removal status.
- Updates member permissions.

### `checkRankPermission(factionName: string, rankName: string, permission: string): Promise<boolean>`

Checks if a rank within a faction has a specific permission.

#### Usage:

```javascript
const hasPermission = await checkRankPermission(
  "FactionName",
  "RankName",
  "Permission"
);
```

#### Behavior:

- Checks if the faction exists.
- Checks if the rank exists within the faction.
- Checks if the rank has the specified permission.
- Logs the permission status.
- Returns `true` if the permission exists, `false` otherwise.

### `updateMemberPermissions(factionName: string, memberId: number, newRankName: string)`

Updates a member's permissions when their rank changes.

#### Usage:

```javascript
await updateMemberPermissions("FactionName", 12345, "NewRankName");
```

#### Behavior:

- Checks if the faction exists.
- Finds the member in the faction.
- Updates the member's rank and permissions.
- Updates the database with the new rank and permissions.
- Logs the update status.

### `revokeAllGroupPermissions(member)`

Revokes all group permissions for a member.

#### Usage:

```javascript
await revokeAllGroupPermissions(member);
```

#### Behavior:

- Logs the member information.
- Removes all group permissions for the member.

## Database Initialization

Ensure the factions collection is created:

```javascript
await Database.createCollection(FactionsConfig.dbCollection);
```

## Logging

The module uses `alt.logWarning` to log various statuses and errors throughout the operations.

## Summary

This module provides comprehensive functionality for managing faction ranks and permissions in `alt-server`, including adding, removing, checking, and updating permissions, as well as revoking all permissions for a specific member. It leverages a caching mechanism to optimize performance and ensure efficient data retrieval.
