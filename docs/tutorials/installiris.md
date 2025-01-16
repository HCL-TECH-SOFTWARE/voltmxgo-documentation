# For Volt MX Go v2.1

Perform a new or an upgrade installation of Volt MX Go Iris.

## Install Volt MX Go Iris 

### Before you begin

- You have downloaded the Volt Iris installer. The minimum required version is v9.5.48.   
- You have downloaded the Volt MX Go Plugin Installer. 

For more information, see [Download HCL Volt MX Go Release package](portaldownload.md#for-volt-mx-go-v21).

### Install Volt Iris

For installing Volt Iris, click the link corresponding to your installation platform and follow the installation steps. 

- [For installing Volt MX Go Iris on Mac](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_starter_install_mac/Content/Installing%20VoltMX%20Iris.html#installing)

- [For installing Volt MX Go Iris on Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_starter_install_win/Content/Installing%20VoltMX%20Iris.html#installing)

### Install Volt MX Go Plugin Installer

The procedure enables the installation of the Volt MX Go Plugin Installer, which is used for installing the Volt MX Go plugins to Volt Iris.

=== "on Mac"

    1. Navigate to the directory of the downloaded installer zip file. 
    1. Extract the zip file to get the installer file. 
    1. Double-click the installer file. The **Volt MX Go Installation Tool** window opens. 
    1. On the **Introduction**, read the details and instructions, and then click **Next**.

        ![Introduction](../assets/images/installtool1.png){: style="height:80%;width:80%"}

    1. On the **License Agreement**, read the agreement details, select the **I accept the terms of the License agreement** checkbox, and then click **Next**.

        ![License Agreement](../assets/images/installtool2.png){: style="height:80%;width:80%"}

    1. On the **Choose Install Folder**, click **Next** if you agree with the indicated default location. 

        ![Choose Install Folder](../assets/images/installtool3.png){: style="height:80%;width:80%"}
        
        !!!tip
            - If you want a different installation location, click **Choose** to select your preferred installation location, and then click **Next**.
            - If you selected a different installation location and decided to revert to the default location, click **Restore Default Folder** and then click **Next**.

    1. On the **Pre-Installation Summary**, review the details and then click **Install**.

        ![Pre-Installation Summary](../assets/images/installtool4.png){: style="height:80%;width:80%"}

    1. On the **Installing** tab, you can see the installation status.

        ![Installing](../assets/images/installtool5.png){: style="height:80%;width:80%"}

    1. On the **Install Complete**, click **Done**.

        ![Install Complete](../assets/images/installtool6.png){: style="height:80%;width:80%"}

=== "on Windows"

    1. Navigate to the folder containing the downloaded installer file. 
    1. Double-click the installer file. The **Volt MX Go Installation Tool** window opens. 
    1. On the **Introduction**, read the details and instructions, and then click **Next**.

        ![Introduction](../assets/images/wininstall1.png){: style="height:80%;width:80%"}

    1. On the **License Agreement**, read the agreement details, select the **I accept the terms of the License agreement** checkbox, and then click **Next**.

        ![License Agreement](../assets/images/wininstall2.png){: style="height:80%;width:80%"}

    1. On the **Choose Install Folder**, click **Next** if you agree with the indicated default location.

        ![Choose Install Folder](../assets/images/wininstall3.png){: style="height:80%;width:80%"} 

        !!!tip
            - If you want a different installation location, click **Choose** to select your preferred installation location or directly enter your preferred installation location in the text box, and then click **Next**.
            - If you selected a different installation location and decided to revert to the default location, click **Restore Default Folder** and then click **Next**.

    1. On the **Pre-Installation Summary**, review the details and then click **Install**.

        ![Pre-Installation Summary](../assets/images/wininstall4.png){: style="height:80%;width:80%"}

    1. On the **Installing** tab, you can see the installation status.

        ![Installing](../assets/images/wininstall5.png){: style="height:80%;width:80%"}

    1. On the **Install Complete**, click **Done**.

        ![Install Complete](../assets/images/wininstall6.png){: style="height:80%;width:80%"}

### Install Volt MX Go Plugin

The procedure enables the installation of Volt MX Go plugins to Volt Iris to enable Volt MX Go features.

!!!warning "Important"
    Installing the MX Go plugins into your workspace requires that your workspace contains a `pluginsInfo.json` file in the `.plugins` directory. Otherwise, an installation error occurs. To create the `pluginsInfo.json` file in the `.plugins` directory, [create a Desktop Web App project](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/CreateKRAProject.html#create-a-volt-mx-iris-reference-architecture-project) with Volt Iris in your workspace, and then [run Live Preview](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/LivePreview.html#preview-your-web-app-with-iris). Running the Live Preview creates the `pluginsInfo.json` file. 

=== "on Mac"

    1. Click **Finder** in the **Dock**, click **Applications** in the sidebar of the **Finder** window, then double-click the **Volt MX Go Plugin Installer** app.
    
        Or

        Click **Launchpad** in the **Dock**, type *Volt MX Go Plugin Installer* in the search field at the top of **Launchpad**, and click the app to open it.

        A new terminal opens showing the available options.

        ![Installation options](../assets/images/plugintool.png){: style="height:80%;width:80%"} 

    2. Enter **4** to install Volt MX Go plugins and press **return**.
    3. Specify a Volt Iris workspace by entering the number corresponding to a detected workspace or enter the full path to the workspace, then press **return**. 
    4. Specify the Iris application installation directory by entering the number corresponding to your installation or enter the full path to your Iris installation directory, then press **return**. 

        You get a confirmation statement about the completion of the installation of the plugins. 
    
    5. Close the terminal.   

=== "on Windows"

    1. Select **Start**, scroll through the alphabetical list, and select **Volt MX Go Plugin Installer**. Depending on your OS, you might need to select **All apps**, scroll through the alphabetical list, and click **Volt MX Go Plugin Installer**.

        OR

        Double-click the **Volt MX Go Plugin Installer** shortcut on your desktop if available. 

        A Command Prompt window opens showing the available options.

        ![Installation options](../assets/images/plugintool.png){: style="height:80%;width:80%"}

    2. Enter **4** to install Volt MX Go plugins and press **Enter**.
    3. Specify an Iris workspace by entering the number corresponding to a detected workspace or enter the full path to the workspace, then press **Enter**. 
    4. Specify the Iris application installation directory by entering the number corresponding to your installation or enter the full path to your Iris installation directory, then press **Enter**. 

        You get a confirmation statement that the plugins have been installed. 

    5. Press **Enter** to close the Command Prompt window.

## Upgrade Volt MX Go Iris 

Upgrades Volt MX Go Iris from Volt MX Go v2.0.4 to Volt MX Go v2.1.

### Before you begin

- You have downloaded the Volt Iris installer - v9.5.48 or later. For more information, see [Download HCL Volt MX Go Release package](portaldownload.md#for-volt-mx-go-v21).

- You have installed the Volt MX Go Plugin Installer. For more information, see [Install Volt MX Go Plugin Installer](#install-volt-mx-go-plugin-installer).

### Upgrade Volt Iris

To upgrade, install the latest version of Volt Iris. Click the link corresponding to your installation platform and follow the installation steps. 

- [For installing Volt Iris on Mac](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_starter_install_mac/Content/Installing%20VoltMX%20Iris.html#installing)

- [For installing Volt Iris on Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_starter_install_win/Content/Installing%20VoltMX%20Iris.html#installing)

!!!note "Important"
    Make sure to use the same Workspace Folder you used for your Volt MX Go Iris v2.0.4 installation to access all the projects you worked on using Volt MX Go Iris v2.0.4.  

### Install Volt MX Go Plugin

Install the Volt MX Go plugins to Volt Iris to enable Volt MX Go features. For the installation steps, see [Install Volt MX Go Plugin](#install-volt-mx-go-plugin).

### Important consideration

Updates for Volt Iris are released regularly, and you will receive an update notification on your Volt Iris instance that prompts you to update to the latest version of Volt Iris. These updates are major release versions, service packs, and fix packs.

**You must reinstall the Volt MX Go plugins every time you update Volt Iris**.

For more information on updating Volt Iris, click the link corresponding to your installation platform: 

- [For updating Volt Iris on Mac](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_starter_install_mac/Content/Upgrade.html)

- [For updating Volt Iris on Windows](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_starter_install_win/Content/Upgrade.html)






   