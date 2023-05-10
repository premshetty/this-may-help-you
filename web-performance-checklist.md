<div class="crayons-article__body text-styles spec__body" data-article-id="1446004" id="article-body">
            <p>Improving performance of web applications will always be sexy. We want the page to load faster, smoother, and without too many layout shifts (Core Web Vitals, I am looking at you 😉).  In this article I wanted to summarize all this knowledge into one single source of truth (with respect to article authors).</p>

<p>This summary document is based on the following articles:</p>

<h2>
  <a name="preload-key-requests-preconnect-to-required-origins" href="#preload-key-requests-preconnect-to-required-origins">
  </a>
  Preload key requests / Preconnect to required origins
</h2>

<p>Declare preload links in your HTML to instruct the browser to download key resources as soon as possible.<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight html"><code><span class="nt">&lt;head&gt;</span>
  <span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"preload"</span> <span class="na">href=</span><span class="s">"critical.css"</span> <span class="na">as=</span><span class="s">"style"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"preload"</span> <span class="na">href=</span><span class="s">"critical.js"</span> <span class="na">as=</span><span class="s">"script"</span><span class="nt">&gt;</span>
<span class="nt">&lt;/head&gt;</span>
</code></pre>
<div class="highlight__panel js-actions-panel">
<div class="highlight__panel-action js-fullscreen-code-action">
    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-on"><title>Enter fullscreen mode</title>
    <path d="M16 3h6v6h-2V5h-4V3zM2 3h6v2H4v4H2V3zm18 16v-4h2v6h-6v-2h4zM4 19h4v2H2v-6h2v4z"></path>
</svg>

    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-off"><title>Exit fullscreen mode</title>
    <path d="M18 7h4v2h-6V3h2v4zM8 9H2V7h4V3h2v6zm10 8v4h-2v-6h6v2h-4zM8 15v6H6v-4H2v-2h6z"></path>
</svg>

</div>
</div>
</div>



<p>Consider adding preconnect or dns-prefetch resource hints to establish early connections to important third-party origins.<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight html"><code><span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"preconnect"</span> <span class="na">href=</span><span class="s">"https://example.com"</span><span class="nt">&gt;</span>
<span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"dns-prefetch"</span> <span class="na">href=</span><span class="s">"https://example.com"</span><span class="nt">&gt;</span>.
</code></pre>
<div class="highlight__panel js-actions-panel">
<div class="highlight__panel-action js-fullscreen-code-action">
    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-on"><title>Enter fullscreen mode</title>
    <path d="M16 3h6v6h-2V5h-4V3zM2 3h6v2H4v4H2V3zm18 16v-4h2v6h-6v-2h4zM4 19h4v2H2v-6h2v4z"></path>
</svg>

    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-off"><title>Exit fullscreen mode</title>
    <path d="M18 7h4v2h-6V3h2v4zM8 9H2V7h4V3h2v6zm10 8v4h-2v-6h6v2h-4zM8 15v6H6v-4H2v-2h6z"></path>
</svg>

</div>
</div>
</div>



<p>dns-prefetch works exactly the same as preconnect but has wider browser support.</p>

<h2>
  <a name="reduce-thirdparty-usage" href="#reduce-thirdparty-usage">
  </a>
  Reduce third-party usage
</h2>

<p>Third-party code can significantly impact load performance. You can however modify the way you are using this third party library by:</p>

<ul>
<li>Loading the script using the async or defer attribute to avoid blocking document parsing.</li>
<li>Self-hosting the script if the third-party server is slow.</li>
<li>Removing the script if it doesn't add clear value to your site.</li>
<li>Use link rel=preconnect or link rel=dns-prefetch to perform a DNS lookup for domains hosting third-party scripts.</li>
</ul>

<h2>
  <a name="eliminate-render-blocking-resources" href="#eliminate-render-blocking-resources">
  </a>
  Eliminate render blocking resources
</h2>

<p>Resources are blocking the first paint of your page. Consider delivering critical JS/CSS inline and deferring all non-critical JS/styles. You can reduce the size of your pages by only shipping the code and styles that you need.</p>

<p>Once you've identified critical code, move that code from the render-blocking URL to an inline script tag in your HTML page.</p>

<p>Inline critical styles required for the first paint inside a style block at the head of the HTML page and load the rest of the styles asynchronously using the preload link.</p>

<p>You can read more about this <a href="https://sia.codes/posts/render-blocking-resources/#how-do-i-test-my-website-for-render-blocking-resources%3F">here</a></p>

