import pandas as pd
import matplotlib.pyplot as plt

def main():
    # URL directa para descargar el CSV desde Zenodo.
    # Nota: Se agrega el parámetro ?download=1 para forzar la descarga.
    url = "https://sandbox.zenodo.org/record/164571/files/USA_cars_dataset.csv?download=1"
    
    try:
        # Cargar el dataset directamente desde la URL
        df = pd.read_csv(url)
        print("Dataset cargado correctamente.")
    except Exception as e:
        print("Error al cargar el dataset:", e)
        return

    # Mostrar las primeras filas para verificar el contenido
    print(df.head())
    
    # Imprimir las columnas disponibles para saber qué variables contiene el dataset
    print("Columnas del dataset:", df.columns.tolist())
    
    # En este ejemplo se crea un gráfico de dispersión (scatter plot) entre 'horsepower' y 'mpg'
    # Verificamos que las columnas existen en el DataFrame
    if 'horsepower' in df.columns and 'mpg' in df.columns:
        plt.figure(figsize=(10, 6))
        plt.scatter(df['horsepower'], df['mpg'], alpha=0.7, color='blue')
        plt.title('Relación entre Horsepower y MPG')
        plt.xlabel('Horsepower')
        plt.ylabel('MPG')
        plt.grid(True)
        plt.show()
    else:
        print("El dataset no contiene las columnas 'horsepower' y 'mpg'.")
        print("Por favor, verifica el contenido del CSV y ajusta el script según las columnas disponibles.")

if __name__ == "__main__":
    main()
