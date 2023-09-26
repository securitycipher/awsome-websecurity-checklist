<p style="text-align: justify;"><span>Security headers are directives used by web applications to configure security defenses in web browsers. Based on these directives, browsers can make it harder to exploit client-side vulnerabilities such as Cross-Site Scripting or Clickjacking. Headers can also be used to configure the browser to only allow valid TLS communication and enforce valid certificates, or even enforce using a specific server certificate.</span></p>

<table style="height: 168px; width: 100%; border-collapse: collapse;" border="1">
<tbody>
<tr style="height: 24px;">
<td style="width: 13.9274%; height: 24px;"><strong>Headers</strong></td>
<td style="width: 23.3123%; height: 24px;"><strong>What it does</strong></td>
<td style="width: 19.8423%; height: 24px;"><strong>Why it's Important</strong></td>
<td style="width: 22.918%; height: 24px;"><strong>Example</strong></td>
</tr>
<tr style="height: 24px;">
<td style="width: 13.9274%; height: 24px;"><strong>Strict-Transport-Security</strong></td>
<td style="width: 23.3123%; height: 24px;">Ensures that a website is only accessed over a secure, encrypted connection (HTTPS).</td>
<td style="width: 19.8423%; height: 24px;">Protects sensitive data by preventing it from being sent over unsecured connections.</td>
<td style="width: 22.918%; height: 24px;">When you visit "example.com," your browser automatically uses HTTPS, even if you type "example.com" in the address bar.</td>
</tr>
<tr style="height: 24px;">
<td style="width: 13.9274%; height: 24px;"><strong>X-Frame-Options</strong></td>
<td style="width: 23.3123%; height: 24px;">Controls whether a web page can be displayed inside an iframe on another website.</td>
<td style="width: 19.8423%; height: 24px;">Prevents clickjacking attacks, where a malicious site can trick you into taking unintended actions.</td>
<td style="width: 22.918%; height: 24px;">Prevents other websites from embedding "example.com" within their own pages without permission.</td>
</tr>
<tr style="height: 24px;">
<td style="width: 13.9274%; height: 24px;"><strong>X-Content-Type-Options</strong></td>
<td style="width: 23.3123%; height: 24px;">Specifies how web browsers should handle content types (MIME types) sent by the server.</td>
<td style="width: 19.8423%; height: 24px;">Helps prevent certain types of web vulnerabilities by ensuring browsers interpret content types correctly.</td>
<td style="width: 22.918%; height: 24px;">Ensures that if "example.com" serves a JavaScript file, it's treated as JavaScript and not as a different type of file.</td>
</tr>
<tr style="height: 24px;">
<td style="width: 13.9274%; height: 24px;"><strong>Content-Security-Policy</strong></td>
<td style="width: 23.3123%; height: 24px;">Defines which sources of content (e.g., scripts, images) are allowed to be loaded on a web page.</td>
<td style="width: 19.8423%; height: 24px;">Mitigates cross-site scripting (XSS) and data injection attacks by restricting what can be loaded.</td>
<td style="width: 22.918%; height: 24px;">"example.com" specifies that only scripts from its own domain are allowed to run, preventing external scripts from running.</td>
</tr>
<tr style="height: 24px;">
<td style="width: 13.9274%; height: 24px;"><strong>Cache-Control</strong></td>
<td style="width: 23.3123%; height: 24px;">Sets rules for how a web page or resource should be cached by the browser or proxy servers.</td>
<td style="width: 19.8423%; height: 24px;">Helps control how often a browser fetches fresh content, improving website performance and security.</td>
<td style="width: 22.918%; height: 24px;">"example.com" instructs browsers to cache images for 24 hours, so they load faster for returning visitors.</td>
</tr>
<tr style="height: 24px;">
<td style="width: 13.9274%; height: 24px;"><strong>Referrer-Policy</strong></td>
<td style="width: 23.3123%; height: 24px;">Determines what information is sent as the "referrer" when you click on a link to another website.</td>
<td style="width: 19.8423%; height: 24px;">Protects user privacy by controlling what data is shared with other websites when you navigate between them.</td>
<td style="width: 22.918%; height: 24px;">"example.com" can specify that it won't send the full URL of the page you were on before clicking a link to another site, protecting your privacy.</td>
</tr>
</tbody>
</table>
<h2 style="text-align: justify;"><span style="font-size: 20pt;">Detailed Explanation on Security Headers</span></h2>
<h3 style="text-align: justify;"><span style="font-size: 18pt;">Strict-Transport-Security</span></h3>
<p style="text-align: justify;"><span>The Strict-Transport-Security (HSTS) header is a security feature used by websites to protect users from certain types of cyberattacks. Its primary purpose is to ensure that web browsers only connect to a website using a secure, encrypted connection (HTTPS), making it harder for attackers to intercept or manipulate data transmitted between the user and the website.</span></p>
<p style="text-align: justify;">The Strict-Transport-Security header has a value that consists of several components:</p>

