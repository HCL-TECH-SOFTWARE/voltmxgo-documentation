# First Touch app

The First Touch Recipe Catalog app is a Domino app written using Volt MX Go. It shows recipe cards for various dishes. The front end of the app is created using Volt MX Go Iris. The information used by the app is accessed from the `FirstTouchRecipes.nsf` in Domino via Domino REST API using the Domino Adapter in Volt MX Go Foundry.

![First Touch Recipe Catalog app](../assets/images/ftrecipeapp.png)

You can click a recipe card to open an expanded view that shows recipe details such as ingredients and cooking instructions.

![Recipe card expanded view](../assets/images/recipecardexpanded.png){: style="height:80%;width:80%"}

You can enter text or keywords in a **Search Recipes** box, which highlights the recipe cards with information matching the text or keywords. 

![Recipe card search](../assets/images/recipesearch.png)

You can add a new recipe by clicking **+ Add Recipe**. It opens the **Add Recipe** window, which allows you to add the recipe name, prep time, cooking time, number of servings, needed ingredients, and cooking direction. You can also upload a picture of the cooked dish using the recipe.

![Add Recipe window](../assets/images/addrecipe.png)

The app also allows you to edit each recipe by clicking the menu icon in the recipe card and selecting **Edit** to open the **Update Recipe** window. You can also click **Edit** when in the expanded view.

![Edit recipe](../assets/images/editrecipe.png){: style="height:40%;width:40%"}

In the **Update Recipe** window, you can change the values of the different fields.   

![Update Recipe window](../assets/images/updaterecipe.png)

If you want to remove a recipe, click the menu icon in the recipe card and select **Delete**. You can also click **Delete** when in the expanded view.

![Delete recipe](../assets/images/deleterecipe.png){: style="height:40%;width:40%"}