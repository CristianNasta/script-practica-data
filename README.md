import pandas as pd
import matplotlib.pyplot as plt

# Leer correctamente el archivo CSV
data = pd.read_csv('USA_cars_datasets.csv', delimiter=',')
data['date'] = pd.to_datetime(data['year'], format='%Y')  

# Graficar los datos
data.plot(x='date', y='price')  
plt.show()

# Calcular el precio medio por marca
precioMedio = data.groupby('brand')['price'].mean()
res1 = precioMedio.index

# Graficar el precio medio por marca
plt.title('Marca y precio de los coches')
plt.ylabel('Marca')
plt.xlabel('Precio medio')
plt.xticks(rotation=90)
plt.bar(res1, precioMedio)
plt.show()