<h2>
  <a name="minifyremove-unnecessary-css-and-js" href="#minifyremove-unnecessary-css-and-js">
  </a>
  Minify/Remove unnecessary CSS and JS
</h2>

<p>When you are building a big application, you will get to a place where your project may have much more code that it actually needs and uses.</p>

<p>Use tools like <a href="https://web.dev/minify-css/#css-minification-with-webpack">CSS Minification</a> or <a href="https://github.com/terser/terser">Terser JS Plugin</a>.</p>

<p>To eliminate unused css use a tool like <a href="https://purgecss.com/">PurgeCSS</a>.</p>

<p>To eliminate unnecessary JavaScript you can use Terser mentioned previously or utilize <a href="https://webpack.js.org/guides/tree-shaking/">Tree Shaking</a> to allow Dead Code Elimination. You can also use <a href="https://developer.mozilla.org/en-US/docs/Glossary/Code_splitting">Code Splitting</a> which will split code into bundles that can be loaded on demand.</p>

<h3>
  <a name="scan-modules-for-duplicates" href="#scan-modules-for-duplicates">
  </a>
  Scan modules for duplicates
</h3>

<p>Remove large, duplicate JavaScript modules from bundles to reduce final bundle size.</p>

<p><a href="https://res.cloudinary.com/practicaldev/image/fetch/s--IR1cNC44--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/m8jgv7d98jpb0cwdz2gt.png" class="article-body-image-wrapper"><img src="https://res.cloudinary.com/practicaldev/image/fetch/s--IR1cNC44--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/m8jgv7d98jpb0cwdz2gt.png" alt="image" loading="lazy" width="800" height="405"></a></p>

<p>Use <a href="https://www.npmjs.com/package/webpack-bundle-analyzer">Webpack Bundle Analyzer</a></p>

<h2>
  <a name="reduce-execution-time" href="#reduce-execution-time">
  </a>
  Reduce execution time
</h2>

<p>The combination of code splitting, minification and compression, removal of unused code and caching techniques will greatly improve execution time.</p>

<p>Consider reducing the time spent parsing, compiling and executing JS. You may find delivering smaller JS payloads helps with this.<br>
The idea is to optimize both our JS and CSS code, minimizing it and removing unused code, as well as the third-party libraries we are using.</p>

<p>Keep the server response time for the main document short because all other requests depend on it.</p>

<p>You can read more about this <a href="https://gtmetrix.com/reduce-javascript-execution-time.html">here</a></p>
<h2>
  <a name="image-handling" href="#image-handling">
  </a>
  Image handling
</h2>
<h3>
  <a name="properly-size-images" href="#properly-size-images">
  </a>
  Properly size images
</h3>

<p>Serve images that are appropriately-sized to save cellular data and improve load time.<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight html"><code><span class="nt">&lt;img</span> <span class="na">src=</span><span class="s">"cat-large.jpg"</span> <span class="na">srcset=</span><span class="s">"cat-small.jpg 480w, cat-large.jpg 1080w"</span> <span class="na">sizes=</span><span class="s">"50vw"</span><span class="nt">&gt;</span>
</code></pre>
<div class="highlight__panel js-actions-panel">
<div class="highlight__panel-action js-fullscreen-code-action">
    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-on"><title>Enter fullscreen mode</title>
    <path d="M16 3h6v6h-2V5h-4V3zM2 3h6v2H4v4H2V3zm18 16v-4h2v6h-6v-2h4zM4 19h4v2H2v-6h2v4z"></path>
</svg>

    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-off"><title>Exit fullscreen mode</title>
    <path d="M18 7h4v2h-6V3h2v4zM8 9H2V7h4V3h2v6zm10 8v4h-2v-6h6v2h-4zM8 15v6H6v-4H2v-2h6z"></path>
</svg>

</div>
</div>
</div>



<p>You can read more about this <a href="https://web.dev/uses-responsive-images/?utm_source=lighthouse&amp;utm_medium=cli">here</a></p>

<h3>
  <a name="efficiently-encode-images" href="#efficiently-encode-images">
  </a>
  Efficiently encode images
</h3>

<p>Optimized images load faster and consume less cellular data.<br>
Using your image CDN service or the compression of your image should be enough.</p>

<p>You can read more about this <a href="https://web.dev/uses-optimized-images/">here</a></p>

<p>And also you can read an article that I have released some time ago <a href="https://dev.to/jacobandrewsky/optimizing-images-in-js-apps-with-ipx-37b1">here</a></p>
<h3>
  <a name="serve-images-in-nextgen-formats" href="#serve-images-in-nextgen-formats">
  </a>
  Serve images in next-gen formats
