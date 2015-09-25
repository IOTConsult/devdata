---
title       : Coursera Slidify Assignment
subtitle    : 
author      : Serge Kestens (IOTConsult)
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [bootstrap, quiz, shiny, interactive]
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction
<br>
<br>
<br>
<br>

For this assignment, we need to create 5 slides in Slidify.<br>
The first slides contain a small description and introduction.<br>
Slide 3 will do the needed calculations on the dataframe.<br>
Slide 4 presents these results in a GoogleVis Line Chart.<br>
Slide 5 presents the same results in a GoogleVis Table.<br>


--- .class #id 
## Data calculations on an imported rds file


```r
setwd ("C:/Users/gjf510/Google Drive/DataScience/Projects/coursera/devdata/IOTConsult")
TotalRevenue <- readRDS("data/TotalRevenue.rds")
#print(TotalRevenue)
library(plyr)
library(reshape2)

Revenue <- ddply(TotalRevenue, c("Year"), summarise,
                Total = sum(Total),
                Services = sum(Services),
                Products = sum(Products))
print(Revenue)
```

```
##   Year    Total  Services Products
## 1 2012 127955.6 110454.45 17501.20
## 2 2013 118762.1 102390.20 16371.95
## 3 2014 106375.7  89603.72 16772.00
## 4 2015  87857.0  72274.50 15582.50
```

--- &interactive
## GoogleVis Linechart example
<br>
<br>
<!-- LineChart generated in R 3.2.2 by googleVis 0.5.10 package -->
<!-- Fri Sep 25 08:33:24 2015 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataLineChartID20ac1b7d31a4 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "2012",
127955.65,
110454.45,
17501.2 
],
[
 "2013",
118762.15,
102390.2,
16371.95 
],
[
 "2014",
106375.725,
89603.725,
16772 
],
[
 "2015",
87857,
72274.5,
15582.5 
] 
];
data.addColumn('string','Year');
data.addColumn('number','Total');
data.addColumn('number','Services');
data.addColumn('number','Products');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartLineChartID20ac1b7d31a4() {
var data = gvisDataLineChartID20ac1b7d31a4();
var options = {};
options["allowHtml"] = true;
options["width"] =    900;
options["height"] =    300;
options["legend"] = "bottom";
options["hAxis"] = {title:'Type'};
options["vAxis"] = {title:'Total'};

    var chart = new google.visualization.LineChart(
    document.getElementById('LineChartID20ac1b7d31a4')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartLineChartID20ac1b7d31a4);
})();
function displayChartLineChartID20ac1b7d31a4() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartLineChartID20ac1b7d31a4"></script>
 
<!-- divChart -->
  
<div id="LineChartID20ac1b7d31a4" 
  style="width: 900; height: 300;">
</div>

---
## GoogleVis Table example
<br>
<br>
<!-- Table generated in R 3.2.2 by googleVis 0.5.10 package -->
<!-- Fri Sep 25 08:33:24 2015 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataTableID20ac35d336ee () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 2012,
127955.65,
110454.45,
17501.2 
],
[
 2013,
118762.15,
102390.2,
16371.95 
],
[
 2014,
106375.725,
89603.725,
16772 
],
[
 2015,
87857,
72274.5,
15582.5 
] 
];
data.addColumn('number','Year');
data.addColumn('number','Total');
data.addColumn('number','Services');
data.addColumn('number','Products');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartTableID20ac35d336ee() {
var data = gvisDataTableID20ac35d336ee();
var options = {};
options["allowHtml"] = true;
options["page"] = "enable";

  var dataFormat1 = new google.visualization.NumberFormat({pattern:"#,###"});
  dataFormat1.format(data, 3);
  var dataFormat2 = new google.visualization.NumberFormat({pattern:"#,###"});
  dataFormat2.format(data, 2);
  var dataFormat3 = new google.visualization.NumberFormat({pattern:"#,###"});
  dataFormat3.format(data, 1);

    var chart = new google.visualization.Table(
    document.getElementById('TableID20ac35d336ee')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "table";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartTableID20ac35d336ee);
})();
function displayChartTableID20ac35d336ee() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartTableID20ac35d336ee"></script>
 
<!-- divChart -->
  
<div id="TableID20ac35d336ee" 
  style="width: 500; height: automatic;">
</div>





