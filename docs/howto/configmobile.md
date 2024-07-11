# Configure mobile app browser

## About this task

This procedure describes how to configure the mobile app browser before building and publishing the Native App.

## Procedure

1. Go to the **Design** tab.
2. In your **Project**, go to **Forms** and click the **Start-Up form**, for example the `frmLogin`.

    ![Project tab](../assets/images/didesignproj.png)

3. Click the login button and click the **Properties** tab.
4. Under **Properties**, click the **Action** tab.
5. Click **Edit** next to the **onClick** item. The **Action Editor** opens.

    ![Action tab](../assets/images/didesignaction.png)

6. Click the **Invoke service**.

    !!!note
        The default view is the **Diagram View**. Make sure to select the **Diagram View** tab if it's not already selected.
    

7. Select **Use Device Browser** under **Select Browser Widget**.

    ![Action Editor](../assets/images/didesigninvoke.png)

8. Click **Save**.