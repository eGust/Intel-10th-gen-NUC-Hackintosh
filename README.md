# Hackintosh on Intel 10th generation NUC

Running macOS on Intel NUC10I5FNH with OpenCore

## Build

* OS: macOS Catalina v10.15.6 (19G2021)
* CPU: Intel Core i5-10210U
* RAM: 2 * PNY Laptop RAM 16GB 2666Mhz (PNY 16GU2X08LIII43-12-K)
* SSD: Kingston A2000 1TB M.2 NVMe (KINGSTON SA2000M81000G)
* OpenCore: 0.6.0

## Usage

1. Copy entire `EFI` directory to your EFI partition.
2. Follow OpenCore [instructions](https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html#platforminfo) to update `SystemSerialNumber`, `MLB` and `SystemUUID` under `PlatformInfo -> Generic`.

### Enabling Wi-Fi

In order to get Wi-Fi working, you need to manually `EFI/OC/Kexts/itlwmx.kext/Contents/Info.plist` duo to [itlwm](https://github.com/OpenIntelWireless/itlwm). There will be 2 `Ethernet` connections under `System Preferences -> Network`.

> Search for `YOUR_WIFI` or `CHANGE-ME!` in `EFI/OC/Kexts/itlwmx.kext/Contents/Info.plist` and replace them with your SSID (aka `Network Name`) and password.

## Others

Here is the [sanity check result](https://opencore.slowgeek.com/?file=cometlake060Ji5sc9&rs=cometlake060):

1. You can remove `OpenCanopy.efi` from `UEFI -> Drivers` and change `Misc -> Boot -> PickerMode` back to `Builtin` to disable OpenCore GUI ([OpenCanopy.efi](https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html#setting-up-opencore-s-gui)).
2. `HideAuxiliary` is set to `No`.
3. `prev-lang:kbd` is set to `en-US:0` to avoid [macOS installer in Russian](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/troubleshooting.html#macos-installer-in-russian). You have to [reset NVRAM](https://dortania.github.io/OpenCore-Install-Guide/why-oc.html#opencore-features) if not in English.

## Credits

Base on [Majesticmatt](https://www.tonymacx86.com/members/majesticmatt.2448862/)'s [build](https://www.tonymacx86.com/threads/intel-nuc-10-frost-canyon.289485/post-2167159) on <https://www.tonymacx86.com>