<ul style="text-align: justify;">
 	<li><strong>max-age</strong>: This specifies the time, in seconds, that the browser should remember to only use HTTPS for the website. For example, "max-age=31536000" means the browser will remember this setting for one year.</li>
 	<li><strong>includeSubDomains</strong>: If present, this part tells the browser to apply the HSTS policy to all subdomains of the website as well. For example, "includeSubDomains" means all subdomains are covered.</li>
 	<li><strong>preload</strong>: Websites can submit their HSTS settings to be preloaded into major web browsers. This ensures that even a user's first visit to the site is secure. Including "preload" in the header indicates that the site wants to be part of this preload list.</li>
</ul>
<p style="text-align: justify;"><strong>Sample header</strong></p>

<div class="hcb_wrap" style="text-align: justify;">
<pre class="prism undefined-numbers lang-html" data-lang="HTML"><code>Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
</code></pre>
</div>
<p style="text-align: justify;"><em>The Strict-Transport-Security (HSTS) header instructs the browser to only connect to the website over a secure (HTTPS) connection. In the sample header, max-age specifies the duration (in seconds) for which the browser should enforce this policy (here, 31,536,000 seconds, which is one year). includeSubDomains indicates that the policy applies to all subdomains, and preload signifies that the site can be included in browser preload lists for enhanced security.</em></p>

<h3 style="text-align: justify;"><span style="font-size: 18pt;">X-Frame-Options</span></h3>
<p style="text-align: justify;">The X-Frame-Options header is a security feature used by web servers to control how a web page can be displayed within an iframe on another website. Its primary purpose is to prevent clickjacking attacks, which occur when a malicious website tries to trick a user into clicking on something different from what they perceive.</p>
<p style="text-align: justify;">The X-Frame-Options header has a value that consists of several components:</p>

<ul style="text-align: justify;">
 	<li><strong>DENY:</strong> When set to "DENY," it means that the web page cannot be displayed in an iframe on any other website. This is the strictest option and provides maximum security.</li>
 	<li><strong>SAMEORIGIN:</strong> When set to "SAMEORIGIN," it allows the web page to be displayed in an iframe, but only if the embedding website is from the same origin (i.e., the same domain and protocol). This is a more permissive option but still provides reasonable security.</li>
 	<li><strong>ALLOW-FROM uri:</strong> This option allows you to specify a specific URI (Uniform Resource Identifier) from which the web page can be embedded in an iframe. It restricts embedding to a specific source.</li>
</ul>
<p style="text-align: justify;"><strong>Sample Header</strong></p>

<div class="hcb_wrap" style="text-align: justify;">
<pre class="prism undefined-numbers lang-html" data-lang="HTML"><code>X-Frame-Options: DENY
</code></pre>
</div>
<p style="text-align: justify;"><em>The X-Frame-Options header helps prevent clickjacking attacks by specifying whether a web page can be embedded within an iframe. In this sample header, DENY means the page cannot be embedded in any frame, providing protection against clickjacking.</em></p>

<ol style="text-align: justify;"></ol>
<h3 style="text-align: justify;"><span style="font-size: 18pt;">X-Content-Type-Options</span></h3>
<p style="text-align: justify;">The X-Content-Type-Options header is a security feature implemented in web browsers to enhance the security of web applications. Its primary purpose is to prevent a certain type of web vulnerability known as MIME sniffing or content-type sniffing.</p>
<p style="text-align: justify;">The X-Content-Type-Options header has a value that consists of several components:</p>

<ul style="text-align: justify;">
 	<li><strong>nosniff</strong> - This is the recommended and widely used value. When set to "nosniff," it instructs the browser to strictly follow the content type provided in the response's Content-Type header. If the content type is declared as "text/html," the browser will treat it as HTML, even if the server sends it with a different MIME type.</li>
 	<li><strong>none</strong> - This value effectively disables the X-Content-Type-Options header. It allows browsers to perform content-type sniffing, which can potentially lead to security vulnerabilities.</li>
