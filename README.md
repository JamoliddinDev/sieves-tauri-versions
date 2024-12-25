# sieves-tauri-versions
This is public Loook POS repo

**How to Create a New Release**
1. Update Version
// src-tauri/tauri.conf.json
{
  "package": {
    "productName": "Loook",
    "version": "X.Y.Z"  // Update this version number
  }
}

**Build the App**
npm run tauri build

**Get the New Signature**
- Go to: src-tauri/target/release/bundle/nsis/Loook_X.Y.Z_x64-setup.nsis.zip.sig
- Copy the contents of this file

**Update latest.json**
{
  "version": "vX.Y.Z",
  "notes": "Your release notes here",
  "pub_date": "CURRENT_DATE_TIME",
  "platforms": {
    "windows-x86_64": {
      "signature": "PASTE_NEW_SIGNATURE_HERE",
      "url": "https://github.com/JamoliddinDev/sieves-tauri-versions/releases/download/vX.Y.Z/Loook_X.Y.Z_x64-setup.nsis.zip"
    }
  }
}

**Create GitHub Release**
- Go to: https://github.com/JamoliddinDev/sieves-tauri-versions/releases/new
- Set tag: vX.Y.Z
- Title: "Version X.Y.Z"
- Upload two files:
  - src-tauri/target/release/bundle/nsis/Loook_X.Y.Z_x64-setup.nsis.zip
  - The updated latest.json

**Test Update**
- Run an older version of the app
- It should detect the new version and prompt for update
- Click "Yes" to update
- 
**Important Notes**
- Always use semantic versioning (X.Y.Z)
- Always prefix tags with 'v' (e.g., v0.2.0)
- Make sure file names in latest.json exactly match the uploaded files
- Keep the TAURI_PRIVATE_KEY environment variable set for signing builds
