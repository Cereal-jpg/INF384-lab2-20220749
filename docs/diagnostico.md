Parte 1:
1.1  1. El paso de publicar, se ejecuta sin que termine el paso de validar, es decir se construye y publica aún si las pruebas fallan.
  2. El pipeline no especifica la rama en la que se ejecuta, entonces en cada push se va a ejecutar.
  3. Las dependencias se instalan desde un archivo .txt, debería usarse el .lock ya que es un archivo ya establecido y que no va a generar conflictos.
  4. Las dependencias no se guardan en el caché para cada ejecución.
  
1.2 El defecto explicativo del caso es el 1, al no tener un needs, se ejecutan ambos pasos en paralelo, lo cuál hace que se genere un tiempo de ejecución menor.

1.3 La validación de las pruebas, en este caso el pipeline no espera a que se realicen las pruebas, independientemente de si pasan o no, se publica el artefacto.

1.4 La métrica de Lead time, ya que se optimizará el pipeline para que demore menos y la tasa de errores en despliegue, haciendo que se cumplan las validaciones antes de publicar el artefacto. En este caso elegí la métrica del Lead Time.

1.5 El número a medir es el de la línea base de 59s en ejecución del pipeline. 