</ul>
<p style="text-align: justify;"><strong>Sample Header</strong></p>

<div class="hcb_wrap" style="text-align: justify;">
<pre class="prism undefined-numbers lang-html" data-lang="HTML"><code>X-Content-Type-Options: nosniff</code></pre>
</div>
<p style="text-align: justify;"><em>The X-Content-Type-Options header prevents browsers from interpreting files as a different MIME type than what is declared by the server. In this sample header, nosniff instructs the browser not to "sniff" the content type and to respect the declared MIME type.</em></p>

<h3 style="text-align: justify;"><span style="font-size: 18pt;">Content-Security-Policy</span></h3>
<p style="text-align: justify;">The Content-Security-Policy (CSP) header is a security feature used by websites to control and specify how resources on a web page can be loaded and executed. It's like setting rules for who can enter your house and what they can do once they're inside. This header helps protect websites and their visitors from various types of cyberattacks, such as cross-site scripting (XSS) and data injection.</p>
<p style="text-align: justify;">The Content-Security-Policy header has a value that consists of several components:</p>

<ul style="text-align: justify;">
 	<li><strong>default-src</strong>: Specifies the default source for various resource types if not explicitly defined by other directives.</li>
 	<li><strong>script-src</strong>: Controls which sources can load JavaScript code. For example, <strong>'self'</strong> allows scripts from the same origin (your own website), while <strong>'unsafe-inline'</strong> permits inline scripts, but this is considered risky.</li>
 	<li><strong>style-src</strong>: Determines the sources from which stylesheets (CSS) can be loaded. Similar to <strong>script-src</strong>, it can include values like <strong>'self'</strong> and <strong>'unsafe-inline'</strong>.</li>
 	<li><strong>img-src</strong>: Specifies allowed sources for images. <strong>'self'</strong> permits images from your website, and you can add other domains as well.</li>
 	<li><strong>font-src</strong>: Manages the sources for web fonts.</li>
 	<li><strong>connect-src</strong>: Governs which domains can be accessed via network requests, like AJAX or Fetch API calls.</li>
 	<li><strong>frame-src</strong>: Controls where your web page can be embedded in an iframe.</li>
 	<li><strong>report-uri</strong> or <strong>report-to</strong>: Specifies where to send violation reports if the CSP is breached. It's useful for monitoring and debugging.</li>
</ul>
<p style="text-align: justify;"><strong>Sample Header</strong></p>

<div class="hcb_wrap" style="text-align: justify;">
<pre class="prism undefined-numbers lang-html" data-lang="HTML"><code>Content-Security-Policy: default-src 'self'; script-src 'self' cdn.example.com; img-src data:; upgrade-insecure-requests</code></pre>
</div>
<p style="text-align: justify;"><em>The Content-Security-Policy header defines which resources can be loaded and executed on a web page, helping to mitigate various types of attacks like cross-site scripting (XSS) and data injection. In this sample header, it allows scripts to be loaded only from the same origin and from a specific CDN, allows images from data URIs, and enables automatic upgrading of insecure HTTP requests to HTTPS.</em></p>
<p style="text-align: justify;">Tool to check misconfigured CSP Header: <a href="https://csp-evaluator.withgoogle.com">https://csp-evaluator.withgoogle.com</a></p>

<h3 style="text-align: justify;"><span style="font-size: 18pt;">Cache-Control</span></h3>
<p style="text-align: justify;">The Cache-Control header is an important part of HTTP (Hypertext Transfer Protocol) used for communication between web clients (like browsers) and servers. This header plays a crucial role in controlling how web content is cached, stored, and retrieved by the client and intermediary devices, such as proxies and CDNs (Content Delivery Networks).</p>
<p style="text-align: justify;">The Cache-Control header has a value that consists of several components:</p>

