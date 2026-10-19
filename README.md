# Capsulla download tests

Harmless files for checking that the Capsulla extension stops downloads of
restricted file types. Every file in `files/` is one line of plain text with
an executable's extension: nothing here runs.

## What should happen

| File | Default rule that blocks it (MIME type) | Extension rule |
| --- | --- | --- |
| `test.exe` | `application/x-msdownload`, `application/x-dosexec`, `application/vnd.microsoft.portable-executable`, `application/x-msdos-program` | `.exe` |
| `test.dll` | same as `.exe` | `.dll` |
| `test.msi` | `application/x-ms-installer`, `application/x-msdownload` | `.msi` |
| `test.dmg` | `application/x-apple-diskimage` | `.dmg` |
| `test.lnk` | `application/x-ms-shortcut` | `.lnk` |
| `test.scr` | `application/x-scr` | `.scr` |
| `test.sh` | `application/x-sh`, `text/x-sh`, `application/x-shellscript` | `.sh` |
| `test.bat` | `application/x-bat` | `.bat` |
| `test.cmd` | `application/x-cmd` | `.cmd` |
| `test.ps1` | `application/x-powershell` | `.ps1` |
| `test.jar` | `application/java-archive`, `application/x-java-archive` | `.jar` |
| `test.iso` | `application/x-iso9660-image` | `.iso` |
| `allowed.txt` | none: the control, it should download | — |

A blocked download is cancelled, the page shows "File download blocked due
to restricted file type: …", and Audit & Events in the console gets a
`block` / `download` event.
