<p><em><strong>ELL-417: Introduction to bioinformatics for microbiologists</strong></em></p>
<h1 id="day-6---introduction-to-metagenomics--r">Day 6 - Introduction to metagenomics &amp; R</h1>
<p><strong>by Dr. Igor S. Pessi</strong><br>
<em>Arctic Microbial Ecology<br>
Department of Microbiology, UH<br>
<a href="mailto:igor.pessi@helsinki.fi">igor.pessi@helsinki.fi</a></em></p>
<h2 id="section"></h2>
<h3 id="recommended-literature">Recommended literature</h3>
<h4 id="metagenomics">Metagenomics</h4>
<ul>
<li><a href="https://www.nature.com/articles/nbt.3935">https://www.nature.com/articles/nbt.3935</a></li>
<li><a href="https://academic.oup.com/bib/article/13/6/696/194123">https://academic.oup.com/bib/article/13/6/696/194123</a></li>
<li><a href="https://www.nature.com/news/mining-the-microbial-dark-matter-1.17774">https://www.nature.com/news/mining-the-microbial-dark-matter-1.17774</a></li>
<li><a href="https://www.nature.com/articles/nrmicro3468">https://www.nature.com/articles/nrmicro3468</a></li>
<li><a href="https://www.sciencedirect.com/science/article/pii/S0958166911007245">https://www.sciencedirect.com/science/article/pii/S0958166911007245</a></li>
<li><a href="https://www.nature.com/articles/nmeth.4458">https://www.nature.com/articles/nmeth.4458</a></li>
<li><a href="https://bmcgenomics.biomedcentral.com/articles/10.1186/s12864-017-3918-9">https://bmcgenomics.biomedcentral.com/articles/10.1186/s12864-017-3918-9</a></li>
</ul>
<h4 id="r-and-rstudio">R and RStudio</h4>
<ul>
<li><a href="https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf">https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf</a></li>
<li><a href="https://kannu.csc.fi/s/Xk2jIQT7wiB3H1c/download">https://kannu.csc.fi/s/Xk2jIQT7wiB3H1c/download</a></li>
</ul>
<h2 id="section-1"></h2>
<h3 id="installing-r-and-rstudio">Installing R and RStudio</h3>
<p>First we need to install R. Just download below the appropriate version for your computer and follow the instructions:</p>
<p><strong>Windows:</strong> <a href="https://cran.rstudio.com/bin/windows/base/R-3.5.0-win.exe">https://cran.rstudio.com/bin/windows/base/R-3.5.0-win.exe</a><br>
<strong>Mac OS X 10.6 (Snow Leopard) – 10.8 (Mountain Lion):</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.2.1-snowleopard.pkg">https://cran.rstudio.com/bin/macosx/R-3.2.1-snowleopard.pkg</a><br>
<strong>Mac OS X 10.9 (Mavericks) and higher:</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.3.3.pkg">https://cran.rstudio.com/bin/macosx/R-3.3.3.pkg</a><br>
<strong>Mac OS X 10.11 (El Capitan) and higher</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.5.0.pkg">https://cran.rstudio.com/bin/macosx/R-3.5.0.pkg</a></p>
<p>Once R has finished installing, we can then install RStudio:</p>
<p><strong>Windows Vista/7/8/10:</strong> <a href="https://download1.rstudio.org/RStudio-1.1.447.exe">https://download1.rstudio.org/RStudio-1.1.447.exe</a><br>
<strong>Mac OS X 10.6+ (64-bit):</strong> <a href="https://download1.rstudio.org/RStudio-1.1.447.dmg">https://download1.rstudio.org/RStudio-1.1.447.dmg</a></p>
<h2 id="section-2"></h2>
<h3 id="activity-1-browsing-and-downloading-data-from-mg-rast">Activity 1: Browsing and downloading data from MG-RAST</h3>
<ol>
<li>Go to <a href="https://www.mg-rast.org/">https://www.mg-rast.org/</a></li>
<li>Click <em>download</em></li>
<li>Click <em>search website</em></li>
<li>In the top-left of the page, search for a metagenome of interest (e.g. cow rumen)</li>
<li>Go through the search results and select a study
<ul>
<li>Make sure that <strong>seq type</strong> is <em>shotgun metagenome</em> NOT <em>amplicon metagenome</em></li>
<li>If you want you can narrow down the search using the <em>Refine Search</em> box in the right-hand of the page (e.g. <strong>field</strong> = <em>seq type</em>, <strong>term</strong> = <em>shotgun metagenome</em>)</li>
</ul>
</li>
<li>In the study page, take a moment to familiarize yourself with the project
<ul>
<li>How many samples are there? What are the differences between them?</li>
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
<h2 id="section-3"></h2>
<h3 id="activity-2-understanding-the-basics-of-r">Activity 2: Understanding the basics of R</h3>
<p>Start R (NOT RStudio)</p>
<p><strong>On Windows:</strong><br>
<strong>On Mac:</strong> Open the <em>Finder</em>, go to <em>Applications</em> and double-click <em>R</em><br>
<strong>On Linux:</strong></p>
<p>We will now create two variables (<em>x</em> and <em>y</em>). In the command prompt, type:</p>
<pre><code>x = rnorm(50)
</code></pre>
<p>and hit <em>enter</em>. Now for the second variable:</p>
<pre><code>y = rnorm(x)
</code></pre>
<p>Let’s now take a look at the variables we just created. Simply type their name and hit <em>enter</em> (one at a time):</p>
<pre><code>x
y
</code></pre>
<p>What do you see? Can you understand what the command <em>rnorm</em> did? HINT: try typing:</p>
<pre><code>help(rnorm)
</code></pre>
<p>And now we will plot them:</p>
<pre><code>plot(x, y)
</code></pre>

