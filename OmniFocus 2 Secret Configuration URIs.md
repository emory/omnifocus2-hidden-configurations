# Hidden Configuration Options for OmniFocus 2 (OS X)

> A commonly referenced collection of these was published in a post from May 22, 2014 by Jeroen Sangers, originally posted at [braintags.com](http://braintags.com/blog/2014/05/omnifocus-2-configuration/) but currently [^1] available at [https://jeroensangers.wordpress.com/2014/05/22/omnifocus-2-configuration/](https://jeroensangers.wordpress.com/2014/05/22/omnifocus-2-configuration/). This document hopes to be equally useful and may end up receiving updates.
> — @emory (github) @incumbent (twitter)

## Secret Handshake URLs

All configuration options are activated by opening a special URL starting with omnifocus:///change-preference in a browser or other application that accepts a URI, which will open OmniFocus and apply the configuration option. 

The URLs in the list are clickable to apply the configuration directly from this post.

### ALTERNATE LAYOUT

* Switch to the compact layout, which only uses one line per task:
 * omnifocus:///change-preference?ContentLayout=compact 

Note that this layout is experimental and still has some issues. 

* To return to the default layout:
 * omnifocus:///change-preference?ContentLayout

### HIDE EMPTY CONTEXTS IN THE MAIN OUTLINE

If you’re in a perspective grouped by context, you’ll see that empty perspectives will also show up in the main outline, to mike it easier to reassign tasks by dragging them to another context. If you would rather not see them, you can remove the empty contexts from the main outline: 

* [omnifocus:///change-preference?MainOutlineIncludesEmptyContexts=false](omnifocus:///change-preference?MainOutlineIncludesEmptyContexts=false)

You can also pass the parameter `true` to reactivate the empty contexts.

### HIDE ON HOLD PROJECTS IN FORECAST VIEW

If you put a project on hold, it’s tasks will still show up in the forecast view. The reasoning is that even though the project is on hold, its tasks still have a due date. If you prefer not to see those tasks on the forecast view, disable them using:

* [omnifocus:///change-preference?ForecastIncludesProjectsOnHold=false](omnifocus:///change-preference?ForecastIncludesProjectsOnHold=false)

To restore the default behavior:

* [omnifocus:///change-preference?ForecastIncludesProjectsOnHold](omnifocus:///change-preference?ForecastIncludesProjectsOnHold)

### REORGANISE THE SIDE BAR

This 'hack' is a little bit more complicated. The issue was that the order of the perspectives in the sidebar could not be reorganised. Note that in the final release the default perspectives behave just like any other perspective, and can be organised in any way you like it. However, if you want to freak out with URL schemes, this is the way.

The default perspectives are on top (Inbox, Projects, Contexts…), followed by any starred perspectives. To add another perspective, you first have to star the perspective and open the URL:

* [omnifocus:///change-preference?SidebarTabs](omnifocus:///change-preference?SidebarTabs)

Which will return a list of the current tabs. *Note the ID of the starred perspective*.

Once you know the ID of your custom perspective, you can define the order of the tabs with (unclickable, edit to your environment):

* omnifocus:///change-preference?SidebarTabs=(hdDT8UyDkVe,ForecastTab,InboxTab)

### SEND CLIPPINGS DIRECTLY TO THE INBOX

Whenever you clip something from another application, the Quick Entry window shows up so you can specify some further meta-information about the task — project, context, dates… — and change the task description. If you would rather send the clipped information directly to the Omnifocus inbox, use the configuration URL 

* [omnifocus:///change-preference?ClippingsGoToQuickEntry=false](omnifocus:///change-preference?ClippingsGoToQuickEntry=false)

### SYNC SETTINGS

There are two setting for configuring the synchronisation interval. First, you can set the maximum sync time ***in seconds*** with:

* [omnifocus:///change-preference?MaximumTimeBetweenSync=600](omnifocus:///change-preference?MaximumTimeBetweenSync=600)
 * This sets the maximum to 10 minutes.
 
* [omnifocus:///change-preference?MaximumTimeBetweenSync](omnifocus:///change-preference?MaximumTimeBetweenSync)
 * To restore the default setting of one hour.

The other option is for setting how long after making an edit Omnifocus should synchronise. The URL is:

* [omnifocus:///change-preference?TimeFromFirstEditToSync=15](omnifocus:///change-preference?TimeFromFirstEditToSync=15)
* [omnifocus:///change-preference?TimeFromFirstEditToSync](omnifocus:///change-preference?TimeFromFirstEditToSync)
 * To get back to the default setting of one minute.

### TOOLBAR COLOUR

If you have setup your mac to use the ‘Graphite’ appearance instead of the default ‘Blue’ theme, Omnifocus will have black and white icons in the toolbar instead of the modern coloured icons. If you prefer this to be different, you can use 

* omnifocus:///change-preference?ToolbarItemTint=aqua
 * to force the use of coloured buttons or 
* omnifocus:///change-preference?ToolbarItemTint=graphite 
 * to get the black and white icons in the toolbar. 
 
As usual, with `omnifocus:///change-preference?ToolbarItemTint` you’ll go back to the default setting.

### SET DEFER DATE WHEN DRAGGING A TASK IN FORECAST VIEW

This option was contributed by Colter in the comments of this post. When in Forecast view, you can drag a task to another date in the calendar to change its due date. You can change the defer date instead by holding the ⌘ key. If you would like to change the defer date by default, you can use the URL omnifocus:///change-preference?ForecastDragSetsDeferDate=true.

### CHANGE THE PROJECT HIERARCHY SEPARATOR CHARACTER

If you’re using folders, OmniFocus will show the complete path in the project selection drop-down list using a colon as the hierarchy separation character, e.g. Personal : Finance. You can configure the character used to separate the project hierarchy with the URL:

* omnifocus:///change-setting?OFMNamedObjectHierarchicalNameSeparator=%20:%20 
 * Note that `%20` is the code for a `space`).


----

[^1]: I saw [this thread](https://discourse.omnigroup.com/t/is-there-a-list-of-urls-to-change-all-the-hidden-preferences/3723) on the OmniGroup Discourse on 2016-06-21.