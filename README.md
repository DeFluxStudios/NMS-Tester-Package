# NMS tester package (temporary)

The newest files for the **Glyph 1** test server (it shows as **Thunderdome** on the server list).
Everything here is being built and tested on Glyph for an eventual release on Triune.

This is a temporary download while the Glyph patcher catches up. It will be removed later.
Your normal Triune game is not changed: Glyph gets its own copy called **NMS Glyph**.

## Install Glyph (4 steps)

Before you start: start your normal game once with your usual NMS Triune icon so it updates, then close it.

1. Download **[Install_Glyph.cmd](https://github.com/DeFluxStudios/NMS-Tester-Package/releases/latest/download/Install_Glyph.cmd)**
   (or click the **Install Glyph** button on https://defluxstudios.dev/testers.html).
   A small download box appears at the top right of Chrome or Edge. Click **Install_Glyph.cmd** in it.
   If you cannot see it, hold **Ctrl** and press **J** to open your downloads, then click **Install_Glyph.cmd**.
2. If your browser says the file isn't commonly downloaded, click the **...** next to it, then **Keep**
   (in Edge you may also need **Show more**, then **Keep anyway**). Then click the file.
   If Windows shows "Windows protected your PC", click **More info**, then **Run anyway**.
3. Click the buttons. Before you click **Install Glyph**, start your normal game once so it updates, then close
   it, and tick the box. The installer finds your game, makes the NMS Glyph copy, downloads and checks the Glyph
   files, and makes two desktop icons. At the end, click **Start Glyph now**.
4. From then on, start Glyph with the **Glyph (test server)** icon on your desktop. Pick **Thunderdome** on the
   server list.

To get newer Glyph files later, click the **Update Glyph** icon on your desktop.

Never run LaunchPad or any patcher from the NMS Glyph copy: it puts back older files. Use the desktop icons.

## If something goes wrong

- The installer stops with a message: it says what happened and where it saved a log. Nothing in your Triune
  game was changed. Run it again. If it happens again, ask in tester Discord and paste the message.
- The game will not start and mentions VCRUNTIME140.dll or MSVCP140.dll: download
  https://aka.ms/vs/17/release/vc_redist.x86.exe (Microsoft Visual C++ 2015-2022, x86), click it in your download
  box, then click **Install**. Then click the Glyph icon again.
- The game closes when you tab back in: see https://defluxstudios.dev/testers.html#discord-hook
- New spells show odd names: click **Update Glyph** on your desktop.
- To remove Glyph, ask in tester Discord and we will walk you through it. Your Triune game is untouched.

## Report a bug

- In game, hail **Pip Ledgerwick** in Jaggedpine and click **Report a bug**. Reports from the in-game reporter
  upload to the project's bug site.
- Or use the web bug reporter: https://192-9-140-204.sslip.io/bugs/new
- Please mention that you installed the 2026-11-22 files.

## Notes

- Non-commercial test files. The spell and string files are the server's own files, shared with the server
  admin's permission.
- Some settings files have lines marked TEST-ONLY: REMOVE BEFORE TRIUNE. Those lines are only for the Glyph test
  server and will be taken out before anything is released on Triune. You do not need to change them.
- Security scanners: the NMS overlay DLLs are new and unsigned, so some scanners are cautious about them.
  `dinput8.dll` is the server admin's client file. `d3d9on12.dll` and `dxbcSigner.dll` are Microsoft components.
  The installer checks every file against the file list before copying it.

<details>
<summary><strong>Install by hand (advanced)</strong></summary>

Only if you prefer not to use the installer.

What is in the zip: `files/` holds 116 client files plus `Start_Glyph.cmd`, in the same layout as the game
folder. `MANIFEST.sha256` lists one SHA-256 checksum per file (117 lines). `Verify_Files.ps1` checks every file
against it (it reads only and changes nothing).

Compared with the Glyph patch channel (list 20261121152742), six files are newer test builds: `d3d9.dll`,
`d3d9_blade.ini`, `nms_overlay.ini`, `spells_us.txt`, `dbstr_us.txt` and `Resources/OnDemandResources.txt`.
`dxbcSigner.dll` is included because `d3d9on12.dll` needs it.

1. Run the normal NMS Triune patcher on your normal game folder, then close it and the game.
2. Copy your whole game folder (the one with `eqgame.exe`) and name the copy `NMS Glyph`.
3. Unzip `NMS_tester_package_2026-11-22.zip`, open its `files` folder, and copy everything inside into
   `NMS Glyph`, replacing files when asked.
4. Make a desktop shortcut to `Start_Glyph.cmd` in `NMS Glyph` (it runs `eqgame.exe patchme`) and always start
   Glyph with it.

Zip download: https://github.com/DeFluxStudios/NMS-Tester-Package/releases/download/tester-2026-11-22/NMS_tester_package_2026-11-22.zip
(481,340,706 bytes, SHA-256 `6669c3636ac3c9bc7d1e4bb88764c43e42c0004b69d553ffcafd8e87cc5a2429`).

Checking the download: In PowerShell: `Get-FileHash .\NMS_tester_package_2026-11-22.zip`.
To check every file, run `powershell -ExecutionPolicy Bypass -File .\Verify_Files.ps1` in the unzipped folder; it
ends with `All 117 files OK`.

</details>
