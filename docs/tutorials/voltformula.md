# VoltFormula tutorial

This tutorial shows you how to use VoltFormula in Volt Iris to convert formulas from OpenFormula and NotesFormula into Volt MX Go Rosetta JavaScript. This feature in Volt Iris allows you to enter into source [OpenFormula](https://docs.oasis-open.org/office/OpenDocument/v1.3/OpenDocument-v1.3-part4-formula.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"} and [Notes Formula Language](https://help.hcltechsw.com/dom_designer/10.0.1/basic/H_NOTES_FORMULA_LANGUAGE.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"} and have it translated automatically into JavaScript code.

## Before you begin

- You have completed the [Volt MX Go installation](installupgrade/index.md).

- You have created your [Volt Foundry admin account](../howto/install/foundryadminaccount.md).

- You know how to use [Actions](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/working_with_Action_Editor.html#search-for-an-action-in-action-editor "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}.

## Launch Volt Iris

1. Open Volt Iris. When the **Sign-in** dialog opens, close it.

    !!! note

        If you have already configured the login settings while performing the other tutorials, enter your email and password for Volt Foundry on the **Sign in to your account** page and click **Sign In**. You don't need to execute the steps below for configuring the login settings and logging in.

2. Configure the login settings.

    1. Go to **Preferences**.

        For Windows, select **Edit** &rarr; **Preferences**.

        For Mac, depending on your macOS, select **Volt Iris** &rarr; **Preferences** or **Settings**.

    2. In the **Volt Iris Preferences** dialog, click **Volt Foundry**.

        ![Preferences](../assets/images/dipreference.png){: style="height:80%;width:80%"}

    3. On the **Volt Foundry** tab, enter your Foundry URL in the **Foundry URL** text box, and then click **Validate**.

        You should see the “Validation Successful” message at the top of the dialog.

    4. Click **Done**.

3. Log in to Volt Iris.

    1. Click **Login** on the upper right corner of the Volt Iris screen.
    2. Enter your email and password for Volt Foundry on the **Sign in to your account** page.
    3. Click **Sign In**. Your username appears next to the profile icon.

## Open VoltFormula using the Action Editor

1. On the **Project** tab, find and expand the **Forms** directory.

    !!! info

        If you cannot see the **Project** tab, click the **Design** tab beside the **Storyboard** tab.

2. Select a form under the **Forms** directory. The selected form opens.
3. Drag a widget or component to the form.
4. Right-click the widget and select an action from the menu.

    The example image shows the **Button** widget added to the form and the **onClick** action selected from the menu.

    [![Selecting action from menu](../assets/images/VF1.png){: style="height:80%;width:80%"}](../assets/images/VF1.png){: target="_blank" rel="noopener noreferrer"}

    The **Action Editor** opens and creates an action sequence for you to configure.

5. On the left side of the **Action Editor**, click **Add Formula** under **Formula** to add it to the action sequence and open the **Formula Editor** on the right side of the **Action Editor**.  

    [![Action Editor](../assets/images/VF2.png){: style="height:80%;width:80%"}](../assets/images/VF2.png){: target="_blank" rel="noopener noreferrer"}

<!--

3. On the `form` canvass, select the widget or object you want to apply action to. **Right-click** it, and then select one of the action sequences, such as `onTouchStart`, `onClick` and others. 

    ![Context menu](../assets/images/vfaction.png){: style="height:80%;width:80%"}

    The **Action Editor** opens and creates an action sequence for you to configure.

4. On the left side of the **Action Editor**, go to **Formula** and click the **Add Formula**.

    ![Formula Editor](../assets/images/vfactioneditor.png){: style="height:80%;width:80%"}
-->
## Translate OpenFormula and Notes Formula into JavaScript

1. On the **Action Editor**, enter a valid formula in the **Formula Language** window of the **Formula Editor**.

    !!! tip

        - Enter a Notes Formula by starting with the **@** character or enter an OpenFormula by starting with the **=** character. 
        - IntelliSense will provide formula suggestions and corresponding formula descriptions, examples, and details as you enter your formula in the **Formula Language** window of the **Formula Editor**.
        - You can click **Samples** to open the **Formula Samples** dialog that provides descriptions and sample snippets for **Notes**, **OpenFormula**, and **Custom** formula samples.

            ![Formula Sample](../assets/images/V10.png){: style="height:70%;width:70%"}  
        
        - Click **Results** to open the **Formula Results** window below the **Formula Language** window and see the result of the entered formula.

    The formula you entered in the **Formula Language** window is automatically converted to JavaScript code and is viewable from the window on top of the **Formula Language** window.

    [![Action Editor](../assets/images/VF3.png){: style="height:80%;width:80%"}](../assets/images/VF3.png){: target="_blank" rel="noopener noreferrer"}

2. Click **Save**.

<!--
1. On the **Action Editor**, click the **Add Formula** on the diagram. On the right side of the **Action Editor** window, you can see the properties of the VoltFormula.
    - **window for the translated OpenFormula and NotesFormula in JavaScript.**
    - **window for the formula language** - OpenFormula and NotesFormula are the accepted formulas to add in this window.
    - **window for the formula results**.

    ![Action Editor](../assets/images/vfactioneditor.png){: style="height:90%;width:90%"}

2. Click on **Formula Language** window and enter a valid formula.

    !!!note
        In Formula language  window, it can detect the **Notes** and **Open** formula. You must enter the **@** character before the formula in NotesFormula and enter the **=** character before the formula in OpenFormula.

       Upon typing your formula, the intellisence will appear and return the syntax, descriptions, and examples of your chosen formula.

    You can see automatically the JavaScript code with the formula you type in the **Formula Language** window.

    ![Formula Language window](../assets/images/vfactionformula.png){: style="height:90%;width:90%"}

    You can also see the result upon clicking the **Results** button.

    ![Formula Results window](../assets/images/vfjavaresults.png){: style="height:90%;width:90%"}

3. Click **Save**.
-->
## Use VoltFormula in a Controller module

### Add formula in a controller

1. On the **Project** tab, find and expand the **Controllers** directory.
2. Select a controller under the **Controllers** directory. The selected controller opens.
3. Right-click the code window and select **Add Code from Formula**. 

    [![Controller](../assets/images/VF4.png){: style="height:80%;width:80%"}](../assets/images/VF4.png){: target="_blank" rel="noopener noreferrer"}

    The **Formula Language** window appears.

    [![Controller](../assets/images/VF5.png){: style="height:80%;width:80%"}](../assets/images/VF5.png){: target="_blank" rel="noopener noreferrer"}

4. Enter a valid formula in the **Formula Language** window

    !!! tip

        - Enter a Notes Formula by starting with the **@** character or enter an OpenFormula by starting with the **=** character. 
        - IntelliSense will provide formula suggestions and corresponding formula descriptions, examples, and details as you enter your formula in the **Formula Language** window.
        - You can click **Samples** to open the **Formula Samples** dialog that provides descriptions and sample snippets for Notes, Open Formula, and Custom API formula samples.

            ![Formula Sample](../assets/images/V10.png){: style="height:70%;width:70%"}

        - Click **Formula Results** to open the **Formula Results** window below the **Formula Language** window and see the result of the entered formula.

    The formula you entered in **Formula Language** window is automatically converted to JavaScript code and is viewable in the code window on top of the **Formula Language** window.

    The following example image shows a formula being entered in the Formula Language window and with IntelliSense providing suggestions.

    [![Controller](../assets/images/VF6.png){: style="height:80%;width:80%"}](../assets/images/VF6.png){: target="_blank" rel="noopener noreferrer"}

5. Save your changes.
<!--
1. Open a controller on **Project Explorer.**
2. Select and open your controller. This opens the code window.
3. Right-click the code window and select **Add Code from Formula**. The Formula Language window appear.

    ![Selecting Add Code from Formula](../assets/images/vfaddcode.png){: style="height:90%;width:90%"}

4. Add the code in the **Formula Language** window.

	!!! note

        - **@** character for *NotesFormula*
	    - **=** character  for *OpenFormula*
	    - You can see the code hinting or the IntelliSense for the formula that you choose.
        - Each formula is accompanied by its category.
	    - If you don't know how to convert the JavaScript in Volt MX Go `rosettajs` from **OpenFormula** and **NotesFormula**, you may use the Formula Language window to do so.

    ![Add code in Formula Language window](../assets/images/vfsyntax.png){: style="height:90%;width:90%"}
  
    The code you enter in **Formula Language** is translated to autogenerated RosettaJS code in the code window.

    ![Translated Formula Language](../assets/images/vfrosoutput.png){: style="height:90%;width:90%"}  
-->
### Edit formula in a controller

1. On the **Project** tab, find and expand the **Controllers** directory.
2. Select a controller under the **Controllers** directory. The selected controller opens.
3. Right-click the existing code and select **Edit Formula Code**.

    [![Controller](../assets/images/VF7.png){: style="height:80%;width:80%"}](../assets/images/VF7.png){: target="_blank" rel="noopener noreferrer"}

    The **Formula Language** window appears.

4. Edit the formula in the **Formula Language** window.

    !!! note

        - Make sure to follow the correct syntax.
        - You can add more than one line of code. 
        - IntelliSense will provide formula suggestions and corresponding formula descriptions, examples, and details as you enter your formula in the **Formula Language** window.

5. Save your changes.
<!--
1. Open a controller on **Project Explorer**.
2. Select and open your controller. This opens the code window.

    !!! note

        You can see the conversion formula that comes from the OpenFormula and NotesFormula inbetween the comment  of rosetta autogenerated code.
        
    ![autogenerated code](../assets/images/vfeditform.png)

3. Right-click the existing code and select **Edit Formula Code**. The Formula Language window appear and you can see the existing formula in the Formula Language window.

    ![Edit Formula](../assets/images/vfclickedit.png)

4. You can edit the code you want in the Formula Language window.

    !!!note
        - **@** character for *NotesFormula*
        - **=** character  for *OpenFormula*
        - You can see the code hinting or the IntelliSense for the formula that you choose.
        - Each formula is accompanied by its category.
        - If you don't know how to convert the JavaScript in Volt MX Go `RosettaJS` from **OpenFormula** and **NotesFormula**, you may use the Formula Language window to do so.
        - You can add or edit code in the formula language window as long as you follow the syntax.
        - You can add more than one line of code. 

    ![Formula Language editor](../assets/images/vfsyntax1.png){: style="height:90%;width:90%"}

    !!! note

        - The code you enter in **Formula Language** is translated to autogenerated `RosettaJS` code in the code window.  
        - You can also see the result in **Formula Results** tab.


    ![Formula Language editor](../assets/images/vfresedit.png){: style="height:90%;width:90%"}
-->
### Edit Rosetta JavaScript

1. On the **Project** tab, find and expand the **Controllers** directory.
2. Select a controller under the **Controllers** directory. The selected controller opens.

    The piece of rosetta autogenerated code from OpenFormula or Notes Formula is provided  between comments as shown in the following image.

    [![Controller](../assets/images/VF8.png){: style="height:80%;width:80%"}](../assets/images/VF8.png){: target="_blank" rel="noopener noreferrer"} 

3. Edit or update the JavaScript code in the code window of the controller.

    !!! note

        Make sure you know the syntax for coding the `rosetta` JavaScript.

    IntelliSense provides suggestions as you edit or update the code as shown in the following image.

    [![Controller](../assets/images/VF9.png){: style="height:80%;width:80%"}](../assets/images/VF9.png){: target="_blank" rel="noopener noreferrer"}

4. Save your changes.

<!--
1. Open a controller on **Project Explorer**.
2. Select and open your controller. This opens the code window.

    !!! note

        You can see the conversion formula that comes from the OpenFormula and Notes Formula inbetween the comment of rosetta autogenerated code.
        
    ![autogenerated code](../assets/images/vfeditform.png)

3. Add your formula in `rosettajs` in the code window, or edit the existing formula in the code window without opening the **Formula Language** window.

    !!! note

        - When you add `rosetta` JavaScript,  you'll be able see the code hinting or the IntelliSense for the formula that you choose in code window.
        - Make sure you know the syntax for coding the `rosetta` JavaScript.
        
    ![Edit Rosetta JS](../assets/images/vfjavaedit.png)
-->
## Additional information

- The default Rosetta VoltFormula setting can be modified according to your need for your app. To change the configuration, see [Configure VoltFormula](../howto/voltformula/configrosetta.md).

- To know more about the proper way of handling codes, see [VoltFormula coding exercise examples in Volt Iris](../topicguides/voltformula/vfcodingguides.md).
