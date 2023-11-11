# Create a new project in mobile app

## About this task

The procedure guides you in creating new project in Design Import using the mobile app.

## Before you start

- You have completed the [Volt MX Go installation](installation.md).
- You have created your [Foundry admin account](../howto/foundryadminaccount.md).
- You have created Domino REST API.

- All users in VoltMX Go that are performing a Design Import need to be [added to the LocalKeepAdmins](https://help.hcltechsw.com/notes/12.0.2/client/sec_acl_useradd_t.html) group in the Domino Keep Configuration (KeepConfig.nsf) Access Control List for access to administrative API used by Design Import. 

- You have a configured `.nsf` file, `schema`,`scopes` and application in [Domino Rest API](https://opensource.hcltechsw.com/Domino-rest-api/references/usingdominorestapi/administrationui.html){: target="_blank"}.

    -  When you configure the `schema`, open Configured Database Form and set the **Formula for Delete Access** to `@True` in default `Mode` in all `Forms`.See [Changes in Configuration Forms of Domino Rest API](https://opensource.hcltechsw.com/Domino-rest-api/references/usingdominorestapi/administrationui.html#configure-a-form)

    -  When you configure the `schema`, open Database Form (configured) and set in `dql mode`, you must include all the fields of the `Form`. Both the `default` and `dql modes` fields must match for the form and fields to be seen as configured in the design import.

    -  When you configure the `schema`, open Database Views and set the Status to active.

    -  When you configure the `scopes`, you need a *Maximum Access Level* set to Designer or Manager. See [Scope in Domino Rest API](https://opensource.hcltechsw.com/Domino-rest-api/references/usingdominorestapi/administrationui.html#add-a-scope)

    -  When you configure your DRAPI application, it's mandatory to add `$SETUP` to return proper values.

- Launch Volt MX Go Iris and set the validation of MX Go preference.

## Procedure

### To create a new project in mobile app
        
1. On the top menu, **Project** &rarr; **New Project**.
2. On the **What do you want to start with now?** dialog, select **Native App** and click **Next**.

    ![](../assets/images/distart.png){: style="height:80%;width:80%"}

3. On the **Which device size do you want to start building for first?** dialog, select **Mobile** and click **Next**.

    ![](../assets/images/didevice.png){: style="height:80%;width:80%"}

4. Enter your **Project Name** and click **Create**.    
    ![](../assets/images/diprojectname.png){: style="height:80%;width:80%"}

5. You can see your project name in the upper-left corner of the Iris canvass.

    ![](../assets/images/diappnamemob.png){: style="height:80%;width:80%"}