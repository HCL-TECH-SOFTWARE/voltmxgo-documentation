# Uninstall VoltScript plugins

!!! note

    The information in this topic applies starting with the Volt MX Go v10 release.

## About this task

Guides you in uninstalling VoltScript plugins from Volt Foundry.

## Before your begin

You have installed the VoltScript Plugin Installer. For more information, see [Install VoltScript Plugin Installer](../install/voltscript.md#install-voltscript-plugin-installer).

## Procedure

### Uninstall VoltScript plugins from Volt Foundry

=== "on Linux"

    1. Open Terminal.
    1. Go to the directory where you installed the VoltScript Plugin Installer.
    2. Run the VoltScript Plugin Installer by entering the following command and press **Enter**

        `./<installerfilename>`

        The installation tool opens on the Terminal.

    3. Enter **2** to uninstall VoltScript plugins and press **Enter**.
    4. Specify the Tomcat WebApps directory by entering the number corresponding to your installation or enter the full path to your Tomcat WebApps directory, and then press **Enter**.

        You get a confirmation statement that the plugins have been uninstalled.

    6. Enter **7** and press **Enter** to exit the installation tool. 

=== "on Windows"

    1. Select **Start**, scroll through the alphabetical list, and select **VoltScript Plugin Installer**. Depending on your OS, you might need to select **All apps**, scroll through the alphabetical list, and click **VoltScript Plugin Installer**.

        OR

        Double-click the **VoltScript Plugin Installer** shortcut on your desktop if available. 

        A Command Prompt window opens.

    2. Enter **2** to uninstall VoltScript plugins and press **Enter**.
    3. Specify the Tomcat WebApps directory by entering the number corresponding to your installation, or enter the full path to your Tomcat WebApps directory, then press **Enter**. 

        You get a confirmation statement that the plugins have been uninstalled. 

    5. Press **Enter** to close the Command Prompt window.

!!! tip

    Make sure to restart Volt Foundry to completely implement the changes.

## Expected result

You have uninstalled VoltScript plugins from Volt Foundry.

## Additional information

If you have installed VoltScript Runtime and now wants it removed, use the **Uninstall VoltScript Runtime Zip** option in the VoltScript Plugin Installer and then press **Enter**.
