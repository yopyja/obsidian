```powershell
# Define the script block
$scriptBlock = {
    # Get Discord program
    $discord = Get-WmiObject -Class Win32_Product | Where-Object { $_.Name -like 'Discord' }

    # Check if Discord is installed
    if ($discord) {
        # Uninstall Discord
        Write-Host "Uninstalling Discord"
        $discord.Uninstall()
    } else {
        Write-Host "Discord not found"
    }
}

# Specify the target computer
$computerName = 'TargetComputerName' # Replace this with your target computer's name

# Run the script on the remote computer
Invoke-Command -ComputerName $computerName -ScriptBlock $scriptBlock
```

