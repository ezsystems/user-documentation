# Content types

With the Personalization service, you can build different recommendation domains. 
You do this by splitting all the products into different content types. 
There are several possible use cases for content types, for example:

- A publisher can track articles, pictures and videos as three different types.
- A store can split all the products into food and non-food product groups.
- An owner of several web shops can use a single account for all of them.

Based on the content types concept, it is possible to make so-called cross domain recommendations (like 
"Users who watched this film also read this book" or 
"Users who bought these wallets also bought these belts").

Apart from the logical separation of the content domains, content types provide another 
important advantage. 
You can use them to adjust recommendation weight if different types of products/content items 
are not equally popular but must be recommended equally often. 
For example, on a content publisher's page, users watch videos less often than they read articles. 
If the most popular products were requested without content type splitting, 
there would most likely be no videos in the recommendation result. 
If articles and videos are split into different content types, you can explicitly request 
popular videos and/or popular articles.

Here is a comparison of different approaches that you can take when defining content types:

|Use case|Content types solution (domain context)|Attribute based sub-models (group context)|Different Personalization service accounts|
|---|---|---|---|
|Cross-group recommendation requests are possible|yes|yes|no|
|Products must belong to one group|mandatory|optional|mandatory|
|Products can belong to multiple groups|no|yes|no|
|Single recommendation request can contain products from different groups|no|yes|no|
|Product can change the group it belongs to|no|yes|no|
|Different content types share the scenario and model configuration|yes|yes|no|

### Content types and scenarios

If multiple content types are enabled in your configuration, for every scenario that 
should recommend a specific type, you must enable this output type.
For more information about scenario configuration, see [Scenarios](scenarios.md).
