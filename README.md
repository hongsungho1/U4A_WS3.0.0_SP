<p>IP address utilities for node.js</p>
<h2><a id="user-content-installation" class="anchor" href="https://www.npmjs.com/package/ip#installation" aria-hidden="true"></a>Installation</h2>
<h3><a id="user-content-npm" class="anchor" href="https://www.npmjs.com/package/ip#npm" aria-hidden="true"></a>npm</h3>
<div class="highlight highlight-source-shell">
<pre>npm install ip</pre>
</div>
<h3><a id="user-content-git" class="anchor" href="https://www.npmjs.com/package/ip#git" aria-hidden="true"></a>git</h3>
<div class="highlight highlight-source-shell">
<pre>git clone https://github.com/indutny/node-ip.git</pre>
</div>
<h2><a id="user-content-usage" class="anchor" href="https://www.npmjs.com/package/ip#usage" aria-hidden="true"></a>Usage</h2>
<p>Get your ip address, compare ip addresses, validate ip addresses, etc.</p>
<div class="highlight highlight-source-js">
<pre><span class="pl-k">var</span> <span class="pl-s1">ip</span> <span class="pl-c1">=</span> <span class="pl-en">require</span><span class="pl-kos">(</span><span class="pl-s">'ip'</span><span class="pl-kos">)</span><span class="pl-kos">;</span>

<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">address</span><span class="pl-kos">(</span><span class="pl-kos">)</span> <span class="pl-c">// my ip address</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">isEqual</span><span class="pl-kos">(</span><span class="pl-s">'::1'</span><span class="pl-kos">,</span> <span class="pl-s">'::0:1'</span><span class="pl-kos">)</span><span class="pl-kos">;</span> <span class="pl-c">// true</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">toBuffer</span><span class="pl-kos">(</span><span class="pl-s">'127.0.0.1'</span><span class="pl-kos">)</span> <span class="pl-c">// Buffer([127, 0, 0, 1])</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">toString</span><span class="pl-kos">(</span><span class="pl-k">new</span> <span class="pl-v">Buffer</span><span class="pl-kos">(</span><span class="pl-kos">[</span><span class="pl-c1">127</span><span class="pl-kos">,</span> <span class="pl-c1">0</span><span class="pl-kos">,</span> <span class="pl-c1">0</span><span class="pl-kos">,</span> <span class="pl-c1">1</span><span class="pl-kos">]</span><span class="pl-kos">)</span><span class="pl-kos">)</span> <span class="pl-c">// 127.0.0.1</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">fromPrefixLen</span><span class="pl-kos">(</span><span class="pl-c1">24</span><span class="pl-kos">)</span> <span class="pl-c">// 255.255.255.0</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">mask</span><span class="pl-kos">(</span><span class="pl-s">'192.168.1.134'</span><span class="pl-kos">,</span> <span class="pl-s">'255.255.255.0'</span><span class="pl-kos">)</span> <span class="pl-c">// 192.168.1.0</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">cidr</span><span class="pl-kos">(</span><span class="pl-s">'192.168.1.134/26'</span><span class="pl-kos">)</span> <span class="pl-c">// 192.168.1.128</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">not</span><span class="pl-kos">(</span><span class="pl-s">'255.255.255.0'</span><span class="pl-kos">)</span> <span class="pl-c">// 0.0.0.255</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">or</span><span class="pl-kos">(</span><span class="pl-s">'192.168.1.134'</span><span class="pl-kos">,</span> <span class="pl-s">'0.0.0.255'</span><span class="pl-kos">)</span> <span class="pl-c">// 192.168.1.255</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">isPrivate</span><span class="pl-kos">(</span><span class="pl-s">'127.0.0.1'</span><span class="pl-kos">)</span> <span class="pl-c">// true</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">isV4Format</span><span class="pl-kos">(</span><span class="pl-s">'127.0.0.1'</span><span class="pl-kos">)</span><span class="pl-kos">;</span> <span class="pl-c">// true</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">isV6Format</span><span class="pl-kos">(</span><span class="pl-s">'::ffff:127.0.0.1'</span><span class="pl-kos">)</span><span class="pl-kos">;</span> <span class="pl-c">// true</span>

<span class="pl-c">// operate on buffers in-place</span>
<span class="pl-k">var</span> <span class="pl-s1">buf</span> <span class="pl-c1">=</span> <span class="pl-k">new</span> <span class="pl-v">Buffer</span><span class="pl-kos">(</span><span class="pl-c1">128</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-k">var</span> <span class="pl-s1">offset</span> <span class="pl-c1">=</span> <span class="pl-c1">64</span><span class="pl-kos">;</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">toBuffer</span><span class="pl-kos">(</span><span class="pl-s">'127.0.0.1'</span><span class="pl-kos">,</span> <span class="pl-s1">buf</span><span class="pl-kos">,</span> <span class="pl-s1">offset</span><span class="pl-kos">)</span><span class="pl-kos">;</span>  <span class="pl-c">// [127, 0, 0, 1] at offset 64</span>
<span class="pl-s1">ip</span><span class="pl-kos">.</span><span class="pl-en">toString</span><span class="pl-kos">(</span><span class="pl-s1">buf</span><span class="pl-kos">,</span> <span class="pl-s1">offset</span><span class="pl-kos">,</span> <span class="pl-c1">4</span><span class="pl-kos">)</span><span class="pl-kos">;</span>            <span class="pl-c">// '127.0.0.1'</span></pre>
</div>