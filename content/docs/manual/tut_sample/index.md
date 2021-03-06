---
title: "Create a Sample"
description: "Create a sample from an Illumina FASTQ file."
menu:
  manual:
    parent: "Tutorials"
    weight: 40
---

# Upload a FASTQ File

Go to **Samples** view via the main navigation bar.

![Empty Sample Manager](empty.png)

Click **Files** in the left sidebar to go to the sample read file manager.

![Sample File Manager](files.png)

Upload a FASTQ read file.

{{< video "upload.mp4" >}}

In the **Samples** view, click {{< icon "fa fa-plus-square" >}} to open the sample creator. The file you uploaded should now be available in file list.

![Sample Creator](create.png)

# Create a Sample

Fill out the fields in the sample creator. Only the sample name, subtraction host, and one or two read files are required.

![Sample Creator Filled](filled.png)

Click {{< icon "fas fa-save" >}} **Save** and you should immediately see a placeholder for your sample in the **Samples** view. The spinner indicates that the sample
is still being created.

![Sample Creator Filled](creating.png)

When the sample creation process is finished your sample will look something like this:

![Sample Creation Complete](ready.png)

When the sample is ready, you can see some information about your sample by clicking the sample entry in the **Samples** view.

![Sample General Information](general.png)

You can view a quality assessment generated using [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/), by clicking the **Quality** tab.

![Sample Quality](quality.png)
