# Actividad-Integradora-M6
Actividad Integradora M6 :)
En este codigo se encuentra mi actividad integradora del M6, creo que una de las cosas que mas me costó trabajo fue saber la sintaxis correcta para gráficar lo que quería y además lograr que se viera friendly para el usuario. 
Me di cuenta de que streamlit y todas las librerias que usamos a lo largo de la actividad tienen muchísimos elementos para hacer que un dashboard como en este caso, sean un metodo de visualización mucho más sencillo y friendly para el user. Creo que puedo explotar muchísimo más estas herramientas con práctica y muchas más consulas. Trate de hacer una gráfica de pie, e incluso corrió en colab pero no logré que funcionara en streamlit. Adjunto el codigo por si existe algun feedback del por qué no corrio

'''
#CRIMENES POR HORA EJEJJE SUEÑO PERDIDO :(


df2 = df
df2['Incident Datetime'] = pd.to_datetime((df2['Incident Datetime']))

df2.index = df2['Incident Datetime']
robos_mañaneros = df2.between_time('00:00','08:00').count()
robos_tardecita = df2.between_time('08:01','16:00').count()
robos_nocturnos = df2.between_time('16:01','23:59').count()

y = np.array([robos_mañaneros['Row ID'],robos_tardecita['Row ID'], robos_nocturnos['Row ID']])
labels = ('0 a 8', '8 a 16', '16 a 24')
fig = plt.pie(y, 
              labels = labels)
plt.style.use('dark_background')

'''

Al final pude añadir una cajita de más información en el código por si se tiene tiempo de ver jeje, tiene una imagen de un perrito. 

