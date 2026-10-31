# Vaill-e-Bus_Thermostat releases

Binary releases of the firmware for the eBusDThermostat project (a boiler controller for Vaillant eBUS and its room sensors).
This repository contains **only release files**, no source code.

Each release has:
- `<name>-<version>.bin`, the firmware image,
- `manifest.json` with the version, size, SHA-256 and an ECDSA P-256 signature of the image.

Devices accept only images signed with the project's key (public part: `release-public.pem`). Verify by hand:

```bash
sha256sum room-sensor-0.2.0.bin                       # compare with "sha256" in manifest.json
base64 -d <<< "<signature from manifest.json>" > sig.der
openssl dgst -sha256 -verify release-public.pem -signature sig.der room-sensor-0.2.0.bin
```

Firmware is provided as is, use at your own risk. Never connect a prototype to a boiler you cannot safely do without.
