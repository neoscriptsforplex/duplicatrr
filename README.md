Here is a concise breakdown of what this PowerShell script does:

Overview
This script is an interactive Plex Media Server Database Utility designed to find, analyze, and purge lower-quality duplicate movie files directly from your local storage drives, helping you reclaim wasted disk space.

Core Functionality
Plex API Integration: It securely connects to a local Plex Media Server using a custom IP/Port configuration and an account authentication token (X-Plex-Token) to fetch library metadata.

Intelligent Duplicate Identification: The script polls your target Plex libraries specifically for item duplicates. Crucially, it tracks down files that might be unmerged (appearing as separate items on your Plex dashboard) by grouping media properties strictly by matching Title and Release Year.

Quality Sorting Logic: Within every identified duplicate group, the script dynamically evaluates each file's technical statistics (Video Resolution and Bitrate). It automatically flags the highest-quality version to KEEP and marks all lower-quality files for DELETION.

Operating Modes
When you select a media library, the script provides two ways to manage the deletions:

Single Deletion (Interactive One-by-One)

Iterates through duplicate groups one movie at a time.

Prints a clean visual comparison showing the file resolution, size, exact file path, and a [KEEPING] vs [DELETING] status.

Prompts you individually after each title to confirm if you want to permanently erase the inferior copy from your drive.

Bulk Deletion (Mass Review & Clear)

Scans the entire library and prints out a comprehensive list of all duplicate groups at once.

Calculates and summarizes the metrics at the bottom of the feed—displaying the Total Number of Files Slated for Removal and the Total Aggregate Storage Space (in GB) you will recover.

Provides a singular, double-confirmed prompt to mass delete every lower-quality file on the list in one action.

Hard Drive Safety Focus
Rather than telling Plex to delete the file (which can sometimes delete an entire un-split movie cluster completely from your dashboard), this script uses native PowerShell file-system logic (Test-Path and Remove-Item). It verifies the files physically exist on your drive and deletes the specific file paths directly off the disk, leaving your pristine, higher-quality version untouched.

Crafted by Luke Young
