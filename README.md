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


<img width="1512" alt="Screen Shot 2023-06-27 at 11 03 55" src="https://github.com/lebreRafael/poc-lcp-render-order/assets/13899924/f8ab03a7-1d8c-43fd-ae7e-66b08f3aec60">
<img width="1512" alt="Screen Shot 2023-06-27 at 11 04 02" src="https://github.com/lebreRafael/poc-lcp-render-order/assets/13899924/e13643f6-3ac8-4ffa-a5fc-43f96953225e">


After we move the Cookie Notice div up in the DOM to be the first element in the body and refresh the page on Performancce Tab we can see that the first paint already paints the Cookie Notice and the LCP is now around 700ms

<img width="1512" alt="Screen Shot 2023-06-27 at 11 07 41" src="https://github.com/lebreRafael/poc-lcp-render-order/assets/13899924/3e004062-005e-4fea-a526-7d1036151727">
<img width="1512" alt="Screen Shot 2023-06-27 at 11 07 54" src="https://github.com/lebreRafael/poc-lcp-render-order/assets/13899924/5dac7b59-fea3-49a2-8cd5-fc78b0b8d43c">
<img width="1512" alt="Screen Shot 2023-06-27 at 11 08 07" src="https://github.com/lebreRafael/poc-lcp-render-order/assets/13899924/10d73a64-580a-4c51-bb4a-39e12f23676d">


