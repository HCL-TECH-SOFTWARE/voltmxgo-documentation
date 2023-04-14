# Uninstall First Touch

## About this procedure

The procedure guides you in manually uninstalling First Touch in case you want to start over with the First Touch installation or you want to completely remove First Touch.

## To uninstall First Touch

To uninstall First Touch, you have to uninstall the Domino REST API configuration and also uninstall the Foundry configuration.

### To uninstall the Domino REST API configuration

1. Log in to the Domino REST API Admin console at `http://drapi.mymxgo.com/admin/ui/`. 
2. From the left navigation panel, click **Schemas**. The **Schema Management** page opens. 
3. Hover over the `firsttouchrecipesschema`, click the trash icon, and then confirm deletion. 
5. From the left navigation panel, click **Scopes**. The **Scope Management** page opens.
6. Click the `firsttouchrecipesscope`, and then click **Delete** under **Edit Scope**, Confirm the deletion.  
8. From the left navigation panel, click **Applications**. The **Application Management** page opens. 
9. Hover over the First Touch Recipes app, click the trash icon, and then confirm deletion. 

### To uninstall the Foundry configuration

1. Log in to Foundry at `http://foundry.mymxgo.com/mfconsole/`. The **Volt MX Foundry Console** opens with the **Apps** page shown by default.
2. Click the First Touch Recipes app.
3. Check the app publication status:

    1. Click the **Publish** tab.
    2. Under **APP STATUS**, check if the app is in the Published state. 
    3. If the app is in the Published state, click **UNPUBLISH** and wait for the app to be unpublished.

4. Delete the object service: 
    
    1. Select **Configure Services** &rarr; **Objects**.
    2. In the **Objects** tab, select the checkbox corresponding to `FirstTouchRecipesObj`, and then click **Delete**. 
    3. Confirm the deletion of the object service.

5. Delete the identity service:

    1. Click the **Identity** tab.
    2. Select the checkbox corresponding to `FirstTouchDRAPIOAuth`, and then click **Delete**
    3. Confirm the deletion of the identity service.

6. Delete the First Touch Recipes app:

    1. Click the **Apps** icon in the left navigation panel. The **Apps** page opens. 
    2. Hover over the menu icon in the First Touch Recipes app, and then click **Delete Application**.
    3. Confirm the deletion of the app.

7. Delete the environment:

    1. Click the **Environments** icon in the left navigation panel. The **Environment** page opens. 
    2. Check if there is a `FirstTouchEnv` environment.
    3. If there is a `FirstTouchEnv` environment, click the menu icon in the upper right
corner of `FirstTouchEnv` environment, and then click **Delete**.
    4. On the confirmation dialog, select the **Server** checkbox, and then click **Delete**.