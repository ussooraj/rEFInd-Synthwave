# rEFInd-Synthwave

A sleek, synthwave-inspired theme for the rEFInd boot manager, featuring vibrant neon aesthetics and retro-futuristic design elements.

## About
<img src="resources/preview.png" alt="rEFInd Synthwave Theme Preview" align="right" width="450">

rEFInd-Synthwave is a custom visual theme for [rEFInd](https://www.rodsbooks.com/refind/), a customizable boot manager for UEFI-based systems. This theme transforms the standard boot experience with a stunning synthwave aesthetic, combining nostalgic 80s-inspired neon colors with modern design.

### Prerequisites

Before installing this theme, ensure you have:

- A UEFI-based computer (not BIOS/Legacy mode)
- rEFInd boot manager already installed on your system
- Access to your EFI System Partition (ESP)

If you haven't installed rEFInd yet, please visit the [official rEFInd installation guide](https://www.rodsbooks.com/refind/installing.html).

## Installation

> [!CAUTION]
> This method will replace your existing rEFInd configuration and icons. 
>
> A full backup is created first as a safety measure.

1.  **Clone this repository**

    ```bash
    git clone https://github.com/ussooraj/rEFInd-Synthwave.git
    cd ./rEFInd-Synthwave
    ```

2.  **Backup your entire rEFInd directory**

    Before making any changes, create a complete backup of your current rEFInd setup.</br>
    Navigate to your ESP's `EFI` directory and execute the following command:
    
    ```bash
    # assumes your ESP is mounted at /boot/efi
    sudo cp -r /boot/efi/EFI/refind /boot/efi/EFI/refind.backup
    ```
    
    If anything goes wrong, you can restore your original setup by deleting the `refind` folder and renaming `refind.backup` back to `refind`.

3.  **Remove old icons and copy new theme files**

    Now remove the default rEFInd icons and copy the theme's assets.</br> 
    run these commands:
    
    ```bash
    # Delete the original icons directory
    sudo rm -rf /boot/efi/EFI/refind/icons
    
    # Copy the new theme components
    sudo cp -r icons /boot/efi/EFI/refind/
    sudo cp -r assets /boot/efi/EFI/refind/
    ```

4.  **Replace the configuration file**

    Copy the theme's `refind.conf`. This will overwrite your existing configuration.
    
    ```bash
    sudo cp refind.conf /boot/efi/EFI/refind/refind.conf
    ```

5.  **Edit the configuration**

    The `refind.conf` you just copied is a **template**. You must edit it to match your operating systems.</br>
    For more details on how to do this, see the [Configuration](#configuration) section below.

## Configuration

### Customizing Boot Entries

The included `refind.conf` contains "my" menuentry stanzas.</br> 
You'll need to modify these to match your system:

```
menuentry "your_os_name" {
    icon /EFI/refind/icons/your_os_icon.png
    #volume YOUR_VOLUME_PARTUUID 
    loader /EFI/path/to/your/bootloader.efi
}
```

- Replace `your_os_name` with the name you want displayed in the boot menu.
- Update the `icon` path to point to the appropriate icon for your OS.
- Set the `loader` path to the correct EFI bootloader for your OS.
- **(optional)** Uncomment `volume` if you are using multiple bootable partitions. use `sudo lsblk -o +PARTUUID` to find the PARTUUID for the corresponding boot partition.

you can also add custom icons, banner and selection box</br>
just need to place them in the `icons` or `assets` folder and reference them here.</br>

For detailed information on configuring rEFInd, lookup [resources](#resources).

> [!NOTE]
> **Fallback Binary Included**
>
> The `/resources/refind-bin-0.14.1.zip` file is provided as a fallback option. 
>
> This specific version (0.14.1) has been tested and confirmed to work reliably with this theme. If you encounter issues with newer rEFInd versions (like myself), you can use this binary as a stable alternative.
>
> For installation, simply extract and run the `refind-install` shell script in the `/refind-bin-0.14.1` directory (also verify dependencies for installation).

## Resources

- [rEFInd Official Website](https://www.rodsbooks.com/refind/)
- [rEFInd Documentation](https://www.rodsbooks.com/refind/configfile.html)
- [UEFI Boot Process](https://www.rodsbooks.com/refind/bootmode.html)

## License

This project is licensed under MIT, the terms specified in the [LICENCE](LICENCE) file.

## Acknowledgments

- Built for [rEFInd](https://www.rodsbooks.com/refind/) by Roderick W. Smith
- Background and design elements created specifically for this theme

---

<p align="center">Made with 💜 for the rEFInd community</p>
