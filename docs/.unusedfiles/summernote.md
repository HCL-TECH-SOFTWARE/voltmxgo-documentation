# Import Summernote Editor

## About this task

Imports the Summernote Editor component in Volt Iris. The Summernote Editor component is a simple WYSIWYG editor that allows a developer to enter or edit rich text content in a rich text field in a form in Volt Iris.  

## Before you begin

- You have created a Domino data model in a Volt Foundry Object Service for which you want to generate forms.

## Procedure

### To import Summernote Editor:

1. On the top menu of Volt Iris, select **Project** &rarr; **Import** &rarr; **Summernote Editor**.

    ![Select Summernote](../assets/images/summernoteselect.png)

    An **Import Component** dialog opens and shows the import progress. 

    ![Select form](../assets/images/snimportcomp.png)

2. Wait for the import completion. Once completed, the **Import Component** dialog shows the “Component imported successfully” message.

    ![Select form](../assets/images/snimportsuccess.png)

3. Click **Close**.

The Summernote Editor component is now successfully imported.

### To test Summernote Editor implementation: 

1. Open a project, and then go **Data & Services** &rarr; **Project Services**.
2. Expand the **ObjectService** and click a data model.

    ![Select form](../assets/images/snprojservices.png)

3. Select **Generate Forms** &rarr; **Responsive Web**. A dialog indicates the generation of forms.

    ![Generate form](../assets/images/sngenforms.png)

4. Once the forms are generated, go to Project &rarr; select the “Create” or “Update” form.

    ![Select form](../assets/images/sncreateform.png)

    On the selected form, the rich text field now has a WYSIWYG editor instead of just being a text field.

    ![Summernote editor rich text field](../assets/images/snrichtextfield.png)

## Additional information

To learn more, see [Summernote Editor component](../topicguides/summernotewidget.md).