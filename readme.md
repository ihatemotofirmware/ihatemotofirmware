# Moto G23 / G13 Bootloader Unlock & TWRP Flash Guide

> **Disclaimer:** Unlocking the bootloader and flashing custom images can **brick your device, void warranty, and wipe all data**. Backup everything and keep stock firmware handy.

---

## 1. Prerequisites

* Latest **ADB & Fastboot** installed (Android Platform Tools).
* Verified **TWRP image** for `penangf`.
* **vbmeta image** (stock or patched).
* OEM key generated from the community tool ([https://cxzstuff.github.io/Moto-G23-G13-OEM-Key-Generator/](https://cxzstuff.github.io/Moto-G23-G13-OEM-Key-Generator/)).

---

## 2. Reboot to Bootloader

```bash
adb reboot bootloader
```

* Wait until the device is in fastboot mode.
* Verify connection:

```bash
fastboot devices
```

---

## 3. Apply OEM Unlock Key

```bash
fastboot oem key <PASTE_GENERATED_KEY_HERE>
```

* If errors occur, check `penangf` community posts for correct command syntax.

---

## 4. Unlock Bootloader

```bash
fastboot flashing unlock
```

* Alternatively, some firmware versions use:

```bash
fastboot oem unlock
```

* This **will wipe userdata**.

---

## 5. Flash TWRP to `vendor_boot`

```bash
fastboot flash vendor_boot twrp_penangf.img
```

* Ensure the TWRP image is verified against checksums from the XDA thread.

---

## 6. Flash vbmeta (disable verification)

```bash
fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img
```

* Use a **patched vbmeta** if already prepared.
* Flashing incorrectly may cause bootloops.

---

## 7. Reboot Device

```bash
fastboot reboot
```

---

## Safety Tips

* Always use the **latest Fastboot binary**.
* Keep **stock firmware & rescue images** available.
* Community threads contain examples for recovering from **vbmeta bootloops**.
* Verify all images and keys with **official checksums** from XDA threads.

---

## References

* [TWRP for `penangf`](https://xdaforums.com/attachments/twrp_penangf-img.6217174/)
* [vbmeta Image](https://xdaforums.com/attachments/vbmeta-img.6196313/)
* [OEM Key Generator](https://cxzstuff.github.io/Moto-G23-G13-OEM-Key-Generator/)

---

**Note:** Always read the community threads carefully; command syntax may vary by firmware version.
