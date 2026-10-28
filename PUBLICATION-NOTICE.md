# Publication notice — MediaTek MT6878 module source mirror

This is a sanitized C48 provenance mirror of the MediaTek-owned source in the
LieppOS GQ5012BF1 combined kernel tree. It is not a build root and it is not a
preservation of the external eight-commit vendor history.

## Source

- Kernel publication commit: `d0feaaee4484e2fdd5cd87ebbf4c9e273a50b8b0`
- Kernel publication tree: `5b87650c888eab5b14925e7799ec900d4f94f307`
- C47 local import commit (not published): `7a75e19ebf5d7e4b3876c19f4e77cad385dff4f0`
- C44/C45/C46 source lineage: `ce07b664` + `d02a8942` + `2c896fab`

## Excluded from this mirror

| Path | Reason |
| --- | --- |
| `drivers/misc/mediatek/performance/lieppos14/source/` | Proprietary FPSGO wrapper; `a Proprietary module-license string` and an explicit MediaTek no-redistribution notice |
| `drivers/misc/mediatek/performance/lieppos14/{tools,tests,targets}/` | LieppOS experimental tooling, not MediaTek source |
| `drivers/misc/mediatek/tiny_lcd/` except `Kconfig` | Ulefone board driver containing a 1.4 MB vendor logo/init blob |
| `drivers/misc/mediatek/nfc/st21nfc/`, `yft_usb/`, `sensor/2.0/yft_devinfo/` | Ulefone-owned board drivers |

The canonical kernel tree still contains the Ulefone-owned sources. They are
omitted here to keep Git ownership disjoint and to avoid republishing
firmware/calibration material whose redistribution status is unresolved.

## Licensing

GPL-2.0 is dominant. Per-file SPDX identifiers and the upstream `COPYING` /
`LICENSES/` notices are preserved. Files without an SPDX header are not
relicensed by LieppOS; their original notices continue to apply. No private key
or signing secret is present. The C49 local update adds the MediaTek `gpu`, `connectivity`, `mtkcam` and
MET module sources under `vendor/mediatek/kernel_modules/`; see its
`SOURCE-MANIFEST.json` for exclusions.
