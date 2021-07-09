# Integrating scenario results

When the Personalization service is [enabled](enabling_personalization.md) and properly 
[configured](perso_configuration.md), as an editor, you can embed the recommendations 
that come from the service, to show them to the end users.
You can, for example, modify a Page to include a block that shows what 
Content items/products are recommended to end users when specific [scenarios](scenarios.md) are triggered. 
Depending on the scenario type, you may need to provide additional information 
to see the recommendation results.

The number and selection of available scenarios depends on the arrangements that 
your organization makes with Ibexa when defining the initial configuration.

1. Navigate to the **Site** > **List** tab, and then click the **Preview** 
icon next to the site in which you want to place a personalization block.

1. On the Page Builder screen, click the **Preview/Edit** selector to switch to editing mode.

1. From the **Elements** menu, drag and drop the **Personalized** block to a location on the page layout.
 
1. Click the **Block settings** icon to modify the **Personalized** block:
 
    1. On the **Basic** tab, set values in the following fields:
        -	**Block name** – Optionally, enter a name for the page block, for example, "Bestsellers".
        -	**Select a scenario** – Select "Landing page" or "Top clicked".
        -	**Select a Content Type...** – Select "Product".
        -	**Display limit** – Set the number of products to be displayed, for example, 4.
        
    1. On the **Design** tab, in the **View** field, change the layout to "Products" and submit your changes.
    
      The preview of the Page changes to display a list of products recommended by the Personalization service.
 
1. Save your changes to the draft or publish the Page.

For more information about collecting events and embedding recommendation results, 
see [Basic integration](https://doc.ibexa.co/en/master/guide/personalization/personalization_quickstart/#integration).
