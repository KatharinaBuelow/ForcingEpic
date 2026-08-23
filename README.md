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
Würde dies für dich passen ? https://esgf-data.dwd.de/csys/project/climateprojectionsde/ 
Daten:
Die CMIP5 bias-korrigierten Daten sind über unseren ESGF-Server abrufbar - Project: ClimateProjectionsDE:
https://esgf-data.dwd.de/metagrid/search

# Workflow

## 1. create environment


conda create --name epic python==3.13
conda activate epic

install index_calculation from :

https://codebase.helmholtz.cloud/gerics_infrastructure/index_calculation

frist clone it to the directory wher you keep repositories

git clone https://codebase.helmholtz.cloud/gerics_infrastructure/index_calculation.git

cd index_calculation


install with

pip install -e .

check if it works with:
index_calculation -h

Now you are ready to create your first catalogue and your first index

Catalogue
path to your data:

## Wir müssen doch die Daten ruterladen

Hier ein test /work/bb1364/g260070/CMIP5-EUR12-Data/DWD_Referenz_2018_biascor/tas

Catalogue:

index_calculation -p CORDEX build_catalogue -o /work/ch0636/g300047/FORCING-EPIC/index_calculation/catalogues/ -i /work/bb1364/g260070/CMIP5-EUR12-Data/DWD_Referenz_2018_biascor/tas -no_idx -show


   