</h3>

<p>Image formats like WebP or Avif often provide better compression than PNG or JPEG, which means faster downloads and less data consumption.</p>

<p>You can read more about this <a href="https://web.dev/uses-webp-images/">here</a></p>
<h3>
  <a name="image-elements-have-explicit-width-and-height" href="#image-elements-have-explicit-width-and-height">
  </a>
  Image elements have explicit width and height
</h3>

<p>Set an explicit width and height on image elements to reduce layout shifts and improve CLS.</p>

<p>You can read more about this <a href="https://gtmetrix.com/use-explicit-width-and-height-on-image-elements.html">here</a></p>
<h3>
  <a name="preload-largest-contentful-paint-lcp" href="#preload-largest-contentful-paint-lcp">
  </a>
  Preload largest contentful paint (LCP)
</h3>

<p>Preload the image used by the LCP element in order to improve your LCP time.<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight html"><code><span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"preload"</span> <span class="na">href=</span><span class="s">"/path/to/image.jpg"</span> <span class="na">as=</span><span class="s">"image"</span><span class="nt">&gt;</span>
</code></pre>
<div class="highlight__panel js-actions-panel">
<div class="highlight__panel-action js-fullscreen-code-action">
    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-on"><title>Enter fullscreen mode</title>
    <path d="M16 3h6v6h-2V5h-4V3zM2 3h6v2H4v4H2V3zm18 16v-4h2v6h-6v-2h4zM4 19h4v2H2v-6h2v4z"></path>
</svg>

    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-off"><title>Exit fullscreen mode</title>
    <path d="M18 7h4v2h-6V3h2v4zM8 9H2V7h4V3h2v6zm10 8v4h-2v-6h6v2h-4zM8 15v6H6v-4H2v-2h6z"></path>
</svg>

</div>
</div>
</div>





