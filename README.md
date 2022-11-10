"My first project" 

pip install palmerpenguins
import pandas as pd
from palmerpenguins import load_penguins


# In[88]:


penguins = load_penguins()
print(penguins)


# In[89]:


p_notna=penguins.dropna() 
#eliminamos aquellas filas que contengan NA
print(p_notna) 


# In[90]:


print(p_notna.isna().any()) 
#comprobamos que si en las columnas hay N


# In[91]:


fem = p_notna[p_notna.sex== "female"].count() 
#contamos aquellas variables que sean female
print(fem)


# In[92]:


mal = p_notna[p_notna.sex== "male"].count() 
#contamos aquellas variables que sean male
print(mal)


# In[93]:


bySex = p_notna.groupby("sex") 
#hacemos la agrupación según sexo


# In[94]:


fem_value= p_notna.loc[bySex.groups['female'].values] 
#filtramos todas las filas según sexo, creando un nuevo dataframe
print(fem_value)


# In[95]:


media_fem = (fem_value.bill_length_mm).mean() 
#hacemos la media de la longitud del pico por female
print(media_fem)


# In[96]:


mal_value= p_notna.loc[bySex.groups['male'].values] 
#hacemos igual con male
print(mal_value)


# In[97]:


media_mal = (mal_value.bill_length_mm).mean() 
#hacemos la media de la longitud del pico por female
print(media_mal)


# In[98]:


bill_area = p_notna.bill_length_mm * p_notna.bill_depth_mm 
#multiplicamos la variable bill_length_mm con bill_depth_mm
p_notna['bill_area'] = bill_area 
#añadimos una nueva variable bill_area
print(p_area)


# In[99]:


p_fem = p_notna[p_notna['sex']=='female'] 
#filtramos los datos según female y creamos un dataframe
p_fem


# In[100]:


pfs = p_fem.groupby(['species']).mean() 
#aquí tomamos el dataframe filtrado, y agrupamos según species y aplicamos la función media
print(pfs.bill_length_mm)


# In[101]:


body_mass_kg = p_notna.body_mass_g / 100 
#dividimos la variable por 100 para obtener resultados en kg


# In[102]:


p_kg = p_notna 
#creamos un nuevo dataframe para no alterar los datos anteriores
p_kg['body_mass_kg'] = body_mass_kg 
#añadimos la variable al dataframe
print(p_kg)


# In[103]:


p_kg.drop(['body_mass_g'],axis=1) 
#eliminamos la variable body_mass_g"# My first project" 
