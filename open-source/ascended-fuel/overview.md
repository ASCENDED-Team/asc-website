---
label: "Overview"
icon: book
order: 200
---

![](/static/Fuel.jpg)

# Ascended Fuel System Overview

The **Ascended Fuel System** for Alt:V servers provides advanced vehicle fuel management features, including real-time fuel consumption tracking, fuel type handling, and interaction with the player's vehicle engine.

## Features

### 1. Fuel Properties for Vehicles

- Assigns fuel-related properties such as consumption rate, max capacity, and fuel type.
- Managed using the Rebar system.

### 2. Fuel Consumption Tracking

- Tracks vehicle fuel consumption based on distance traveled and speed in real-time.

### 3. Fuel Refill

- Allows players to refill their vehicles or nearby vehicles with a specified amount or fully.

### 4. Fuel Type Handling

- Supports multiple fuel types, detecting and managing fuel type mismatches.

### 5. Out of Fuel Scenario

- Automatically turns off the engine when fuel runs out and notifies the player.

### 6. Engine Control

- Allows players to toggle the engine on/off, preventing start when fuel is empty or the engine is damaged.

### 7. Notifications

- Sends in-game notifications for events such as low fuel, refuel success, and engine breakdown.

### 8. Getter Functions

- Utility functions to retrieve fuel properties like type, consumption, max fuel, and current fuel level.

### 9. Engine Breakdown and Repair

- Handles engine breakdowns due to fuel type mismatches and allows repairs.

---

## Dependencies

- **Alt:V Server**
- **Rebar**: For vehicle data management.
- **Ascended Notification API**: For sending notifications.

---

## Configuration Options

- **checkForUpdates**: Check for updates automatically.
- **AscHUD**: Use default ASC-Hud.
- **ASCHudPro**: Use ASCHudPRO.
- **Debug**: Enable or disable debug mode.
- **DefaultConsumption**: Default vehicle consumption rates.
- **AscNotification**: Enable or disable fuel notifications.
- **DefaultFuel**: Set default fuel type.
- **DefaultMax**: Set default maximum fuel capacity.
- **enableSound**: Enable or disable engine sound effects.
