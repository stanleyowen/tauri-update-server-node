# tauri-update-server-node

[Tauri's App updater](https://tauri.app/v1/guides/distribution/updater/) with Node JS with your git repository's releases.

## Usage

### Development

1. Fork this repository
2. Clone your fork locally using folooing command
   ```bash
   $ git clone https://github.com/<your_github_username>/tauri-update-server-node.git
   ```
3. Change directory to `tauri-update-server-node`
   ```bash
   $ cd tauri-update-server-node
   ```
4. Install dependencies using [`yarn`](https://yarnpkg.com/)
   ```bash
   $ yarn install
   ```
5. Rename the `.env.example` file to `.env` and fill in the required details (`GH_OWNER` and `GH_REPO`)
6. Run the server using
   ```bash
   $ yarn start
   ```

### Configure apps

In `tauri.conf.json` :

```json
{
  // For more information, see https://tauri.app/v1/guides/distribution/updater/#tauri-configuration
  "tauri": {
    "updater": {
      "active": true,
      "endpoints": [
        "https://releases.myapp.com/{{target}}/{{arch}}/{{current_version}}"
      ],
      "dialog": true,
      "pubkey": "YOUR_UPDATER_SIGNATURE_PUBKEY_HERE"
    }
  }
}
```

### Publish updates

In your releases, please follow the following naming convention:
| Operating System | x86_64 (64-bit) | i686 (32-bit) | armv7 (ARM32) | aarch64 (ARM64) |
| --- | --- | --- | --- | --- |
| macOs | Installer: <br>`*x64.app.tar.gz`<br>`*x64.dmg.tar.gz`<br> Signature:<br>`*x64.app.tar.gz.sig`<br>`*x64.dmg.tar.gz.sig` | ❌ | ❌ | Installer: <br>`*amd64.app.tar.gz` <br> `*amd64.dmg.tar.gz` <br> Signature: <br>`*amd64.app.tar.gz.sig` <br> `*amd64.dmg.tar.gz.sig` |
| Linux | ❌ | ❌ | Installer: <br>`*amd32.AppImage.tar.gz` <br> `*amd32.deb.tar.gz`<br> Signature: <br>`*amd32.AppImage.tar.gz.sig` <br> `*amd32.deb.tar.gz.sig` | Installer: <br>`*amd64.AppImage.tar.gz` <br> `*amd64.deb.tar.gz`<br> Signature: <br>`*amd64.AppImage.tar.gz.sig` <br> `*amd64.deb.tar.gz.sig` |
| Windows | Installer: <br>`*x64.msi.zip`<br> Signature: <br>`*x64.msi.zip.sig` | Installer: <br>`*x32.msi.zip`<br> Signature: <br>`*x32.msi.zip.sig` | ❌ | ❌ |

### License

[MIT](LICENSE)
