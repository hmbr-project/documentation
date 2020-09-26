# Downloading File and Sample Metadata

<!-- To get started with this tutorial, it is recommended that Steps 1 - 3 are followed in the [**Search for Data in the HMBR Portal**](Search-for-Data-in-the-HMBR-Portal) page so that there are files in the Shopping Cart. -->

For this example we will start with the two files from the shopping cart as picture below.

![shopping cart image](https://github.com/hmbr-project/documentation/blob/master/images/hmbr_data_portal/hmbr-shopping-cart-details.png)

The data portal has been designed to optimize bulk data downloads. Although the user can use the URLs to download individual files, we recommend that users use the bulk downloading capability. Bulk downloads are accomplished by creating a file manifest of the items in the cart. This file manifest can be used in conjunction with the [Portal Client](https://github.com/IGS/portal_client) or you may write a simple command line script to iterate over the manifest file to download the data.

Click on the shopping cart icon in the top-right of the screen to view the contents of the shopping cart. The details include a summary of the contents including the file count, and the data volume. In addition it gives a listing of the files with some details (See Figure below).

![Shopping cart display](https://github.com/hmbr-project/documentation/blob/master/images/hmbr_data_portal/hmbr-shopping-cart-details.png)

The user can download the manifest file(s) which includes the information needed by the [Portal Client](https://github.com/IGS/portal_client) to fetch the data from HMBR. There are two manifest files associated with the items in the cart, the file manifest and the file metadata manifest. The file manifest has the information needed to download the files including the unique ID of the file, the MD5 check sum if available, the file size, the URL(s), and the unique ID of the sample that this file is associated with. The metadata manifest has all the metadata information associated with the samples. The unique sample ID in the metadata manifest can be used to correlate the samples with specific files. Please note that one sample may be associated with one or more files.

![Download manifest files](https://github.com/hmbr-project/documentation/blob/master/images/hmbr_data_portal/hmbr-download-manifest.png)

Click on the **Download->File-Manifest** menu item (see highlighted box in Figure above) to download the manifest file to the local computer. You may also optionally download the sample metadata associated with the files in the manifest by downloading the **Sample Metadata** file.

***File Manifest Example***

NOTE: The file is a TSV file but it is been prettied up in a readable table format

file_id|md5|size|urls|sample_id
---|---|---|---|---
b14c198fc08f27987915bbecfd000c2e|ff2c73291a93d5a547b8ae48705ce125|147088|http://downloads.microbiome-bioactives.org/16s/HMBR_data/Pouchitis/G20000.tsv|5275f121f24f899514cfea0f303c15a8
b14c198fc08f27987915bbecfd009446|2373f32d064b4f454fc4a7746d4c1903|15863|http://downloads.microbiome-bioactives.org/16s/HMBR_data/Pouchitis/G20011.fasta.tar.gz|5275f121f24f899514cfea0f303c7808

***Sample Metadata Manifest Example***

NOTE: The file is a TSV file but it is been prettied up in a readable table format

sample_id|study_name|assay_prep|subject_accession|pmid|sample_accession|gender|disease|race|bmi|age_category|age_at_diagnosis_category|family_id|family_id_original_encoding|montreal_b_classification|montreal_l_classification|montreal_e_classification|montreal_a_classification|smoking_history|alcohol|calprotectin|immunosuppressants|immunosuppressants_original_encoding|steroids|steroids_original_encoding|antibiotics|antibiotics_original_encoding|control|database|sample_accession_database|sample_type|body_site|body_site_original_encoding|perianal|pcdai|5ASA|5ASA_original_encoding|batch|timepoint|timepoint_original_encoding|study_accession_database
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
5275f121f24f899514cfea0f303c15a8|Pouchitis|16S rRNA gene seq|IBD2721:1|25887922|N00268|Male|IC|None|19.0311418685|Senior (65+)|None|IBD2721|Family ID|None|None|E3|A3|Current|None|None|False|None|False|None|True|None|None|None|None|Biopsy|Ileum|Pouch|None|None|None|None|None|1|None|None
5275f121f24f899514cfea0f303c7808|Pouchitis|16S rRNA gene seq|NIH0524:1|25887922|N00280|Male|UC|None|17.1753203858|Adult (<65yrs)|None|NIH0524|Family ID|None|None|E3|A1|Never|None|None|False|None|False|None|False|None|None|None|None|Biopsy|Ileum|Pouch|None|None|None|None|None|1|None|None


Once you have the manifest files on your computer use the **Portal Client** to download the files described in the manifest files to your computer.

[top](#top)
