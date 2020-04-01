# Publishing Content

When you **Publish** a Content item, it is given a Location ID and placed in the Content tree.
It is then immediately available to the visitor.

Instead of instantly publishing you can also save, discard changes, [publish later](advanced_publishing_options.md#date-based-publishing) and [send for review](editorial_workflow.md).
All these options are available in the menu when you are in the edit mode.

![Publishing options](img/publishing_options.png "Publishing options")

### Publishing vs. saving

Choosing **Save** does not immediately publish the Content item.
Instead, it will save the new version of the content as a **draft**.
You can then keep on editing the same content and save it again when needed.
You can then leave the editor by using the **X** icon in the upper left corner, it will also save the working copy as a draft.

!!! caution

    Only selecting **Delete draft** removes the whole draft and all the work you have done on it.
    A discarded draft is removed instantly, not placed in the Trash, so it can't be restored.
    The **X** icon in the upper left corner and the browser's **back button** will save the current Content item as a draft.

Once you leave the editor after saving your draft, you can return to modify it, or create a new draft.
To edit an existing draft, go to the **Versions** tab and click the edit icon in the proper line.
When you select **Edit** in a Content item that has one or more open drafts, you will be asked which draft you want to continue working on.
You will also have the option to create a new draft based on the currently published version.

Note that you cannot edit an unpublished draft created by another user.

### Content versions

Content in the repository can have more than one version.
Each version is either published, archived, or a draft.

The **published version** is the version that is currently used on the website.
Every Content item can have only one published version at a time.

Whenever you edit and publish a Content item again, its previous published version becomes an **archived version**.
It is not available to the visitor and you cannot edit it, but you can create new drafts based on any archived version.

Finally, **drafts** are version that have not been published yet.

You can view all versions of a Content item in the **Versions** tab.

![All versions of a Content item](img/content_item_versions.png "All versions of a Content item")

#### Comparing versions

You can compare two versions of the same Content item by clicking the compare icon
in the Versions tab:

![](img/compare_icon.png)

Select the two version you want to compare in the drop-down menus at the top of the screen.

![](img/compare_results_2_col.png "Version comparison in two-column view")

You can also choose to view the comparison in two columns, side by side,
or in one column, with differences highlighted.

![](img/compare_results_1_col.png "Version comparison in one-column view")

!!! note

    Not all Field Types are available for comparison. You cannot preview the difference in the following Field Types:

    - Content Relation and Content Relations
    - Image Asset and Image
    - Form
    - Landing Page
    - Matrix
    - Media
    - User account
