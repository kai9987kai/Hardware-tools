
# Browser Hardware Tools Pro

**Browser Hardware Tools Pro** is a standalone, single-file browser hardware/API laboratory for testing modern Web APIs directly from the browser. It combines media tools, system telemetry, permission checks, sensors, clipboard access, device connector probes, diagnostics, and quick system actions into one polished local dashboard.

The project runs entirely in the browser. No backend, database, build step, or server logic is required.

---

## Features

### Core Tools

- **Audio Analyzer**
  - Real-time microphone input
  - FFT frequency visualizer
  - Oscilloscope waveform mode
  - Adjustable FFT size
  - Live level and peak meters
  - Proper microphone stream cleanup

- **Speech Synth**
  - Text-to-speech playback
  - Browser voice selection
  - Pitch control
  - Rate control
  - Volume control
  - Pause, resume, and stop
  - Saves last speech text locally

- **System Vitals**
  - Battery level and charging state where supported
  - CPU thread count
  - Approximate device memory
  - FPS monitor
  - JavaScript heap memory where supported
  - Screen size
  - Viewport size
  - Pixel ratio
  - Platform and language data

- **Color / Spectral Analysis**
  - EyeDropper API support where available
  - Manual color picker fallback
  - HEX, RGB, and HSL output
  - Copy color values to clipboard
  - Saved local palette history
  - Validation against corrupted localStorage data

- **Geolocation**
  - One-shot location acquisition
  - Live location watch mode
  - Latitude and longitude
  - Accuracy estimate
  - Altitude where available
  - Speed where available
  - Copy coordinates

- **Camera / Visual Sensor**
  - Webcam activation
  - Camera device selector
  - Mirror preview mode
  - Snapshot capture
  - PNG snapshot download
  - Safe camera stream shutdown

- **Clipboard Console**
  - Write custom text to clipboard
  - Read clipboard text where permission allows
  - Permission-safe error handling
  - Fallback clipboard copy support

- **Gyroscope Lab**
  - Device orientation readout
  - Alpha, beta, and gamma values
  - Motion XYZ values
  - Mobile sensor permission handling

- **Page Visibility**
  - Live visibility state
  - Visibility change counter
  - Useful for testing background/foreground browser behavior

- **Idle Detector**
  - Real Idle Detection API implementation where supported
  - User idle state
  - Screen lock state
  - Graceful unsupported-browser handling

---

## New Advanced Tools

### Capability Radar

A browser feature-detection panel that checks support for:

- Camera / microphone
- Speech synthesis
- AudioContext
- Screen capture
- Geolocation
- Device motion
- Battery API
- Wake Lock API
- Clipboard API
- Permissions API
- Storage API
- Network Information API
- WebUSB
- Web Serial
- Web Bluetooth
- Web MIDI

---

### Permission Matrix

Queries browser permission states for supported APIs, including:

- Geolocation
- Camera
- Microphone
- Notifications
- Clipboard read
- Clipboard write
- Idle detection

Permission states are shown as:

- `granted`
- `prompt`
- `denied`
- `unsupported`

---

### Network Monitor

Displays network-related browser information where supported:

- Online/offline state
- Effective connection type
- Downlink estimate
- Round-trip time estimate
- Save-data mode

---

### Screen Wake Lock

Allows the app to request a screen wake lock so the display stays awake while testing tools or monitoring diagnostics.

---

### Storage Quota

Shows browser storage usage and quota estimates.

Includes:

- Storage used
- Storage quota
- Usage percentage bar
- Persistent storage state
- Request persistent storage button

---

### Device Connectors

Checks and tests availability of modern device connection APIs:

- Web Serial
- WebUSB
- Web Bluetooth
- Web MIDI

This makes the project useful as a quick compatibility lab for browser-to-device experiments.

---

### Quick Actions

Includes upgraded versions of the original simple hardware/system actions:

- Native Web Share
- Fullscreen toggle
- Orientation lock
- Vibration / haptics test
- Pointer Lock
- Notification test

---

### Diagnostic Notes

A local notes panel for recording observations while testing.