<ul style="text-align: justify;">
 	<li><strong>public</strong>: Indicates that the response can be cached by any intermediate cache, like a CDN or proxy server. It's suitable for content that can be shared among multiple users.</li>
 	<li><strong>private</strong>: Specifies that the response is intended for a single user and should not be cached by intermediate caches. This is often used for sensitive or personalized content.</li>
 	<li><strong>max-age</strong>: This value defines the maximum time (in seconds) a response can be cached before it's considered stale. For example, "max-age=3600" means the response can be cached for one hour.</li>
 	<li><strong>no-store</strong>: Instructs the client and intermediaries not to store a cached copy of the response. It must be fetched from the server every time it's needed. This is used for highly sensitive data.</li>
 	<li><strong>no-cache</strong>: Tells the client to revalidate the cached content with the server before using it, even if it's not expired. This ensures that the cached content is still fresh.</li>
 	<li><strong>must-revalidate</strong>: This directive indicates that the cached content must be revalidated with the server before use, regardless of its expiration time.</li>
 	<li><strong>s-maxage</strong>: Similar to "max-age," but specifically for shared caches (like proxies and CDNs). It sets the maximum age for cached content in shared caches.</li>
</ul>
<p style="text-align: justify;"><strong>Sample Header</strong></p>

<div class="bg-black rounded-md mb-4" style="text-align: justify;">
<div class="p-4 overflow-y-auto">
<div class="hcb_wrap">
<pre class="prism undefined-numbers lang-html" data-lang="HTML"><code>Cache-Control: no-store, no-cache, must-revalidate, max-age=0
</code></pre>
</div>
</div>
<div><em>The Cache-Control header controls caching behavior in the browser and intermediary caches. In this sample header, it directs browsers and caches not to store or cache the response, always revalidate it with the server, and sets the maximum age to 0 seconds, effectively preventing any caching.</em></div>
<div></div>
</div>
<h3 style="text-align: justify;"><span style="font-size: 18pt;">Referrer-Policy</span></h3>
<p style="text-align: justify;">The Referrer-Policy header is a security feature implemented by web browsers to control how much information a web page should share about the user's previous web activity (referrer) when they click on a link or navigate to a new page. This header helps protect user privacy and security by allowing website owners to specify how much referrer information should be disclosed to the destination website.</p>
<p style="text-align: justify;">The Referrer-Policy header has a value that consists of several components:</p>

<ul style="text-align: justify;">
 	<li><strong>no-referrer</strong>: This value means that no referrer information will be sent to the destination website. It provides the highest level of privacy but may break some functionality on certain websites.</li>
 	<li><strong>no-referrer-when-downgrade</strong>: This value is the default setting if the header is not specified. It sends the full referrer when navigating from an HTTPS site to an HTTP site, but it sends no referrer when moving from an HTTPS site to another HTTPS site. This helps maintain security during downgrades from secure to non-secure connections.</li>
 	<li><strong>same-origin</strong>: It only includes the referrer information if the source and destination URLs have the same origin (same protocol, domain, and port). This is useful for preserving privacy while still allowing referrer information within a website.</li>
 	<li><strong>origin</strong>: It includes only the origin part of the referrer URL (protocol, domain, and port), but not the path or query parameters. This helps protect privacy while allowing some context.</li>
 	<li><strong>strict-origin</strong>: Similar to "origin," but it only sends a referrer when the source and destination URLs have the same origin.</li>
 	<li><strong>origin-when-cross-origin</strong>: It sends the full referrer when navigating within the same origin but only the origin part when moving to a different origin. This balances privacy and functionality.</li>
 	<li><strong>strict-origin-when-cross-origin</strong>: Similar to "origin-when-cross-origin," but it only sends a full referrer when the source and destination URLs have the same origin.</li>
 	<li><strong>unsafe-url</strong>: It sends the full referrer information, including sensitive path and query parameters, to all destinations. This option provides the least privacy and should be used with caution.</li>
</ul>
<p style="text-align: justify;"><strong>Sample Header</strong></p>

<div class="bg-black rounded-md mb-4" style="text-align: justify;">
<div class="p-4 overflow-y-auto">
<div class="hcb_wrap">
<pre class="prism undefined-numbers lang-html" data-lang="HTML"><code>Referrer-Policy: strict-origin-when-cross-origin</code></pre>
</div>
</div>
</div>
<p style="text-align: justify;"><em>In this sample header, the website is instructing the browser to only include the full referrer information when navigating to a different origin (i.e., a different website). If you're moving within the same website (same origin), it will only share the origin part of the referrer URL. This setting strikes a balance between privacy and functionality.</em></p>

<h2 style="text-align: justify;"><span style="font-size: 20pt;">Tools to check header information</span></h2>
<ul>
 	<li style="text-align: justify;"><a href="https://securityheaders.com">https://securityheaders.com</a></li>
 	<li><a href="https://observatory.mozilla.org">https://observatory.mozilla.org</a></li>
</ul>
