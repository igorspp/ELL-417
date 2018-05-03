<p><em><strong>ELL-417: Introduction to bioinformatics for microbiologists</strong></em></p>
<h1 id="day-6---introduction-to-metagenomics--r">Day 6 - Introduction to metagenomics &amp; R</h1>
<p><strong>by Dr. Igor S. Pessi</strong><br>
<em>Arctic Microbial Ecology<br>
Department of Microbiology, UH<br>
<a href="mailto:igor.pessi@helsinki.fi">igor.pessi@helsinki.fi</a></em></p>
<h2 id="program-of-the-day">Program of the day</h2>
<p>30’ – Overview of metagenomics<br>
30’ – Activity 1<br>
15’ – Break<br>
30’ – Overview of R<br>
30’ – Activity 2<br>
15’  –  Break<br>
30’ – Activity 3</p>
<h2 id="section"></h2>
<h3 id="installing-r-and-rstudio">Installing R and RStudio</h3>
<p>First we need to install R. Just download below the appropriate version for your computer and follow the instructions:</p>
<p><strong>Windows:</strong> <a href="https://cran.rstudio.com/bin/windows/base/R-3.5.0-win.exe">https://cran.rstudio.com/bin/windows/base/R-3.5.0-win.exe</a><br>
<strong>Mac OS X 10.6 (Snow Leopard) – 10.8 (Mountain Lion):</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.2.1-snowleopard.pkg">https://cran.rstudio.com/bin/macosx/R-3.2.1-snowleopard.pkg</a><br>
<strong>Mac OS X 10.9 (Mavericks) and higher:</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.3.3.pkg">https://cran.rstudio.com/bin/macosx/R-3.3.3.pkg</a><br>
<strong>Mac OS X 10.11 (El Capitan) and higher</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.5.0.pkg">https://cran.rstudio.com/bin/macosx/R-3.5.0.pkg</a></p>
<p>Once R has finished installing, we can then install RStudio:</p>
<p><strong>Windows Vista/7/8/10:</strong> <a href="https://download1.rstudio.org/RStudio-1.1.447.exe">https://download1.rstudio.org/RStudio-1.1.447.exe</a><br>
<strong>Mac OS X 10.6+ (64-bit):</strong> <a href="https://download1.rstudio.org/RStudio-1.1.447.dmg">https://download1.rstudio.org/RStudio-1.1.447.dmg</a></p>
<h2 id="section-1"></h2>
<h3 id="activity-1-browsing-and-downloading-data-from-mg-rast">Activity 1: Browsing and downloading data from MG-RAST</h3>
<ol>
<li>First create a folder called <em>metagenomics_course</em> (no spaces!) somewhere in your computer. This is where the data we will use and generate later (<em>i.e.</em> the working directory) will be stored.</li>
<li>Go to <a href="https://www.mg-rast.org/">https://www.mg-rast.org/</a></li>
<li>Click <em>download</em></li>
<li>Click <em>search website</em></li>
<li>In the top-left of the page, search for a metagenome of interest (e.g. <em>cow rumen</em>)</li>
<li>Go through the search results and select a study
<ul>
<li>Make sure that <strong>seq type</strong> is <em>shotgun metagenome</em> NOT <em>amplicon metagenome</em></li>
<li>If you want you can narrow down the search using the <em>Refine Search</em> box in the right-hand of the page, for example:
<ul>
<li><strong>field</strong> = <em>seq type</em>, <strong>term</strong> = <em>shotgun metagenome</em></li>
<li><strong>field</strong> = <em>country</em>, <strong>term</strong> = <em>Finland</em></li>
</ul>
</li>
</ul>
</li>
<li>In the study page, take a moment to familiarize yourself with the project
<ul>
<li>How many samples are there?</li>
<li>What are the differences between them?</li>
</ul>
</li>
<li>For each sample, go to the results page and:
<ul>
<li>Check results</li>
<li>Download the <em>Subsystems</em> functional annotation (download CSV)</li>
<li>Download the <em>phylum level</em> taxonomic annotation (download CSV)</li>
<li><strong>Metadata???</strong></li>
<li><strong>Rename files??</strong></li>
</ul>
</li>
</ol>
<h2 id="section-2"></h2>
<h3 id="activity-2-understanding-the-very-basics-of-r">Activity 2: Understanding the <em>very</em> basics of R</h3>
<p><em><strong>DISCLAIMER:</strong> The only way to become proficient in R is by typing things, making mistakes, and trying again. So I strongly advise that, in the examples below, you type the commands instead of copying and pasting them. You have been warned!</em></p>
<p>In this activity we will do some basic operations to get a feeling of how R works. We start by, of course, launching RStudio.</p>
<p>You then need to tell RStudio where your working directory is located. This is the <em>metagenomics_course</em> folder where you have put the data you downloaded from MG-RAST in the previous activity.</p>
<p>To do this, we will use the <em>setwd()</em> function. Simply type the command below in the RStudio console  and press <em>ENTER</em>:</p>
<pre><code>setwd("&lt;Path to the metagenomics_course folder&gt;")
</code></pre>
<p>Change <em>&lt;Path to the metagenomics_course folder&gt;</em> to the FULL address of where the metagenomics_course folder is located. Something along these lines:</p>
<pre><code># On Windows:
setwd("C:/Documents and Settings/metagenomics_course")
# On Mac:
setwd("~/Desktop/metagenomics_course")
</code></pre>
<p>If you are having trouble setting your working directory, do not panic, there is an easier way to do this. <em>But remember, you only learn R by using it (and typing) extensively, so only do it this way if you have tried the command above without success.</em> In the RStudio menu bar (on the top of the window), click in <em>Session &gt; Set Working Directory &gt; Choose Directory</em>. In the window that popped-up, navigate to your <em>metagenomics_course</em> folder, select it and click <em>Open</em>.</p>
<p>Take a look at the console. What has happened? What we did here is simply a shortcut to the <em>setwd()</em> command. What appeared in the console is what you should have written in the first place.</p>
<p>We will now do some simple calculations and assignments. In the console, type:</p>
<pre><code>3*5+10 
</code></pre>
<p>Take a look at the ouput. What has happened? Pretty obvious, no?</p>
<p>Now we will calculate the area of a circle with radius 10. For this, we will first create a variable called <em>radius</em>, and assign it the value of 10. In the console, type (one line at a time):</p>
<pre><code>radius &lt;- 10
area &lt;- pi * radius^2
area
</code></pre>
<p>Take a look at the <em>Environment</em> tab in the top-right of the RStudio window. What has changed after you typed in the commands above? Also, can you understand what the command <em>area &lt;- pi * radius^2</em> has done? (HINT: remember the math classes you had in school). What would happen if you assign another value to the radius variable)?</p>
<p>We will now use the built-in function <em>rnorm()</em> to create two  variables (<em>x</em> and <em>y</em>). In the console, type:</p>
<pre><code>x = rnorm(50)
y = rnorm(x)
</code></pre>
<p>Once again, the <em>Environment</em> tab now contains these two new variables. Let’s see what they are. Simply type their name in the console (one at a time):</p>
<pre><code>x
y
</code></pre>
<p>Can you understand what the command <em>rnorm</em> has done for us?<br>
HINT: try typing <em>help(rnorm)</em></p>
<pre><code>plot(x, y)
</code></pre>
<p>That was a <strong>very</strong> basic overview of R. In activity 3, we will learn how to import external data and generate slightly more complex plots.</p>
<h2 id="section-3"></h2>
<h3 id="activity-3-plotting-metagenomic-profiles-in-rstudio">Activity 3: Plotting metagenomic profiles in RStudio</h3>
<p>See wrangling wit R pdf</p>