Also includes a one-click diagnostic JSON export containing:

- App version
- Export timestamp
- User agent
- Screen information
- CPU thread estimate
- Memory estimate
- User notes

---

## Interface Features

- Standalone dashboard layout
- Dark cyber-style glass UI
- Tool filtering/search
- Compact and roomy layout modes
- Browser capability summary
- Toast notification system
- Error boundaries so one failed panel does not crash the whole app
- Safer browser API error handling
- LocalStorage-backed settings where useful
- Mobile-friendly responsive layout
- Reduced-motion support

---

## Why This Exists

Modern browsers expose many hardware-adjacent APIs, but support varies heavily between browsers, devices, operating systems, permissions, and security contexts.

Browser Hardware Tools Pro gives developers and experimenters a single place to test those APIs and quickly see what the current browser environment can actually do.

It is useful for:

- Web API experimentation
- Browser compatibility testing
- Device capability inspection
- Hardware-oriented web projects
- Sensor demos
- Web Serial / WebUSB / Bluetooth prototyping
- Local diagnostics
- Teaching browser API concepts
- Debugging permissions and secure-context issues

---

## Getting Started

### Option 1: Open Directly

Download or clone the project and open the HTML file in your browser.

```bash
git clone https://github.com/your-username/browser-hardware-tools-pro.git
cd browser-hardware-tools-pro
````

Then open:

```text
index.html
```

Some APIs may not work from a plain `file://` URL. For best results, use localhost.

---

### Option 2: Run with a Local Server

Using Python:

