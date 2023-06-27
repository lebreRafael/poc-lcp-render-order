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
the first paint only paint the links and then in a second paint the cookie notice shows up. Running on my computer the LCP for this test is around ***3.2s***.

<img width="1512" alt="Screen Shot 2023-06-27 at 11 01 14" src="https://github.com/lebreRafael/poc-lcp-render-order/assets/13899924/adba33e4-53d4-4c49-b3b8-d573814e1059">

After we move the Cookie Notice div up in the DOM to be the first element in the body and refresh the page on Performancce Tab we can see...
