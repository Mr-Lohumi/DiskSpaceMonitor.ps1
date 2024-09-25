# DiskSpaceMonitor.ps1

Here’s the updated **README.md** file for your **DiskSpaceMonitor.ps1** script:

---

# Disk Space Monitoring Script

## SYNOPSIS

This PowerShell script monitors disk space on multiple servers or workstations and sends email alerts when free space falls below a specified threshold.

## DESCRIPTION

The script retrieves disk space information from the specified servers and checks if the free space on each logical disk is below a user-defined threshold. If a disk has insufficient free space, an email alert is sent to notify the administrator. It supports secure SMTP with a custom port and uses SSL for secure email communication.

## Features

- Monitor multiple servers or workstations
- Customizable free space threshold (in GB)
- Sends email alerts for low disk space
- Secure SMTP configuration with custom ports
- Easily scheduled using Task Scheduler for automated monitoring

## Requirements

- PowerShell (version 5.0 or later)
- SMTP server details for sending email alerts
- Network access to the servers or workstations being monitored

## Parameters

- **$servers**: List of server or workstation names to monitor for disk space.
- **$threshold**: Minimum free disk space (in GB) before an alert is triggered.
- **$smtpServer**: SMTP server used for sending email alerts.
- **$smtpPort**: SMTP server port (e.g., 587 for SSL).
- **$smtpCredential**: Credentials for authenticating with the SMTP server (set with `Get-Credential`).

## Example

This is how the script would typically run:

```powershell
.\DiskSpaceMonitor.ps1
```

This command will check the disk space on the servers listed in the script and send an email alert if any of the drives have less free space than the defined threshold.

## Setup and Usage

1. **Edit the Script**:
    - Update the `$servers` array with the server names you want to monitor.
    - Adjust the `$threshold` variable to set the free space limit in GB.
    - Configure SMTP settings, including server, port, and email addresses.

2. **Run the Script Manually**:
    You can execute the script directly in PowerShell to monitor disk space immediately:

    ```powershell
    .\DiskSpaceMonitor.ps1
    ```

3. **Schedule the Script**:
    You can schedule the script using Task Scheduler for automated execution:

    - Create a batch file (`RunDiskSpaceMonitor.bat`) to run the script:
        ```batch
        @echo off
        PowerShell.exe -ExecutionPolicy Bypass -File "C:\Path\To\Your\DiskSpaceMonitor.ps1"
        ```

    - Open Task Scheduler and set up a new task with triggers for the script to run at a regular interval (e.g., daily or weekly).

## Customization

- **Add More Servers**: Modify the `$servers` array to include more machines.
- **Change Threshold**: Set the `$threshold` variable to define the minimum free disk space in GB.
- **SMTP Settings**: Update `$smtpServer`, `$smtpPort`, `$from`, `$to`, and `$smtpCredential` to fit your email server setup.

## Email Alert Example

An example alert message sent when a drive falls below the free space threshold:

```
Warning: Server1 - Drive C: has only 15.32 GB free out of 100.00 GB.
```

## License

This script is licensed under the [MIT License](LICENSE).

---

This **README.md** provides a clear overview, instructions, and examples for anyone looking to use or modify the script. You can save this as `README.md` in your repository’s root directory. Let me know if you need any more changes!