```bash
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

Using Node:

```bash
npx serve .
```

---

## Recommended Browser

For the widest API support, use a recent Chromium-based browser such as:

* Google Chrome
* Microsoft Edge
* Brave
* Chromium

Some features may also work in Firefox or Safari, but support will vary.

---

## Important Browser Requirements

Many hardware APIs require:

* HTTPS or localhost
* A direct user gesture
* Browser permission approval
* A compatible browser
* A compatible device
* A non-restricted iframe/sandbox environment

For example:

| Feature        | Common Requirement            |
| -------------- | ----------------------------- |
| Camera         | HTTPS/localhost + permission  |
| Microphone     | HTTPS/localhost + permission  |
| Geolocation    | HTTPS/localhost + permission  |
| Clipboard read | Permission + user gesture     |
| EyeDropper     | Chromium support              |
| Wake Lock      | Secure context                |
| WebUSB         | Chromium support              |
| Web Serial     | Chromium support              |
| Web Bluetooth  | Chromium support              |
| Device Motion  | Mobile device + permission    |
| Idle Detection | Chromium support + permission |

---

## Known Console Warnings

When running the standalone version, you may see warnings such as:

```text
cdn.tailwindcss.com should not be used in production
```

This is expected because the app uses Tailwind through the CDN for easy standalone usage.

You may also see:

```text
You are using the in-browser Babel transformer
```

This is also expected because JSX is compiled in the browser to keep the app as a single HTML file.

These warnings do not mean the app is broken.

---

## Production Notes

The current version is designed as a powerful standalone prototype.

For production deployment, you should consider:

* Precompiling React/JSX instead of using Babel in the browser
* Installing Tailwind through the Tailwind CLI or PostCSS
* Bundling dependencies locally
* Replacing CDN scripts with pinned local versions
* Adding a stricter Content Security Policy
* Adding service worker caching
* Adding automated tests
* Splitting large tools into separate modules
* Adding TypeScript
* Adding accessibility testing
* Adding browser support documentation

---

## Troubleshooting

### The app crashes on the color tool

The latest version validates color history before using it. If you still have old corrupted localStorage data, run this in the browser console:

```js
localStorage.removeItem("bht_color_history_v4");
location.reload();
```

---

### Camera or microphone does not work

Check that:

* You are using HTTPS or localhost
* Browser permissions are allowed
* No other app is blocking the camera or microphone
* The browser supports `navigator.mediaDevices.getUserMedia`

---

### Geolocation does not work

Check that:

* Location permission is allowed
* Your browser supports Geolocation
* You are using HTTPS or localhost
* Your OS location services are enabled

---

### EyeDropper does not work

The EyeDropper API is not supported in every browser. Use Chrome or Edge for best support.

The manual color picker still works as a fallback.

---

### WebUSB / Web Serial / Bluetooth are unavailable

These APIs are browser-dependent and usually require Chromium-based browsers.

They may also be disabled by:

* Browser policy
* Operating system permissions
* Insecure context
* Sandboxed iframe
* Unsupported hardware

---

### Console shows ad or iframe warnings

Warnings involving things like:

```text
pubads_impl.js
googletag
Topics
SharedId
safeFrame
```

usually come from the host page, ad scripts, or the environment where the app is embedded. They are not part of Browser Hardware Tools Pro itself.

---

### Grammarly error appears in console

Errors involving:

```text
Grammarly-check.js
```

come from the Grammarly browser extension, not from the app.

---

## Privacy

Browser Hardware Tools Pro runs locally in your browser.

The app does not include a backend and does not intentionally upload your camera, microphone, clipboard, location, or diagnostic data anywhere.

However, permissions are still controlled by your browser. Only grant permissions you are comfortable testing.

If you deploy the app on a website, review any hosting analytics, ads, third-party scripts, or CDN usage separately.

---

## File Structure

For the standalone version:

```text
browser-hardware-tools-pro/
├── index.html
└── README.md
```

The whole app can live inside a single `index.html` file.

---

## Technology Stack

* HTML5
* CSS3
* Tailwind CSS CDN
* React 17 UMD
* ReactDOM 17 UMD
* Babel Standalone
* Lucide Icons
* Web Audio API
* MediaDevices API
* SpeechSynthesis API
* Clipboard API
* Geolocation API
* Permissions API
* Storage API
* Battery Status API where available
* Network Information API where available
* Wake Lock API where available
* WebUSB where available
* Web Serial where available
* Web Bluetooth where available
* Web MIDI where available

---

## Browser APIs Used

The project experiments with:

* `navigator.mediaDevices.getUserMedia`
* `navigator.mediaDevices.enumerateDevices`
* `AudioContext`
* `AnalyserNode`
* `speechSynthesis`
* `SpeechSynthesisUtterance`
* `navigator.geolocation`
* `navigator.clipboard`
* `navigator.permissions`
* `navigator.storage`
* `navigator.getBattery`
* `navigator.connection`
* `navigator.wakeLock`
* `navigator.vibrate`
* `navigator.share`
* `Notification`
* `document.fullscreenElement`
* `document.documentElement.requestFullscreen`
* `document.body.requestPointerLock`
* `screen.orientation.lock`
* `DeviceOrientationEvent`
* `DeviceMotionEvent`
* `IdleDetector`
* `navigator.serial`
* `navigator.usb`
* `navigator.bluetooth`
* `navigator.requestMIDIAccess`
* `EyeDropper`

---

## Suggested Future Improvements

* Convert to Vite + React
* Add TypeScript
* Add full PWA support
* Add offline mode
* Add service worker caching
* Add downloadable diagnostics report
* Add benchmark mode
* Add camera frame analysis
* Add screen capture tool
* Add microphone recording test
* Add WebRTC diagnostics
* Add WebGPU/WebGL capability scanner
* Add gamepad input tester
* Add keyboard event visualizer
* Add touch and pointer event lab
* Add MIDI device monitor
* Add serial terminal mode
* Add Bluetooth GATT explorer
* Add USB descriptor viewer
* Add accessibility audit panel
* Add export/import settings
* Add local plugin system for custom tools

---

## Safety Notes

This app can request access to sensitive browser capabilities such as camera, microphone, clipboard, location, and connected devices.

Use it responsibly.

Do not deploy a modified version that secretly collects or transmits user data.

Always make permission requests clear and intentional.

---

## License

Add your chosen license here.

Example:

```text
MIT License
```

---

## Project Status

Browser Hardware Tools Pro is an experimental but feature-rich standalone browser hardware/API dashboard.

It is suitable for demos, testing, learning, and further development into a full browser diagnostics suite.

```
```
