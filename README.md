# psMouseMover
Create a shortcut with a hotkey and you can have the mouse randomly move every 5 seconds to stop computer locking

This PowerShell script (one liner) subtly moves the mouse cursor in small, random increments every 5 seconds. It is particularly useful for preventing screensavers, sleep modes, or automatic logouts from activating due to inactivity while still keeping cursor movements minimal and less intrusive.

# How It Works:

The script calculates new cursor positions based on the current position by adding a small, random offset between -10 and +10 pixels in both the X and Y directions. It ensures that the cursor does not move off-screen using boundary checks.

# Usage:

To use this script, follow these instructions:

Open Command Prompt: Press Win + R, type cmd, and press Enter.

# Execute the Command:

```powershell
powershell -ExecutionPolicy Bypass -Command "Add-Type -AssemblyName System.Windows.Forms; while ($true) { $currentPos = [System.Windows.Forms.Cursor]::Position; $newX = [Math]::Max(0, [Math]::Min([System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Width, $currentPos.X + (Get-Random -Minimum -10 -Maximum 11))); $newY = [Math]::Max(0, [Math]::Min([System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Height, $currentPos.Y + (Get-Random -Minimum -10 -Maximum 11))); [System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($newX, $newY); Start-Sleep -Seconds 5 }"
```

This command bypasses the default PowerShell execution policy to allow the script to run without interruptions, and it continuously adjusts the cursor position within the bounds of the screen.

# Features:

Minimal Cursor Movement: Moves the cursor subtly, reducing the likelihood of interrupting active work.
Boundary Safe: Ensures the cursor does not move outside the visible area of the screen.
Continuous Operation: Runs indefinitely until manually stopped.

**Stopping the Script**

To stop the script, you can either:

Close the Command Prompt window where the script is running.
Press Ctrl + C within the Command Prompt to interrupt the script.

**Requirements**

Windows operating system with PowerShell support.

System.Windows.Forms assembly available on your system (typically available by default on Windows).

**Disclaimer**

This script is intended for personal use and should not be used to circumvent company policies or other administrative controls regarding workstation management. Always use responsibly and with permission where required.

