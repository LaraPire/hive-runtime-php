# 🐝 Hive PHP Runtime

### Managed PHP runtime distributions for Hive

![Hive Logo](https://raw.githubusercontent.com/LaraPire/hive-art/main/Hive-Logo.png)

---

## ✨ About

**Hive PHP** provides versioned, portable, and production-ready PHP runtimes used by Hive.

Instead of relying on system-installed PHP, Hive downloads and manages isolated PHP environments per version — ensuring consistency, stability, and zero configuration conflicts.

---

## 🎯 Purpose

This repository contains:

- ✅ Versioned PHP runtime builds (8.1, 8.2, 8.3, 8.4)
- ✅ Cross-platform distributions (Windows / Linux)
- ✅ Hive-compatible configurations
- ✅ Release assets for automated runtime downloads
- ✅ Version manifest for Hive Runtime Manager

---

## 📦 Runtime Structure

Each release contains a packaged PHP runtime:

```
php/
├── php.exe (Windows) or php (Linux)
├── php.ini
├── ext/
├── php-cgi
└── required shared libraries
```

Installed by Hive to:

```
~/.hive/runtimes/php/<version>/
```

---

## 🔄 Version Management

Hive reads the `manifest.json` file to determine:

- Available PHP versions
- Supported platforms
- Download URLs for each build
- Extension recommendations

### Example manifest entry:

```json
{
  "php": {
    "8.4": {
      "full": "8.4.5",
      "windows": {
        "url": "https://github.com/LaraPire/hive-php/releases/download/v8.4.5/php-8.4.5-nts-Win32-vs17-x64.zip",
        "type": "zip",
        "architecture": "x64"
      },
      "linux": {
        "url": "https://github.com/LaraPire/hive-php/releases/download/v8.4.5/php-8.4.5-ubuntu22.04-x86_64.tar.gz",
        "type": "tar.gz",
        "architecture": "x86_64"
      }
    }
  }
}
```

---

## 🛠️ Supported Platforms

| Platform | Architecture | Status |
|----------|--------------|--------|
| Windows 10/11 | x64 | ✅ |
| Linux (Ubuntu 22.04+) | x86_64 | ✅ |
| macOS | x64 / arm64 | 🔜 Planned |

---

## 📋 Included Extensions

### Common (enabled by default):
`curl`, `json`, `mbstring`, `openssl`, `pdo_mysql`, `pdo_sqlite`, `zip`, `fileinfo`, `sodium`, `opcache`

### Recommended (configurable in Hive):
`gd`, `intl`, `redis`, `imagick`, `xdebug`

---

## ⚙️ Default php.ini Settings

| Setting | Value |
|---------|-------|
| `memory_limit` | 256M |
| `max_execution_time` | 30 |
| `upload_max_filesize` | 2M |
| `post_max_size` | 8M |
| `date.timezone` | UTC |
| `opcache.enable` | 1 |
| `opcache.memory_consumption` | 128M |

---

## 🔐 Philosophy

- No system pollution
- No dependency conflicts
- Isolated per-version runtimes
- Fast switching between PHP versions
- Predictable development environments

---

## 🏢 Organization

Part of the [LaraPire](https://github.com/LaraPire/) ecosystem — building modern developer infrastructure.

---

## 📄 License

Distributed under the MIT License.

---

## 🤝 Contributing

Runtime updates and improvements are welcome.  
Open an issue or submit a pull request.

---

**🐝 Powering Hive with clean, isolated PHP environments.**