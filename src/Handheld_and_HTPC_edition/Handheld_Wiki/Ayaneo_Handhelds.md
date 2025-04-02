---
authors:
  - "@zetarancio"
  - "@nicknamenamenick"
  - "@aarron-lee"
---

<!-- ANCHOR: METADATA -->
<!--{"url_discourse": "https://universal-blue.discourse.group/docs?topic=2417", "fetched_at": "2024-09-03 16:43:20.646543+00:00"}-->
<!-- ANCHOR_END: METADATA -->


!!! disclaimer

    This wiki may contain outdated information.

# Ayaneo Geek 1S

![photo_5875160389711413569_y|663x500, 100%](../../img/Ayaneo_Geek_1S.jpeg)

**Status**: Gold

## Installing Bazzite

Read the [**Installing Bazzite on Handheld PCs documentation**](/General/Installation_Guide/Installing_Bazzite_for_Handheld_PCs.md).

## Post-Installation Setup

- Complete the Bazzite Portal
- Login to Steam
- Reboot device
- Configure the HHD Overlay by opening it with QAM button
- Virtual keyboard is Steam's keyboard, but needs to be setup in Steam's settings in Desktop Mode (See "Desktop Controls" section below)
- HHD's support of both LEDs and Gyroscope is fine out of the box (with bmi260 from [ublue-os/akmod].

## Workarounds / Known Issues

- Suspending the device requires the latest BIOS update.
  - Reports of controller issues on wake have been reported inconsistency.
- VRAM size option is missing from BIOS as it's controlled by AYASPACE application under windows.
- For certain Ayaneo devices, Wi-Fi stops working after suspend-resume cycles.
  - Workaround: You need to `modprobe -r mt7921e` right before suspend to disable the Wi-Fi, then run `modprobe mt7921e` after suspend to re-enable the Wi-Fi.
    - You can find an automatic installer for the workaround [here](https://github.com/aarron-lee/gpd-win-tricks/tree/mt7921e_fix/suspend-fix).

### Functional HHD

```
sudo systemctl enable --now hhd@$(whoami)
```

### External Graphics:

- eGPU Thunderbolt 3/4 over USB4 is supported. USB4 enclosure needs proper testing, but there is no reason to suspect it should not work.
  - **AMD**:
    - Automatic switch at boot with [all-ways-egpu](https://github.com/ewagner12/all-ways-egpu/tree/main) works fine using method 2 and 3 at boot, unfortunately method 1 is not supported but seems to be related to Steam Gaming Mode.
      - The script needs to be installed with [Steam Deck/User Installation](https://github.com/ewagner12/all-ways-egpu/blob/main/README.md#steamosbazziteuser-installation).
    - No issue in booting with eGPU attached. Tested on RX 6800 and no kernel parameters are needed since bazzite is now enabling the needed argument by default (amdgpu .ppfeaturemask).
      - Using `rpm-ostree kargs --append-if-missing=pci=nommconf` (or editing the kernel command line with `rpm-ostree kargs –editor`) is still needed according to my testing because some applications otherwise may underperform.
    - Some AMD cards requires to set a correct limit for GPU and Memory Clocks, this is a known issue that is present also on Desktops. I suggest installing LACT and setting the correct limits for the card.
  - **NVIDIA**: currently untested but _may_ work with the “-nvidia-deck” variant of bazzite.

### External Resource

Check out the [original thread](https://universal-blue.discourse.group/t/ayaneo-geek-1s-2s-linux-bazzite-support-is-already-almost-there-lets-add-them-to-the-officially-supported-devices/1046) for more information and updates on this device.

<hr>

## Additional Information

This applies to most handhelds running Bazzite.

### TDP Controls

![TDP|690x431, 75%](../../img/TDP.jpeg)

There are a few options for TDP Controls that work with Bazzite:

- The [HHD-overlay](https://github.com/hhd-dev/hhd/blob/master/readme.md) supports TDP controls.
  - Also has a desktop app that is pre-installed, look for the Handheld Daemon app in Desktop Mode.
- [SimpleDeckyTDP](https://github.com/aarron-lee/SimpleDeckyTDP) supports TDP, GPU, Power Governor, and among other settings.
  - Also has a [graphical application](https://github.com/aarron-lee/SimpleDeckyTDP-Desktop), but needs to be manually installed.
- [PowerControl](https://github.com/mengmeet/PowerControl) supports TDP, GPU, and fan controls on select devices.

### How do I open the HHD Overlay?

![Overlay|690x431, 75%](../../img/HHD_Overlay.jpeg)
![Settings Example|690x432, 75%](../../img/HHD_Settings_Example.jpeg)

Press, hold, or double-tap the Quick Access Menu button.

### Controller Information

For most handheld hardware, besides the Steam Deck, emulation of a DualSense controller is used for full functionality. Double tap or hold the side menu button to access settings for controller emulation including switching to an Xbox controller with reduced functionality.

If your device has paddles, you will want to use the DualSense Edge controller. It’s disabled by default because some games do not map it correctly.

Some games and emulators may need Steam Input **disabled** to work correctly with your controls.

#### Desktop Controls

Desktop Mode Controller Layout: It may not exist by default if Steam doesn't setup your handheld controller properly. This can be fixed in Steam's controller settings.

![desktop_controls_step_1|588x500, 75%](../../img/handheld_desktop_controls_1.png)

![desktop_controls_step_2|690x431, 75%](../../img/handheld_desktop_controls_2.png)

![desktop_controls_step_3|690x431, 75%](../../img/handheld_desktop_controls_3.jpeg)

Make sure to **apply** the desktop controls when you select them.

<hr>

## Contributing

This page is a **wiki**, edit it to add any relevant information you may have regarding the handheld and your experience with Bazzite on it. Make sure to follow proper [contributing guidelines](/CONTRIBUTE.md) before adding any edits.

<hr>

**See also**: [Steam Gaming Mode Overview](../Steam_Gaming_Mode.md)

**<-- Back to [Handheld Wiki](./index.md)**
