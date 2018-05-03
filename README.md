<h1 id="introduction-to-bioinformatics-for-microbiologists">Introduction to bioinformatics for microbiologists</h1>
<h2 id="day-6-friday-04.05.18-introduction-to-metagenomics--r">Day 6 (Friday 04.05.18): Introduction to metagenomics &amp; R</h2>
<p><strong>by Dr. Igor S. Pessi</strong><br>
<em>Arctic Microbial Ecology<br>
Department of Microbiology, UH<br>
<a href="mailto:igor.pessi@helsinki.fi">igor.pessi@helsinki.fi</a></em></p>
<h3 id="program-of-the-day">Program of the day</h3>
<ul>
<li>45’ – Overview of metagenomics</li>
<li>15’ – Break</li>
<li>30’ – Activity 1</li>
<li>15’ – Overview of R</li>
<li>30’ – Activity 2</li>
<li>15’  –  Break</li>
<li>30’ – Activity 3</li>
</ul>
<h3 id="installing-r-and-rstudio">Installing R and RStudio</h3>
<p>First we need to install R. Just download below the appropriate version for your computer and follow the instructions:</p>
<p><strong>Windows:</strong> <a href="https://cran.rstudio.com/bin/windows/base/R-3.5.0-win.exe">https://cran.rstudio.com/bin/windows/base/R-3.5.0-win.exe</a><br>
<strong>Mac OS X 10.6 (Snow Leopard) – 10.8 (Mountain Lion):</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.2.1-snowleopard.pkg">https://cran.rstudio.com/bin/macosx/R-3.2.1-snowleopard.pkg</a><br>
<strong>Mac OS X 10.9 (Mavericks) and higher:</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.3.3.pkg">https://cran.rstudio.com/bin/macosx/R-3.3.3.pkg</a><br>
<strong>Mac OS X 10.11 (El Capitan) and higher</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.5.0.pkg">https://cran.rstudio.com/bin/macosx/R-3.5.0.pkg</a></p>
<p>Once R has finished installing, we can then install RStudio:</p>
<p><strong>Windows Vista/7/8/10:</strong> <a href="https://download1.rstudio.org/RStudio-1.1.447.exe">https://download1.rstudio.org/RStudio-1.1.447.exe</a><br>
<strong>Mac OS X 10.6+ (64-bit):</strong> <a href="https://download1.rstudio.org/RStudio-1.1.447.dmg">https://download1.rstudio.org/RStudio-1.1.447.dmg</a></p>
<h3 id="activity-1-browsing-and-downloading-data-from-mg-rast">Activity 1: Browsing and downloading data from MG-RAST</h3>
<ol>
<li>First create a folder named <em>metagenomics_course</em> (no spaces!) somewhere in your computer. This is will be our working directory, that is, where the data we will use and generate later will be stored.</li>
<li>Go to <a href="https://www.mg-rast.org/">https://www.mg-rast.org/</a></li>
<li>Click <em>download</em></li>
<li>Click <em>search website</em></li>
<li>In the top-left of the page, search for a metagenome of interest. It can be everything, be creative! You can search for a biome, a country, an animal…</li>
<li>Go through the search results and select a study at random
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
<li>Now click the link under the <em>study</em> column. This will take you to the study page</li>
<li>In the study page, scroll down to the <em>metagenomes</em> section. This table lists all the samples included in this study. For the first sample, click the link under the <em>MG-RAST ID</em> column. This will take you to the metagenome page for that sample</li>
<li>Investigate the results
<ul>
<li>Are the data of good quality?</li>
<li>How many proteins were identified?</li>
<li>How many of them have predicted functions?</li>
</ul>
</li>
<li>Scroll down to the <em>Functional Hits</em> section and download the <em>Subsystems</em>  annotation
<ul>
<li>Next to the graph, click the cloud symbol and select <em>download CSV</em></li>
</ul>
</li>
<li>Do the same for the <em>phylum level</em> annotation under the <em>Taxonomic Hits</em> section</li>
<li>Go back to the study page (step 8) and do the same for another 1–2 samples.</li>
<li>Move the downloaded files to the <em>metagenomics_course</em> folder you created in step 1.</li>
<li>If you have time left, go back to step 2 and search for a different metagenome. If you chose, for example, <em>cow rumen</em> the first time, try now a completely different environment (like <em>Arctic</em>)</li>
</ol>
<h3 id="activity-2-playing-around-with-r-and-rstudio">Activity 2: Playing around with R and RStudio</h3>
<p><strong>DISCLAIMER:</strong> The only way to become proficient in R is by typing, making mistakes and trying again. So I strongly advise that in the examples given below you type the commands instead of copying and pasting them. You have been warned!</p>
<p><strong>DISCLAIMER 2:</strong> R (as many other programming languages) is <em>case-sensitive</em>. That means that <em>a</em> and <em>A</em> are treated as different symbols, so pay attention when you’re typing!</p>
<p>In this activity we will do some basic operations to get a feeling of how R works. We start by, of course, launching RStudio.</p>
<p>We will now do some simple calculations and assignments. In the console, type:</p>
<pre><code>3*5+10 
</code></pre>
<p>Take a look at the ouput. What has happened? Pretty obvious, no?</p>
<p>Now we will calculate the area of a circle with radius 10. For this, we will first create a variable called <em>radius</em>, and assign it the value of 10. Then, we will calculate the area of a circle and store the results on another variable we will call <em>area</em>. In the console, type (one line at a time):</p>
<pre><code>radius &lt;- 10
area &lt;- pi * radius^2
</code></pre>
<p>Take a look at the <em>Environment</em> tab in the top-right of the RStudio window. What has changed after you typed in the commands above? Differently from the first example, here we gave R an <em>argument</em> and told it to store the results in a variable instead of printing it to the screen. To take a look at these variables we just created, simply type their name in the console:</p>
<pre><code>radius
area
</code></pre>
<p>What has the command <em>area &lt;- pi * radius^2</em> has done? How does the syntax work? What does the characters * and <em>^2</em> denote? Finally, what would happen if you assign another value to the variable <em>radius</em>? Try it and see it for yourself!</p>
<p>We will now use the built-in function <em>rnorm()</em> to create two  variables (<em>x</em> and <em>y</em>). In the console, type:</p>
<pre><code>x = rnorm(50)
y = rnorm(x)
</code></pre>
<p>Once again, the <em>Environment</em> tab now contains these two new variables. To see what they are, again simply type their name in the console. Can you understand what the command <em>rnorm</em> has done? HINT: try typing <em>help(rnorm)</em></p>
<p>In addition to the <em>help()</em> function, there is a lot of content out there to guide you on using R and discovering new tools. For example, take a look at one <em>cheat sheet</em> developed by RStudio: <a href="https://www.rstudio.com/wp-content/uploads/2016/10/r-cheat-sheet-3.pdf">https://www.rstudio.com/wp-content/uploads/2016/10/r-cheat-sheet-3.pdf</a></p>
<p>Now, using what we have learned so far and taking a look at the cheat sheet, see if you can figure out yourself how to do the following basic tasks:</p>
<ol>
<li>Calculate the circumference of a circle</li>
<li>Transform the <em>x</em> and <em>y</em> variables to the logarithmic scale</li>
<li>Calculate the sum and standard deviation of <em>x</em> and <em>y</em></li>
</ol>
<p>This was a <em>very</em> basic introduction to R. If you want to learn more, I recommend the material below as good starting points. But remember, you only learn R by using it!</p>
<ul>
<li><a href="https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf">https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf</a></li>
<li><a href="https://kannu.csc.fi/s/Xk2jIQT7wiB3H1c/download">https://kannu.csc.fi/s/Xk2jIQT7wiB3H1c/download</a></li>
</ul>
<h3 id="activity-3-plotting-metagenomic-profiles-in-rstudio">Activity 3: Plotting metagenomic profiles in RStudio</h3>
<p>We then need to tell RStudio where our working directory is located. This is the <em>metagenomics_course</em> folder where we have put the data we downloaded from MG-RAST in the previous activity.</p>
<p>To do this, we will use the <em>setwd()</em> function. Simply type the command below in the RStudio console  and press <em>ENTER</em>:</p>
<pre><code>setwd("&lt;Path to the metagenomics_course folder&gt;")
</code></pre>
<p>Change <em>&lt;Path to the metagenomics_course folder&gt;</em> to the FULL address where the metagenomics_course folder is located. Something along these lines:</p>
<pre><code># On Windows:
setwd("C:/Documents and Settings/metagenomics_course")
# On Mac:
setwd("~/Desktop/metagenomics_course")
</code></pre>
<p>If you are having trouble setting your working directory, do not panic, there is an easier way to do this. <em>But remember, you only learn R by using it (and typing) extensively, so only do it this way if you have tried the command above without success.</em> In the RStudio menu bar (on the top of the window), click in <em>Session &gt; Set Working Directory &gt; Choose Directory</em>. In the window that popped up, navigate to your <em>metagenomics_course</em> folder, select it and click <em>Open</em>.</p>
<p>Take a look at the console. What has happened? What we did here is simply a shortcut to the <em>setwd()</em> command. What appeared in the console is what you should have written in the first place.</p>
<p>See wrangling wit R pdf</p>

