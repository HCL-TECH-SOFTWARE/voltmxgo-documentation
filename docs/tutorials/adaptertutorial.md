# Domino Adapter tutorial

The tutorial guides you in creating an app in Foundry and connecting the app to your Domino database as an endpoint via the Domino REST API, and testing the GET and POST methods.

## Before you start

- You have completed the [Volt MX Go installation](installation.md).
- You have created your [Foundry admin account](../howto/foundryadminaccount.md). 
- You have noted the following Domino REST API details:

    - Server URL: http://drapi.mymxgo.com 
    - username: mxgo admin
    - password: password

- You have added and configured a schema and a scope in the Domino REST API. 
- Your schema should have a configured form with a `dql` mode similar to the `default` mode. 

## Log in to Volt MX Foundry

1. Open `http://foundry.mymxgo.com/mfconsole/` in your browser.  
2. Enter your username and password on the **Sign in to your account** page.
3. Click **Sign In**.  

   The **Volt MX Foundry Console** opens with the **Apps** page shown by default. 

## Create an app in Volt MX Foundry

1. On the **Apps** page, click **Add New**. 
2.	A new app is added, and you are directed to the **Configure Services** &rarr; **Identity** page of the new app. 
3.	Click the **Edit App Name** icon to give a unique name to your app.

!!!tip
    For more information, see [How to Add Applications](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_user_guide/Content/Adding_Applications.html) in the HCL Volt MX documentation. 

## Configure an Identity service

1. On the **Identity** page, enter a name for the identity service in the **Name** text box.
2. From the **Type of Identity** drop-down list, select `OAuth2.0`.
3. Under **Provider Details**:
    
    1. Select `Authorization Code` in the **Grant Type** dropdown list.
    2. Enter the Domino REST API server URL concatenated with `/oauth/authorization` in the **Authorize Endpoint** field.

        Example: `[Domino REST API server URL]/oauth/authorization`

    3. Enter the Domino REST API server URL concatenated with `/oauth/token` in the **Token Endpoint** field.

        Example:  `[Domino REST API server URL]/oauth/token`

    4. In the **Callback URL** text box, click **Copy**. <br/> You need the callback URL when configuring your app in Domino REST API. 
    5. Enter `$DATA` in the **Scope** text box.

![](../assets/images/identityproviderdetails.png)

5.	Under **Client Details**:

    1. Select **Basic authentication** as the **Client Assertion Type**. 
    2. Enter the App ID of your app in Domino REST API in the **Client ID** text box.
    3. Enter the App Secret of your app in Domino REST API in the **Client Secret** text box.

    !!!tip
        The App ID and App Secret are generated when you add an app in Domino REST API. For more information, see [Using Web UI](https://opensource.hcltechsw.com/Domino-rest-api/references/usingdominorestapi/administrationui.html) in the Domino REST API documentation.  

6.	Under **Advanced**:
    
    1. Select **Form Param** as the **Client Authentication Scheme**. 
    2. Use the default for the rest of the settings.

7.	Click Save.

!!!tip
    You can click **Test Login** to verify if the configured Identity service works. If the configuration works, a Domino REST API login dialog opens where you need to enter your Domino REST API administrator username and password. After successful login, click **Allow** in the  Domino REST API **Access consent required** dialog. 

## Add an environment 

1.	On the left pane on the **Volt MX Foundry Console**, click **Environments**.
2.	On the **Environments** page, click **Add New**. The **Add a New Environment** dialog opens. 
3.	In the **Environment Name** text box, enter an environment name.

    !!!note
        Your environment name can only contain letters, numbers, and hyphens (-). A hyphen can't appear at the beginning or at the end of a name. A number can't appear at the beginning of a name. A name should be a minimum of three characters and a maximum of 20 characters long.

4.	In the **Server** tab, enter the URL of your Volt MX Foundry in the **URL** text box.
    The URL format is: <http or https>://<server_host>:<server_port>
    For example, URL: http://mbaastest30.hcl.net:53504
5.	Click **Test Connection** to verify that the entered URL is correct. If the test is successful, a check mark appears beside the **Server** tab.
6. Click **Save**.

    ![](../assets/images/addenvironment.png)

## Configure an Object service

1. On the left pane on the **Volt MX Foundry Console**, click **Apps**.
2. On the **Apps** page, select the app you created. 
3. Go to **Configure Services** &rarr; **Objects**, and then click **Configure New**.
4. Enter the object service name in the **Name** text field. For example, `EmployeeModelSchema`.
5. Select **HCL Domino** under **Business Adapters** for the **Endpoint Type**.
4. Set the **Metadata Security Level** to **Authenticated App Users** to restrict the download of object service metadata to users that have successfully authenticated using the Identity Service.
5.	Under **Connection Parameters**:

    1. Enter the Domino REST API server URL in the **Keep API Base URL** text field.
    2. Enter a value in the **Connection Timeout text** field. By default, the value is set 30.
     
    !!!tip
        To test the connection parameters, select the environment you added from the **Select an Environment** drop-down list and then click **Test Connection**. You will see a "Connection Successful" message if the configured connection parameters are correct. 

6.	Under **Authentication**: 

    1. Select the **Use Existing Identity Provider** radio button.
    2. Select the identity service you configured in the drop-down list.
    
    !!!tip
        To test the authentication, click **Test Login**. If the configuration works, a Domino REST API login dialog opens where you need to enter your Domino REST API administrator username and password. After successful login, click **Allow** in the Domino REST API **Access consent required** dialog. A Test Login Successful message is then displayed. 

7.	Click **Save and Configure**.

## Configure a data model

1. On the **Data Model** tab, click **Generate**.
2. In the Domino REST API **Access consent required** dialog, click **Allow**. The **Import Objects from Backend** dialog appears. 
3. Expand the scope, **Forms**, and **View Entities**.
4. Select the checkboxes corresponding to the forms and view entities you want to import, and then click **Next**. The **Backend Object Name** and **Data Model Object Name** of the selected forms and view entities are shown. 

    !!!tip
        You can change the data model object names of the selected forms and view entities.

5. Click **Generate**. The forms and view entities are now added to the **Data Model**. 

## Testing the GET method by viewing a record

!!!note
    For every action on the Mappings tab, there may be a Domino REST API authorization prompt. Enter your administrator credentials to log in to Domino REST API and click **Allow** when the Domino REST API **Access consent required** dialog appears.

1. Click the **Mapping** tab, and then click the expand icon corresponding to a data model name to display a list of available methods.
2. From the list, click GET. 
4. Expand the **base mapper1**, and then select the **Test** tab.
5. Click Send.
6. The records are displayed on the Response console. Click Save after viewing. 

## Testing the POST Method by creating a record

!!!note
    For every action on the Mappings tab, there may be a Domino REST API authorization prompt. Enter your administrator credentials to log in to Domino REST API and click **Allow** when the Domino REST API **Access consent required** dialog appears.

1. Click the **Mapping** tab, and then click the expand icon corresponding to a data model name to display a list of available methods.
2. From the list, click POST to create a record.
3. Expand the **base mapper1**, and then select the **Test** tab.	
4. On the **Request Payload**, the fields of the data model should be displaying.
5. Beside the fields, input the value, then click **Send**. The ID of the record is displayed on the **Response** console after the successful insertion of the record.
6. Save the ID for updating or deleting the record using PUT or DELETE method, respectively.
