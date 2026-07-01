<img width="2816" height="1536" alt="Duplicatrr Logo Transparent" src="https://github.com/user-attachments/assets/a6a22b78-aca2-4f0e-9171-32f69bd846f2" />


A smart, interactive PowerShell utility that connects to your Plex Media Server API to find duplicate movies, compare their quality metrics, and permanently purge the inferior versions directly from your local storage drives to reclaim wasted disk space.

Unlike standard Plex-based deletion—which can sometimes accidentally wipe out an entire un-split movie cluster—this tool identifies exactly which file is the bottleneck and removes only the low-quality file path directly from the file system, leaving your pristine high-quality copy untouched.

🚀 Features
🔍 Smart Detection & Cross-Grouping
Unmerged Duplicate Matching: Automatically groups media by matching Title and Release Year. This ensures that even if duplicates are sitting as completely separate entries on your Plex dashboard, the script will still catch them.

Deep Metadata Inspection: Polls the deepest layout structures of the Plex API to extract exact file resolutions, bitrates, file sizes, and absolute storage track paths.

📊 Automated Quality Sorting
Smart Hierarchy: Automatically evaluates every file inside a duplicate cluster based on Video Resolution and Bitrate.

Clear Tagging: Intuitively flags the highest-quality file as [KEEPING] and isolates the inferior versions as [DELETING].

🛠 Dual Processing Modes
Mode 1: Single Deletion (Interactive) * Loops through detected duplicates one movie at a time.

Shows a side-by-side comparison of the files and prompts you individually before wiping anything from the disk.

Mode 2: Bulk Deletion (Mass Clear)

Scans and prints a comprehensive roster of all library duplicates in one scrolling feed.

Storage Space Tally: Aggregates the raw byte sizes of all files flagged for removal and outputs a final tally of the Total Files and Total Gigabytes (GB) to be saved right before giving you a double-confirmed option to mass delete.

🔒 Direct Storage Safety
File-System Level Execution: Bypasses Plex deletion APIs in favor of native PowerShell Remove-Item commands.

Path Validation: Integrates strict Test-Path logic to verify a file's physical presence and connectivity (e.g., handling network drops) before executing any destructive logic.

🛠 Setup & Usage
Open the script and configure your environment variables at the top:

PowerShell
$PlexUrl   = "http://127.0.0.1:32400"
$PlexToken = "YOUR_PLEX_TOKEN_HERE"
Run the script in an elevated PowerShell console.

Select your target media library from the dynamically generated menu.

Choose between Single or Bulk deletion mode to start reclaiming your storage space!

⚠️ Note: After executing deletions, your lower-quality files will be immediately erased from the disk. Plex will reflect a red trash icon on those items until your server runs its next scheduled library scan or you manually click "Scan Library Files" on your dashboard.
