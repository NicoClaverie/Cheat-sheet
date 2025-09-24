### To uninstall the Agent:

This process should be used instead of the SentinelOne Cleaner utility. Using the new Stainless Installer (SentinelOneInstaller.exe), perform the below steps to "Clean only" the impacted endpoint. This action uninstalls the SentinelOne Agent and does not reinstall one automatically after reboot.

Note: In normal mode - you only need the passphrase. In safe mode - you do not need the passphrase. In both cases the site token is optional.

1.  Follow all steps in the Prerequisites section.

2.  Open the command line locally on the impacted endpoint.

3.  (Optional) If you have the passphrase, run:

    ```
    SentinelOneInstaller.exe -c -k "PASSPHRASE" -t sitetoken
    ```

    Example:

    ```
    SentinelOneInstaller_windows_64bit_v22_1_5_13825.exe -c -k "PASSPHRASE" -t sitetoken
    ```

    Replace `<sitetoken>` with the site token you got from the Prerequisites section, and replace PASSPHRASE with the passphrase you generated.

4.  If Agent anti-tampering is disabled, the passphrase is unavailable. Run:

    ```
    SentinelOneInstaller.exe -c -t sitetoken
    ```

    Example:

    ```
    SentinelOneInstaller_windows_64bit_v22_1_5_13825.exe -c -t sitetoken
    ```

    Replace `<sitetoken>` with the site token you got from the Prerequisites section.

5.  Get the return (exit) code. Run:

    * From CMD:
        ```
        echo %errorlevel%
        ```
    * From PowerShell:
        ```
        $LastExitCode
        ```

6.  Review Return Codes After Installing or Updating Windows Agents to determine the potential next action.
