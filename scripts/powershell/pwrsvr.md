```powershell
# Create a new power plan called "CustomPlan" using the Balanced power plan as a template
$planGuid = (powercfg /create /duplicatescheme 381b4222-f694-41f0-9685-ff5bb260df2e CustomPlan).Split(':')[1].Trim()

# Set the "Turn off the display" setting to 15 minutes (900 seconds)
powercfg /setacvalueindex $planGuid SUB_VIDEO VIDEOIDLE 900

# Set the "Put the computer to sleep" setting to 60 minutes (3600 seconds)
powercfg /setacvalueindex $planGuid SUB_SLEEP STANDBYIDLE 3600

# Set the new plan as the active plan
powercfg /setactive $planGuid

# Invoke Remotely

# Define the script block
$scriptBlock = {
    # Create a new power plan called "CustomPlan" using the Balanced power plan as a template
    $planGuid = (powercfg /create /duplicatescheme 381b4222-f694-41f0-9685-ff5bb260df2e CustomPlan).Split(':')[1].Trim()

    # Set the "Turn off the display" setting to 15 minutes (900 seconds)
    powercfg /setacvalueindex $planGuid SUB_VIDEO VIDEOIDLE 900

    # Set the "Put the computer to sleep" setting to 60 minutes (3600 seconds)
    powercfg /setacvalueindex $planGuid SUB_SLEEP STANDBYIDLE 3600

    # Set the new plan as the active plan
    powercfg /setactive $planGuid
}

# Specify the target computer
$computerName = 'TargetComputerName' # Replace this with your target computer's name

# Run the script on the remote computer
Invoke-Command -ComputerName $computerName -ScriptBlock $scriptBlock
```
