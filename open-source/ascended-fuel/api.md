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

FuelAPI.setFuelTypes();
// ...
// See Functions below this section
```

# Exposed API Functions - Serverside

```typescript
async function setFuelTypes() {
  await setVehicleFuelTypes();
}

async function setConsumptionRates() {
  await setVehicleConsumptionRates();
}

async function getFuelType(model: string) {
  await getVehicleFuelType(model);
}

async function getFuelConsumption(model: string) {
  await getVehicleFuelConsumption(model);
}

async function refill(player: alt.Player) {
  await refillVehicle(player);
}

async function refillCloseVehicle(player: alt.Player, amount: number) {
  await refillClosestVehicle(player, amount);
}

async function getMaxFuel(model: string | number) {
  return await getVehicleMaxFuel(model);
}
```
