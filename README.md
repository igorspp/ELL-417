<p><em><strong>ELL-417: Introduction to bioinformatics for microbiologists</strong></em></p>
<h1 id="day-6---introduction-to-metagenomics--r">Day 6 - Introduction to metagenomics &amp; R</h1>
<p><strong>by Dr. Igor S. Pessi</strong><br>
<em>Arctic Microbial Ecology<br>
Department of Microbiology, UH<br>
<a href="mailto:igor.pessi@helsinki.fi">igor.pessi@helsinki.fi</a></em></p>
<h2 id="section"></h2>
<h2 id="recommended-literature">Recommended literature</h2>
<h3 id="metagenomics">Metagenomics</h3>
<ul>
<li><a href="https://www.nature.com/articles/nbt.3935">https://www.nature.com/articles/nbt.3935</a></li>
</ul>
<h3 id="r-and-rstudio">R and RStudio</h3>
<ul>
<li><a href="https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf">https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf</a></li>
<li><a href="https://kannu.csc.fi/s/Xk2jIQT7wiB3H1c/download">https://kannu.csc.fi/s/Xk2jIQT7wiB3H1c/download</a></li>
</ul>
<h2 id="section-1"></h2>
<h2 id="installing-r-and-rstudio">Installing R and RStudio</h2>
<p>First we need to install R. Just download below the appropriate version for your computer and follow the instructions:</p>
<p><strong>Windows:</strong> <a href="https://cran.rstudio.com/bin/windows/base/R-3.5.0-win.exe">https://cran.rstudio.com/bin/windows/base/R-3.5.0-win.exe</a><br>
<strong>Mac OS X 10.6 (Snow Leopard) - 10.8 (Mountain Lion):</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.2.1-snowleopard.pkg">https://cran.rstudio.com/bin/macosx/R-3.2.1-snowleopard.pkg</a><br>
<strong>Mac OS X 10.9 (Mavericks) and higher:</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.3.3.pkg">https://cran.rstudio.com/bin/macosx/R-3.3.3.pkg</a><br>
<strong>Mac OS X 10.11 (El Capitan) and higher</strong> <a href="https://cran.rstudio.com/bin/macosx/R-3.5.0.pkg">https://cran.rstudio.com/bin/macosx/R-3.5.0.pkg</a></p>
<p>Once R has finished installing, we can then install RStudio:</p>
<p><strong>Windows Vista/7/8/10:</strong> <a href="https://download1.rstudio.org/RStudio-1.1.447.exe">https://download1.rstudio.org/RStudio-1.1.447.exe</a><br>
<strong>Mac OS X 10.6+ (64-bit):</strong> <a href="https://download1.rstudio.org/RStudio-1.1.447.dmg">https://download1.rstudio.org/RStudio-1.1.447.dmg</a></p>
<h2 id="section-2"></h2>
<h2 id="activity-1-browsing-and-downloading-data-from-mg-rast">Activity 1: browsing and downloading data from MG-RAST</h2>
<ol>
<li>Go to <a href="https://www.mg-rast.org/">https://www.mg-rast.org/</a></li>
<li>Click “download”</li>
<li>Click “search website”</li>
<li>In the top-left of the page, search for a metagenome of interest (e.g. cow rumen)</li>
<li>Go through the search results and select a study
<ul>
<li>Make sure that <strong>seq type</strong> is <em>shotgun metagenome</em> NOT <em>amplicon metagenome</em></li>
<li>If you want you can narrow the search using the <em>Refine Search</em> box in the right-hand of the page (<strong>field</strong> = <em>seq type</em>, <strong>term</strong> = <em>shotgun metagenome</em>; and click <em>add</em>)</li>
</ul>
</li>
</ol>

