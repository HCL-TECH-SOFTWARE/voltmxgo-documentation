# voltFormula Tutorial
The following tutorial shows you how to use voltFormula in Volt MX Iris to convert formulas from OpenFormula and NotesFormula into Volt MX Go rosetta javascript.

## Before you start

- You have completed the [Volt MX Go installation](installation.md).
- You have created your [Foundry admin account](../howto/foundryadminaccount.md).
- You have noted the following Domino REST API details:
    - Server URL: `http://drapi.mymxgo.com` 
    - username: `mxgo admin`
    - password: `password`
- You have to used the [actions](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/working_with_Action_Editor.html#search-for-an-action-in-action-editor) in Volt MX Iris.

## Launch Volt MX Go Iris

1. Open the **Volt MX Go Iris**. This opens the log-in screen of Iris.

    \****NOTE***\* You can also start Iris by going to the folder where it's stored and double-clicking it.
		
   	On launching Iris, the Volt MX Go cloud login screen appears for license validation.

2.  Enter your **credentials** in Volt MX Go Iris and click **Sign-In**.
    The Volt MX Go Iris app canvas opens.

<img src="../assets/images/dilogin.png"  width="60%" height="60%" style="display: block; margin: 0 auto" />

## Validating Volt MX Go Foundry
	
1. Open the **Volt MX Iris** menu bar for **Mac** or **Edit** menu bar for **Windows** and click **Preferences**.
2. This opens the **Volt MX Iris Preferences**. Click to **Volt MX Foundry**.
3. Fill-in the Foundry URL with `http://foundry.mymxgo.com` and click **Validate**. 
4. Click **Done**. 

<img src="../assets/images/dipreference.png"  width="80%" height="80%" style="display: block; margin: 0 auto" />

## Introduction to the voltFormula

This feature in Volt MX Go Iris is an added action in Volt MX Iris where you can insert the [OpenFormula](https://docs.oasis-open.org/office/OpenDocument/v1.3/OpenDocument-v1.3-part4-formula.html) and [Notes Formula Language](https://help.hcltechsw.com/dom_designer/10.0.1/basic/H_NOTES_FORMULA_LANGUAGE.html) translated into a JavaScript code.


## Open voltFormula through `Actions`

1. Open your **Project.**
2. From the **Project** tab of the **Project Explorer**, select the widget you want to apply the action to. 
3. Once it’s highlighted on the Iris Canvas, right-click it, and then select one of the action sequences, such as `onTouchStart`, `onClick` and others. 

    <img src="../assets/images/vfaction.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />

4. Doing so opens the **Action Editor** and creates an action sequence for you to configure.
5. On the left side of the **Action Editor**, go to **Formula** and click the **Add Formula**.
    <img src="../assets/images/vfactioneditor.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />

## Translating the OpenFormula and NotesFormula into javascript

1. On the **action editor**, click the **Add Formula** on the diagram. On the right side of the **action editor** window, you can see the properties of the Volt Formula.
    - **window for the translated OpenFormula and NotesFormula in JavaScript.**
    - **window for the formula language** - OpenFormula and NotesFormula are the accepted formulas to add in this window.
    - **window for the formula results**.
    <img src="../assets/images/vfactioneditor.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />

2. Click on **Formula Language** window and enter a valid formula.

    \****NOTE***\*
    	In Formula language  window, it has the abilty to detect the **Notes** and **Open** formula. You must enter the **@** character before the formula in NotesFormula.
        and enter the **=** character before the formula in OpenFormula.
    
3. You can see the JavaScript code and the result.

4. Click **Save**.
  <img src="../assets/images/vfactioneditor.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />    

## Using the voltFormula in Container

1. Open a controller on Project Explorer
2. Select and open your container. This opens the code window.
3. Right-click on the code window and select **Add Code from Formula**. The Formula Language window appear.
   <img src="../assets/images/vfaddcode.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />  
4. Add the code in the **Formula Language** window.

	\****NOTE***\*
	 - **@** chraracter for *NotesFormula*
	 - **=** character  for *OpenFormula*
	 - You can the see the syntax code or the intellisense for the formula that you choose.
	 - If you don't know how to convert the JavaScript in Volt MX Go `rosettajs` from **OpenFormula** and **NotesFormula**, you may use the Formula Language window to do so.
      <img src="../assets/images/vfsyntax.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />  

5. The code you enter in **Formula Language** is translated to auto-generated rosettajs code in the code window.  
### Expected Ouput
    
<img src="../assets/images/vfrosoutput.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />  


<!--add changes in voltFormula1.md-->
