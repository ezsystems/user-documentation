# Filters

Filters are tools that you can use to eliminate, demote or promote specific recommendation results.

## General filters

For every recommendation [scenario](scenarios.md), you can define a set of filters. 
Filters are applied to all recommendations that come from [models](recommendation_models.md) selected in the strategy.

![General filters](img/scenario_filters.png "General filters in a scenario")

For more information about configuring models that make up a scenario, 
see [Advanced model configuration](recommendation_models.md#advanced-model-configuration).

### User profile-based filters

User profile-based filters are applicable in both publishing and eCommerce use cases. 

|Filter|Requirements and restrictions|
|---|---|
|Do not recommend the item currently viewed|When you activate this filter, it removes the context items from the recommendation list. You might not want to use this filter if your strategy is based on the ["Bundle" and "Ultimately bought" models](recommendation_models.md#ultimately-bought).|
|Do not recommend items the user already consumed|The Personalization service stores the CONSUME events of every user for one year. When you activate this filter, the user will not be recommended the consumed content again.|
|Max. repeated shows of identical recommendations per session|When you activate this filter and set a value, after a content item/product is recommended a certain number of times during the current user session, it is removed from all recommendation lists.|

#### Boost filters

Apart from filters that remove specified elements from recommendations, user 
profile-based filters include a filter for moving certain items up on the list. 
If enabled, boosting is triggered when values of a selected attribute from 
a user profile and the recommended item match. 
For example, news from the user's home country can have higher priority than from 
the rest of the world.

In the diagram below, every item has the `country` attribute and user profiles 
have the `country_of_origin` attribute.
You can configure the boost filter to promote recommendations for certain users:

![Boost filter example](img/boost_example.png "Boost filter example")

Item boosting requires that the Personalization service is fed with both item 
and user attribute data.
For more information about importing data, see [Importing data](content_import.md).

### eCommerce-specific filters

The following filters are only applicable in eCommerce use cases.

|Filter|Requirements and restrictions|
|---|---|
|No top-selling items|When you activate this filter, items that come from the top selling model (even if the model itself is not linked to this scenario) are not placed on the recommendations list. This way you can stop promoting products that are already popular. If you apply this filter to a top selling scenario as it will filter out all recommendations.|
|Item price should be equal or higher than the price of the context product|You can use this filter to filter out items that could be more attractive to the user from the recommendation list. It compares prices exported to the Personalization service with metadata of the currently viewed product.|
|Minimum price of the recommended product|You can use this filter to remove cheap and popular items from the recommendation list. For example, as an optometrist you might prefer showing the most popular designer frames on the home page and avoid promoting insurance subsidized cheap models or cleaning cloths. Again, this filter relies on product metadata and uses prices exported to the Personalization service.|
|Do not recommend if price unknown|If a product's price is not available then it will not be recommended.|
|Do not recommend items the user already purchased|When you activate this filter, the user will not be recommended the purchased products again.|

## Category path filters

Apart from filters that you define at the scenario level, you can use category path 
filters to narrow down recommendation results returned by each of the priority levels 
in the scenario strategy. 
When you activate a filter of this type, the service recommends only items from a specific 
item/product category. 
The actual category used to filter on is taken from recommendation request parameters.

![Category path filters](img/categorypath_filter.png "Category path filters in strategy settings")

There are two ways to specify a category path in a recommendation request:

- When there are no context items, but the category is provided in the request: 
  You might want to place such recommendation calls on category overview pages 
  to display the most popular items/products of the currently viewed category 
  (or "reference category").
- When context items are provided and categories of all context items are used for the request: 
  This approach is recommended only if it is technically impossible (or too complex) 
  to provide the category information explicitly.

Depending on how you configure the filters, the Personalization service can take 
different paths to find the actual set of categories to recommend the items/products from.

The following example shows the category structure (which basically corresponds to site navigation):

![Example of a category path tree](img/categorypath_tree.png "Example of a category path tree")

The table below lists all possible configurations and categories that recommended 
items/products are fetched from, based an assumption that the reference category passed in the request is "/Furniture/Desks&Tables/Tables".

|Category path filter configuration|Categories to fetch recommended items from|
|---|---|
|"Recommend items from the whole site"|All categories ("Plants", "Furniture" and below).|
|"Recommend items from the same category"</br>"Also include the parent category and its subcategories" not selected|Category "Tables" and all the sub-categories below ("Garden tables" and "Living room tables").|
|"Recommend items from the same category"</br>"Also include the parent category and its subcategories" set to 1 level up|Category "Desks/Tables" and below including "Desks", "Tables" and all their sub-categories.|
|"Recommend items from the same category"</br>"Also include the parent category and its subcategories" set to 2 levels up|Category "Furniture" and below.|
|"Recommend items from the same main category and its subcategories" set to 1 category level and below|Category "Furniture" and below.|
|"Recommend items from the same main category and its subcategories" set to 2 category levels and below|Category "Desks/Tables" and below.|
|"Recommend items from the same main category and its subcategories" set to 3 category levels and below|Category "Tables" and below.|

You can provide multiple reference categories (both in the request and by defining 
a context item or items).
In such a case, the superset of the recommendations is returned, and the results 
are sorted based on a global weight of the recommendations. 
Depending on the popularity of the categories, the more popular categories push 
the less popular categories out of the results.

If the recommended item is located in more than one category,
at least one category should be requested in the recommendation call.

### Multiple category path dimensions for popularity models

The category path parameter is a powerful tool. 
A typical approach is to represent the default content in the navigation-based 
structure of a website. 
If you need to represent available items of a website in different dimensions (taxonomies), 
you can do this out of the box, by enriching the `categorypath` information of an item.

For example, in a shop that sells furniture and plants, 
products can be structured based on site navigation. 
Typically, customers would look for computer desks and get a list of recommendations 
of all computer desks in the shop. 
When necessary, the Personalization service can also use another dimension 
for filtering recommendations, for example, a "brand" dimension. 
In this case, users would get recommendations for all items from the same "brand".

With popularity-based recommendations, you can get the most popular products based on 
the main navigation tree (for example, the most popular desks) or based on the brand 
(for example, the most popular IKEA products).

Here are the examples of common representation dimensions of items beyond the site navigation:

|Business|Possible dimensions|
|---|---|
|eCommerce|manufacturer (BOSCH, Renault, etc.)</br>season (winter, spring, etc.)</br>price range (entry, middle, premium, etc.)</br>platform (Mac, Windows, Linux, etc.)|
|Book store|genre (romance, action, science, etc.)</br>design (hardcover, paperback, audiobook, etc.)</br>author (George R. R. Martin, Steven Spielberg, etc.)|
|Content publishing|global subject (politics, sports, tech, etc.)</br>physical location (France, Norway, Berlin, etc.)</br>timeframe (today, this week, exact date, etc.)|

You should avoid using category filtering with "Also clicked/purchased" and stereotype models. 
These models usually contain similar items, and additional filtering might remove 
the best results from the list of possible recommendations. 
The only exception could be coping with copyright or legal issues by removing 
unlicensed or adult content in certain markets or for certain customers. 
However, this use case could be handled with equal or greater success by using [submodels](recommendation_models.md#submodels) or [item types](content_types.md).

To support category filtering, the Personalization service must be fed with both 
content and user attribute data.
For more information about importing data, see [Importing data](content_import.md).
