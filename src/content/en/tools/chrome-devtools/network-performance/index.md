project_path: /web/tools/_project.yaml
book_path: /web/tools/_book.yaml
description: TODO

{# wf_updated_on: 2019-02-04 #}
{# wf_published_on: 2019-02-01 #}
{# wf_blink_components: Platform>DevTools #}

# Inspect Network Activity In Chrome DevTools {: .page-title }

{% include "web/_shared/contributors/kaycebasques.html" %}

This hands-on tutorial teaches you how to use Chrome DevTools to inspect a web page's
network activity.

## When to use the Network panel {: #overview }

In general, use the Network panel when you need to make sure that resources are being
downloaded or uploaded as expected. The most common use cases for the Network panel are:

* Making sure that resources are actually being uploaded or downloaded at all.
* Inspecting the properties of an individual resource, such as its HTTP headers, content,
  size, and so on.

[speed]: /web/tools/chrome-devtools/speed/get-started

If you're looking for ways to improve page load performance, *don't* start with the Network
panel. There are many types of load performance issues that aren't related to network
activity. Start with the Audits panel because it gives you targeted suggestions on how to
improve your page. See [Optimize Website Speed][speed].

## Open the Network panel {: #open }

This is a hands-on tutorial. You're going to open up DevTools alongside web pages
in order to gain firsthand experience with the Network panel.

1. Open the [Get Started Demo](https://devtools.glitch.me/network/basics.html){: .external }.

     You might prefer to move the demo to a separate window.

1. [Open DevTools](/web/tools/chrome-devtools/open) by pressing
   <kbd>Control</kbd>+<kbd>Shift</kbd>+<kbd>J</kbd> or 
   <kbd>Command</kbd>+<kbd>Option</kbd>+<kbd>J</kbd> (Mac). The **Console**
   panel opens.
1. Click the **Network** tab. The Network panel opens.

     You might prefer to dock DevTools to the bottom of your window.

Right now the Network panel is empty. That's because DevTools only logs network activity
while it's open and no network activity has occurred since you opened DevTools.

## Log network activity {: #load }

To view the network activity that a page causes:

[reload]: /web/tools/chrome-devtools/images/shared/reload.png

1. Click **Reload** ![Reload][reload]{: .inline-icon }. The Network panel logs all network
   activity that occurs while the page is loading in the **Network Log**.

     Each row of the **Network Log** represents a resource.

     By default the resources are listed chronologically. The network activity for the top
     resource initiated first, and the network activity for the bottom resource initiated last.

     When inspecting page load network activity, the top resource is usually the network request
     for the main HTML document.

1. So long as you've got DevTools open, it will record network activity in the Network Log.
   To demonstrate this, first look at the bottom of the **Network Log** and make a mental
   note of the last activity.
1. Now, click the **Get Data** button in the demo.
1. Look at the bottom of the **Network Log** again. There's a new resource called
   `getstarted.json`. Clicking the **Get Data** button caused the page to request this file.

## Show more information {: #information }

The columns of the Network Log are configurable. You can hide columns that you're not using.
There are also many columns that are hidden by default which you may find useful.

1. Right-click the header of the Network Log table and select **Method**. The HTTP request
   method for each resource is now shown.

## Simulate a slower network connection {: #throttle }

The network connection of the computer that you use to build sites is probably
faster than the network connections of the mobile devices of your users. By throttling
the page you can get a better idea of how long a page takes to load on a mobile device.

1. Click the **Throttling** dropdown, which is probably set to **Online**.
1. Select **Slow 3G**.
1. Long-press **Reload** ![Reload][reload]{: .inline-icon }
   and then select **Empty Cache And Hard Reload**.

[cache]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching

     On repeat visits, the browser usually serves some files from its [cache][cache]{: .external },
     which speeds up the page load. **Empty Cache And Hard Reload** forces the browser to go
     the network for all resources. This is helpful when you want to see how a first-time
     visitor experiences a page load.

<aside class="objective">
  <b>Tip!</b> See <a href="/web/tools/chrome-devtools/device-mode/">Simulate Mobile Devices
  With Device Mode</a> to discover other DevTools features related to simulating
  mobile devices, such as overriding geolocation and simulating device orientations.
</aside>

## Inspect a resource's details {: #details }

To view more information about a particular resource:

1. Click `getstarted.html`. The **Headers** tab is shown.

1. Click the **Preview** tab. A basic rendering of the HTML is shown.

     This tab is helpful when an API returns an error code in HTML and it's easier to read
     the rendered HTML than the HTML source code, or when inspecting images.

1. Click the **Response** tab. The HTML source code is shown.

1. Click the **Timing** tab. A breakdown of the network activity for this resource is shown.

## Search network headers and responses {: #search }

Use the **Search** pane when you need to search the HTTP headers and responses of all resources
for a certain string or regular expression.

[policies]: /web/tools/lighthouse/audits/cache-policy

For example, suppose you want to check if your resources are using reasonable [cache
policies][policies].

[search]: /web/tools/chrome-devtools/images/shared/search.png

1. Click **Search** ![Search][search]{: .inline-icon }. The Search pane opens to the left
   of the Network log.

1. Type `Cache-Control` and press <kbd>Enter</kbd>. The Search pane lists all instances of
   `Cache-Control` that it finds in resource headers or responses.

## Filter resources {: #filter }

DevTools provides numerous workflows for filtering out irrelevant resources.

To enable filters:

[filter]: /web/tools/chrome-devtools/images/shared/filter.png

1. Click **Filter** ![Filter][filter]{: .inline-icon }. The Filters pane opens below the
   Toolbar.

### Filter by resource type {: #type }

Hold Command and click to select multiple.

## Block requests {: #block }

1. Press <kbd>Control</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> or
   <kbd>Command</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (Mac) to open the **Command Menu**.
1. Type `block`, select **Show Request Blocking**, and press <kbd>Enter</kbd>.

[add]: /web/tools/chrome-devtools/images/shared/add.png

1. Click **Add Pattern** ![Add Pattern][add]{: .inline-icon }.
1. Type `main.css`.
1. Click **Add**.
1. Reload the page. The page's styling is messed up because its stylesheet has been blocked.

     Note the `main.css` row in the Network Log. The red text means that the resource was blocked.

## Next steps {: #next-steps }

Check out the [Network Reference](/web/tools/chrome-devtools/network-performance/reference)
to discover more DevTools features related to inspecting network activity.

## Test your knowledge {: #test }

Answer the questions below to reinforce the knowledge and skills that you learned throughout
this tutorial.

<div class="devsite-tracking-question">
  <div>
    When figuring out how to improve load performance, the Network panel is the best place
    to start.
  </div>
  <div class="gc-analytics-event"
       data-category="TODO" data-value="1"
       data-label="TODO">
    <div>True</div>
    <div>TODO</div>
  </div>
  <div class="gc-analytics-event"
       data-category="TODO" data-value="0"
       data-label="TODO">
    <div>False</div>
    <div>TODO</div>
  </div>
</div>

<div class="devsite-tracking-question">
  <div>
    Sometimes the Network panel is empty. Why is that?
  </div>
  <div class="gc-analytics-event"
       data-category="TODO" data-value="1"
       data-label="TODO">
    <div>Because DevTools only logs network activity when it's open.</div>
    <div>Correct.</div>
  </div>
  <div class="gc-analytics-event"
       data-category="TODO" data-value="0"
       data-label="TODO">
    <div>Because something is broken.</div>
    <div>Incorrect. Please try again.</div>
  </div>
</div>

## Feedback {: #feedback }

{% include "web/_shared/helpful.html" %}
