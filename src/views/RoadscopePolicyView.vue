<template>
  <main class="policy">
    <h1>RoadScope Privacy Policy</h1>
    <p class="meta">Publisher: NaturalTwitch &middot; Last updated: October 24, 2026</p>

    <p>RoadScope ("the app") is an Android and Android Auto app that shows public road information: traffic camera images, road events, road conditions, alerts and weather. This policy explains what information the app uses and what happens to it.</p>

    <h2>Information we collect</h2>
    <p><strong>We do not collect your personal information.</strong> The publisher has no servers that receive your data, and there are no accounts, sign-ups, advertising or analytics in the app.</p>

    <h2>Information the app uses on your device</h2>
    <ul>
      <li><strong>Location.</strong> If you allow location permission, the app uses your device's approximate or precise location to show nearby cameras and events and to set your patrol area centre. Your location stays on your device. It is not sent to the publisher.</li>
      <li><strong>Settings and saved reports.</strong> Your settings (such as yard name, area centre, radius, alert choices and theme) and any patrol reports or reminders you write are stored only on your device. You can clear them in the app's Settings, or by uninstalling the app.</li>
      <li><strong>Notifications.</strong> If you allow notifications, the app checks for new closures and incidents in your area in the background and shows alerts on your device. It may run a small foreground service for this and can start again after your device restarts.</li>
      <li><strong>Crash information.</strong> If the app crashes, a short log may be saved on your device only. It is not sent anywhere.</li>
    </ul>

    <h2>Third-party services the app connects to</h2>
    <p>To work, the app requests public data over the internet (HTTPS) from these services. These services receive standard technical information such as your IP address, and they receive the area coordinates needed for the request. Their own privacy policies apply.</p>
    <ul>
      <li><strong>511 Ontario</strong> (Ontario Ministry of Transportation) for cameras, events, road conditions and alerts.</li>
      <li><strong>Open-Meteo</strong> for weather and wind forecasts for your area centre.</li>
    </ul>
    <p>The app does not use your phone's camera. The "cameras" are public roadside traffic camera images provided by 511 Ontario.</p>

    <h2>Sharing and selling</h2>
    <p>We do not sell, rent or share your personal information with anyone.</p>

    <h2>Data retention and deletion</h2>
    <p>Because data stays on your device, you control it. Clear it in Settings or uninstall the app to remove everything the app stored.</p>

    <h2>Children</h2>
    <p>RoadScope is not directed at children and does not knowingly collect information from anyone.</p>

    <h2>Not an official government app</h2>
    <p>RoadScope is an independent app. It is not made, endorsed or operated by the Government of Ontario, the Ministry of Transportation or 511 Ontario. Road information may be delayed or incomplete and must not be relied on for safety decisions.</p>

    <h2>Changes to this policy</h2>
    <p>If this policy changes, the updated version will be posted on this page with a new date.</p>

    <h2>Contact</h2>
    <p>Questions about this policy: <a href="mailto:Norm@mursybot.com">Norm@mursybot.com</a></p>
  </main>
</template>

<style scoped>
.policy {
  font-family: system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
  max-width: 720px;
  margin: 0 auto;
  padding: 24px 16px;
  line-height: 1.6;
  color: #1b1f24;
  background: #fff
}

h1 {
  font-size: 1.8rem;
  margin-bottom: .2em
}

h2 {
  font-size: 1.2rem;
  margin-top: 1.8em
}

.policy .meta {
  color: #5a6570
}

.policy a {
  color: #0b5fd1
}

@media (prefers-color-scheme:dark) {
  .policy {
    background: #10151b;
    color: #e6eaee
  }

  .policy .meta {
    color: #9aa6b2
  }

  .policy a {
    color: #6aa8ff
  }
}
</style>
