---
label: "Config"
icon: book
order: 100
---

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
