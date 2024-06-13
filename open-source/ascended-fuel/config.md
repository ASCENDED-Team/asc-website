---
label: "Config"
icon: book
order: 100
---

```typescript
import * as alt from "alt-server";
import { FUEL_TYPES } from "./fuelTypes.js";

// Default Settings - Used when nothing is set in VEHICLE_CONSUMPTION.
export const FUEL_SETTINGS = {
  AscHUD: true, // Use with our HUD? (https://github.com/ASCENDED-Team/asc-hud)
  Debug: true, // Debug? For logs and stuff.
  DefaultConsumption: 0.003, // Consume if not existent in VEHICLE_CONSUMPTION Array below
  DefaultFuel: FUEL_TYPES.Diesel, // Fuel Type if not existent in the 4 Arrays below.
  DefaultMax: 30, // Default Max_Fuel per Vehicle - Used if not exists in VEHICLE_CONSUMPTION Array below
};

export const VEHICLE_CONSUMPTION: Array<{
  model: number;
  consume: number;
  maxFuel: number;
}> = [
  { model: alt.hash("t20"), consume: 0.009, maxFuel: 40 },
  { model: alt.hash("zentorno"), consume: 0.1, maxFuel: 30 },
  { model: alt.hash("panto"), consume: 0.05, maxFuel: 15 },
  { model: alt.hash("italirsx"), consume: 0.002, maxFuel: 30 },
  { model: alt.hash("krieger"), consume: 0.01, maxFuel: 50 },
];

// Vehicles that should use Gasolin
export const GASOLIN = ["sultanrs", "t20", "krieger", "zentorno"];

// Vehicles that should use Kerosin
export const KEROSIN = ["maverick"];

// Vehicles that should use Diesel
export const DIESEL = ["panto"];

// Vehicles that use Electric
export const ELECTRIC = ["italirsx"];
```
