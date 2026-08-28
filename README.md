# google-sheets-pdf-automator
<img width="1280" height="720" alt="maxresdefault" src="https://github.com/user-attachments/assets/447ea5e8-b638-4930-b1f2-4957a6b1bd4f" />
# 📊 Google Sheets PDF Automator

Professional desktop application that automatically converts Google Sheets data into PDF documents with multi-threading support, rate limiting, and comprehensive error handling.

## ✨ Features

- **🔑 Multi-API Key Support**: Add multiple Google API keys for load balancing
- **🚀 Multi-threaded Processing**: Process hundreds of rows concurrently
- **📊 Real-time Progress Tracking**: Visual progress bars and statistics
- **🔄 Auto-Resume**: Automatically resume from failures or interruptions
- **⚡ Rate Limiting**: Intelligent rate limiting to prevent API quota exhaustion
- **📝 Comprehensive Logging**: Detailed logs for troubleshooting
- **🎨 Customizable Templates**: Multiple PDF templates (default, table, invoice)
- **💾 Database Tracking**: SQLite database tracks processed files to prevent duplicates
- **📜 License System**: Demo (10 days) and full version support
- **🖥️ Cross-platform**: Works on Windows, macOS, and Linux

## 🎯 Use Cases

- Bulk certificate generation
- Invoice automation
- Report generation from spreadsheets
- Data export to PDF format
- Any scenario requiring Google Sheets → PDF conversion

## 📋 Requirements

- Python 3.8+
- Google Cloud Project with Sheets API enabled
- Google Service Account credentials (JSON)

## 🚀 Quick Start

### 1. Installation

```bash
# Clone or extract the project
cd google_sheets_pdf_automator

# Install dependencies
pip install -r requirements.txt
```

### 2. Get Google API Credentials

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create a new project
3. Enable Google Sheets API and Google Drive API
4. Create a Service Account
5. Download JSON credentials
6. Share your Google Sheet with the service account email

**Detailed instructions available in the app: Settings → API Keys → How to Get API Key**

### 3. Run the Application

```bash
python main.py
```

### 4. Configure

1. Click **Settings**
2. Add your API key(s)
3. Enter your Google Sheets URL
4. Select output directory
5. Click **Save Settings**

### 5. Process

Click **Start Processing** and watch the magic happen! ✨

## 🔨 Building Executable

### Windows

```bash
# Install PyInstaller
pip install pyinstaller

# Build executable
pyinstaller build.spec

# The .exe will be in the dist folder
```

### macOS

```bash
# Same as Windows
pyinstaller build.spec

# The .app will be in the dist folder
```

### Linux

```bash
pyinstaller build.spec

# The binary will be in the dist folder
```

## 📁 Project Structure

```
google_sheets_pdf_automator/
├── main.py                 # Application entry point
├── config.py              # Configuration management
├── requirements.txt       # Python dependencies
├── build.spec            # PyInstaller build configuration
├── ui/                   # User interface modules
│   ├── main_window.py   # Main application window
│   ├── settings_dialog.py # Settings configuration
│   └── help_dialog.py   # API key help dialog
├── core/                # Core functionality
│   ├── sheets_client.py # Google Sheets API client
│   ├── pdf_generator.py # PDF generation
│   ├── processor.py     # Main processing engine
│   └── license_manager.py # License validation
└── utils/               # Utility modules
    ├── logger.py        # Logging system
    ├── database.py      # SQLite database
    └── rate_limiter.py  # API rate limiting
```

## ⚙️ Configuration

Configuration is stored in `~/.pdf_automator/config.json`

### Key Settings

- **api_keys**: List of Google API keys
- **output_directory**: Where PDFs are saved
- **spreadsheet_url**: Google Sheets URL
- **sheet_name**: Sheet name to process
- **max_workers**: Number of concurrent threads (1-16)
- **rate_limit_delay**: Delay between API requests (seconds)
- **auto_resume**: Resume from last processed row
- **pdf_template**: Template to use (default, table, invoice)

