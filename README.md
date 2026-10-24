# Paver_Firmware

Released firmware for the LED pavers, ready to download. The phone app reads
this repo to see whether a paver needs an update. Source code stays in the
private repos (MPLAB_Paver_PIC32_App, MPLAB_Paver_PIC18_App); only finished
release files go here.

## What's here

| File | What it is |
|---|---|
| `latest.json` | The newest version of each program and where its file is. The phone app reads this. |
| `pic32/PIC32_App_vX.Y.Z.hex` | PIC32 application, as built by MPLAB X (`dist/default/production/PIC32_App.X.production.hex`). |
| `pic18/PIC18_App_vX.Y.Z.img` | PIC18 application as an MDFU image (built from the `.hex` by the Python program, the same image its Bootload PIC18 tab sends). |

The phone downloads `latest.json` from
`https://raw.githubusercontent.com/brungsmc/Paver_Firmware/main/latest.json`
and the files next to it.

## Publishing a new release

1. In the program's own repo: set `APP_VERSION`, test on the board, merge to
   main and tag the version (for example `v2.5.0`).
2. Copy the release file in here with the version in its name:
   - PIC32: `PIC32_App.X.production.hex` -> `pic32/PIC32_App_v2.5.0.hex`
   - PIC18: make the image with the Python program, save it as
     `pic18/PIC18_App_v2.6.0.img`
3. Change that program's `version` and `file` in `latest.json`.
4. Commit ("PIC32 v2.5.0") and push.

Keep the older files: they let you go back to a previous version if a new
one has a problem.
