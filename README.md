<h1 id="introduction-to-bioinformatics-for-microbiologists">Introduction to bioinformatics for microbiologists</h1>
<h2 id="day-6-friday-04.05.18-introduction-to-metagenomics--r">Day 6 (Friday 04.05.18): Introduction to metagenomics &amp; R</h2>
<p><strong>by Dr. Igor S. Pessi</strong><br>
<em>Arctic Microbial Ecology<br>
Department of Microbiology, UH<br>
<a href="mailto:igor.pessi@helsinki.fi">igor.pessi@helsinki.fi</a></em></p>
<h3 id="program-of-the-day">Program of the day</h3>
<ul>
<li>45’ – Overview of metagenomics</li>
<li>30’ – Activity 1</li>
<li>15’ – Break</li>
<li>15’ – Overview of R and RStudio</li>
<li>60’ – Activity 2</li>
<li>15’  – Conclusion</li>
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
<li>In the top-left of the page, search for a metagenome of interest. It can be anything, be creative! You can search for a specific biome, a country, an animal…</li>
<li>Go through the search results and select one study
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
<li>Do the same for the <em>phylum level</em> annotation under the <em>Taxonomic Hits</em> section further down</li>
<li>Go back to the study page (step 8) and do the same for one or two more samples</li>
<li>Once you have finished, move the downloaded files to the <em>metagenomics_course</em> folder you created in step 1</li>
</ol>
<h3 id="activity-3-plotting-metagenomic-profiles-in-rstudio">Activity 3: Plotting metagenomic profiles in RStudio</h3>
<p><strong>DISCLAIMER:</strong> The only way to become proficient in R is by typing, making mistakes and trying again. So I strongly advise that in the examples given below you type the commands instead of copying and pasting them. You have been warned!</p>
<p><strong>DISCLAIMER 2:</strong> R (as many other programming languages) is <em>case-sensitive</em>. That means that <em>a</em> and <em>A</em> are treated as different symbols, so pay attention when you’re typing!</p>
<p>We will start by doing some basic operations to get a feeling of how R works. We start by, of course, launching RStudio.</p>
<p>We will now do some simple calculations and assignments. In the RStudio console, type and press <em>ENTER</em>:</p>
<pre><code>3*5+10 
</code></pre>
<p>Take a look at the ouput. What has happened? Pretty obvious, no?</p>
<p>Now we will calculate the area of a circle with a radius of 10. For this, we will first create an object called <em>radius</em>, and assign it the value of 10. Then, we will calculate the area of a circle and store the results on another object we will call <em>area</em>. In the console, type (one line at a time):</p>
<pre><code>radius &lt;- 10
area &lt;- pi * radius^2
</code></pre>
<p>Take a look at the <em>Environment</em> tab in the top-right of the RStudio window. What has changed after you typed in the commands above? Differently from the first example, here we gave R a command and told it to store the results in an object instead of printing it to the screen. To take a look at these objects we just created, simply type their name in the console:</p>
<pre><code>radius
area
</code></pre>
<p>What has the command <em>area &lt;- pi * radius^2</em> done? Can you understand how the syntax works? What does the characters * and <em>^2</em> denote? Finally, what would happen if you assign another value to the object <em>radius</em>? Try it and see it for yourself!</p>
<p>We will now do some slightly more complicated operations. As it is mentioned in the disclaimer above, learning R is a bit of a steep curve so don’t be upset if you don’t understand 100% of what is happening. This brief introduction is intended to  give you an overview of the capabilities of R and hopefully will entice you to keep learning!</p>
<p>Now for some real metagenome analyses. To make life easier for us, we will first work with two samples I have pre-selected for you. Go to <a href="https://github.com/igorspp/ELL-417/tree/data">https://github.com/igorspp/ELL-417/tree/data</a> and click <em>Clone or download &gt; Download ZIP</em>.  Unzip the file and move the contents to your <em>metagenomics_course</em> folder.</p>
<p>We now need to tell it where our working directory is located. This is the <em>metagenomics_course</em> folder you created in the previous activity and which contains the data we will analyse. In the RStudio menu bar (on the top of the window), click in <em>Session &gt; Set Working Directory &gt; Choose Directory</em>. In the window that popped up, navigate to your <em>metagenomics_course</em> folder, select it and click <em>Open</em>.</p>
<p>Now we have to install some R packages we need but that are not installed by default. We will use the package <em>reshape2</em> for data manipulation and <em>ggplot2</em> for plotting the graphs. In the console, type:</p>
<pre><code>install.packages("reshape2")
install.packages("ggplot2")
</code></pre>
<p>Wait until the installation has finished. It will give some warnings in red, but these can be ignored for the time being. The next step now is to load the newly-installed packages:</p>
<pre><code>library(reshape2)
library(ggplot2)
</code></pre>
<p>We will now import the data we downloaded from MG-RAST using the <em>read.table()</em> function. You will see now that the commands start to be slightly more complex, with many options (also called <em>arguments</em>). Take a moment to inspect the command below:</p>
<pre><code>mgs636528_phylum &lt;- read.table("mgs636528_phylum.csv", header = TRUE, sep = "\t")
</code></pre>
<p>The first part (left of the &lt;- symbol) tells RStudio that we want to create an object called <em>mgs636528_phylum</em>. Then, we type the name of the function we want to use – <em>read.table()</em> – and inside the parenthesis we pass additional arguments. The first argument is the name of the file we want to import; <em>header = TRUE</em> tells RStudio that our columns have names (in this case, the phyla names); and <em>sep = “\t”</em> tells RStudio that the columns are separated by tabs. This is needed because, in some cases, data can be organised so that columns are delimited by commas, semi-colons or spaces. Now that you understand a bit better the command, type it in the console and hit <em>ENTER</em>. It will give a warning message in R but we can ignore it for the time being. Just make sure that the object <em>mgs636528_phylum</em> we have created is visible in the <em>Environment</em> tab. Take a look at the object (simply type its name in the console and hit <em>ENTER</em>) to see how the data we will analyse looks like.</p>
<p>The command below is used to transform our data to relative abundances. This will be important after, when we will compare multiple samples. If the number of sequences we are analysing for each sample is different, they cannot be easily compared. Dividing the abundance of each phyla by the total number of sequences in the sample (that is, transforming to relative abundances) is a way to circumvent this.</p>
<pre><code>mgs636528_phylum &lt;- sweep(mgs636528_phylum, 1, rowSums(mgs636528_phylum), "/")
</code></pre>
<p>Take a look again at the object <em>mgs636528_phylum</em>. What has changed after you typed in the command above? Also, how is the data organised? This is a typical R data frame (table), where each column is a variable (in our case, phyla) and each row an observation (in our case, samples). Unfortunately this is not good for plotting. To change how the data is structured so we can plot it after, we will use the function <em>melt()</em>:</p>
<pre><code>mgs636528_phylum &lt;- melt(mgs636528_phylum)
</code></pre>
<p>Inspect the object <em>mgs636528_phylum</em> again. What has changed?</p>
<p>Now, we have many phyla in our metagenomes, many of them that are present at very low abundances. This will pollute our graphs a bit, and we won’t be able to see the differences that really matter. With the command below, we will select only the abundant groups, those which are present at more than 1% relative abundance:</p>
<pre><code>mgs636528_phylum &lt;- mgs636528_phylum[mgs636528_phylum$value &gt; 0.01, ]
</code></pre>
<p>Don’t freak out if the command above scares you, we don’t need to understand it 100% at the moment. But please, take one minute and try to figure out what it is doing.</p>
<p>And now, finally, we get to plot the data! For this we will use the <em>ggplot</em> package we installed in the beginning of this exercise. Just type the command below in the console:</p>
<pre><code>ggplot(mgs636528_phylum, aes(x = variable, y = value)) + 
	geom_bar(stat = "identity") 
