---
label: "Usage"
icon: book
---

![](/static/Camera.jpg)

To start using our camera script, ensure you have a Lifecycle Hook (Webview) set up. Additionally, you'll need a camera.ts file on the client side to utilize the plugin correctly.

### Clientside (TypeScript)

```javascript
import { useWebview } from "@Client/webview/index.js";
import { useClientApi } from "@Client/api/index.js";

// Get the CameraAPI through Rebar's Plugin API-System
const CameraAPI = useClientApi().get("ascended-camera-api");

const webview = useWebview();

//This one is a bit tricky: false is what you want if the camera should start
CameraAPI.onMovementControl(false);

webview.on("CAMERA_MOVE_START", CameraAPI.cameraMoveStart);
webview.on("CAMERA_MOVE_END", CameraAPI.cameraMoveEnd);
webview.on("CAMERA_SCROLL_UP", CameraAPI.cameraMoveIn);
webview.on("CAMERA_SCROLL_DOWN", CameraAPI.cameraMoveOut);
```

### Mounted - Lifecycle Hook (VueJS)

```javascript
onMounted(async () => {
  // Move Camera (Holding LMB)
  document.addEventListener("mousedown", (e) => {
    events.emitClient("CAMERA_MOVE_START");
  });

  document.addEventListener("mouseup", (e) => {
    events.emitClient("CAMERA_MOVE_END");
  });

  // Zoom In & Out (Mousewheel)
  document.addEventListener("wheel", (e) => {
    if (e.deltaY < 0) {
      events.emitClient("CAMERA_SCROLL_UP");
    } else if (e.deltaY > 0) {
      events.emitClient("CAMERA_SCROLL_DOWN");
    }
  });
});
```

### Config file

```javascript
export const ASC_CameraConfig = {
  ease: true, //Should the camera have a smooth transition?
  easeTime: 1500, //If yes how long should it take
  focusOnPlayer: false, //Focus the camera on the player
  focusOnVehicle: false, //Focus the player on the vehicle in which the player sits
  cameraOffset: {
    //Offset the camera
    x: 0,
    y: 0,
    z: 0,
  },
};
```

### Demonstration

[!embed](https://youtu.be/DtqyogIMWv0)
