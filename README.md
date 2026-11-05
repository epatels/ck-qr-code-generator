# CK QR Code Generator

Branded, print-ready QR codes for any URL. Add your logo, pick your colours, show the URL underneath, and export to PNG, JPG, SVG or PDF. Everything runs offline on your PC.

![CK QR Code Generator](docs/screenshot.png)

## Features

- **Live preview** that updates as you type
- **Logo in the centre** with an adjustable size (10-30%) and a white shield behind it so it stays scannable
- **Highest error correction (level H)**, so QR codes with a logo still scan reliably
- **Colours**: 12 presets, custom hex values and a colour picker for the QR and the background
- **Transparent background** option with a checkerboard preview
- **Contrast checker** that warns when your colours are too close to scan
- **URL caption** below the code, with font, size, colour and word wrap
- **Print controls**: quiet-zone border (1-10 modules) and DPI (72-1200), with a physical size readout in cm and a warning when the code is too small to scan
- **Export** to PNG, JPG, SVG (vector) and PDF (sized to the chosen DPI)
- **Copy image** straight to the clipboard
- **Drag and drop** a link or text onto the window to fill the URL, or an image to use as the logo
- **Default logo**: save one logo and load it in a click
- **Dark and light themes**, remembered between sessions

## Keyboard shortcuts

| Shortcut | Action |
|---|---|
| Ctrl+L | Focus the URL box |
| Ctrl+S | Export as PNG |
| Ctrl+Shift+C | Copy image to clipboard |

## Install

### Microsoft Store
Search for **CK QR Code Generator** in the Microsoft Store.

### MSIX from Releases
1. Download `CKQRCodeGenerator_<version>_x64.msix` from the Releases page.
2. Double-click it and choose **Install**.

Test builds signed with a self-signed certificate need the certificate trusted first. Open PowerShell as Administrator and run:

```powershell
Import-Certificate -FilePath .\test_signing.cer -CertStoreLocation Cert:\LocalMachine\TrustedPeople
Add-AppxPackage .\CKQRCodeGenerator_<version>_x64.msix
```

### Run from source
Requires Python 3.9+ (64-bit recommended).

```bat
pip install -r requirements.txt
python qr_code_generator_qt.pyw
```

On Windows you can also double-click `qr_code_generator_qt.bat`.

## Build the MSIX yourself

Needs 64-bit Python 3 and the Windows 10/11 SDK (`makeappx`, `signtool`). Keep `build.bat`, `qr_code_generator_qt.pyw` and `requirements.txt` together.

```bat
build.bat          :: test package, self-signed, installable on this PC
build.bat store    :: unsigned package for Microsoft Store upload
build.bat clean    :: delete the build and dist folders
```

For the Store build, fill in `STORE_IDENTITY`, `STORE_PUBLISHER` and `STORE_PUBLISHER_DISPLAY` at the top of `build.bat` (from Partner Center, Product identity). To use your own app icon, put a PNG at `packaging\logo.png`.

## Settings

Your theme and default logo are saved in `qr_generator_config.json`. When run from source it sits next to the script. In the installed (packaged) app it is stored in `%APPDATA%\CK QR Code Generator`.

## Privacy

The app works entirely on your computer. It makes no network connections and collects, stores or sends no personal data.

## Tips for scanning

- Keep strong contrast between the QR colour and the background, dark on light works best.
- Keep the logo at 20% or smaller for small prints.
- For print, use 300 DPI or higher and keep the code at least 2 cm wide.
- The spec recommends a 4-module quiet zone. Raise the border setting if the code will sit against a busy background.

## Dependencies

PySide6, qrcode[pil], Pillow, reportlab.
