# NMS tester package (temporary)

**Download:** `NMS_tester_package_2026-11-22.zip` (481,340,659 bytes) from release `tester-2026-11-22`:
https://github.com/DeFluxStudios/NMS-Tester-Package/releases/tag/tester-2026-11-22

Zip SHA-256: `8e3b09afc5f8ce234c730ea9489a650146735608f355384640316b21aa5a3cee`

This repository is temporary and will be removed later. The text below is the same README that is inside the zip.

---

## About the 2026-11-22 package

These are the full client files for the **Glyph 1** test server (it shows as **Thunderdome** on the server list).
Everything here is being built and tested on Glyph for an eventual release on Triune.

**This zip is a temporary convenience.** The Glyph patcher normally delivers these files. Use this zip when the
patcher is not working for you, or when you want the newest test files in one download. It will be removed later.

For the Glyph test server only. Do not put these files in the game folder you use for Triune.

## What is inside

- `files/`: 116 client files (zone and model files, sounds, maps, spell and string files, the overlay DLLs and
  their settings files) plus `Start_Glyph.cmd`. The folder layout matches the game folder.
- `MANIFEST.sha256`: one SHA-256 checksum per file (117 lines).
- `Verify_Files.ps1`: checks every file against the manifest.
- This README.

Compared with the Glyph patch channel (list 20261121152742), six files here are newer test builds:
`d3d9.dll`, `d3d9_blade.ini`, `nms_overlay.ini`, `spells_us.txt`, `dbstr_us.txt` and
`Resources/OnDemandResources.txt`. The spell and string files include the newest custom spells.
`dxbcSigner.dll` is also included because `d3d9on12.dll` needs it.

## Install (separate Glyph copy)

Your Triune game folder is never changed by these files. Glyph gets its own copy.

1. Run the normal NMS Triune patcher on your normal game folder, so the base files are current. Then close it.
2. Close the game.
3. Make a copy of your whole game folder (the folder that holds `eqgame.exe`). Name the copy `NMS Glyph`.
4. Unzip this package anywhere, for example your Downloads folder.
5. Open the unzipped `files` folder, select everything inside it, and copy it into `NMS Glyph`.
   When Windows asks, choose **Replace the files in the destination**.
6. In `NMS Glyph`, right-click `Start_Glyph.cmd` and choose **Send to**, then **Desktop (create shortcut)**.
   Always start Glyph with that shortcut. It starts the game without patching.
7. Log in as usual and pick **Thunderdome** on the server list.

**Important:** never run LaunchPad or any patcher inside the `NMS Glyph` folder. It overwrites the package files
with older ones. To update, download the newer zip and copy its files in again.

**Undo:** delete the `NMS Glyph` folder and its desktop shortcut. Your Triune folder was never touched.

## Check the files (optional)

Before copying, you can confirm the download is complete and unchanged.

1. Check the zip itself: its SHA-256 is listed on the release page and on the testers page. In PowerShell:
   `Get-FileHash .\NMS_tester_package_2026-11-22.zip`
2. Check every file: in the unzipped folder, right-click `Verify_Files.ps1` and choose **Run with PowerShell**, or
   in a PowerShell window inside the unzipped folder run `powershell -ExecutionPolicy Bypass -File .\Verify_Files.ps1`.
   It reads files only and changes nothing. It ends with `All 117 files OK` or lists any file that does not match.

## Troubleshooting

- **A file fails the check:** download the zip again. A partly downloaded zip is the usual cause.
- **Windows says the script is not signed or blocked:** right-click the file, choose **Properties**, tick
  **Unblock**, then run it again. You can also open it in Notepad and read every line first.
- **Thunderdome is not on the server list:** make sure you started the game with the `Start_Glyph.cmd` shortcut.
- **New spells show odd names or no description:** a patcher may have put back older spell files. Copy
  `spells_us.txt` and `dbstr_us.txt` from this zip again.
- **The game will not start or says a DLL such as VCRUNTIME140.dll or MSVCP140.dll is missing:** install the
  Microsoft Visual C++ 2015-2022 Redistributable (x86) from Microsoft's website, then try again.
- **The game closes when you tab back in:** see the Discord game hook fix at
  https://defluxstudios.dev/testers.html#discord-hook
- **Windows Defender or another scanner flags a DLL:** check the file against `MANIFEST.sha256`. The NMS overlay
  DLLs are new and unsigned, so some scanners are cautious about them. `dinput8.dll` is the server admin's client
  file. `d3d9on12.dll` and `dxbcSigner.dll` are Microsoft components.

## Report a bug

- In game, hail **Pip Ledgerwick** in Jaggedpine and click **Report a bug**, or
- use the web bug reporter: https://192-9-140-204.sslip.io/bugs/new
- Testers page: https://defluxstudios.dev/testers.html

Bug reports from the in-game reporter upload to the project's bug site. Please mention that you installed from the
2026-11-22 zip.

## Notes

- Non-commercial test files. The spell and string files are the server's own files, shared with the server
  admin's permission.
- Some settings files have lines marked TEST-ONLY: REMOVE BEFORE TRIUNE. Those lines are only for the Glyph test
  server and will be taken out before anything is released on Triune. You do not need to change them.