</code></pre>
<p>Hmmm, things are a bit messy… With one additional line of code, we quickly solve this issue:</p>
<pre><code>ggplot(mgs636528_phylum, aes(x = variable, y = value)) +
	geom_bar(stat = "identity")  + 
	theme(axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.5))
</code></pre>
<p>We can add many more features to the graph: we can add colors, change the title of the axes, add some text; the sky is the limit! But for the moment we will keep it like this. If you want to find out a bit more on how to customise ggplots, you can take a look at this nice cheat sheet: <a href="https://www.rstudio.com/wp-content/uploads/2015/12/ggplot2-cheatsheet-2.0.pdf">https://www.rstudio.com/wp-content/uploads/2015/12/ggplot2-cheatsheet-2.0.pdf</a></p>
<p>Now we will do the same for the remaining sample. OK, at this point you can copy and past the commands below, as they are exactly the same as the ones we have just used. The only difference, of course, is the name of the file we are importing and the name we are giving to the R object we are creating. In other words, each sample will have a different name. Go ahead, indulge yourself and copy the commands below and paste them in the console. But please, do it one line at a time, so if something goes wrong, it will be easier to understand why.</p>
<pre><code>mgs636513_phylum &lt;- read.table("mgs636513_phylum.csv", header = T, sep = "\t")
mgs636513_phylum &lt;- sweep(mgs636513_phylum, 1, rowSums(mgs636513_phylum), "/")
mgs636513_phylum &lt;- melt(mgs636513_phylum)
mgs636513_phylum &lt;- mgs636513_phylum[mgs636513_phylum$value &gt; 0.01, ]
ggplot(mgs636513_phylum, aes(x = variable, y = value)) +
	geom_bar(stat = "identity")  + 
	theme(axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.5))
