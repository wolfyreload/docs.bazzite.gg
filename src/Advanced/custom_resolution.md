---
title: Custom Resolutions
authors:
  - "@ykshek"
tags:
  - Guide
---

# `custom-resolution-helper`

![Custom Resolution Helper Preview|1265x1108](../../img/Custom_Resolution_Helper_Preview.png)

!!! warning "Remove any custom resolutions if you encounter an unexpected display issue with `crh rm all`. Any modifications to your device should be done appropriately **at your own risk**"

!!! info "Custom resolutions created with this method require a reboot to take effect."

A command-line utility that assists with **creating** and **managing** custom resolutions for your Bazzite installation.

## Using `custom-resolution-helper`

![Custom Resolution Helper Command|1011x737](../../img/Custom_Resolution_Helper_Command.png)

Open a host terminal and **enter**:

```command
custom-resolution-helper
```

There is also an **alias** which is less typing for those on handhelds or HTPC setups without a keyboard:

```command
crh
```

### Options Available:

- `current`: Show your current resolutions, if any.
- `add`: Add a custom resolution.
- `rm`: Remove a custom resolution.
- `rm all`: Remove all custom resolutions.
- Run without arguments for **Interactive Mode**

### Guide for creating a custom resolution

1. Run `custom-resolution-helper` in a terminal.
2. Verify that you do **not** have a duplicate resolution.
3. Choose `Add`, using arrow keys to navigate and enter to submit.
4. Select the Display you want to create a custom resolution for. This display should be `connected`.
5. Follow the Instructions on-screen in **Interactive Mode**.
- If your refresh rate is not currently selectable in **System Settings** (e.g. you are overclocking your display from 60Hz to 75Hz, but 75Hz is currently not an available refresh rate), select **Yes** for timings to be calculated using the **VESA(TM) Coordinated Video Timings(CVT)**.
- If your monitor has a high resolution or refresh rate, you will also want to select **Yes** for calculating the display timing with **Reduced Blanking**.
- If you are using something like a Plasma TV or CRT Display, you may want the resolution to be **Interlaced**.
- If you are using a wide-screen TV, you may want the resolution to have **Margins**.
6. Once you finished selecting the options, you will get a prompt to change the boot configuration. Simply authorize it with your password.
7. Once the command finishes, you can reboot and select the new resolution in your **System Settings**.

### Guide for creating a custom resolution for Sunshine Game Streaming

Let's say you are streaming from your host PC (running Bazzite) to your Laptop:

- Your host PC has a resolution of `1920x1080@144Hz`,
- but your Laptop has a resolution of `2560x1600@120Hz`.

...and text in the stream looks blurry because of resolution scaling.

You can use `custom-resolution-helper` to add a virtual display to your host PC (running Bazzite) without a dummy plug!

Simply follow the steps for creating a custom resolution, and select the option to make the display **always enabled**.

!!! info "Using DisplayPort for virtual displays is recommended, as custom resolutions on HDMI ports may require an additional `edid` file, which this tool does not support."

### Advanced Usage

This tool adds a **kernel argument** with `video=[RESOLUTION]`. The `[RESOLUTION]` string follows the format `<name>:<xres>x<yres>[M][R][-<bpp>][@<refresh>][i][m][eDd]`, as specified in the [kernel documentation for modedb](https://www.kernel.org/doc/Documentation/fb/modedb.txt).

If you feel confident enough and know what you are doing, you can use the

```command
custom-resolution-helper add [RESOLUTION]
```

to add a resolution with functionality not included in this script, such as forcing a DVI-I port to use digital output.

