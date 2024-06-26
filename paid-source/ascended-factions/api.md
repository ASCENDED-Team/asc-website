# Faction API

## General Operations

### `createFaction(name: string)`

Creates a new faction with the specified name if it doesn't already exist.

- **Parameters:**
  - `name` (string): The name of the faction to be created.
- **Returns:** Void.
- **Logs:** Logs a warning if the faction already exists.

---

### `deleteFaction(factionName: string)`

Deletes the faction with the given name.

- **Parameters:**
  - `factionName` (string): The name of the faction to delete.
- **Returns:** Void.
- **Logs:** Logs a warning if the faction does not exist.

---

### `renameFaction(factionName: string, newName: string)`

Renames an existing faction.

- **Parameters:**
  - `factionName` (string): The current name of the faction.
  - `newName` (string): The new name to assign to the faction.
- **Returns:** Void.
- **Logs:** Logs a warning if the faction does not exist.

---

### `clearFaction(factionName: string)`

Removes all members from a faction, leaving only the leader.

- **Parameters:**
  - `factionName` (string): The name of the faction to clear.
- **Returns:** Void.
- **Logs:** Logs a warning if the faction does not exist.

## Member Management

### `inviteMember(factionName: string, memberId: number, rankName: string)`

Invites a new member to join the faction.

- **Parameters:**
  - `factionName` (string): The name of the faction to invite the member to.
  - `memberId` (number): The ID of the player to invite.
  - `rankName` (string): The initial rank to assign to the new member.
- **Returns:** Void.
- **Logs:** Logs a warning if the member is already in a faction.

---

### `kickMember(memberId: number)`

Removes a member from their faction.

- **Parameters:**
  - `memberId` (number): The ID of the member to kick.
- **Returns:** Void.
- **Logs:** Logs a warning if the member is not found in any faction.

---

### `promoteMember(memberId: number, newRank: string)`

Promotes a member within their faction to a higher rank.

- **Parameters:**
  - `memberId` (number): The ID of the member to promote.
  - `newRank` (string): The new rank to assign to the member.
- **Returns:** Void.
- **Logs:** Logs a warning if the member is not found in any faction.

---

### `demoteMember(memberId: number, newRank: string)`

Demotes a member within their faction to a lower rank.

- **Parameters:**
  - `memberId` (number): The ID of the member to demote.
  - `newRank` (string): The new rank to assign to the member.
- **Returns:** Void.
- **Logs:** Logs a warning if the member is not found in any faction.

## Utility Functions

### `getPlayersFaction(playerId: number): Promise<Faction | null>`

Retrieves the faction of a player based on their ID.

- **Parameters:**
  - `playerId` (number): The ID of the player whose faction is to be retrieved.
- **Returns:** A `Promise` resolving to the `Faction` object if the player is in a faction, otherwise `null`.
- **Logs:** Logs a warning if the player is not a member of any faction.

## Internal Functions

### `getAllFactions(): Promise<Faction[]>`

Retrieves all factions from the database.

- **Returns:** A `Promise` resolving to an array of `Faction` objects.
- **Logs:** Logs a warning if no factions are found in the database.

---

### `getFactionByName(factionName: string): Promise<Faction | undefined>`

Retrieves a faction from the database by its name.

- **Parameters:**
  - `factionName` (string): The name of the faction to retrieve.
- **Returns:** A `Promise` resolving to the `Faction` object if found, otherwise `undefined`.
- **Logs:** Logs a warning if the faction with the specified name is not found.

---

### `clearFactionsCache()`

Clears the cached factions data.

- **Returns:** Void.
- **Notes:** Called after database operations (create, update, delete) to ensure data consistency.

## Initialization

### `createFactionsCollection()`

Creates the database collection for factions using the configuration.

- **Returns:** Void.
- **Notes:** Should be called during application startup to ensure the database collection exists.
