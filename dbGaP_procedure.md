# dbGap website

##Request the data
Now, the data request go through [dbGaP website](https://dbgap.ncbi.nlm.nih.gov/aa/wga.cgi?page=list_viewonly&login=NFL).

A PI identificator is necessary to log in. The procedure is to create a new project, submit it, and wait for dbGaP NCBI comitee agreement.

The dataset you need to select during you project creation is the following one if you want to have access to all TCGA data (also controlled data) : 
>TCGA - The Cancer Genome Atlas (phs000178.v9.p8)
>
>General Research Use (phs000178.v9.p8.c1), TCGA

##Get dbGap repository key
Once accepted, you can go in tab "My Projects", and you can click on "get dbGaP repository key" on "Action" column of the table.

[F1](f1.png)

This will allow you to download a file with ".ngc" extension. Save this file.

##SRA toolkit
You need SRAtoolkit that you can download [here](https://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?cmd=show&f=software&m=software&s=software).

Then follow the procedure describe [here](https://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=toolkit_doc&f=std) to install and to configure it.

```bash
./vdb-config -i
```
You have to load the ".ngc" file into SRAtoolkit software.
For this, follow the procedure describe [here](https://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=toolkit_doc&f=dbgap_use).

##Go through AsperaConnect plugin
Let get back to [dbGaP website](https://dbgap.ncbi.nlm.nih.gov/aa/wga.cgi?page=list_viewonly&login=NFL).
Now, go on "Downloads" tab (once logged) and click on "Download" on "Action" column of the table.

[F2](f2.png)

You will be redirected to a page telling you to use [AsperaConnect plugin](http://downloads.asperasoft.com/en/documentation/8). Download it.

Launch the command line that should be in the same page :

```bash
"%ASPERA_CONNECT_DIR%\bin\ascp" -QTr -l 300M -k 1 -i "%ASPERA_CONNECT_DIR%\etc\asperaweb_id_dsa.openssh" -W A78E825FFD74A20A584CA459143DDE96325980DFAFCZS6A64C57459D67EA81C43D dbtest@gap-upload.ncbi.nlm.nih.gov:data/instant/username/54221 .
```
It will download file to the directory you are.

You can go through the downloaded files, that should finish with "enc" because it's encoded files.
You can use this SRAtoolkit command to be able to unencode the files :

```bash
vdb-decrypt file_enc
```

>I don't understand the purpose of this step with aspera software, but it has allow me to have access to TCGA gdc portal only once I've done this step. Before, I was unable to get the token, and I was disconnected when click on "Download Token".

[F3](f3.png)

##Go back to the initial procedure in the README.md file of this Git repository.
