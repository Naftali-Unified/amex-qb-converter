# Amex → QBO Converter

A simple, client-side web tool that converts American Express Excel statements into OFX (QBO) format for seamless import into QuickBooks.

## Features

- 🚀 **Client-side Processing** - No server needed, all conversion happens in your browser
- 📁 **Excel Import** - Upload `.xlsx` or `.xls` files directly from your Amex statement export
- 💾 **QBO Export** - Download properly formatted OFX files compatible with QuickBooks Online
- 🔧 **Automatic FITID Generation** - Generates unique transaction IDs for duplicates prevention
- 💾 **Local Storage** - Remembers your account settings between sessions
- 🔐 **Private** - Your data never leaves your computer

## How to Use

1. **Export Your Statement**: Download your American Express statement as an Excel file
2. **Open the Converter**: Navigate to the tool (hosted at `index.html` in this repository)
3. **Fill in Required Fields**:
   - **Select File**: Choose your Amex Excel export
   - **Account ID**: Your bank account number or unique ID used in QuickBooks mapping
   - **Last 5 of CC**: The last 5 digits of your credit card (or identifier Amex uses)
   - **Balance** (Optional): Your current ledger balance to display in QB bank feeds
4. **Configure Options**:
   - **Randomize Blank FITID**: Check to automatically generate unique IDs for transactions missing one (prevents duplicates in QuickBooks)
5. **Download**: Click "Download QBO" to generate and download your formatted file
6. **Import to QuickBooks**: Open QuickBooks Online and import the downloaded `.qbo` file

## Requirements

- Modern web browser (Chrome, Firefox, Safari, Edge)
- American Express Excel statement export
- QuickBooks account

## Technical Details

### Supported Formats
- **Input**: Excel files (`.xlsx`, `.xls`)
- **Output**: OFX 2.0 format (`.qbo`)

### Data Processing
- Extracts transactions from column positions in the Amex export
- Automatically converts amounts (handles $ signs and commas)
- Supports both DEBIT and CREDIT transaction types
- Sanitizes transaction names and memos for QuickBooks compatibility
- Preserves transaction date ranges in the exported file

### JavaScript Libraries
- [XLSX.js](https://github.com/SheetJS/sheetjs) - Excel file parsing

## Privacy & Security

This tool:
- ✅ Processes all data locally in your browser
- ✅ Does not send any data to servers
- ✅ Does not store your files or data remotely
- ✅ Uses localStorage only to remember your form preferences

## Troubleshooting

### "Button is disabled"
Ensure you've filled in all required fields:
- Selected an Excel file
- Entered your Account ID
- Entered Last 5 of CC (minimum 5 characters)

### Transactions not appearing in QuickBooks
- Verify the Account ID matches your QuickBooks setup
- Check that the Last 5 of CC identifier is correct
- Ensure the transaction dates fall within your import range in QB

### Duplicate transactions in QuickBooks
- Keep "Randomize Blank FITID" checked to auto-generate IDs for missing transaction identifiers

## File Structure

```
amex-qb-converter/
├── README.md          # This file
├── LICENSE            # The Unlicense
└── index.html         # Complete web application (HTML, CSS, JavaScript)
```

## License

This project is licensed under [The Unlicense](LICENSE) - do whatever you want with it!

## Contributing

Found a bug or have a suggestion? Feel free to:
- Open an issue to report problems
- Submit a pull request with improvements
- Share feedback on the converter's functionality

## Notes

- Amex statement exports may vary in format; this tool is optimized for standard Amex Excel downloads
- The tool currently skips zero-amount transactions and rows without valid dates
- Transaction description fields are limited to 32 characters (NAME) and 255 characters (MEMO) per OFX specification
- Special characters are removed from transaction descriptions to ensure QuickBooks compatibility

---

Made with ❤️ for accounting workflows
