---
label: "Config"
icon: book
order: 100
---

![](/static/Fuel.jpg)

```typescript
import { useRebar } from "@Server/index.js";
import * as alt from "alt-server";

const Rebar = useRebar();
const ServerConfig = Rebar.useServerConfig();

ServerConfig.set("disableVehicleEngineAutoStart", true); // Disables Engine Auto Start

export const FUEL_TYPES = {
  Gasolin: "Gasolin",
  Diesel: "Diesel",
  Electric: "Electric",
  Kerosin: "Kerosin",
};

export const FUEL_SETTINGS = {
  checkForUpdates: true, // Check automatically for updates through asc-versioncheck api?
  AscHUD: true, // Use with our HUD? (https://github.com/ASCENDED-Team/asc-hud)
  AscNotification: false, // Use Notification System? (https://github.com/ASCENDED-Team/asc-notifications)
  Debug: true, // Debug for logs and stuff?
  DefaultConsumption: 0.003, // Default consumption if none is set in the the array below.
  DefaultFuel: FUEL_TYPES.Diesel, // Default fuel_type if none is set in the array below.
  DefaultMax: 30, // Default max_fuel if none is set in the array below.
  enableSound: false, // For toggle_engine you can enable this and replace the sound in /sounds folder.
};

export const VEHICLE_CONSUMPTION: Array<{
  model: number;
  consume: number;
  type?: string;
  maxFuel: number;
}> = [
  {
    model: alt.hash("t20"),
    consume: 0.009,
    type: FUEL_TYPES.Diesel, // Optional set fuel_type individually per vehicle. Otherwise it uses DEFAULT_FUEL.
    maxFuel: 40,
  },
  {
    model: alt.hash("zentorno"),
    consume: 0.0035,
    type: FUEL_TYPES.Gasolin,
    maxFuel: 30,
  },
  { model: alt.hash("panto"), consume: 0.05, maxFuel: 15 },
  { model: alt.hash("italirsx"), consume: 0.1, maxFuel: 30 },
  { model: alt.hash("krieger"), consume: 0.01, maxFuel: 50 },
];
```
