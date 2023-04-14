# VoltFormula Tutorial
The following tutorial shows you how to use voltFormula in Volt MX Iris to convert formulas from OpenFormula and NotesFormula into Volt MX Go Rosetta Javascript.
## Before you start

- You have completed the [Volt MX Go installation](installation.md#installing-volt-mx-go-iris).
- You have created your [Foundry admin account](../howto/foundryadminaccount.md).
- You have noted the following Domino REST API details:
    - Server URL: `http://drapi.mymxgo.com` 
    - username: `mxgo admin`
    - password: `password`
- You have to used the [actions](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/working_with_Action_Editor.html#search-for-an-action-in-action-editor) in Volt MX Iris.

## Launch Volt MX Go Iris

1. Open the **Volt MX Go Iris**. This opens the log-in screen of Iris.

    !!!note
        You can also start Iris by going to the folder where it's stored and double-clicking it.
		
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

## Introduction to the VoltFormula

This feature in Volt MX Go Iris is an added action in Volt MX Iris where you can insert the [OpenFormula](https://docs.oasis-open.org/office/OpenDocument/v1.3/OpenDocument-v1.3-part4-formula.html) and [Notes Formula Language](https://help.hcltechsw.com/dom_designer/10.0.1/basic/H_NOTES_FORMULA_LANGUAGE.html) translated into a JavaScript code.


## Open voltFormula through `Actions`

1. Open your **Project**.
2. From the **Project** tab of the **Project Explorer**, go on `Forms` navigation and select the widget or object you want to apply action to. 
3. Once in the Iris forms, right-click it, and then select one of the action sequences, such as `onTouchStart`, `onClick` and others. 

    <img src="../assets/images/vfaction.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />

    The **Action Editor** opens and creates an action sequence for you to configure.

4. On the left side of the **Action Editor**, go to **Formula** and click the **Add Formula**.
    <img src="../assets/images/vfactioneditor.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />

## Translating the OpenFormula and NotesFormula into javascript

1. On the **action editor**, click the **Add Formula** on the diagram. On the right side of the **action editor** window, you can see the properties of the voltFormula.
    - **window for the translated OpenFormula and NotesFormula in JavaScript.**
    - **window for the formula language** - OpenFormula and NotesFormula are the accepted formulas to add in this window.
    - **window for the formula results**.
    <img src="../assets/images/vfactioneditor.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />

2. Click on **Formula Language** window and enter a valid formula.

    !!!note
        In Formula language  window, it has the abilty to detect the **Notes** and **Open** formula. You must enter the **@** character before the formula in NotesFormula and enter the **=** character before the formula in OpenFormula.
    
    You can see the JavaScript code and the result.

4. Click **Save**.
  <img src="../assets/images/vfactioneditor.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />    

## Using the voltFormula in Controller 
### Add formula in a controller
1. Open a controller on **Project Explorer.**
2. Select and open your controller. This opens the code window.
3. Right-click on the code window and select **Add Code from Formula**. The Formula Language window appear.
   <img src="../assets/images/vfaddcode.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />  
4. Add the code in the **Formula Language** window.

	!!!note
        - **@** chraracter for *NotesFormula*
	    - **=** character  for *OpenFormula*
	    - You can the see the syntax code or the IntelliSense for the formula that you choose.
	    - If you don't know how to convert the Javascript in Volt MX Go `rosettajs` from **OpenFormula** and **NotesFormula**, you may use the Formula Language window to do so.
      <img src="../assets/images/vfsyntax.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />  


    The code you enter in **Formula Language** is translated to autogenerated rosettajs code in the code window.   
    
<img src="../assets/images/vfrosoutput.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />  

### Edit formula in a controller
1. Open a controller on Project Explorer.
2. Select and open your controller. This opens the code window.

    !!!note
        You can easily see the conversion formula that comes from the openFormula and notesFormula inbetween the comment  of rosetta autogenerated code.
        ![autogenerated code](../assets/images/vfeditform.png)

3. Right-click on the existing code and select **Edit Formula Code**. The Formula Language window appear and you can see the existing formula in the Formula Language window.
    ![Edit Formula](../assets/images/vfclickedit.png)

4. You can edit the code you want in the Formula Language window.

    !!!note
        - **@** chraracter for *NotesFormula*
        - **=** character  for *OpenFormula*
        - You can the see the syntax code or the IntelliSense for the formula that you choose.
        - If you don't know how to convert the Javascript in Volt MX Go `rosettajs` from **OpenFormula** and **NotesFormula**, you may use the Formula Language window to do so.
        - You can add or edit code in the formula language window as long as you folow the syntax.
        - You can add more than one line of code. 
      <img src="../assets/images/vfsyntax1.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />  

    The code you enter in **Formula Language** is translated to autogenerated `rosettajs` code in the code window.   
    
<img src="../assets/images/vfresedit.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />  

### Edit Rosetta Javascript

1. Open a controller on **Project Explorer.**
2. Select and open your controller. This opens the code window.

    !!!note
        You can easily see the conversion formula that comes from the openFormula and notesFormula inbetween the comment  of rosetta autogenerated code.
        ![autogenerated code](../assets/images/vfeditform.png)

3. Add your formula in `rosettajs` in the code window, or edit the existing formula in the code window without opening the **Formula Language** window.

    !!!note
        - When you add `rosetta` javascript,  you'll be able see the syntax code or the intellisense for the formula that you choose in code window.
        - Make sure you know the syntax for coding the `rosetta` javascript
        
    ![Edit Rosettajs](../assets/images/vfjavaedit.png)
     
<!--ALSO NEEDS EDIT EXISTING FORMULA  (right click on the javascript code to pop menu that shows EDIT formula)
ALSO NEEDS REVERTING FORMULA (when you change the javascript converted formula and then try to edit formula) 
MISSING ROSETTA CONFIGURATION PANEL OF IRIS  (eg.  Iris -> Project Settings -> Rosetta "Tab"
-->

## Configuring Volt Formula's Rosetta API Options
1. Open the **Project Settings** icon.
    ![settings](../assets/images/vfrosettasetting.png)
2. The **Project Setting** window appears. Click the **Rosetta** tab.
    ![settings](../assets/images/vfsetting.png)

    |Rosetta Area | Description|
    |-------------|------------|
    |**API configuration**|This section allows you to configure options specific to the APIs' implementation and execution|
    | |**Register Custom API** allows you upload a file with custom APIs.  Refer to the API reference documentation under the rosetta-api module for method `registerAPI` for more details on expected file format and parameters|
    | |**Preferred API implementation** allows you specify whether to execute the Notes Formula or the OpenFormula implementation when calling an API method which has an existing implementation in either formula language.  Example, `@Abs()` and `=ABS()` are encapsulated by Rosettas `abs()` method.  Selecting `Notes` option will make Rosetta call the Notes implementation.  In most cases either implementation will behave the same.  But in other cases, there may be difference in parameters, execution, or returned results.  For example, most Notes formula functions allow lists to be passed in as arguments while OpenFormula allows lists as ranges for only a number of methods.  Refer to the API reference documentation for details on each API|
    |**Converter Configuration**|This section allows you to configure options related to how formulas are converted into their corresponding Rosetta enabled JavaScript|
    | | **Passthrough formula language** allows you specify whether the converter allow unrecognize formula code to be made part of the javascript conversion results without any massaging, or if it should throw and error when encounters unrecognizable formula code.  This allows greater flexibility but also exposes the API to injection of code.  Use with care.|
    | | **Use Native vs. API Conversion** allows you specify whether the converter will use native JavaScript or API calls for methods where a native JavaScript function exists.  Example, convert `@If( )` into JavaScript native `if( )` or call the API `rosettajs.Logical.if( )`.  Sometimes it will make sense and produce cleaner code to select "convert into native JavaScript" than using the API.  Other times you may want to go through the API call itself in order to allow for additional checks and/or handle the parameters differently|
    |**Version**| This is where you get the version of the `SDK` plugin,`API`,`Converter`, and `prettifier`|

