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

FuelAPI.getFuelType(vehicle); // Gets the fuel type of the current vehicle.
FuelAPI.getFuelTypes(); // Returns all available fuel_types from the config file.
// ...
// See Functions below this section
```

# Exposed API Functions - Serverside

```typescript
async function createAscendedFuelPropertie(vehicle: alt.Vehicle) {
  try {
    const vehicleDocument = Rebar.document.vehicle.useVehicle(vehicle);
    await vehicleDocument.setBulk({
      fuel: 30,
      ascendedFuel: {
        consumption: 0,
        max: 0,
        type: "",
      },
    });
    await setConsumptionRates();
    console.log(
      `Added ascended fuel properties for Vehicle Model: ${Rebar.utility.vehicleHashes.getNameFromHash(
        vehicle.model
      )} | Fuel: ${vehicleDocument.getField("fuel")}`
    );
  } catch (error) {
    console.error("Error while setting ASCENDED-Fuel Properties:", error);
  }
}

async function setConsumptionRates() {
  await setVehicleConsumptionRates();
}

function toggleVehicleEngine(player: alt.Player) {
  toggleEngine(player);
}

async function getFuelType(vehicle: alt.Vehicle) {
  await getVehicleFuelType(vehicle);
}

async function getFuelConsumption(vehicle: alt.Vehicle) {
  await getVehicleFuelConsumption(vehicle);
}

async function refill(player: alt.Player, amount?: number) {
  await refillVehicle(player, amount);
}

async function refillCloseVehicle(player: alt.Player, amount: number) {
  await refillClosestVehicle(player, amount);
}

async function getMaxFuel(vehicle: alt.Vehicle) {
  await getVehicleMaxFuel(vehicle);
}

function getFuelTypes() {
  return FUEL_TYPES;
}
```
