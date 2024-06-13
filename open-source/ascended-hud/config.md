---
label: "Config"
icon: book
order: 100
---

```typescript
import { useRebar } from "@Server/index.js";
import { HudConfig } from "../../shared/config.js";

const Rebar = useRebar();
const serverConfig = Rebar.useServerConfig();

export const HudServerConfig = {
  init() {
    if (HudConfig.hideAreaName) {
      serverConfig.set("hideAreaName", true); // Hide Area Name?
    }

    if (HudConfig.hideHealthArmor) {
      serverConfig.set("hideHealthArmour", true); // Hide Health & Armour?
    }

    if (HudConfig.hideMinimapOnFoot) {
      serverConfig.set("hideMinimapOnFoot", true); // Hide Minimap Outside of Vehicle?
    }

    if (HudConfig.hideStreetName) {
      serverConfig.set("hideStreetName", true); // Hide Street Name?
    }

    if (HudConfig.hideVehicleClass) {
      serverConfig.set("hideVehicleClass", true); // Hide class of current vehicle?
    }

    if (HudConfig.hideVehicleName) {
      serverConfig.set("hideVehicleName", true); // Hide name of current vehicle?
    }
  },
};
```