## 📊 PDF Templates

### Default Template
- Clean, professional layout
- Field labels and values
- Automatic formatting

### Table Template
- Tabular layout
- Color-coded headers
- Compact format

### Invoice Template
- Invoice-specific fields
- Customer and amount details
- Professional invoice format

### Custom Templates
You can create custom templates by modifying `core/pdf_generator.py`

## 🔑 License System

### Demo Version
- 10-day trial period
- Full features
- No limitations during trial

### Full Version
- Lifetime license
- All features unlocked
- Format: `XXXXX-XXXXX-XXXXX-XXXXX`

### Activation

1. Go to Settings → License tab
2. Enter license key
3. Click Activate

**For development/testing**: Use "Generate Test License Key" button in settings

## 🐛 Troubleshooting

### Common Issues

#### "Invalid API Key"
- Ensure you copied the entire JSON file
- Check that APIs are enabled in Google Cloud
- Verify service account has correct permissions

#### "Quota Exceeded"
- Add multiple API keys for rotation
- Increase rate_limit_delay in settings
- Contact Google to increase quota

#### "Permission Denied"
- Share the Google Sheet with service account email
- Check that service account has "Editor" or "Viewer" access

#### "No Module Named..."
- Reinstall dependencies: `pip install -r requirements.txt`

### Logs

Logs are stored in `~/.pdf_automator/logs/`

To export logs: Click "Export Log" button in the application

## 📝 Database

Processing history is stored in `~/.pdf_automator/tracking.db`

### Tables

- **processed_files**: Tracks completed, failed, and processing rows
- **sessions**: Processing session history

### Reset Database

Tools → Reset Database (clears all history)

## 🚦 API Rate Limiting

The application implements intelligent rate limiting:

- **60 requests per minute** (Google's limit)
- **100 requests per 100 seconds**
- Exponential backoff on errors
- Automatic API key rotation

## 🔒 Security

- API keys encrypted using Fernet (cryptography)
- License tied to machine ID
- Credentials never logged
- Secure storage in user directory

## 🎨 Customization

### Adding Custom PDF Templates

Edit `core/pdf_generator.py`:

```python
def generate_custom_template(self, data: Dict[str, Any], output_path: Path):
    # Your custom PDF generation code here
    pass
```

### Modifying UI

UI files are in the `ui/` directory using PyQt6

## 📄 License

This software is proprietary. 

- Demo version: 10-day free trial
- Full version: Commercial license required

## 🤝 Support

For support, please contact:
- Email: support@example.com
- Website: https://example.com

## 🔄 Version History

### v1.0.0 (2024-01-12)
- Initial release
- Multi-threaded processing
- Multiple API key support
- Auto-resume functionality
- Comprehensive logging
- License system (demo + full)

## 📚 Additional Resources

- [Google Sheets API Documentation](https://developers.google.com/sheets/api)
- [ReportLab Documentation](https://www.reportlab.com/docs/)
- [PyQt6 Documentation](https://www.riverbankcomputing.com/static/Docs/PyQt6/)

## ⚠️ Important Notes

1. **Keep API keys secure** - never share or commit them
2. **Respect API quotas** - use rate limiting wisely
3. **Test with small datasets** first before bulk processing
4. **Backup your data** before processing
5. **Monitor logs** for any issues

## 🎯 Future Enhancements

Planned features for future versions:

- [ ] Cloud storage integration (Dropbox, OneDrive)
- [ ] Email notification on completion
- [ ] Scheduled processing
- [ ] Custom field mapping UI
- [ ] PDF encryption support
- [ ] Batch template editing
- [ ] Web interface option

## 🙏 Credits

Built with:
- PyQt6 for GUI
- gspread for Google Sheets API
- ReportLab for PDF generation
- SQLite for database
- cryptography for encryption

---

**Made with ❤️ for automation enthusiasts**
