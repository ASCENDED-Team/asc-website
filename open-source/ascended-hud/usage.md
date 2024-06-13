---
label: "Usage"
icon: book
order: 200
---

![](/static/Hud.jpg)

### Use HUD API

- Only supports pushFuel currently.

````typescript
const HudAPI = await useApi().getAsync('ascended-hud-api');
const fuelCalc = ((await getVehicleFuel(player.vehicle.model)) / (await getVehicleMaxFuel(player.vehicle.model))) * 100;
HudAPI.pushFuel(player, fuelCalc);```
````
