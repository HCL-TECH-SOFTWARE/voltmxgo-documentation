# Delete existing forms while using the Design Import wizard

## About this procedure

The procedure guides you on how to delete forms when importing a Domino application into an existing project.

## Before you start

- You must complete the [Volt MX Go installation](../tutorials/installation.md).
- You already imported a Domino application on your project.
- You must create a Domino application on your existing project.


## Procedure

1. On the top menu, select **Project** &rarr; **Import** &rarr; **Domino Application**. The **VoltMX Design Import Wizard** opens. You may do the steps in importing a Domino application until you reach the  **Summary** page.

2. Click the **Build Iris Application**. If existing MX Go Iris forms are detected, a prompt will occur. This prompt will notify the user whether to overwrite the current forms.

    ![Screenshot](../assets/images/dideleteform.png)

3. Click **Yes** to delete the existing forms or click **No** to keep the existing forms.

    This will **not** guarantee you that your imported application will generate and build successfully.

5. Click **Done** on the **Result** page. The project forms will retrieve a fresh copy from an imported Domino app.

