# Counting San Diego Homeless


The ``source_files`` director holds all of the source PDFs. images are extracted from them with the ``dsdp_extract``
program. The program builds the set of images in the ``images`` directory.

The ``dsdp_text`` program tries to read the images to determine what the neighborhood name is. It will also rotate
the image and move the rotated, renamed images to the ``process_images`` directory.


# Running Updates

First, install the ``dtcv`` package in ``src/dtcv``

```bash
pip install -e src/dtcv
```

Unpack your files for your update into one of the update directories, 
like ``update-2024``. The directory should have your files in it in the 
same format as the other directories in ``update-2022``, for instance:

update-2022/SDDT_092623
├── count
├── gcp
├── gcp-errors
├── intersection.csv
└── output

* ``count`` has all of the JSON files for the counts that were saved out of VIA
* ``gcp`` has all of the GCP files saved outof VIA
* ``intersection.csv`` lists your GCP intersections. 

The ``gcp-errors`` and ``output`` directories are created by the programs. 


To process the files, run these programs: 

```bash
dt_process -i intersection.csv -c count output
dt_process -i intersection.csv -g gcp output
dt_process --final output
```


