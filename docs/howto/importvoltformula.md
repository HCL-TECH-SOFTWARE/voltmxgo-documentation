# Import actions from Domino View applying VoltFormula function

## About this procedure

The procedure guides you in importing Domino app integrating the VoltFormula. The imported **actions** from the Domino view will have the integration of formula language like **Notes** and **OpenFormula** and converted it automatically with `voltmx.rosettajs` syntax.

## Before you start

- You must complete the [Design Import tutorial](../tutorials/designimport.md)
- You need to have **actions** on your Domino view configuration. 
- You need to configure your Domino view as **Active**.

## Procedure

1. On the top menu, select **Project** &rarr; **Import** &rarr; **Domino Application**. The **VoltMX Design Import Wizard** opens.
2. Finished all the steps in the **VoltMX Design Import Wizard**.
3. Find the form that have the **actions** (i.e., `Create Customer`) button in Domino view.

    ![](../assets/images/dibutton.png)

4. On the **Action** properties tab, select **onClick**.
5. Click **Edit**. The Action Editor page will appear.
6. Double-click the **Add Formula** in the flowchart.
7. The formula language window will appear containing the *Formula Language* and the auto-converted `voltmmx.rosettajs` syntax.

    ![](../assets/images/divoltformula.png) 

8. Click **Save**.