</code></pre>
<p>Now we will combine the data from both samples and plot them together in one single graph. But first we will add an extra column to our data: we will call this column <em>Sample</em>. This column will contain the sample name, so that each sample can be identified after the data has been merged. This can be done using the commands below:</p>
<pre><code>mgs636528_phylum$Sample &lt;- "mgs636528"
mgs636513_phylum$Sample &lt;- "mgs636513"
</code></pre>
<p>What this command is doing is telling R that we want to create a new column (denoted by the <em>$</em> symbol) called <em>Sample</em> inside our data frame <em>mgs636528_phylum</em>. This column will consist of the name of the sample, which is the string (text) we are giving in the right-hand side of the command. See how the commands are different for each sample?</p>
<p>And now we will combine both datasets into one new object we will call <em>phylum_merged</em>. For this we will use the function <em>rbind()</em>:</p>
<pre><code>phylum_merged &lt;- rbind(mgs636513_phylum, mgs636528_phylum)
</code></pre>
<p>Inspect this newly-created object. Can you see what has been done?</p>
<p>And now, we plot the merged data, with some small modifications to the code we used before for the individual samples:</p>
<pre><code>ggplot(all_phylum, aes(x = variable, y = value)) +
	geom_bar(aes(fill = Sample), stat = "identity", position = "dodge")  + 
	theme(axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.5))
</code></pre>
<p>Take a look at the graph. What is/are the most abundant microbial groups in the samples? Are there differences between the two samples?</p>
<p>Now, it is time to take this to take this to the next level and work with the data you downloaded yourself from MG-RAST. First we will erase everything and start from scratch, so that there is no conflict between the new and the old data. To do this, type:</p>
<pre><code>rm(list = ls())
</code></pre>
<p>To make it easier, I copy below once again the commands we have used so far. All you have to do is change the sample name (<em>mgmXXXXXX</em>) to match the names of the data you downloaded. Remember to change all the instances, not only the first one!</p>
<pre><code>mgmXXXXXX_phylum &lt;- read.table("mgmXXXXXX_phylum.csv", header = T, sep = "\t")
mgmXXXXXX_phylum &lt;- sweep(mgmXXXXXX_phylum, 1, rowSums(mgmXXXXXX_phylum), "/")
mgmXXXXXX_phylum &lt;- melt(mgmXXXXXX_phylum)
mgmXXXXXX_phylum &lt;- mgmXXXXXX_phylum[mgmXXXXXX_phylum$value &gt; 0.01, ]
ggplot(mgmXXXXXX_phylum, aes(x = variable, y = value)) +
	geom_bar(stat = "identity")  + 
	theme(axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.5))
</code></pre>
<p>Do one sample first and then the other(s). When all samples have been added to RStudio, combine the data from all samples into one new object (again, remember to change the sample names):</p>
<pre><code>mgmXXXXXX_phylum$Sample &lt;- "mgmXXXXXX"	###SAMPLE 1
mgmXXXXXX_phylum$Sample &lt;- "mgmXXXXXX"	###SAMPLE 2
phylum_merged &lt;- rbind(mgmXXXXXX_phylum, mgmXXXXXX_phylum)
ggplot(phylum_merged, aes(x = variable, y = value)) +
	geom_bar(aes(fill = Sample), stat = "identity", position = "dodge")  + 
	theme(axis.text.x = element_text(angle = 90, hjust = 1, vjust = 0.5))
</code></pre>
<p>Again, take a look at the graph. What is/are the most abundant microbial groups in the samples? Go around the room and check the results from your colleagues. Are there any differences in microbial community composition between the environments you and your colleagues have analysed? What are them? Remember to consider the metadata! What are the samples you are analysing from? And your colleagues’? Do you think that the differences you are seeing are due to what?</p>
<p>If you have time left, why not investigate the functional composition of the metagenomes? Simply redo everything from the top, but this time work with the <em>mgmXXXXXX_subsystems.csv</em> files, which contains the functional annotations. And remember to change the variable names as well!</p>
<h2 id="final-remarks">Final remarks</h2>
<p>This was a <em>very</em> basic introduction to R and how to use it to analyse metagenome data. If you want to learn more, I recommend the material below as good starting points. But remember, you only learn R by using it!</p>
<ul>
<li><a href="https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf">https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf</a></li>
<li><a href="https://kannu.csc.fi/s/Xk2jIQT7wiB3H1c/download">https://kannu.csc.fi/s/Xk2jIQT7wiB3H1c/download</a></li>
<li><a href="https://www.rstudio.com/wp-content/uploads/2016/10/r-cheat-sheet-3.pdf">https://www.rstudio.com/wp-content/uploads/2016/10/r-cheat-sheet-3.pdf</a></li>
</ul>

