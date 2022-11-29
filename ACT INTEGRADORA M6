#IMPORTAR LIBRERIAS 

import streamlit as st 
import pandas as pd 
import numpy as np 
import plotly.express as px 
import matplotlib.pyplot as plt
from bokeh.io import output_file, show
from bokeh.plotting import figure
import plotly.graph_objects as go


st.title('Police Department Incidents Reports from 2018 to Present')
df = pd.read_csv("Police.csv")
st.subheader('A guide to visualise the crime zones in the US')

st.write("The Police Department of San Francisco have been collecting incident reports from 2018 to 2020. This dataset includes police incident reports filed by officer and by individuals through self-service online reporting for non-emergency cases. Reports included are those for incidents that occurred starting January 1, 2018 onward and have been approved by a supervising officer")
         
#st.experimental_singleton

if st.button('Quiero ver el dataset completo'):
    st.dataframe(df)

    
#CAMBIAR NOMBRE COLUMNA (lon y lat) AL DF

df = df.rename(columns = {'Latitude':'lat', 'Longitude':'lon'})


#FILTRO DEL DISTRITO POLICIA

police_district_options = df['Police District'].unique()
filter_police_selection = st.sidebar.selectbox('Seleccione el distrito de policia que quiera visualizar', police_district_options)
df = df[df['Police District'] == filter_police_selection]



#CRIMENES POR DIA SEMANA

st.title('Incidentes por dia de la semana')
st.subheader('En esta gráfica se puede observar el numero de incidentes clasificados por año de cada uno de los días de la semana')

filter_crimes_per_day = df[['Incident Year','Incident Day of Week']]
grafica_perrona = px.histogram(filter_crimes_per_day, x = "Incident Day of Week" , color = "Incident Year")
st.plotly_chart(grafica_perrona, use_container_width = True)


#VECINDARIO 

neigb_options = df['Analysis Neighborhood'].unique()
filter_neigb = st.sidebar.selectbox('SELECCIONAR VECINDARIO', neigb_options)
df = df[df['Analysis Neighborhood'] == filter_neigb]




st.header('Number of reports by year')
st.write('En esta sección se puede visualizar el número de reportes por año dependiendo del filtro que se le coloque')

freq = df.groupby('Incident Year')[['Analysis Neighborhoods']].count()
fig = go.Figure()
fig.add_trace(go.Bar(x=freq.index, y=freq['Analysis Neighborhoods']))
fig.update_layout(title="Number of reports by year",
     xaxis_title="Year",
     yaxis_title="Total",
     legend_title="Variables",
     font=dict(
         size=12,))
st.plotly_chart(fig, use_container_width=True)


#FILTRO DEL AÑO CON TABS

tab1,tab2,tab3,tab4 = st.tabs(["2018", "2019", "2020", 'All years'])

with tab1:

    df_tab = df[df['Incident Year'] == 2018]
    st.subheader('Incident Map')
    st.write('Despues de haber seleccionado los filtros que se quieren visualizar, este mapa despliega información sobre incidentes dentro del mapa de la ciudad. Podemos observar que hay una serie de tabs en donde se puede consultar la información de diferentes años que contiene el dataset asi como la información de todos los años juntos.')
    mapa_tab1 = df_tab
    st.map(mapa_tab1)
    
    st.subheader('Incident Category')
    st.write('En esta sección se puede visualizar los incidentes por categoria y su status actual, puede ser Open or Active, Cite or Arrest, Exceptional Adult')
    
    tab1 = df[['Incident Category', 'Resolution']]
    histo_tab1 = px.histogram(tab1, x = 'Incident Category', color='Resolution')
    st.plotly_chart(histo_tab1, use_container_width = True, text_auto=True)



with tab2:
    
    st.subheader('Numero de incidentes en el año')
    
    df_tab2 = df[df['Incident Year'] == 2019]
    mapa_tab2 = df_tab2
    st.map(mapa_tab2)
                   
    st.subheader('Incident Category')
    st.write('En esta sección se puede visualizar los incidentes por categoria y su status actual, puede ser Open or Active, Cite or Arrest, Exceptional Adult')
    
    tab2 = df_tab2[['Incident Category', 'Resolution']]
    histo_tab1 = px.histogram(tab1, x = 'Incident Category', color='Resolution')
    st.plotly_chart(histo_tab1, use_container_width = True, text_auto=True)

with tab3:
    st.subheader('Numero de incidentes en el año')
    df_tab3 = df[df['Incident Year'] == 2020]
    mapa_tab3 = df_tab3
    st.map(mapa_tab3)
                   
    st.subheader('Incident Category')
    st.write('En esta sección se puede visualizar los incidentes por categoria y su status actual, puede ser Open or Active, Cite or Arrest, Exceptional Adult')
    
    tab3 = df_tab3[['Incident Category', 'Resolution']]
    histo_tab3 = px.histogram(tab3, x = 'Incident Category', color='Resolution')
    st.plotly_chart(histo_tab3, use_container_width = True, text_auto=True)
    
with tab4:
    st.subheader('Numero de incidentes en el año')
    df_tab4 = df
    mapa_tab4 = df_tab4
    st.map(mapa_tab4)
                   
    st.subheader('Incident Category')
    st.write('En esta sección se puede visualizar los incidentes por categoria y su status actual, puede ser Open or Active, Cite or Arrest, Exceptional Adult')
    
    tab4 = df_tab4[['Incident Category', 'Resolution']]
    histo_tab4 = px.histogram(tab4, x = 'Incident Category', color='Resolution')
    st.plotly_chart(histo_tab4, use_container_width = True, text_auto=True)
    
with st.expander("Mas información"):
    st.write("""
        Si se requiere consultar mas información, es de utilidad descargar el csv en donde estan los datos presentados anteriormente, gracias por consultar este dashboard de información
    """)
    st.title('GRACIAS')
    st.image("https://i.pinimg.com/736x/d4/89/05/d48905d8b74be48507aed15cfbed84e4.jpg")

