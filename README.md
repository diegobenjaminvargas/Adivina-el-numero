# ¡Adivina el número!

## Resumen
Esta es mi primera práctica del Máster en Data Science, Big Data & Business Analytics, para el módulo de Programación Básica con Python. El objetivo consistía en desarrollar un programa que simule un juego de adivinanza, utilizando todo lo aprendido durante el módulo. 

## Instrucciones de la práctica
Al comenzar el juego y durante el desarrollo del mismo las opciones que se muestran
hasta elegir la opción salir son:
  1. Partida modo solitario
  2. Partida 2 Jugadores
  3. Estadística
  4. Salir

El modo solitario supone que el número a adivinar es generado aleatoriamente por el
ordenador.

El modo 2 jugadores: primero se escribe un número a adivinar y luego un segundo jugador
intenta adivinarlo.

El número a adivinar debe ser entre 1 y 1000.

Tanto la opción 1 como la opción 2 tendrán el siguiente submenú para elegir la
dificultad
  1. Fácil (20 intentos)
  2. Medio (12 intentos)
  3. Difícil (5 intentos)

En ambos menús debe chequearse que la opción elegida es válida y avisar en caso contrario.

Si se adivina el número se gana la partida y se vuelve al menú principal, sino se indica si el número buscado es mayor o menor.

Si se supera el número de intentos se pierde y se vuelve al menú principal.

Se gane o se pierda se pide el nombre del jugador y se guarda esta información junto con el resultado de la partida en un fichero Excel.

La opción estadística nos mostrara los datos almacenados en Excel.

## Herramientas utilizadas
- Jupyter Notebook, a través de [Anaconda](https://www.anaconda.com/anaconda-navigator)

## Aprendizajes
### Módulo Getpass
En la práctica también se valoraba implementar mejoras al juego como ocultar el número a adivinar en el modo 2 jugadores, de modo que el segundo jugador no viera el número tecleado por el primer jugador. Para ello, tuve que investigar y encontré que podía utilizar el módulo getpass y, así, ocultar el número. Lo pude utilizar tecleando la siguiente línea de código en la función "partida_2_jugadores":
```python
numero_a_adivinar = getpass.getpass(prompt="Número a adivinar: ")
```
### Estadísticas
Para la función que guarda los resultados del juego en un archivo Excel, aprendí que tenía que considerar la posibilidad de que algún nuevo usuario no tuviera el archivo para iniciar. Por eso tuve que crear una condicional que verificara, primeramente, que hubiera un archivo ya creado; en caso de que no lo hubiera, la función crearía un nuevo archivo como se muestra:
```python
def guardar_resultados(fecha, nombre_jugador, resultado, dificultad, modo_juego):
    if not os.path.exists("Estadísticas_Adivina_el_Numero.xlsx"):
        wb = openpyxl.Workbook()
        wb.active.append(["Fecha y hora", "Jugador", "Resultado", "Dificultad", "Modo de juego"])
        wb.save("Estadísticas_Adivina_el_Numero.xlsx")
```
A partir de ahí, los datos de cada nueva partida se guardarían y se podrían visualizar utilizando la función "estadística".
### Fecha y hora
Para mejorar la opción "Estadística" del juego, decidí que sería apropiado utilizar la fecha y hora como índice. Para esto, importé el módulo datetime y al inicio de las funciones "partida_solitario" y "partida_2_jugadores" cree una variable titulada "fecha", que guardaba los datos haciendo uso de la función `datetime.now()` y se introduciría luego en la función "guardar_resultados" para añadirse en el archivo de Excel.

## Conclusiones
Fue una práctica entretenida que, a pesar de hacerme reforzar todos los fundamentos de Python aprendidos en el módulo de Programación Básica, también me invitó a investigar y aprender por mi propia cuenta para optimizar y entregar un mejor resultado. 

¡Invito a leer mi código y agregar o comentar mejoras!
