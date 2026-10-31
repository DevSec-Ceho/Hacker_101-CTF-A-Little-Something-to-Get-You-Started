# Hacker101 CTF Write-up: A Little Something to Get You Started

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Hacker101-4CAF50?style=for-the-badge" alt="Hacker101">
  <img src="https://img.shields.io/badge/Category-Web%20Security-blue?style=for-the-badge" alt="Web Security">
  <img src="https://img.shields.io/badge/Difficulty-Trivial-brightgreen?style=for-the-badge" alt="Trivial Difficulty">
  <img src="https://img.shields.io/badge/Status-Solved-success?style=for-the-badge" alt="Successfully Solved">
</p>

<h2>📌 Challenge Information</h2>

<table>
  <tr><th>Information</th><th>Details</th></tr>
  <tr><td>Platform</td><td>Hacker101 CTF</td></tr>
  <tr><td>Challenge Name</td><td>A Little Something to Get You Started</td></tr>
  <tr><td>Category</td><td>Web Security</td></tr>
  <tr><td>Difficulty</td><td>Trivial</td></tr>
  <tr><td>Vulnerability</td><td>Information Disclosure</td></tr>
  <tr><td>Status</td><td>Successfully Solved</td></tr>
</table>

<h2>📝 Introduction</h2>

<p>This write-up documents my successful completion of the <strong>A Little Something to Get You Started</strong> challenge on Hacker101 CTF.</p>

<p>The objective was to investigate a simple web application, inspect its source code, identify an interesting resource, and retrieve the hidden flag.</p>

<p>Although the challenge appears simple at first, it demonstrates an important web security concept: sensitive information can sometimes be exposed through publicly accessible resources.</p>

<h2>🔍 Step 1: Initial Reconnaissance</h2>

<p>After launching the challenge instance, I was presented with a simple webpage displaying the following message:</p>

<blockquote>
  <p>Welcome to level 0. Enjoy your stay.</p>
</blockquote>

<p>The page contained no visible links, forms, or interactive elements.</p>

<p>Rather than stopping at what was displayed in the browser, I decided to inspect the underlying HTML source code.</p>

<h3>Screenshot 1: Initial Challenge Page</h3>

<p align="center">
 <img width="1920" height="811" alt="image" src="https://github.com/user-attachments/assets/7a62a261-be3e-494f-b176-cf8343ff3894" />

</p>
<p align="center"><em>Figure 1: The initial challenge page displaying the Level 0 welcome message.</em></p>

<h2>🔎 Step 2: Inspecting the HTML Source Code</h2>

<p>Using the browser's <strong>View Page Source</strong> functionality, I examined the application's HTML and CSS.</p>

<p>The following code caught my attention:</p>

<pre><code class="language-html">&lt;!doctype html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;style&gt;
        body {
            background-image: url("background.png");
        }
    &lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;p&gt;Welcome to level 0. Enjoy your stay.&lt;/p&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>

<p>The most interesting part was the following CSS declaration:</p>

<pre><code class="language-css">background-image: url("background.png");</code></pre>

<p>This revealed that the application was requesting a resource named <code>background.png</code>.</p>

<p>This filename became my next point of investigation.</p>

<h3>Screenshot 2: HTML Source Code</h3>

<p align="center">
 
</p>
<img width="1920" height="811" alt="Screenshot 2026-10-20 at 16-49-38 https __7487849b036c64a408941d75e9a3bde5 ctf hacker101 com_" src="https://github.com/user-attachments/assets/a0d6a235-86a4-49fc-8ad7-27d2ad6ed587" />

<p align="center"><em>Figure 2: Inspecting the HTML source revealed the background.png resource.</em></p>

<h2>🚩 Step 3: Discovering the Hidden Resource</h2>

<p>After identifying the resource, I decided to access it directly through the browser.</p>

<p>I appended <code>/background.png</code> to the challenge instance URL:</p>

<pre><code>https://&lt;challenge-instance&gt;.ctf.hacker101.com/background.png</code></pre>

<p>I replaced <code>&lt;challenge-instance&gt;</code> with the hostname assigned to my own running challenge.</p>

<p>Accessing the resource revealed the hidden flag.</p>

<p>This demonstrated why inspecting referenced resources is an important part of web application reconnaissance.</p>

<h2>✅ Step 4: Flag Submission</h2>

<p>After retrieving the flag, I navigated to the <strong>Submit Flag</strong> section of Hacker101 CTF.</p>

<p>I entered the discovered flag into the submission field and clicked the <strong>Check</strong> button.</p>

<p>The platform displayed the following confirmation:</p>

<blockquote>
  <p><strong>Congratulations, you found a flag!</strong></p>
</blockquote>

<p>This confirmed that the challenge had been successfully completed.</p>

<h3>Screenshot 3: Successful Flag Submission</h3>

<p align="center">
<img width="1920" height="811" alt="Screenshot 2026-10-20 at 16-53-55 Hacker101 CTF" src="https://github.com/user-attachments/assets/9f9d7c37-014f-4328-abe7-ac4b7f2a7186" />

</p>

<p align="center"><em>Figure 3: Hacker101 CTF confirming the successful flag submission.</em></p>

<h2>🛡️ Vulnerability Analysis</h2>

<p>The challenge demonstrates information disclosure through a publicly accessible resource.</p>

<p>The application referenced a resource in its CSS that could be accessed directly without authentication.</p>

<p>The important security observations include:</p>

<ul>
  <li>Publicly accessible resources can expose unintended information.</li>
  <li>HTML and CSS source code can reveal useful information about an application's structure.</li>
  <li>File extensions should not be trusted as proof of actual file contents.</li>
  <li>Sensitive information should never be stored in publicly accessible static resources.</li>
</ul>

<h2>💡 Lessons Learned</h2>

<p>This challenge reinforced several important web security practices:</p>

<ol>
  <li>Always inspect HTML source code during web reconnaissance.</li>
  <li>Investigate referenced resources, including images, scripts, and stylesheets.</li>
  <li>Do not assume that a resource is harmless simply because it has an image extension.</li>
  <li>Understand how browsers retrieve external resources.</li>
  <li>Never expose sensitive information through publicly accessible files.</li>
</ol>

<h2>🧰 Tools Used</h2>

<ul>
  <li>Web Browser</li>
  <li>Browser Developer Tools</li>
  <li>View Page Source</li>
  <li>Hacker101 CTF Platform</li>
</ul>

<h2>🏁 Conclusion</h2>

<p>The <strong>A Little Something to Get You Started</strong> challenge was a great introduction to web application reconnaissance and information disclosure.</p>

<p>By inspecting the HTML source, identifying the <code>background.png</code> resource, and accessing it directly, I was able to discover the hidden flag and successfully complete the challenge.</p>

<p>This exercise reinforced the importance of looking beyond a webpage's visual appearance and investigating the resources loaded by the application.</p>

<p><strong>Challenge Status: Successfully Completed! 🚀</strong></p>

<hr>

<p align="center">
  <strong>Hack. Learn. Improve. Repeat.</strong>
  <br>
  <em>Documenting my journey in cybersecurity and ethical hacking.</em>
</p>
