# Check installation status of VoltScript plugins

!!!note
    The information in this topic applies starting with the VoltScript v10 release.

## About this task

Guides you in checking the installation status of VoltScript plugins to Volt Foundry.

## Before your begin

You have installed the VoltScript Plugin Installer. For more information, see [Install VoltScript Plugin Installer](../install/voltscript.md#install-voltscript-plugin-installer).

## Procedure

### Check installation status of VoltScript plugins in Volt Foundry

=== "on Linux"

    1. Open Terminal.
    1. Go to the directory where you installed the VoltScript Plugin Installer.
    2. Run the VoltScript Plugin Installer by entering the following command and press **Enter**

        `./<installerfilename>`

        The installation tool opens on the Terminal.

    3. Enter **3** to check installation status of VoltScript plugins and press **Enter**.
    4. Specify the Tomcat WebApps directory by entering the number corresponding to your installation or enter the full path to your Tomcat WebApps directory, and then press **Enter**.
        
        You get a confirmation statement on whether VoltScript plugins are installed in the specified Tomcat WebApps directory.

    6. Enter **7** and press **Enter** to exit the installation tool. 

=== "on Windows"

    1. Select **Start**, scroll through the alphabetical list, and select **VoltScript Plugin Installer**. Depending on your OS, you might need to select **All apps**, scroll through the alphabetical list, and click **VoltScript Plugin Installer**.

        OR

        Double-click the **VoltScript Plugin Installer** shortcut on your desktop if available. 

        A Command Prompt window opens.

    2. Enter **3** to check the installation status of VoltScript plugins and press **Enter**.
    3. Specify the Tomcat WebApps directory by entering the number corresponding to your installation, or enter the full path to your Tomcat WebApps directory, then press **Enter**. 

        You get a confirmation statement on whether VoltScript plugins are installed in the specified Tomcat WebApps directory. 

    5. Press **Enter** to close the Command Prompt window.

## Expected result

You have checked the installation status of the VoltScript plugins in Volt Foundry.

## Additional information

To check the installation status of VoltScript Runtime, use the **Check the install status of the VoltScript Runtime Zip** option and then press **Enter**. A confirmation statement is shown on whether VoltScript Runtime is installed or not.

For more information on VoltScript Runtime, see the [VoltScript documentation](https://help.hcl-software.com/docs/voltscript/early-access/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"}.
