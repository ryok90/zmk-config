# Corne ZMK Config

This repository contains my ZMK user config for a split Corne keyboard using `nice_nano_v2` controllers.

## What this repo builds

GitHub Actions builds these firmware targets:

- `corne_left` on `nice_nano_v2`
- `corne_right` on `nice_nano_v2`
- `settings_reset` on `nice_nano_v2`

The workflow artifacts contain `.uf2` files you can flash to each half.

## Update firmware after CI build

1. Open the latest successful GitHub Actions run for this repo.
2. Download the build artifact (named like `corne_left-nice_nano_v2-zmk` / `corne_right-nice_nano_v2-zmk`).
3. Unzip the artifact and locate the `.uf2` firmware files.
4. Put one half into bootloader mode (on `nice_nano_v2`, press reset twice quickly).
5. A USB drive named `NICENANO` appears.
6. Drag the matching `.uf2` file onto that drive:
   - flash `corne_left` firmware to the left half
   - flash `corne_right` firmware to the right half
7. Repeat for the other half.
8. Power cycle both halves and reconnect over Bluetooth.

## Optional: clear old Bluetooth bonds

If pairing is unstable after an update, flash `settings_reset` once:

1. Enter bootloader mode on a half.
2. Copy the `settings_reset` `.uf2` file.
3. Repeat on the other half if needed.
4. Re-flash normal left/right firmware.
5. Re-pair your keyboard to host devices.

## Local build (optional)

If you want to build locally instead of waiting for CI, follow the official ZMK config docs:

- https://zmk.dev/docs/config

In most cases, CI artifacts are the easiest way to keep both halves updated.
