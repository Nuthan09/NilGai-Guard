# NilGai Guard Live dashboard

Live web dashboard for the PT6 NilGai boundary prototype (boundary AB).
IoT Lab, CSE Department, IIT (BHU).

**Live page:** https://nuthan09.github.io/NilGai-Guard/

## How the data reaches this page
```
ESP8266 master (node A) --MQTT 1883--> broker.hivemq.com <--secure WebSocket 8884-- this page
```
GitHub Pages is HTTPS, and browsers block an HTTPS page from calling a device's
plain `http://` address, so the device and the page meet at a public MQTT broker.
Anyone in the team can open the link from any network.

Topics (root `nilgaiguard/nuthan09/pt6`): `status` (online/offline), `state` (every 2 s),
`live` (beam changes), `event` (each crossing), `cmd` (page → device), `ack`.

## Deploy
1. Create a new public repository `NilGai-Guard` on github.com/nuthan09.
2. Upload `index.html` (and this README) to the repository root.
3. Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)` → Save.
4. After ~1 minute the page is live at the link above.

## Demo mode
The **Demo mode** button simulates human and NilGai crossings with the same maths as
the firmware — useful if the hotspot or hardware misbehaves during a presentation.
