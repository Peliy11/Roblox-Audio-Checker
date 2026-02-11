# Roblox Audio Checker

This Python script checks the availability of Roblox audio files and provides clickable links to them.

## Features

- ✅ Parses audio lists in the Roblox Lua table format
- ✅ Extracts audio IDs from various formats (rbxassetid://, HTTP URLs, etc.)
- ✅ Checks if each audio is available or removed
- ✅ Generates direct links to Roblox library pages
- ✅ Creates a detailed results report
- ✅ Shows status with visual indicators (✓/✗)

## Requirements

Install the required package:

```bash
pip install requests
```

## Usage

Simply run the script and enter your file path when prompted:

```bash
python roblox_audio_checker.py
```

The script will ask:
```
Which file:
```

Enter the path to your audio list file:
```
Which file: C:\Users\YourName\Documents\audio_list.txt
```

Or on Mac/Linux:
```
Which file: /home/username/audio_list.txt
```

The script will:
- Check all audios in the file
- Generate a results file (`audio_check_results.txt`) in the same directory as your input file
- Display real-time progress in the console

## Input Format

The script accepts Roblox Lua table format like this:

```lua
[1] = {
    [NAME] = Audio Name
    [ID] = rbxassetid://123456789
}
[2] = {
    [NAME] = Another Audio
    [ID] = http://www.roblox.com/asset/?id=987654321
}
```

## Output

The script will:

1. **Print to console**: Real-time status updates for each audio
2. **Generate a results file**: `audio_check_results.txt` with:
   - Summary statistics (total, available, unavailable)
   - Detailed results for each audio
   - Direct links to Roblox library pages

## Example Output

```
[1] Symphony No.7 In A-major Op.92 @ Allegretto
    ID: 1848043853
    Status: UP ✓ (Available)
    Link: https://www.roblox.com/library/1848043853

[2] (Removed for copyright)
    ID: 6404233023
    Status: DOWN ✗ (Content Deleted)
    Link: https://www.roblox.com/library/6404233023
```

## Status Indicators

- **UP ✓**: Audio is available on Roblox
- **DOWN ✗**: Audio is unavailable (deleted, removed, or doesn't exist)

## Rate Limiting

The script includes a 0.5-second delay between checks to be respectful to Roblox servers. You can adjust this in the code if needed.

## Notes

- The script checks the actual Roblox website to verify availability
- Network connection is required
- Some audios may be region-restricted or require login to view
- Built-in Roblox sounds (rbxasset://) cannot be checked and will show as "Invalid ID"

## Troubleshooting

**Network errors**: Make sure you have an active internet connection.

**Rate limiting**: If you get too many errors, try increasing the `sleep()` delay in the script.

**Parsing errors**: Ensure your audio list file matches the expected Lua table format.
