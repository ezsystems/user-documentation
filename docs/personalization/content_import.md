# Importing data

Before the Personalization service can generate relevant recommendations, 
it must be fed with data that relates to content items/products that are monitored, 
and event tracking information.
Some scenarios return better results if provided with user data.

Data import operations are configured at the developer level, based on the arrangements 
that you make with Ibexa. 
Content item import jobs fetch data from the recommendation client, which tracks events, 
to the Personalization service.
The Personalization service then processes the events and calculates the recommendations.

!!! note "Hosting multiple websites"

    If your installation [hosts multiple websites](use_cases.md#hosting-multiple-websites) and returns separate recommendations
    for each of these websites, you must import data separately for each of these sites.

## Content data import

There are several ways to import data into the Personalization service.
For example, one can load an exported file to the Personalization service from a specified location. 
This type of import is intended to upload big portions of information,
and can be used to perform a weekly update of the whole product catalog.

For detailed information about content data import, see [Export content information](https://doc.ibexa.co/en/latest/guide/personalization/recommendation_client/#exporting-content-information) and [Content API](https://doc.ibexa.co/en/master/guide/personalization/developer_guide/content_api) in the developer documentation.

## User data import

The Personalization service has little information about the users of the website. 
Additional attributes, such as the user's age or home city, might help the service generate 
a successful recommendation, for example, by enabling the use of [boost filters](filters.md#boost-filters).
User attributes could be retrieved based on the external user ID.
However, it is rarely possible to combine the external user ID within the user's attribute set.

For more information about user attribute import, see [User API](https://doc.ibexa.co/en/master/guide/personalization/developer_guide/user_api) in the developer documentation.

## Viewing a list of import operations

In the Back Office, from the top bar under **Personalization**, you can access 
the **Import** page that displays a list of historical import operations and their details, 
such as the number of imported content items/products, their type and language.

![Import tab in the Back Office](img/dashboard_import.png "Import tab")
