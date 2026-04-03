# CloudCompare Notes

List of useful CLI commands

Run the following in CloudCompare CLI (actually just CMD in windows)

<pre>"C:\Program Files\CloudCompare\CloudCompare.exe" -SILENT -AUTO_SAVE OFF -O *.las -MERGE_CLOUDS -SAVE_CLOUDS FILE merged.las</pre>

CloudCompare CLI cannot detect wildcards to batch file below has to be used to merge las files

<pre>
@echo off
setlocal enabledelayedexpansion

REM --- Set CloudCompare path ---
set CC="C:\Program Files\CloudCompare\CloudCompare.exe"

REM --- Build list of -O "file.las" arguments ---
set FILES=
for %%f in (*.las) do (
    set FILES=!FILES! -O "%%f"
)

echo Merging the following LAS files:
echo %FILES%
echo.

REM --- Run CloudCompare merge ---
%CC% -SILENT -AUTO_SAVE OFF -C_EXPORT_FMT LAS %FILES% -MERGE_CLOUDS -SAVE_CLOUDS FILE "merged.las"

echo.
echo Merge complete.
pause
</pre>
