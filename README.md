# SURF: Summarizer of User Reviews Feedback

SURF (Summarizer for User Reviews Feedback) Tool - Version 1.0

Tool description:

Continuous Delivery (CD) enables mobile developers to release small, high quality chunks of working software in a rapid manner.  However, faster delivery and a higher software quality do neither guarantee user satisfaction nor positive business outcomes. Previous work demonstrates that app reviews may contain crucial information that can guide developer's software maintenance efforts to obtain higher customer satisfaction. However, previous work also proves the difficulties encountered by developers in manually analyzing this rich source of data, namely (i) the huge amount of reviews an app may receive on a daily basis and (ii) the unstructured nature of their content. In this paper, we introduce SURF (Summarizer of User Reviews Feedback) a tool able to (i) analyze and classify the information contained in app reviews and (ii) distill actionable change tasks for improving mobile applications. Specifically, SURF performs a systematic summarization of thousands of user reviews through the generation of an interactive, structured and condensed agenda of recommended software changes. An end-to-end evaluation of SURF, involving  2622 reviews related to 12 different mobile applications, demonstrates the high accuracy of SURF in summarizing user reviews content. In evaluating our approach we also involve the original developers of some analyzed apps, who confirm the practical usefulness of the software changes recommended by SURF.

Description of the content of folder "SURF-Tool":


This program is a free software you can redistribute it under the terms of the GNU Public License
as published by the Free Software Fundation either version 2 of the License, or (at your option)
any later version.

Please extract the contents of SURF-Tool.zip file in a folder of your choice.

The tool uses the following open source libraries: 
- version 3.4.1 of the Stanford CoreNLP library available at the following link: http://nlp.stanford.edu/software/corenlp.shtml
- version 3.6 of the Weka library available at the following link: http://sourceforge.net/projects/weka/files/?source=navbar
- version 0.6 of the Classifier4J library available at the following link: http://http://classifier4j.sourceforge.net/

You can find the needed jar files for running the tool in the "/lib" folder contained in the SURF-tool.zip file

Please add these jars and SURF.jar to the java classpath and run the org.surf.Main class.

SURF is a command-line tool which automatically extracts (and classifies) 
user feedbacks from app reviews that are useful for software maintenance/evolution.
SURF generates xml summaries of user reviews.

The tool accepts in input xml files having the structure showed
in the following example:

```xml
<reviews>
   <review>
   <review>
      <date>2012-01-28</date>
      <star_rating>4</star_rating>
      <user>Filigio</user>
      <app_version>1.50</app_version>
      <review_title>Walkin'by</review_title>
      <review_text>Great game to sharpen any age level's memory skills.</review_text>
   </review>
   <review>
      <date>2012-01-17</date>
      <star_rating>1</star_rating>
      <user>Teacher K-12 Gifted</user>
      <app_version>1.50</app_version>
      <review_title>Distracting ads</review_title>
      <review_text>Used to be an excellent game, but ads ruin the free version .</review_text>
   </review>
   ....
<reviews>
```
The reviews-downloader.jar utility (provided in the utility folder of SURF package) is an executable
jar file which automatically downloads reviews from the Google Play store and exports them in the required xml structure.
The reviews-downloader utility uses the following libraries:
- version 2.53.1 of the Selenium HQ java library available at the following link: http://www.seleniumhq.org/download/
- version 1.3.4 of the jDatePicker library available at the following link: https://sourceforge.net/projects/jdatepicker/

To use the reviews-downloader utility you need to indicate the Google Play link of the desired app. 
One web browser among Google Chrome and Mozilla Firefox (version 44.0.2 is the more stable) must be installed
in your system (only these two browser are supported). 

Such a utility uses Selenium WebDriver API in order to create local scripts for web browser automating.
While Selenium distribuition provides natively a driver for Mozilla FireFox, this does not happen for Google Chrome.
If you want to use Google Chrome you need to download the appropriate driver from the following link:

https://sites.google.com/a/chromium.org/chromedriver/downloads

Once downloaded the appropriate driver the tool requires to indicate the driver location.
NOTE: Newer versions of Chrome and Firefox could not be supported by the distribution of Selenium we are using.


SURF generates xml summaries to allow developers to easily use them for further analysis
or to integrate the tool outputs in third part frameworks. 

Users can also browse the tool outputs through the report-viewer.html utility we provide
in the utility folder of the SURF package. They just have to open the report-viewer.html 
file through a browser of their choice and select the desired xml report to browse.

Here we provide a running example from command Line:

Running example for Windows systems:
java -classpath "[MYPATH]/lib/*;[MYPATH]/SURF.jar" org.surf.Main inputFile.xml outputFile.xml 

Running example for Unix/Linux/MacOS systems:
java -classpath "[MYPATH]/lib/*:[MYPATH]/SURF.jar" org.surf.Main inputFile.xml outputFile.xml 


where:
  - [MYPATH] is the path in which the contents of the zipped file has been extracted.  
  - inputFile.xml is the input file containing all the user reviews data the tool has to analyze
  - outputFile.xml is the file which will contain the tool outputs.

To better visualize the summaries generated by SURF it is sufficient to open the
"outputFile.xml" file generated using "SURF.jar" with the utility
  "utility/report-viewer.html". 

