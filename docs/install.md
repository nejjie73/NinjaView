# Install NinjaView

Download the latest **`NinjaView-…-NinjaScript.zip`** from the [Releases page](https://github.com/nejjie73/NinjaView/releases/latest). Leave it zipped.

1. In NinjaTrader's Control Center, choose **Tools > Import > NinjaScript Add-On**.
2. Select the `-NinjaScript.zip` you downloaded. Review NinjaTrader's prompts and wait for its success message.
3. Restart NinjaTrader so the DLL and its matching interface load together.
4. Open **New > NinjaView** for the standalone chart window, or add **NinjaView Pine** from a chart's Indicators dialog and choose your local `.pine` file.
5. For oscillator-style scripts (anything that is not `overlay=true`), set **Panel** to **New panel** when adding the indicator. NinjaTrader chooses the panel before the script is loaded; if you forget, the indicator shows a reminder instead of squashing your price chart.

No PowerShell, extraction, administrator access, Node.js or .NET SDK is needed. Reference environment: NinjaTrader 8.1.8.3, Windows x64. The ZIP is unsigned, so NinjaTrader may show its normal third-party add-on warning.

## Trial and license key

The 7-day free trial starts the first time you use the NinjaView Pine indicator or open the NinjaView window. After it ends, both stop calculating until you enter a license key:

- **Control Center > New > NinjaView** shows a license window where you can paste your key, or
- open any **NinjaView Pine** indicator's settings and paste the key into **License > License key**.

The key is stored for your Windows user and unlocks both. **License status** in the indicator settings shows the trial days left or your license expiry date.

## Verify the download

Each release lists a SHA-256 checksum. In PowerShell:

```powershell
Get-FileHash .\NinjaView-<version>-NinjaScript.zip -Algorithm SHA256
```

The hash should match the `.sha256` file published with the release.

## Pine libraries

Scripts that `import` libraries look for them first in a `PineLibraries` folder next to the script, as `PineLibraries/Owner/Library/Version.pine`. If a library isn't there and it's an open-source public library on TradingView, NinjaView downloads that exact version from tradingview.com once, verifies the author, name and version, and caches it (with a SHA-256 check) under `%LOCALAPPDATA%\NinjaView\PineLibraries`. Private or invite-only libraries must be supplied locally.

## Updates and rollback

Keep the last ZIP that worked for you. To update, import the newer ZIP the same way, then restart. To roll back, import the previous ZIP and restart. If NinjaTrader requires removal first: close NinjaView windows, remove NinjaView Pine from charts, then use **Tools > Remove NinjaScript Assembly > NinjaView** before importing the version you want. Don't remove unrelated assemblies.

Save your workspaces before updating. If NinjaTrader reports a conflict or can't replace the DLL, stop and [open an issue](https://github.com/nejjie73/NinjaView/issues/new/choose) with the exact message rather than deleting files by hand.

### Upgrading from a Google Drive copy

Earlier copies were shared through Google Drive. If you installed one by importing a `-NinjaScript.zip`, just import the new release over it and restart. If you used the older PowerShell `-package.zip` installer, import the new NinjaScript ZIP over it; the assembly keeps the same name (`NinjaView.dll`), so don't install a second renamed copy.

## Where files go

The importer installs the assembly under `Documents\NinjaTrader 8\bin\Custom` and resources under `templates\NinjaView\<build-id>`. Older resource folders may remain after upgrades; they're inactive and allow rollback. Keep your own Pine files outside the installation folders. Nothing is uploaded by installation or by the diagnostic report export.