<div class="highlight js-code-highlight">
<pre class="highlight javascript"><code><span class="nx">head</span><span class="p">()</span> <span class="p">{</span>
 <span class="k">return</span> <span class="p">{</span>
    <span class="na">link</span><span class="p">:</span> <span class="p">[</span>
      <span class="p">{</span>
        <span class="na">rel</span><span class="p">:</span> <span class="dl">'</span><span class="s1">preload</span><span class="dl">'</span><span class="p">,</span>
        <span class="na">as</span><span class="p">:</span> <span class="dl">'</span><span class="s1">image</span><span class="dl">'</span><span class="p">,</span>
        <span class="na">href</span><span class="p">:</span> <span class="dl">'</span><span class="s1">path/to/lcp/image</span><span class="dl">'</span><span class="p">,</span>
      <span class="p">},</span>
    <span class="p">],</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
<div class="highlight__panel js-actions-panel">
<div class="highlight__panel-action js-fullscreen-code-action">
    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-on"><title>Enter fullscreen mode</title>
    <path d="M16 3h6v6h-2V5h-4V3zM2 3h6v2H4v4H2V3zm18 16v-4h2v6h-6v-2h4zM4 19h4v2H2v-6h2v4z"></path>
</svg>

    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-off"><title>Exit fullscreen mode</title>
    <path d="M18 7h4v2h-6V3h2v4zM8 9H2V7h4V3h2v6zm10 8v4h-2v-6h6v2h-4zM8 15v6H6v-4H2v-2h6z"></path>
</svg>

</div>
</div>
</div>



<p>You can read more about this <a href="https://gtmetrix.com/preload-largest-contentful-paint-image.html#:~:text=Preloading%20the%20Largest%20Contentful%20Paint,sooner%2C%20enhancing%20their%20user%20experience.">here</a></p>

<h2>
  <a name="fonts" href="#fonts">
  </a>
  Fonts
</h2>

<h3>
  <a name="all-text-remains-visible-during-webfont-loads" href="#all-text-remains-visible-during-webfont-loads">
  </a>
  All text remains visible during webfont loads
</h3>

<p>Leverage the font-display CSS feature to ensure text is user-visible while webfonts are loading.<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight css"><code><span class="k">@font-face</span> <span class="p">{</span>
  <span class="nl">font-family</span><span class="p">:</span> <span class="s2">'Arial'</span><span class="p">;</span>
  <span class="py">font-display</span><span class="p">:</span> <span class="n">swap</span><span class="p">;</span>
<span class="p">}</span>
</code></pre>
<div class="highlight__panel js-actions-panel">
<div class="highlight__panel-action js-fullscreen-code-action">
    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-on"><title>Enter fullscreen mode</title>
    <path d="M16 3h6v6h-2V5h-4V3zM2 3h6v2H4v4H2V3zm18 16v-4h2v6h-6v-2h4zM4 19h4v2H2v-6h2v4z"></path>
</svg>

    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-off"><title>Exit fullscreen mode</title>
    <path d="M18 7h4v2h-6V3h2v4zM8 9H2V7h4V3h2v6zm10 8v4h-2v-6h6v2h-4zM8 15v6H6v-4H2v-2h6z"></path>
</svg>

</div>
</div>
</div>



<p>The font-display API specifies how a font is displayed. swap tells the browser that text using the font should be displayed immediately using a system font. Once the custom font is ready, it replaces the system font.</p>

<p>For Google fonts, for example, is as simple as adding the &amp;display=swap parameter to the end to the Google Fonts URL:<br>
</p>

<div class="highlight js-code-highlight">
<pre class="highlight html"><code><span class="nt">&lt;link</span> <span class="na">href=</span><span class="s">"https://fonts.googleapis.com/css?family=Roboto:400,700&amp;**display=swap**"</span> <span class="na">rel=</span><span class="s">"stylesheet"</span><span class="nt">&gt;</span>
</code></pre>
<div class="highlight__panel js-actions-panel">
<div class="highlight__panel-action js-fullscreen-code-action">
    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-on"><title>Enter fullscreen mode</title>
    <path d="M16 3h6v6h-2V5h-4V3zM2 3h6v2H4v4H2V3zm18 16v-4h2v6h-6v-2h4zM4 19h4v2H2v-6h2v4z"></path>
</svg>

    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" viewBox="0 0 24 24" class="highlight-action crayons-icon highlight-action--fullscreen-off"><title>Exit fullscreen mode</title>
    <path d="M18 7h4v2h-6V3h2v4zM8 9H2V7h4V3h2v6zm10 8v4h-2v-6h6v2h-4zM8 15v6H6v-4H2v-2h6z"></path>
</svg>

</div>
</div>
</div>



<p>You can read more about this <a href="https://web.dev/font-display/">here</a></p>

<h2>
  <a name="what-to-avoid" href="#what-to-avoid">
  </a>
  What to avoid?
</h2>

<h3>
  <a name="large-layout-shifts" href="#large-layout-shifts">
  </a>
  Large layout shifts
</h3>

<p>Cumulative Layout Shift (CLS) is a Core Web Vitals metric calculated by summing all layout shifts that aren’t caused by user interaction.</p>

<h3>
  <a name="avoid-an-excessive-dom-size" href="#avoid-an-excessive-dom-size">
  </a>
  Avoid an excessive DOM size
</h3>

<p>A large DOM will increase memory usage, cause longer style calculations, and produce costly layout reflows.</p>

<h3>
  <a name="multiple-page-redirects" href="#multiple-page-redirects">
  </a>
  Multiple page redirects
</h3>

<p>Redirects introduce additional delays before the page can be loaded.</p>

<h3>
  <a name="serving-legacy-javascript-to-modern-browsers" href="#serving-legacy-javascript-to-modern-browsers">
  </a>
  Serving legacy JavaScript to modern browsers
</h3>

<p>Polyfills and transforms enable legacy browsers to use new JavaScript features. However, many aren't necessary for modern browsers.</p>

<h3>
  <a name="enormous-network-payloads" href="#enormous-network-payloads">
  </a>
  Enormous network payloads
</h3>

<p>Large network payloads cost users real money and are highly correlated with long load times.</p>

<ul>
<li>Defer requests until they're needed. </li>
<li>Optimize requests to be as small as possible, minimizing and compressing, try to use WebP for the images when it's possible. An image CDN will be always there to keep our performance up!</li>
<li>Cache requests so the page doesn't re-download the resources on repeat visits.</li>
</ul>

<h3>
  <a name="documentwrite" href="#documentwrite">
  </a>
  Document.write()
</h3>

<p>For users on slow connections, external scripts dynamically injected via document.write() can delay page load by tens of seconds.</p>

<h3>
  <a name="noncompositioned-animations" href="#noncompositioned-animations">
  </a>
  Non-compositioned animations
</h3>

<p>Animations which are not composited can be heavy and increase CLS. Use <code>translate</code> and <code>scale</code> CSS properties instead.</p>

<h2>
  <a name="summary" href="#summary">
  </a>
  Summary
</h2>

<p>You now know more about improving web performance. Just please remember that improving performance is not an issue that you can just sit once and fix. It is a continuous process and the topic of performance should be addressed regularly so that new features of your website (for sure needed) won't break the performance.</p>
