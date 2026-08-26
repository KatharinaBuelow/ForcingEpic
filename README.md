# Welcome

## How to produce the forcing files for EPIC from RCM data on levante

Niedersachsen

Landkreite

Temp min
Temp max
Precipitation
Humidity
Radiation
Wind velocity), (CO2 concentration

CO2 concentration, nicht täglich, max. jährlich :-> LARS , Du brauchst CMIP5 und CMIP6


Vorschlag:
https://esgf-data.dwd.de/csys/project/climateprojectionsde/ 
Daten:
Die CMIP5 bias-korrigierten Daten sind über unseren ESGF-Server abrufbar - Project: ClimateProjectionsDE:
https://esgf-data.dwd.de/metagrid/search

# Workflow auf levante

## 1. create environment

conda create --name epic python==3.13

      conda activate epic

Next step would be to install what you need in your environment.

install index_calculation from :

https://codebase.helmholtz.cloud/gerics_infrastructure/index_calculation

frist clone it to the directory where you keep repositories

      git clone https://codebase.helmholtz.cloud/gerics_infrastructure/index_calculation.git

      cd index_calculation

      install with

      pip install -e .

check if it works with:

      index_calculation -h
      
The enironmeent only needs to get created once, afterwards you can use it.

    conda activate epic aufrufen.

Please consider to keep your environment upto date and 

       pip install --upgrade xclim



Now you are ready to create your first catalogue and your first index

##Catalogue (theoretisch)

Catalogue (your output directory must exsist):

          index_calculation -p CORDEX build_catalogue -o /work/ch0636/YOUR_USER_NUMBER/FORCING-EPIC/index_calculation -i DATADIR -no_idx -show

If you have a lot of file, you should submit this as a job to levante, otherwise dkrz will complain.

path to your data:

Wir müssen doch die Daten ruterladen

Dann muss ich dir ein neues Project anlegen, denn mit dem CORDEX project lassen sich die dwd Daten nicht einlesen. Das mache ich dann sobald die Daten da sind und ich die Struktur erkennen kann. Dann machen wir jetzt erstmal weiter mit den CORDEX Daten. Der Catalogue existiert und muss nicht erstellt werden.
Hier ist es auch sinnvoll den existierenden Catalogue zu verwenden, da ich hier nur die vollständigen Variablen drinn habe.

Dr CORDEX Catalogue (EUR-11) liegt hier:
/work/ch0636/eddy/pool/intake-esm_catalogues/


Catalogue (your output directory must exsist):

	  index_calculation -p CORDEX build_catalogue -o /work/ch0636/g300047/FORCING-EPIC/index_calculation -i /work/bb1364/g260070/CMIP5-EUR12-Data/DWD_Referenz_2018_biascor/tas -no_idx -show


## Calculate index

index_calculation -p CORDEX create_scripts -idx TX -intake /work/ch0636/eddy/pool/intake-esm_catalogues/CORDEX_EUR-11_ensemble.json -scrpt_dir /scratch/g/g300047/index_calculation/EPIC/ -out_dir /work/ch0636/g300047/FORCING-EPIC/index_calculation -ofreq day -rename_exp -submit



## working with climate fact data

The most tricky part is to set up an environment, it takes a long time,
climate fact data useds xesmf so I always follow their [instructions](https://xesmf.readthedocs.io/en/stable/installation.html)

    conda create --name climfactepic python==3.13
    conda activate climfactepic
    conda install -c conda-forge xesmf
    conda install -c conda-forge dask netCDF4
    conda install -c conda-forge matplotlib cartopy jupyterlab
    