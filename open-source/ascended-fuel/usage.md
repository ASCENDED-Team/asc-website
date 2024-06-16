---
label: "Usage"
icon: book
order: 200
---

![](/static/Fuel.jpg)

To ensure ascended-fuel is working properly you will have to follow these steps.

### Your Vehicle Creaton

- Ensure you vehicle creation has setted values for ascended-fuel. You will find an example command below.

```typescript
Rebar.document.vehicle.useVehicle(createdVehicle).setBulk({
  mods: vehicleMods,
  extras: vehicleExtras,
  fuel: document.fuel,
  ascendedFuel: {
    consumption: 0,
    max: 0,
    type: "",
  },
});
```

# Example Command to create a Vehicle

```typescript
import * as alt from "alt-server";
const Rebar = useRebar();
const messenger = Rebar.messenger.useMessenger();
const FuelAPI = await Rebar.useApi().getAsync("ascended-fuel-api");

messenger.commands.register({
  name: "/addvehicle",
  desc: "Adds a vehicle and creates a database document",
  callback: async (player: alt.Player, model: string | number) => {
    try {
      if (!player?.valid) return;
      const playerData = Rebar.document.character.useCharacter(player).get();

      const createdVehicle = new alt.Vehicle(
        model,
        player.pos.x + 3,
        player.pos.y,
        player.pos.z,
        0,
        0,
        0
      );
      await Rebar.vehicle.useVehicle(createdVehicle).create(playerData._id);
      const document = Rebar.document.vehicle.useVehicle(createdVehicle).get();

      Rebar.document.vehicle.useVehicle(createdVehicle).setBulk({
        fuel: 30,
        ascendedFuel: {
          consumption: 0,
          max: 0,
          type: "",
        },
      });

      Rebar.document.vehicle
        .useVehicleBinder(createdVehicle)
        .bind(Rebar.document.vehicle.useVehicle(createdVehicle).get());
      Rebar.vehicle.useVehicle(createdVehicle).sync();
      Rebar.vehicle.useVehicle(createdVehicle).save();

      alt.logWarning(`Vehicle Creation successfully`);

      await FuelAPI.setConsumptionRates();
    } catch (error) {
      alt.logError(error);
    }
  },
});
```
