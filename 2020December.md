## Decemeber 14, 2020

Today, I looked through the Jupyter Notebook scripts for the Foreseer and the Visual T&D data, to make sure that everything had comments with it. 

## December 21, 2020

Today, I looked through the data that was collected from the meters on December 18 that is on the EMRDA Research Workspace. While looking through the files, it appears that some of the data is missing. I have listed the files that appear to be missing. The majority of the files that appear to be missing contain a hdr file in the set that is of the size 0 B. This condition occurs only on October 21 and is usually the first set, with the exception of 192-168-2-5, which occurs on October 7. The sets that are missing an hdr file should not be a problem, since the Event-to-Influx Jupyter Notebook scripts do not use the hdr file.

- 20
    - 2020-10-21
        - wv00015577.cfg
        - wv00015577.dat
        - wv00015577.hdr (Present and contains 0 B)
- 22
    - 2020-10-20
        - wv00015873.hdr
- 26
    - 2020-10-21
        - wv00019759.cfg
        - wv00019759.dat
        - wv00019759.hdr (Present and contains 0 B)
- 27
    - 2020-10-21
        - wv00003973.cfg
        - wv00003973.dat
        - wv00003973.hdr (Present and contains 0 B)
     - 2020-11-6
        - wv00003979.hdr
- 29
    - 2020-10-21
        - wv00003816.cfg
        - wv00003816.dat
        - wv00003973.hdr (Present and contains 0 B)
- 30
    - 2020-10-21
        - wv00020206.cfg
        - wv00020206.dat
        - wv00020206.hdr (Present and contains 0 B)
    - 2020-10-31
        - wv00020211.hdr 
- 5
    - 2020-10-7 
        - wv00000001.cfg
        - wv00000001.dat
        - wv00000001.hdr (Present and contains 0 B)


The following folders are empty
- 24
- 25


The following has an addition file extention and does not include a cfg or a dat file with it. The size of this file is 0 B.
- 22
    - 2020-10-14
        - wv00000026.hdr.sLccto 


Using the Event-to-Influx-Version2.ipynb script, the following sets were tried. When using Comtrade to load the data, errors occured. 
- 10
    - 2020-10-19
        - wv00000003.cfg
        - wv00000003.dat
        - wv00000003.hdr
        - Error: 'utf-8' codec can't decode byte 0xb0 in position 72: invalid start byte               
- 13
    - 2020-10-21
        - wv00000006.cfg
        - wv00000006.dat
        - wv00000006.hdr
        - Error: 'utf-8' codec can't decode bytes in position 72-73: invalid continuation byte
        
          



