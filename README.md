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
<li>First create a folder named <em>metagenomics_course</em> (no spaces!) somewhere in your computer. This will be our working directory, that is, where we store the data we will use later on with RStudio.</li>
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
<p>We will now do some simple calculations and assignments. In the RStudio console, type and press <em>ENTER</em>:</p>
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
<p>What has the command <em>area &lt;- pi * radius^2</em> done? Can you understand how the syntax works? What does the characters * and <em>^2</em> denote? Finally, what would happen if you assign another value to the variable <em>radius</em>? Try it and see it for yourself!</p>
<p>We will now use the built-in function <em>rnorm()</em> to create two  variables (<em>x</em> and <em>y</em>). In the console, type:</p>
<pre><code>x = rnorm(50)
y = rnorm(x)
</code></pre>
<p>Once again, the <em>Environment</em> tab now contains these two new variables. To see what they are, again simply type their name in the console. Can you understand what the command <em>rnorm</em> has done? HINT: try typing <em>help(rnorm)</em></p>
<p>In addition to the <em>help()</em> function, there is a lot of content out there to guide you on using R and discovering new tools. For example, take a look at one cheat sheet developed by RStudio: <a href="https://www.rstudio.com/wp-content/uploads/2016/10/r-cheat-sheet-3.pdf">https://www.rstudio.com/wp-content/uploads/2016/10/r-cheat-sheet-3.pdf</a></p>
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
<p>We will now do some slightly more complicated operations. As I’ve mentioned before, learning R is a bit of a steep curve so I don’t expect that you will understand 100% of this in the short duration of our course. But hopefully it will give you an overview of the capabilities of R and it will entice you to keep learning!</p>
<p>To make life easier for us, we will first work with two samples I have pre-selected for you. Go to <a href="https://github.com/igorspp/ELL-417/tree/data">https://github.com/igorspp/ELL-417/tree/data</a> and click <em>Clone or download &gt; Download ZIP</em>.  Unzip the file and move the contents to your <em>metagenomics_course</em> folder.</p>
<p>With RStudio open, we now need to tell it where our working directory is located. This is the <em>metagenomics_course</em> folder you created in the previous activity and which contains the data we will analyse. To do this, we will use the <em>setwd()</em> function. Simply type the command below in the RStudio console and hit <em>ENTER</em>:</p>
<pre><code>setwd("&lt;Path to the metagenomics_course folder&gt;")
</code></pre>
<p>Change <em>&lt;Path to the metagenomics_course folder&gt;</em> to the FULL address where the metagenomics_course folder is located. Something along these lines (remember to change to the actual location of the folder in YOUR computer):</p>
<pre><code># On Windows:
setwd("C:/Documents and Settings/metagenomics_course")
# On Mac:
setwd("~/Desktop/metagenomics_course")
</code></pre>
<p>If you are having trouble setting your working directory, do not panic, there is an easier way to do this. <em>But remember, you only learn R by using it (and typing) extensively, so only do it this way if you have tried the command above without success.</em> In the RStudio menu bar (on the top of the window), click in <em>Session &gt; Set Working Directory &gt; Choose Directory</em>. In the window that popped up, navigate to your <em>metagenomics_course</em> folder, select it and click <em>Open</em>.</p>
<p>Take a look at the console. What has happened? What we did here is simply a shortcut to the <em>setwd()</em> command. What appeared in the console is what you should have written in the first place.</p>
<p>Now we have to install some R packages we need but that are not installed by default. We will use the package <em>reshape2</em> for data manipulation and <em>ggplot2</em> for plotting the graphs. In the console, type:</p>
<pre><code>install.packages("reshape2")
install.packages("ggplot2")
</code></pre>
<p>Wait until the installation has finished. It will give some warnings in red, but these can be ignored for the time being. The next step now is to load the newly-installed packages (this has to be redone everytime you quit RStudio):</p>
<pre><code>library(reshape2)
library(ggplot2)
</code></pre>
<p>We will now import the data from MG-RAST using the <em>read.table</em> function. You will see now that the commands we use start to be slightly more complex, with many options (also called <em>arguments</em>). Take a moment to inspect the command below:</p>
<pre><code>mgs636528_phylum &lt;- read.table("mgs636528_phylum.csv", header = TRUE, sep = "\t")
</code></pre>
<p>The first argument to the <em>read.table()</em> function is the file we want to import; <em>header = TRUE</em> tells RStudio that our columns have names (in this case, the phyla names); and <em>sep = “\t”</em> tells RStudio that the columns are separated by tabs (in some cases, it can be commas). Now that you understand the command, type it in the console.</p>
<p>The command below is used to transform our data to relative abundances. This will be important after when we will compare multiple samples. If the number of sequences you are analysing for each sample is different, they cannot be easily compared. Dividing the phyla abundances by the total number of sequences (that is, transforming to relative abundances) is a way to circumvent this.</p>
<pre><code>mgs636528_phylum &lt;- sweep(mgs636528_phylum, 1, rowSums(mgs636528_phylum), "/")
</code></pre>
<p>Take a look at the <em>mgs636528_phylum</em> variable. How is the data organised? Unfortunately this is not good for plotting so we need to change the way it is organised. We will use the function <em>melt()</em> for this:</p>
<pre><code>mgs636528_phylum &lt;- melt(mgs636528_phylum)
</code></pre>
<p>Inspect the <em>mgs636528_phylum</em> variable again. Can you see what has changed?</p>
<p>We have many phyla in our metagenomes, many of them present at very low abundances. With the command below, we will select only the abundant groups, those which are present at more than 1% relative abundance, so that the graph looks nicer in the end:</p>
<pre><code>mgs636528_phylum &lt;- mgs636528_phylum[mgs636528_phylum$value &gt; 0.01, ]
</code></pre>
<p>And now, finally, we get to plot the results! For this we will use <em>ggplot()</em>. Just type the command below in the console:</p>
<pre><code>ggplot(mgs636528_phylum, aes(x = variable, y = value)) + 
	geom_bar(stat = "identity") 
