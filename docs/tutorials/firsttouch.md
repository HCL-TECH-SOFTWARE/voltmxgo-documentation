# First Touch tutorial

This tutorial guides you on accessing and running the First Touch app in Volt MX Foundry to view and explore a sample app. 

## Before you start

- You have completed the [Volt MX Go installation](installation.md).
- You have created your [Foundry admin account](../howto/foundryadminaccount.md).
- You have noted the following Domino REST API details:

    - Server URL: `http://drapi.mymxgo.com` 
    - username: `mxgo admin`
    - password: `password`

## Log in to Volt MX Foundry

1. Open `http://foundry.mymxgo.com/mfconsole/` in your browser. 
2. Enter your username and password on the **Sign in to your account** page. 
3. Click **Sign In**.  

   The **Volt MX Foundry Console** opens with the **Apps** page shown by default. The **VOLT MX GO | First Touch** banner is shown on the **Apps** page.  

   ![First Touch banner](../assets/images/firsttouch.png)

## Run First Touch

1. On the **Apps** page, click **GET STARTED**.

    OR

    Select **VOLT MX GO First Touch** from the side panel. 

    ![Volt MX GO First Touch ](../assets/images/firsttouchsidepanel.png)

2. On the **Welcome to Volt MX Go** dialog, enter the following information:
    
    - URL of your Domino REST API server
    - Domino REST API administrator user ID and password

3. Click **Next**. An installation progress dialog appears. 

4. Wait for the completion of the installation. Once completed, a **Congratulations!** dialog appears confirming the successful installation of the First Touch app and the verification of the connection to the Domino database via Domino REST API. 
 
5. On the **Congratulations!** dialog, click **Launch**. 
    
   You can now view and explore the First Touch sample recipe app Foundry configuration.  
 

The First Touch sample recipe app is a Domino app written using Volt MX Go. It is automatically configured to use Domino REST API for both the Identity Service and the Object Service. For more information, see [Identity Service](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_user_guide/Content/Identity.html) and [Object Service](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_user_guide/Content/Objectservices.html) in the [HCL Volt MX Documentation](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/index.html). 