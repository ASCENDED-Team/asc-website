---
label: "Usage"
icon: book
order: 900
---

![](/static/notification.jpg)

# Interface

```typescript
export interface Notification {
  icon: string;
  title: string;
  subTitle: string;
  message: string;
  duration?: number;
  oggFile?: string;
}
```

# Use Rebar Plugin API (Serverside)

```typescript
import { useRebar } from '@Server/index.js';

const Rebar = useRebar();
const NotificationAPI = Rebar.useApi().get('ascended-notification-api');

NotificationAPI.create({
    icon: '🤡';
    title: 'Task Title';
    subTitle: 'Successfully done';
    message: 'Hello World';
    duration: 5000; // Optional
    oggFile: 'bell'; // Optional
});
```

# Use Rebar Plugin API (Clientside)

```typescript
import { useRebarClient } from '@Client/index.js';

const API = useRebarClient().useClientApi();
const NotificationAPI = API.get('ascended-notification-api');

NotificationAPI.create({
    icon: '🤡';
    title: 'Task Title';
    subTitle: 'Successfully done';
    message: 'Hello World';
    duration: 5000; // Optional
    oggFile: 'bell'; // Optional
});
```

# Config

```typescript
export const NotificationConfig = {
  debugMode: true, // Enables debug notifications
  enableSounds: true, // Enables sounds
  enableRebarSelector: true, // Only use if you use Rebars Character Selector by Stuyk
  notificationDuration: 10000, // Default duration if none is set
  darkMode: false, // Enable/Disable Darkmode
};

// Some Emojis to use with the Notification System
export const NotificationTypes = {
  info: "ℹ️",
  error: "❌",
  success: "✅",
  warning: "⚠️",
};
```

# Preview

![](/static/notify.png)
