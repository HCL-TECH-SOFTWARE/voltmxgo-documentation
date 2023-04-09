# Volt Formula Tutorial

This  tutorial guides you in accesing the VoltFormula in VoltMX Go through the use of VoltMX Iris to convert the formula from OpenFormula and NotesFormula.

## Before you start

- Must have a **VoltMX Iris** app and completed the installation procedure. The installationis provided to the customers/partners that sign up for early release access. 
- Must have a **VoltMX Foundry** app and completed the installation procedure in [Volt MX Foundry](installation.md).
- Must have a **username** and **password** for VoltMX Go Iris and Foundry.
- Must learn to use the [actions](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/working_with_Action_Editor.html#search-for-an-action-in-action-editor) in VoltMX Iris.



## Launch VoltMX Go Iris

1. Open the **VoltMX Go Iris**. This opens the log-in screen of Iris.

	!!!note
		You can also start Iris by going to the folder where it's stored and double-clicking it.
		
   	On launching Iris, the VoltMX Go cloud login screen appears for license validation.

2.  Enter your **credentials** in VoltMx Go Iris and click **Sign-In
   The VoltMX Go Iris app canvass opens.

<img src="../assets/images/dilogin.png"  width="60%" height="60%" style="display: block; margin: 0 auto" />

## Validating VoltMX GO Foundry
	
1. Open the **Volt MX Iris** menu bar for **Mac** or **Edit** menu bar for **Windows** and click **Preferences**.
2. This opens the **VoltMX Iris Preferences**. Click to **Volt MX Foundry**.
3. Fill-in the Foundry URL with `http://foundry.mymxgo.com` and click **Validate**. 
4. Click **Done**. 

<img src="../assets/images/dipreference.png"  width="80%" height="80%" style="display: block; margin: 0 auto" />

## Introduction to the VoltFormula

This feature in VoltMX Go Iris is an added actions in Volt MX Iris where you can insert the [OpenFormula]((https://docs.oasis-open.org/office/OpenDocument/v1.3/OpenDocument-v1.3-part4-formula.html)) and [NoteFormula](https://help.hcltechsw.com/dom_designer/10.0.1/basic/H_NOTES_FORMULA_LANGUAGE.html) translated into a javascript code.


## Open VoltFormula through `Actions`

1. Open your **Project.**
2. From the **Project** tab of the **Project Explorer**, select the widget you want to apply the action to. 
3. Once it’s highlighted on the Iris Canvas, right-click it, and then select one of the action sequences, such as `onTouchStart`, `onClick` and others. 

    <img src="../assets/images/vfaction.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />

4. Doing so opens the **Action Editor** and creates an action sequence for you to configure.
5. On the left side of the **Action Editor**, go to **Formula** and click the **Add Formula**.
    <img src="../assets/images/vfactioneditor.png"  width="90%" height="90%" style="display: block; margin: 0 auto" />

## Translating the OpenFormula and NotesFormula into Javascript
1. On the action editor, click the Ad
<!--add changes in voltformula.md-->