---
label: "API"
icon: book
order: 150
---

![](/static/Fuel.jpg)

# How to use Plugin API - Serverside

```typescript
const Rebar = useRebar();
const messenger = Rebar.messenger.useMessenger();
const FuelAPI = await Rebar.useApi().getAsync("ascended-fuel-api"); // Import the Fuel API async

FuelAPI.vehicle.getFuelType(vehicle); // Gets the fuel type of the current vehicle.
FuelAPI.getFuelTypes(); // Returns all available fuel_types from the config file.
// ...
// See Functions below this section
```

# Exposed API Functions - Serverside

```typescript
class FuelAPI {
  public static global = {
    getFuelTypes: this.getFuelTypes,
  };

  public static vehicle = {
    createPropertie: createAscendedFuelPropertie,
    toggleEngine: toggleEngine,
    toggleEngineNoPlayer: toggleEngineWithoutPlayer,
    getFuelType: getVehicleFuelType,
    getConsumption: getVehicleFuelConsumption,
    refill: refillVehicle,
    refillClose: refillClosestVehicle,
    getMaxFuel: getVehicleMaxFuel,
    repairMismatch: repairFuelTypeMismatch,
  };

  private static getFuelTypes() {
    return FUEL_TYPES;
  }
}
```
