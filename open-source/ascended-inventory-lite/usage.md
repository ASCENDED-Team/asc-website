---
label: "Usage"
icon: book
order: 900
---

![](/static/Inventory-Lite.jpg)

# Use Rebar Plugin API (Serverside)

```typescript
const InventoryAPI = await useApi().getAsync("ascended-inventory-api");

InventoryAPI.inventoryAddItem(player, name, quant); // Add Item
InventoryAPI.inventoryRemoveItem(player, item); // Remove specified item
InventoryAPI.refreshInventory(player); // Refresh Inventory of player after add/removal
```

# Create Items

Items can be created inside of src/items/file.ts - you can also add new files.

```typescript
import { Item } from "plugins/simple-item-manager/shared/types.js";
import { InventoryEvents } from "../../../shared/itemEvents.js";

export const food_items: Array<Item> = [
  {
    uid: "asc-hotdog",
    id: "food-hotdog",
    name: "Hotdog",
    desc: "Some Hotdog...",
    icon: "crate",
    maxStack: 12,
    quantity: 1,
    weight: 0,
    useEventName: InventoryEvents.ToServer.USE_FOOD,
    data: {
      remove: true, // Should item be removed? Else just fires event. (ID-Card for EXAMPLE)
    },
    rules: {},
  },
];
```

If you add new .ts files make sure to update the allItems Array in the index.ts properly.

````typescript
import { drink_items } from './src/items/drinks.js';
import { food_items } from './src/items/food.js';

const allItems = [...food_items, ...drink_items, ...otherItems];

for(const item of allItems) {
    await ItemManager.useItemManager().create(item);
}```
````
