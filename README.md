# CK QR Code Generator

Branded, print-ready QR codes for links, text, Wi-Fi, contacts, email, phone, SMS, WhatsApp, locations, calendar events and UPI payments. Add your logo, pick your colours and styles, add a "Scan me" frame, and export to PNG, JPG, SVG or PDF. Make hundreds at once from a spreadsheet. Everything runs offline on your PC.

![CK QR Code Generator](docs/screenshot.png)

**Links:** [Instructions](INSTRUCTIONS.md) · [Feedback page](https://OWNER.github.io/REPO/) · [Report a problem](https://github.com/OWNER/REPO/issues/new?template=bug_report.yml) · [Privacy policy](PRIVACY.md) · [Releases](https://github.com/OWNER/REPO/releases)

## Highlights

- **11 QR code types:** link, text, Wi-Fi, contact card (vCard), email, phone, SMS, WhatsApp, location, calendar event and UPI payment
- **Batch generation** from an Excel or CSV file, one file per row
- **Your brand:** logo in the centre, 12 colour presets or custom colours, gradients, rounded or dotted styles, circular corner eyes, transparent background and "Scan me" frames
- **Built-in scan test:** every code is decoded after it's drawn, so you know it reads back correctly before you print it
- **Print-ready:** DPI from 72 to 1200, a size readout in centimetres, contrast and "too small to scan" warnings
- **Export** to PNG, JPG, SVG (vector) and PDF, or copy the image to the clipboard
- **Private:** works fully offline, with no accounts, tracking or network connections
- Dark and light themes, and drag and drop for links, logos and spreadsheets

## Install

**Microsoft Store:** [get CK QR Code Generator from the Microsoft Store](https://apps.microsoft.com/detail/9NPSR6HWP1FF), or search for it by name.

**Run from source:** requires Python 3.9+ (64-bit recommended).

```bat
pip install -r requirements.txt
python qr_code_generator_qt.pyw
```

On Windows you can also double-click `qr_code_generator_qt.bat`. `openpyxl` (Excel batch files) and `zxing-cpp` (scan test) are optional: if they are missing, the app still runs and switches those two features off.

## Using the app

See **[INSTRUCTIONS.md](INSTRUCTIONS.md)** for a step-by-step guide to every QR code type, styles, frames, batch generation, keyboard shortcuts, scanning tips and troubleshooting.

## Feedback and support

- **Share feedback, report a problem or suggest a feature:** use the [feedback page](https://OWNER.github.io/REPO/) or [open an issue](https://github.com/OWNER/REPO/issues/new/choose) and pick a form.
- **Questions and ideas:** [Discussions](https://github.com/OWNER/REPO/discussions).
- Please don't post Wi-Fi passwords, UPI IDs or personal phone numbers. Made-up sample values are fine.

## Privacy

Read the full [privacy policy](PRIVACY.md). In short: the app works entirely on your computer. It makes no network connections and collects, stores or sends no personal data. Wi-Fi passwords, contact details and payment details you type in are never saved to disk; only your theme and default logo path are.

## Built with

[PySide6](https://pypi.org/project/PySide6/), [qrcode](https://pypi.org/project/qrcode/), [Pillow](https://pypi.org/project/Pillow/), [ReportLab](https://pypi.org/project/reportlab/), and optionally [openpyxl](https://pypi.org/project/openpyxl/) and [zxing-cpp](https://pypi.org/project/zxing-cpp/).

Maintainers: how to build the Microsoft Store package is in [INSTRUCTIONS.md](INSTRUCTIONS.md#building-the-microsoft-store-package).
