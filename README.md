# "My first project" 

### Instalamos el paquete e importamos la librería 

%pip install palmerpenguins

import pandas as pd
from palmerpenguins import load_penguins

### Importamos los datos

penguins = load_penguins()

print(penguins)


### Eliminamos aquellas filas que contengan NA


p_notna=penguins.dropna() 

print(p_notna) 


### Comprobamos que si en las columnas hay NA


print(p_notna.isna().any()) 



### Contamos aquellas variables que sean female


fem = p_notna[p_notna.sex== "female"].count() 

print(fem)


### Contamos aquellas variables que sean male


mal = p_notna[p_notna.sex== "male"].count() 

print(mal)


### Hacemos la agrupación según sexo


bySex = p_notna.groupby("sex") 



### Filtramos todas las filas según sexo, creando un nuevo dataframe


fem_value= p_notna.loc[bySex.groups['female'].values] 

print(fem_value)


### Hacemos la media de la longitud del pico por female


media_fem = (fem_value.bill_length_mm).mean() 

print(media_fem)


### Hacemos igual con male


mal_value= p_notna.loc[bySex.groups['male'].values] 

print(mal_value)


### Hacemos la media de la longitud del pico por female


media_mal = (mal_value.bill_length_mm).mean() 

print(media_mal)


### Multiplicamos la variable bill_length_mm con bill_depth_mm


bill_area = p_notna.bill_length_mm * p_notna.bill_depth_mm 

### Añadimos una nueva variable bill_area

p_notna['bill_area'] = bill_area 

print(p_area)


### Filtramos los datos según female y creamos un dataframe


p_fem = p_notna[p_notna['sex']=='female'] 

p_fem


### Aquí tomamos el dataframe filtrado, y agrupamos según species y aplicamos la función media


pfs = p_fem.groupby(['species']).mean() 

print(pfs.bill_length_mm)


### Dividimos la variable por 100 para obtener resultados en kg


body_mass_kg = p_notna.body_mass_g / 100 



### Creamos un nuevo dataframe para no alterar los datos anteriores


p_kg = p_notna 

p_kg['body_mass_kg'] = body_mass_kg 


### Añadimos la variable al dataframe

print(p_kg)


### Eliminamos la variable body_mass_g


p_kg.drop(['body_mass_g'],axis=1) 

