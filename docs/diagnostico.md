Parte 1:
1.1  1. El paso de publicar, se ejecuta sin que termine el paso de validar, es decir se construye y publica aún si las pruebas fallan.
  2. El pipeline no especifica la rama en la que se ejecuta, entonces en cada push se va a ejecutar.
  3. Las dependencias se instalan desde un archivo .txt, debería usarse el .lock ya que es un archivo ya establecido y que no va a generar conflictos.
  4. Las dependencias no se guardan en el caché para cada ejecución.
  
1.2 El defecto explicativo del caso es el 1, al no tener un needs, se ejecutan ambos pasos en paralelo, lo cuál hace que se genere un tiempo de ejecución menor.

1.3 La validación de las pruebas, en este caso el pipeline no espera a que se realicen las pruebas, independientemente de si pasan o no, se publica el artefacto.

1.4 La métrica de Lead time, ya que se optimizará el pipeline para que demore menos y la tasa de errores en despliegue, haciendo que se cumplan las validaciones antes de publicar el artefacto. En este caso elegí la métrica del Lead Time.

1.5 El número a medir es el de la línea base de 59s en ejecución del pipeline.

4.1 Medicion posterior

El proxy elegido fue la duracion total de la ejecucion del pipeline. La linea
base fue de 59 s y la ejecucion posterior de la intervencion duro 16 s, segun el
run fallido del 10/09/2026:
https://github.com/Cereal-jpg/INF384-lab2-20220749/actions/runs/34537177256

El cambio fue de 43 s menos, equivalente a una reduccion aproximada de 72.9 %:
((59 - 16) / 59) * 100. La ejecucion posterior termina antes porque la
validacion detiene el pipeline en el analisis de calidad y el artefacto no se
publica.

4.2 Justificacion de la version

Se declaro la version 1.3.0 en `VERSION` y `pyproject.toml`. Desde `v1.2.0`, el
historial contiene cambios de funcionalidad compatibles hacia atras, sustentados
por los commits `e923962` (modelo de pedidos), `0b981ca` (calculo de tarifas),
`b7e44ce` (validaciones) y `562e631` (desglose de tarifas). Por existir nuevas
funcionalidades, corresponde un incremento menor de 1.2.0 a 1.3.0, no un
incremento de parche.

4.3 Lo que no se resolvio

El quality gate de SonarCloud sigue dependiendo de una configuracion externa al
repositorio: sus condiciones de cobertura y los permisos del token se gestionan
en SonarCloud. Para resolverlo completamente habria que configurar alli una
condicion de cobertura sobre codigo nuevo y verificar el proyecto, token y
variables del repositorio. La comprobacion `diff-cover` del workflow funciona
como proteccion versionada mientras esa configuracion externa no este asegurada.

4.4 Declaracion de uso de IA generativa

Se utilizo GitHub Copilot como herramienta de IA generativa para inspeccionar el
repositorio, proponer y aplicar cambios en el workflow, agregar la funcion sin
cobertura y redactar este cierre. Las decisiones sobre la version, los cambios
aceptados y la verificacion mediante pruebas, cobertura y ejecuciones de GitHub
Actions fueron revisadas por el estudiante.
