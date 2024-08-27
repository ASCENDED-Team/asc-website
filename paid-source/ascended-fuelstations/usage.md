---
label: "Usage"
icon: book
---

# Fuel Station System

## Overview

The Fuel Station System is a comprehensive module designed to simulate realistic fuel management in a game environment. It allows players to refuel their vehicles at designated fuel stations, providing an immersive gameplay experience.

## Features

- Multiple fuel types (Gasoline, Diesel, Electric, Kerosene)
- Dynamic pricing for different fuel types
- Interactive UI for fuel selection and purchase
- Support for both targeted and non-targeted interactions
- Customizable blips and markers for fuel stations
- Integration with vehicle fuel consumption system

## Configuration

The fuel station system can be configured using the `FuelstationConfig` object in `config.ts`:

```typescript
export const FuelstationConfig = {
  ASC_TARGET: false,
  BLIPS: true,
};
```

- `ASC_TARGET`: Set to `true` to use targeted interactions, `false` for non-targeted interactions
- `BLIPS`: Set to `true` to display fuel station blips on the map

## Fuel Station Types

### Targeted Fuel Stations

Targeted fuel stations are defined in the `TARGET_FUELSTATIONS` array in `config.ts`. Each station includes:

- Name
- Available fuel types and prices
- Associated prop model

### Non-Targeted Fuel Stations

Non-targeted fuel stations are defined in the `NO_TARGET_FUELSTATIONS` array in `config.ts`. Each station includes:

- Name
- Position (x, y, z coordinates)
- Available fuel types and prices

## Client-Side Implementation

The client-side implementation handles:

- Requesting the model of the nearest fuel pump
- Displaying the fuel station UI
- Sending refuel requests to the server

Key files:

- `client/index.ts`
- `client/Fuelstations.vue`
- `client/components/fueltype.vue`
- `client/components/hero.vue`

## Server-Side Implementation

The server-side implementation manages:

- Setting up fuel station interactions (targeted or non-targeted)
- Processing refuel requests
- Updating vehicle fuel levels
- Handling currency transactions

Key files:

- `server/index.ts`
- `server/src/interactions.ts`
- `server/src/events.ts`

## Usage

### For Players

1. Approach a fuel station in a vehicle
2. Interact with the fuel pump (method depends on configuration)
3. Select the desired fuel type
4. Adjust the amount of fuel to purchase
5. Click the "Refuel" button to complete the transaction

### For Developers

#### Adding a New Fuel Station

1. Open `config.ts`
2. Add a new entry to either `TARGET_FUELSTATIONS` or `NO_TARGET_FUELSTATIONS` depending on your configuration
3. Customize the station properties as needed

Example:

```typescript
{
    name: 'New Fuel Station',
    pos: { x: 100, y: 200, z: 30 },
    availableFuel: [
        {
            Gasolin: { name: 'Gasolin', price: 5 },
            Diesel: { name: 'Diesel', price: 2 },
        },
    ],
}
```

#### Customizing the UI

The fuel station UI is implemented using Vue.js components. To customize the appearance:

1. Modify the relevant `.vue` files in the `client/components` directory
2. Adjust the styles and layout as needed
3. Ensure all necessary data bindings and event handlers are maintained

## Events

The system uses the following events for communication:

- `FuelStationEvents.ToClient.OPEN`: Open the fuel station UI
- `FuelStationEvents.ToClient.REQUEST_MODEL`: Request the model of the nearest fuel pump
- `FuelStationEvents.ToServer.CLOSE`: Close the fuel station UI
- `FuelStationEvents.ToServer.REFILL_VEHICLE`: Send a refuel request to the server
- `FuelStationEvents.WebView.SET_DATA`: Set the data for the fuel station UI

## Integration

The Fuel Station System integrates with other game systems, including:

- Vehicle Management System
- Currency System
- Player Interaction System

Ensure these systems are properly configured and running for full functionality.

## Troubleshooting

If you encounter issues with the Fuel Station System:

1. Check the server and client console for error messages
2. Verify that all configuration settings are correct
3. Ensure that the necessary API dependencies (e.g., `ascended-fuel-api`, `currency-api`) are available and up-to-date
4. Check for conflicts with other systems or mods

For further assistance, please contact the development team or refer to the support documentation.
