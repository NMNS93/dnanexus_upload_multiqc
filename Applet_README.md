# Upload Multiqc v1.1

## What does this app do?
Uploads a multiqc HTML report file to the Viapath Genome Informatics (VGI) web server. Following this, the app updates the web server index file with a link to the new report.

## What are typical use cases for this app?
On completion of a sequencing run, this app is run to present multiqc reports on the VGI server.

## What inputs are required for this app to run?
An HTML report file generated by multiqc.

## What does this app output?
- old_index.html: The HTML file downloaded from the server by an instance of this app
- new_index.html: The HTMl file generated and uploaded to the server by an instance of this app

## How does this app work?
Firstly, the app downloads the given input multiqc report. This is copied to the expected location on the server (/var/www/html/mokaguys/multiqc/reports). To connect to the server, this appl requires SSH keys, which are not included in the github repository for privacy reasons. The `rsync` command is used to perform the copy as it contains a checksum protocol to verify data integrity.

Next, the app adds a link to the top of the server's index.html file, which points to the new multiqc report. The script 'update_index.py' (bundled as an app resource) is used to generate this new index. Here, the beautifulsoup4 python module is used for HTML parsing. Below is an example of the HTML string inserted at the top of the report:
```
<br/>
<div class="well">
  <h1>REPORT</h1>
  <ul><a href="./reports/REPORT-multiqc.html">MultiQC report</a></ul>
</div>
<br/>
``` 

*Developed by Viapath Genome Informatics*