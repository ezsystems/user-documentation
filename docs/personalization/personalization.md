# Introduction to personalization

A cloud-based Personalization service leverages artificial intelligence and machine learning 
technologies to deliver optimized customer experience. 
You can capture user preferences and interests to generate recommendations 
that can be used to offer personalized content to visitors of one or more websites 
hosted by the [[= product_name =]] instance.

There are different areas where you can apply recommendations. 
The most common ones are [eCommerce and content publishing](use_cases.md).

!!! note "eCommerce vs. content publishing"

    This guide mentions eCommerce use cases more often,
    but provides a thorough understanding of the content publishing context as well.

    Both products and Content items can be referred to as content and the BUY [event](event_types.md) can be understood as
    the CONSUME event.

Before you can use the Personalization service, you must [enable it](enabling_personalization.md).
Then, for the service to generate relevant recommendations, 
you can [change the default configuration](perso_configuration.md).
Finally, you can [feed it with data](content_import.md), or wait until the service 
gathers enough information about the [monitored content](content_types.md) and events. 
On a website with more than 100 clicks per day, a day of collecting data should 
be sufficient for the first recommendations to be relevant.
Recommendations become better with time and the amount of data collected.

Once the service generates the results, you can present them to the user 
by embedding recommendation lists in your pages and screens.
Both event tracking and results publishing is done by the administrators, according 
to the procedure [described in the developer documentation](https://doc.ibexa.co/en/latest/guide/personalization/personalization_quickstart/#integration).
