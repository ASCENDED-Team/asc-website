---
label: "Manager | Faction"
icon: book
order: 1500
---

# ASC-Factions Documentation

## Overview

The `ASC-Factions` module provides a set of functions for managing factions within the `alt-server` environment. This includes creating, updating, and deleting factions, as well as managing faction members and ranks.

## Import the FactionAPI

```javascript
const FactionsAPI = useApi().getAsync("ascended-factions-api");

FactionsAPI.manager.someFunction();
```

## Functions

### `createFaction(name: string)`

Creates a new faction with the specified name.

#### Usage:

```javascript
await createFaction("FactionName");
```

#### Behavior:

- Checks if a faction with the given name already exists.
- If not, creates a new faction document and adds it to the database.
- Logs the creation status.

### `addRank(factionName: string, newRankName: string)`

Adds a new rank to the specified faction.

#### Usage:

```javascript
await addRank("FactionName", "NewRank");
```

#### Behavior:

- Checks if the faction exists.
- Adds the new rank if it doesn't already exist.
- Logs the addition status.

### `removeRank(factionName: string, rankNameToRemove: string)`

Removes a rank from the specified faction.

#### Usage:

```javascript
await removeRank("FactionName", "RankName");
```

#### Behavior:

- Checks if the faction exists.
- Removes the rank if it exists.
- Logs the removal status.

### `deleteFaction(factionName: string)`

Deletes the specified faction.

#### Usage:

```javascript
await deleteFaction("FactionName");
```

#### Behavior:

- Checks if the faction exists.
- Deletes the faction document from the database.
- Logs the deletion status.

### `renameFaction(factionName: string, newName: string)`

Renames the specified faction.

#### Usage:

```javascript
await renameFaction("OldName", "NewName");
```

#### Behavior:

- Checks if the faction exists.
- Renames the faction.
- Logs the renaming status.

### `clearFaction(factionName: string)`

Clears all members from the specified faction.

#### Usage:

```javascript
await clearFaction("FactionName");
```

#### Behavior:

- Checks if the faction exists.
- Clears all members from the faction.
- Logs the clearing status.

### `getAllFactions()`

Returns all factions.

#### Usage:

```javascript
const factions = await getAllFactions();
```

#### Behavior:

- Retrieves all factions from the database.
- Uses a cached version if available.

### `getFactionByName(factionName: string)`

Returns the faction with the specified name.

#### Usage:

```javascript
const faction = await getFactionByName("FactionName");
```

#### Behavior:

- Retrieves the faction from the cached list of factions.

### `getPlayersFaction(playerId: number)`

Returns the faction a player belongs to.

#### Usage:

```javascript
const faction = await getPlayersFaction(playerId);
```

#### Behavior:

- Checks all factions to find which one the player is a member of.
- Logs if the player is not found in any faction.

### `getPlayerRank(playerId: number)`

Returns the rank of a player within their faction.

#### Usage:

```javascript
const rank = await getPlayerRank(playerId);
```

#### Behavior:

- Checks all factions to find the player's rank.
- Logs if the player is not found in any faction.

### `clearFactionsCache()`

Clears the cached factions list.

#### Usage:

```javascript
await clearFactionsCache();
```

#### Behavior:

- Resets the cached factions list and the initialization flag.

## Database Initialization

Ensure the factions collection is created:

```javascript
await Database.createCollection(FactionsConfig.dbCollection);
```

## Logging

The module uses `alt.logWarning` to log various statuses and errors throughout the operations.

## Summary

This module provides comprehensive functionality for managing factions in `alt-server`, including creation, updating, and deletion of factions, as well as member and rank management. It leverages a caching mechanism to optimize performance and ensure efficient data retrieval.
