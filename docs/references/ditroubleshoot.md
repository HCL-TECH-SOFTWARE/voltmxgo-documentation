## Design Import troubleshooting

## DRAPI schema issues and report

If the wizard encounters a problem with the DRAPI settings, this **alert box** appears. It will proceed, but there is no assurance that the created app will launch or perform properly. 

![](../assets/images/didrapissues.png)

Issues in DRAPI when importing Domino Application:

These issues are applicable only to **Default** and **DQL** mode.

- **Field value mismatch between modes** - this issue occurs when the **DQL** and **Default** mode have different property values (like fields, type, field access, etc.,) in declaring each mode. They have to be in parallel or similar in property values.

- **Form missing Default mode Fields and DQL mode** - This issue occurs when you have a **DQL** and **Default** mode that isn't declared all the fields. Note that you have to declare the same fields in **DQL** and **Default** mode.

- **Form missing Fields on Default mode** - This issue occurs when you save the **Form** without declaring any fields or fail to declare all fields in the **Default Mode**. You must declare all the fields in the **Default** mode. 

- **Missing DQL mode** - this issue occurs when only **Default mode** is declared. The **DQL** and **Default** mode must be parallel or similar to each other before importing the schema.