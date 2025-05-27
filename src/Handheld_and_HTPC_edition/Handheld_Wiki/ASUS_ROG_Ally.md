---
authors:
  - "@nicknamenamenick"
---

<!-- ANCHOR: METADATA -->
<!--{"url_discourse": "https://universal-blue.discourse.group/docs?topic=2414", "fetched_at": "2024-09-03 16:43:21.670173+00:00"}-->
<!-- ANCHOR_END: METADATA -->


!!! disclaimer

    This wiki may contain outdated information.

# ASUS ROG Ally / ASUS ROG Ally X

![ally|603x500, 100%](../../img/ally.png)

## Installing Bazzite

Read the [**Installing Bazzite on Handheld PCs documentation**](/General/Installation_Guide/Installing_Bazzite_for_Handheld_PCs.md).

## Post-Installation Setup

- Login to Steam
- Configure the HHD Overlay by opening it with the QAM button
- Virtual keyboard is Steam's keyboard, but needs to be setup in Steam's settings in Desktop Mode (See "Desktop Controls" section below)
  - There is **no default keybinding for Steam's on-screen keyboard** (Remap it to <kbd>**X**</kbd> or whatever you prefer)
- Holding the Armoury Crate button (on the side) allows you to switch to Mouse Mode
- Enable the Steam Power Button Handler setting in Handheld Daemon

## Optional Tweaks

- Adjust RGB with Steam Gaming Mode in Handheld Daemon
- Adjust the scaling of the UI in the Display Settings
- Set a charge limit in HHD with Handheld Daemon

## Workarounds / Known Issues
- Changing A/C power sometimes leads to a stuck TDP.
- Some users report that "Auto UMA" in the bios can cause crashes in some games.
  - If you encounter this, then try setting the VRAM in bios to **4GB** or **8GB**.
- LED indicator is on max brightness by default and cannot be changed on any other operating system outside of Windows.
  - This is tied to the firmware.
  - This also affects when the ally is charging and sleeping.
- The Ally does **not support** button holding for the Steam or QAM buttons.
  - Steam Input's chords do not work by default.
    - Swapping the Start/Select button(s) is a workaround.
- Suspend can break if SMT is disabled
- Fingerprint driver does not work.
- Storage shows duplicate drives.
  - This is a visual bug, do **not** attempt to format this drive!
- Turning on the wake animation when resuming from sleep causes the device to act erratically.
  - No controls outside of Steam.
  - Steam's top and bottom panels missing.

### BIOS update breaks Secure Boot key

![secure-boot|603x500, 100%](../../img/secure-boot.png)


Read our [**Secure Boot guide**](/General/Installation_Guide/secure_boot.md#method-b-after-installation-method) to re-enroll the key after a BIOS update if you keep Secure Boot enabled, which is the default for this device.


### CPU Boost?

Disabled by default to prevent excessive power draw to the device.

More information can be found [**here**](https://github.com/aarron-lee/SimpleDeckyTDP/blob/main/README.md#are-there-cpu-boost-controls) about this.

### TDP Controls

![TDP|690x431, 75%](../../img/TDP.jpeg)

- Steam Quick Access Menu TDP limit (part of Steam Gaming Mode) can control TDP the 
- The [**HHD-overlay**](https://github.com/hhd-dev/hhd/blob/master/readme.md) also supports TDP controls.

### How do I open the HHD Overlay?

![Overlay|690x431, 75%](../../img/HHD_Overlay.jpeg)

![Settings Example|690x431, 75%](../../img/HHD_Settings_Example.jpeg)

Double-tap the Quick Access Menu button.

!!! note
    
    ASUS ROG Ally does not support **holding** for the QAM button!

### Controller Information

For most handheld hardware, besides the Steam Deck, emulation of a DualSense controller is used for full functionality. Double tap or hold the side menu button to access settings for controller emulation including switching to an Xbox controller with reduced functionality.

If your device has paddles, you will want to use the DualSense Edge controller. It’s disabled by default because some games do not map it correctly.

Some games and emulators may need Steam Input **disabled** to work correctly with your controls.

### Desktop Controls

Desktop Mode Controller Layout: It may not exist by default if Steam doesn't setup your handheld controller properly. This can be fixed in Steam's controller settings.

![desktop_controls_step_1|588x500, 60%](../../img/handheld_desktop_controls_1.png)

![desktop_controls_step_2|690x431, 60%](../../img/handheld_desktop_controls_2.png)

![desktop_controls_step_3|690x431, 60%](../../img/handheld_desktop_controls_3.jpeg)

Make sure to **apply** the desktop controls when you select them.

## Contributing

This page and all of the links to each specific handheld are **wikis**, edit it to add any relevant information you may have regarding the handheld and your experience with Bazzite on it. Make sure to follow proper [contributing guidelines](/CONTRIBUTE.md) before adding any edits.

<hr>

**See also**: [Steam Gaming Mode Overview](../Steam_Gaming_Mode.md)

**<-- Back to [Handheld Wiki](./index.md)**
