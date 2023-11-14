# Generate CRUD forms for Object Service

## About this task

The procedure guides you in generating CRUD forms and associated form-navigation links for an Object Service after linking your Volt MX Iris project to your Volt MX Foundry app with a defined Object Service data model. 

## Before you start

- You have [created an app in Foundry](https://opensource.hcltechsw.com/voltmxgo-documentation/tutorials/adaptertutorial.html#create-an-app-in-volt-mx-foundry).
- You have [configured an Identity Service for your app in Foundry](https://opensource.hcltechsw.com/voltmxgo-documentation/tutorials/adaptertutorial.html#configure-an-identity-service).
- You have [added an environment for your app](https://opensource.hcltechsw.com/voltmxgo-documentation/tutorials/adaptertutorial.html#add-an-environment).
- You have [configured an Object Service for your app in Foundry](https://opensource.hcltechsw.com/voltmxgo-documentation/tutorials/adaptertutorial.html#configure-an-object-service).
- You have [configured the data model for the Object Service](https://opensource.hcltechsw.com/voltmxgo-documentation/tutorials/adaptertutorial.html#configure-a-data-model).
- You have [created a project in Iris](https://opensource.hcltechsw.com/voltmxgo-documentation/tutorials/designimport.html#create-a-new-project).

## Procedure

1. Open Volt MX Go Iris. When the **Sign-in to your account** page appears, close it by clicking the Volt Iris home icon.

    ![Volt MX Go Iris icon](../assets/images/irisicon.png)

2. Check Foundry settings.
    1. Go to **Preferences**.
        
        For Windows, select **Edit** &rarr; **Preferences**. 
        
        For Mac, depending on your macOS, select Volt MX Iris &rarr; **Preferences** or **Settings**. 

    2. On the **Volt MX Go Iris Preferences** dialog, click **Volt MX Go Foundry**.
    3. On the **Volt MX Go Foundry** tab, enter your Foundry URL in the **Foundry URL** text box, and then click **Validate**.
        
        You should see the “Validation Successful” message at the top of the dialog.
    
    4. Click **Done**.

3. Log in to Volt MX Go Iris.
    1. Click **Login** on the upper right corner of the Volt MX Go Iris screen.
    2. Enter your email and password for Foundry on the **Sign in to your account** page.
    3. Click **Sign In**. Your username appears next to the profile icon.

4. Connect to Foundry.
    1. Click the **Data & Services** tab menu and select **Link to Existing App**. 

        ![Link to Existing App](../assets/images/linktoapp.png){: style="height:60%;width:60%"}
        
        The **Volt MX Go Applications** dialog opens.

    2. Click **Associate** corresponding to a Foundry app that you want to link.

        ![Associate App](../assets/images/associateapp.png)

        In this example, the associated Foundry app is the *First Touch Recipes* app.

    3. Click **Project Services** on the **Data & Services** tab and see the connections to the Foundry data.

6. Generate forms.
    1. Go to the **Data & Services** tab, and expand **Project Services**.  
    2. Right-click the Object Service, and then select **Generate Forms** &rarr; **Responsive Web**.

    Using the *First Touch Recipes* app as an example, right-click the **FirstTouchRecipesObj** and then select **Generate Forms** &rarr; **Responsive Web**. 

    ![Generate Form](../assets/images/genform.png){: style="height:80%;width:80%"}

!!!note
    **Summernote Editor** is automatically applied on Rich Text fields when generating entry forms (CREATE/UPDATE) from the data panel. **Summernote Editor** is a simple WYSIWYG editor that allows a developer to enter or edit rich text content in a Rich Text field in a form in Iris. For more information, see [Summernote Editor](../references/summernotewidget.md).

## Expected result

Five types of forms (*Dashboard*, *Grid*, *Details*, *Create*, and *Update*) are generated for each object in the Object service with the respective navigation links among each other.

![Generate Form](../assets/images/genform1.png)

The Dashboard form displays all the objects of the selected Object service. Users can navigate to the respective Grid, Details, Create, and Update forms from the Dashboard screen. If you haven't defined the startup form of the app, the Dashboard form is made the startup form by default.

If your Object Service has views, they're also generated. In the example, the Object Service *DemoGAObjectService* of the Foundry app *DemoGA* has the view *Main*.

![Generate Form](../assets/images/genform2.png){: style="height:60%;width:60%"}

After the process, there are two types of forms (*Grid* and *Details*) for the view *Main*, and five types of forms for the object *Recipe*.   

![Generate Form](../assets/images/genform3.png)
