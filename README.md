# poc-lcp-render-order
This POC shows how the render order matters (at least on chrome) for LCP when you have a big HTML.

### Quick start
* `npm i`
* `node index.js`
* Access `http://localhost/cookie-notice.html` on Chrome
* Open Devtools and go to Performance Tab
* Set up throttling ***Fast 3g*** and ***4x slow CPU***
* Click on the refresh icon on Performance Tab
* Open `/public/cookie-notice.html` on your code editor
* Move `<div id="cooki-notice">Cookie notice</div>` from last element in the body to first element in the body
* Click on the refresh icon on Performance Tab again

### POC explanation and result showcase
In this example we have a cookie notice which is our LCP element and we are rendering it as last element of the body. To make
the HTML big I added a lot of links to the page.

When we load the page using the performance tab on Chrome Devtools (using ***Fast 3g*** and ***4x slow CPU***) we can see in the screenshots that
the first paint only paint the links and then in a second paint the cookie notice shows up. Running on my computer the LCP for this test is around ***3.2s***. See screenshots for first scenario on the screenshots folder.

After we move the Cookie Notice div up in the DOM to be the first element in the body and refresh the page on Performancce Tab we can see...
See screenshots for second scenario on the screenshots folder.
