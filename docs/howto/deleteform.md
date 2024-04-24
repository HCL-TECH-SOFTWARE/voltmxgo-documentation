# Delete existing forms while using the Design Import wizard

## About this procedure

The procedure guides you on how to delete forms when importing a domino application into an existing project.

## Before you start

- You must complete the [Volt MX Go installation](../tutorials/installation.md).
- You already import a domino application on your project.
- You must create a domino application on your existing project.


## Procedure

1. On the top menu, select Project → Import → Domino Application. The VoltMX Design Import Wizard opens. You may do the steps in importing a domino application until you reach the  **Summary** page.

2. Click the **Build Iris Application**. If existing MXGo Iris forms are detected, a prompt will occur. This prompt will notify the user whether or not to overwrite the current forms.

 ![Screenshot](../assets/images/dideleteform.png)

3. Click **Yes** to delete the existing forms. 

4. Click **No** to keep the existing forms. This will **not** guarantee you that your imported application will generate and build successfully.

5. Click the **Done** on the **Result** page. The project forms will retrieves a fresh copy from an imported domino app.

