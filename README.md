# MediaTek MT6878 kernel module source mirror

This repository holds a **verified, sanitized source mirror** of the MediaTek-owned
kernel source used by the LieppOS Ulefone Armor 29 Pro Thermal (GQ5012BF1 /
MT6878T) build. It is not a standalone kernel build root.

## Source

| Field | Value |
| --- | --- |
| Kernel repository | `android_kernel_ulefone_gq5012bf1` |
| Source commit | `d0feaaee4484e2fdd5cd87ebbf4c9e273a50b8b0` (C48 publication snapshot) |
| Source tree | `5b87650c888eab5b14925e7799ec900d4f94f307` |
| Source base | C44 `ce07b664` + C45 `d02a8942` + C46 `2c896fab` |
| Reference build | C44 `6.1.115-mt6878-gq5012bf1-c29+` |

The source commit is a **sanitized C48 publication snapshot**, not the local C47
import commit `7a75e19e`. The C47 local history is not published because it
contained a non-redistributable FPSGO private wrapper. Every retained file hash
is recorded in `SOURCE-MANIFEST.json`.

## Included

- `drivers/misc/mediatek/` - MediaTek platform, power, thermal, audio-IPI,
  camera, connectivity helpers, display helpers and board drivers that are not
  Ulefone-owned.
- `drivers/gpu/drm/mediatek/` - MediaTek DRM/KMS and `mediatek_v2` panel provider.
- `drivers/clk/mediatek/`, `drivers/soc/mediatek/`,
  `drivers/thermal/mediatek/` - MediaTek clock, SoC and thermal support.
- `drivers/mmc/host/mtk-mmc{,-dbg}.{c,h}` - the MMC host driver fixed in C46.

## Publication exclusions (C48)

| Path | Reason |
| --- | --- |
| `drivers/misc/mediatek/performance/lieppos14/source/` | Proprietary FPSGO wrapper (`a Proprietary module-license string`, explicit no-redistribution notice) |
| `.../lieppos14/{tools,tests,targets}/` | LieppOS experimental tooling, not MediaTek source and not a build input |
| `drivers/misc/mediatek/tiny_lcd/` (except `Kconfig`) | Ulefone board driver with a 1.4 MB vendor logo/init blob |
| `drivers/misc/mediatek/nfc/st21nfc/`, `yft_usb/`, `sensor/2.0/yft_devinfo/` | Ulefone-owned board drivers |

The canonical kernel tree still contains the excluded Ulefone sources. This
mirror is deliberately limited to MediaTek-owned paths to avoid duplicate Git
ownership. The Ulefone mirror is withheld from publication pending a
firmware/calibration redistribution review.

## Not included

MediaTek's out-of-tree module trees (`gpu/`, `connectivity/`, `mtkcam/`,
`met_drv_v3/`) are separate source units referenced by the build environment.
They were not imported in C47 because they are large, separately licensed and
not required to reproduce the kernel `Image`, the panel module or `mtk-mmc.ko`.

## Build relationship

Kbuild, generated headers, `Module.symvers`, KCFI type hashes and modversion CRCs
are produced by the combined kernel tree. This mirror preserves the original
relative paths and license notices for review and provenance; it is not
compiled independently.

## Licensing

GPL-2.0 is the dominant license. `SOURCE-MANIFEST.json` records the SPDX
identifier found in each file. The C48 publication removes the only files with
explicit MediaTek no-redistribution notices. Files without an SPDX header
remain subject to their original notices; no relicensing is claimed.
