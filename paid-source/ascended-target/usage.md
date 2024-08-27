---
label: "Usage"
icon: book
---

# Ascended Target System

The Ascended Target System is a robust interaction framework designed for alt:V, allowing developers to create dynamic and interactive experiences within their game world. This system enables the creation of both entity-based and position-based interactions, providing a flexible solution for various gameplay scenarios.

## Table of Contents

1. [Key Components](#key-components)
2. [Events](#events)
3. [API](#api)
4. [Types](#types)
5. [Client-Side Implementation](#client-side-implementation)
6. [Usage Examples](#usage-examples)

## Key Components

The Ascended Target System consists of several key components:

- **Server-side API**: Manages the creation and destruction of interactions.
- **Client-side Vue component**: Renders the interaction UI.
- **Shared types and events**: Ensures consistency between server and client.

## Events

The system uses a set of predefined events for communication between the server and client:

```typescript
export const TARGET_EVENTS = {
  ToClient: {
    SET_ENTITY_INTERACTIONS: "asc-target:set-entity-interactions",
    SET_POSITION_INTERACTION: "asc-target:set-position-interactions",
    REMOVE_POSITION_INTERACTION: "asc-target:remove-position-interaction",
  },
  ToServer: {
    CALLBACK: "asc-target:callback",
  },
  WebView: {
    POSITIONS: "asc-target:positions",
    POSITION_REMOVE: "asc-target:position-remove",
  },
};
```

## API

The Ascended Target API provides the following main functions:

- `createModelInteraction`: Creates an interaction for a specific entity model.
- `createPosInteraction`: Creates a position-based interaction.
- `destroyPosInteraction`: Removes a position-based interaction.
- `getTargetEvents`: Returns the TARGET_EVENTS object.
- `getAvailableObjects`: Returns a list of predefined interactive objects.

## Types

The system uses several TypeScript types to ensure type safety:

```typescript
type EntityID = number;
type Position = { x: number; y: number; z: number };

export type target_interaction = {
  uid: string;
  id: EntityID | Position | string;
  model: number;
  canInteract: boolean;
  currentPos?: alt.Vector3;
  originalPos: alt.Vector3;
  screenPos: alt.Vector3 | null;
  interactions: Array<target_buttons>;
};

export type target_buttons = {
  uid: string;
  text: string;
};

export type global_interactions = {
  uid: string;
  model?: number;
  pos?: alt.Vector3;
  interactions: {
    uid: string;
    text: string;
    handle: InteractionHandler;
  }[];
};
```

## Client-Side Implementation

The client-side is implemented using a Vue component (`Target.vue`) that renders the interaction UI. Key features include:

- Dynamic rendering of interaction points and buttons
- Keyboard navigation for selecting interactions
- Smooth transitions for interaction visibility

## Usage Examples

Here's an example of how to create a position-based interaction:

```typescript
const pos = new alt.Vector3(player.pos.x, player.pos.y, player.pos.z + 0.5);
const interactions = [
  {
    text: "Test Interaction",
    uid: utility.uid.generate(),
    handle: (player: alt.Player) => {
      console.log(`Test Interaction executed`);
    },
  },
];

TargetAPI.createPosInteraction(pos, interactions, true);
```

And here's how to create an entity-based interaction:

```typescript
TargetAPI.createModelInteraction(player, {
  uid: utility.uid.generate(),
  model: alt.hash(entry),
  interactions: [
    {
      text: "Open Banking",
      uid: utility.uid.generate(),
      handle: bankingTest,
    },
    {
      text: "Open Tuner",
      uid: utility.uid.generate(),
      handle: tunerTest,
    },
  ],
});
```

This documentation provides an overview of the Ascended Target System. For more detailed information on specific components or usage, please refer to the individual source files or reach out to the development team.
