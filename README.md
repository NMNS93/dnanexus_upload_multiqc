# Upload MultiQC 

![Application logo](_assets/download.png)

A DNAnexus applet for hosting MultiQC reports on the Viapath Genomics web server:

```
dx run upload_multiqc_v1.1 -imultiqc_html=index.html
```

## Features

* Uploads MultiQC reports to the /reports folder for hosting
* Creates hyperlink to report in the webserver index
* Returns original and updated index file for auditing

## Installation

Clone and build the applet using the [DNAnexus SDK](https://documentation.dnanexus.com/downloads).


```bash
git clone https://github.com/NMNS93/dnanexus_upload_multiqc.git
## Note: Application keys should be copied to dnanexus_upload_multiqc/src/.ssh before build
dx build ./dnanexus_upload_multiqc
```

## Usage

```bash
usage: dx run upload_multiqc_v1.1 [-iINPUT_NAME=VALUE ...]

Applet: Upload Multiqc v1.1

Uploads multiqc file to the Viapath Genomics server

Inputs:
  Multiqc HTML: -imultiqc_html=(file)
        A multiqc html output file

Outputs:
  MultiQC server index.html files: upload_multiqc (array:file)
        Upload MultiQC app outputs
```

## License
MIT License. Copyright (c) 2019 Nana Mensah
