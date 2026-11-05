# CK QR Code Generator

Branded, print-ready QR codes for links, text, Wi-Fi, contacts, email, phone, SMS, WhatsApp, locations, calendar events and UPI payments. Add your logo, pick your colours and styles, add a "Scan me" frame, and export to PNG, JPG, SVG or PDF. Make hundreds at once from a spreadsheet. Everything runs offline on your PC.

![CK QR Code Generator](docs/screenshot.png)

## What's new in 3.1.0

- **11 QR code types**, not just links (see below)
- **Batch generation** from an Excel or CSV file
- **Styles**: rounded or dotted modules, rounded or circular corner eyes, gradient colours and a separate eye colour
- **"Scan me" frames** with your own label and colour
- **Scan test**: every code is decoded after it's drawn, so you know it reads back correctly before you print it

## Features

### QR code types

| Type | What scanning it does |
|---|---|
| URL / Link | Opens the web address |
| Text | Shows any text, in any language |
| Wi-Fi | Joins the network (name, password, security, hidden network) |
| Contact (vCard) | Adds a contact with name, phones, email, website, address and note |
| Email | Starts an email with the recipient, subject and message filled in |
| Phone call | Dials the number |
| SMS | Starts a text message, optionally pre-filled |
| WhatsApp | Opens a chat with a pre-filled message |
| Location | Opens a map at the coordinates |
| Calendar event | Adds an event, including all-day events |
| UPI payment | Opens a payment to a UPI ID, with optional amount and note |

### Design

- **Live preview** that updates as you type
- **Logo in the centre** with an adjustable size (10-30%) and a white shield behind it
- **Highest error correction (level H)**, so QR codes with a logo still scan reliably
- **Colours**: 12 presets, custom hex values and a colour picker, a transparent background, and a contrast checker
- **Styles**: dots (square, rounded, round), corner eyes (square, rounded, circle), gradient with three directions, optional separate eye colour
- **Frames**: label above or below the code ("SCAN ME" or your own text) in any colour
- **Caption** below the code, automatic or your own text, with font, size, colour and word wrap

### Output

- **Print controls**: quiet-zone border (1-10 modules) and DPI (72-1200), with a physical size readout in cm and a warning when the code is too small to scan
- **Export** to PNG, JPG, SVG (vector, with all styles) and PDF (sized to the chosen DPI)
- **Copy image** straight to the clipboard
- **Scan test** after every change: a green tick means the finished image decodes back to exactly what you entered

### Batch generation

Click **Batch...** (Ctrl+B), or drop an .xlsx or .csv file onto the window.

1. Choose the type in the main window and set the colours, style, frame and logo you want.
2. Pick your spreadsheet. The first row must hold column names.
3. Match each field to a column. Fields you leave unmatched use the value in the main window. Columns with names like the field names (for example `ssid`, `Mobile`, `Email`) are matched for you.
4. Optionally choose a caption column and a file-name column, pick a format and an output folder, and click **Generate**.

Rows with problems (for example a missing Wi-Fi name) are skipped and listed so you can fix them. Duplicate file names get a number added. For calendar events use dates like `2026-12-25 18:30`.

### Other

- **Drag and drop** a link or text onto the window, or an image to use as the logo
- **Default logo**: save one logo and load it in a click
- **Dark and light themes**, remembered between sessions

## Feedback and support

- **Share feedback, report a problem or suggest a feature:** use the [feedback page](https://OWNER.github.io/REPO/) or [open an issue](https://github.com/OWNER/REPO/issues/new/choose) and pick a form.
- **Questions and ideas:** [Discussions](https://github.com/OWNER/REPO/discussions).
- Please don't post Wi-Fi passwords, UPI IDs or personal phone numbers. Made-up sample values are fine.

## Keyboard shortcuts

| Shortcut | Action |
|---|---|
| Ctrl+L | Focus the first input box |
| Ctrl+S | Export as PNG |
| Ctrl+Shift+C | Copy image to clipboard |
| Ctrl+B | Open batch generation |

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
Requires Python 3.9+ (64-bit recommended). `openpyxl` (Excel batch files) and `zxing-cpp` (scan test) are optional: if they are missing, the app still runs and switches those two features off.

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

The app works entirely on your computer. It makes no network connections and collects, stores or sends no personal data. Wi-Fi passwords, contact details and payment details you type in are never saved to disk; only your theme and default logo path are.

## Tips for scanning

- Keep strong contrast between the QR colour and the background, dark on light works best.
- Keep the logo at 20% or smaller for small prints.
- For print, use 300 DPI or higher and keep the code at least 2 cm wide.
- Styled codes (dots, gradients, frames) look great but read less easily. Check for the green scan test tick, and test with a real phone before printing many.
- Contact cards and calendar events hold a lot of data and make dense codes. Print them larger and leave out fields you don't need.
- Check UPI IDs carefully: a payment goes to whoever owns the ID. The app asks you to confirm the payee before you export.
- The spec recommends a 4-module quiet zone. Raise the border setting if the code will sit against a busy background.

## Dependencies

PySide6, qrcode[pil], Pillow, reportlab, openpyxl (optional), zxing-cpp (optional).