</code></pre>
<p>Hmmm, things are a bit messy aren’t they? With one additional line of code, we quickly solve this issue:</p>
<pre><code>ggplot(mgs636528_phylum, aes(x = variable, y = value)) +
	geom_bar(stat = "identity")  + 
	theme(axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.5))
</code></pre>
<p>And there we go! Now we will do the same for the second sample. OK, at this point you can copy and past the commands below, as they are exactly the same as the ones we have just used. The only difference, of course, is the sample name. Go ahead, indulge yourself and copy the commands below and paste it in the console. But please, do it one line at a time, so if something goes wrong, it is easier to deal with it.</p>
<pre><code>mgs636513_phylum &lt;- read.table("mgs636513_phylum.csv", header = T, sep = "\t")
mgs636513_phylum &lt;- sweep(mgs636513_phylum, 1, rowSums(mgs636513_phylum), "/")
mgs636513_phylum &lt;- melt(mgs636513_phylum)
mgs636513_phylum &lt;- mgs636513_phylum[mgs636513_phylum$value &gt; 0.01, ]
ggplot(mgs636513_phylum, aes(x = variable, y = value)) +
	geom_bar(stat = "identity")  + 
	theme(axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.5))
</code></pre>
<p>Now we will combine the results from both samples and plot them together:</p>
<pre><code>mgs636528_phylum$Sample &lt;- "mgs636528"
mgs636513_phylum$Sample &lt;- "mgs636513"
all_phylum &lt;- rbind(mgs636513_phylum, mgs636528_phylum)
ggplot(all_phylum, aes(x = variable, y = value)) +
	geom_bar(aes(fill = Sample), stat = "identity", position = "dodge")  + 
	theme(axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.5))
</code></pre>
<p>See wrangling wit R pdf</p>

