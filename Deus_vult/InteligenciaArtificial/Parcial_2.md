Inteligencia Artificial

# Consigna segundo parcial

Segundo parcial Inteligencia Artificial

Fecha 14/11/2024

El parcial constara de una demostración en Image y defensa del código in situ.

Las implementaciones deben hacerse con las técnicas utilizadas en clase, no utilizando librerías de terceros.

Se tendrá en cuenta la calidad del código entregado, incluyendo el buen uso de tipos genéricos, interfaces y namespaces.

Se corregirá el código que este pusheado al repositorio, hasta las 17:00 Hs del día de la fecha del parcial.

Deben tener una build subida como release en su repositorio para la corrección.

Todo el código fuente del parcial deberá estar alojado en un repositorio GIT público, de lo contrario no se corregirá el parcial y la calificación será 0 (cero).

La entrega será el repositorio en sí, pero además debe haber varios archivos que contengan el genoma de los agentes en distintos puntos del entrenamiento para poder ver rápidamente el avance del mismo. Mínimo 5.

  

Condición mínima de aprobación (0 - 4)

- [ ] Existen tres tipos de agentes; herbívoros, carnívoros y carroñeros. Los cuales aprenden a desempeñarse en la simulación mediante el uso de algoritmos genéticos.

(Aclaración: 1 turno = 1 ciclo de update)

La simulación cuenta con:

- [ ] Existe una grilla cuadrada de ancho y alto configurable.
- [ ] Los agentes herbívoros comienzan cada generación en casillas aleatorias del cuarto inferior de la grilla.
- [ ] Los agentes carnívoros comienzan cada generación en casillas aleatorias del cuarto superior de la grilla.
- [ ] Los agentes carroñeros comienzan en posiciones aleatorias del mapa, los mismos no están limitados a las posiciones de la grilla ni se mueven siguiendo la misma.
- [ ] En la grilla aparecen al comienzo de la simulación una cantidad de plantas igual al doble de la cantidad de agentes herbívoros con los que comenzó la primera generación.
- [ ] Cada generación dura una cantidad de turnos configurable.

El comportamiento de los agentes herbívoros es el siguiente:

- [ ] Pueden moverse a razón de un máximo de tres casillas por turno.
- [ ] Deben ir a una casilla donde haya una planta.
- [ ] Deben permanecer cinco turnos en una casilla con planta (no necesariamente seguidos) para poder alimentarse.
- [ ] Si una planta estuvo con un agente herbívoro comiendola por cinco turnos desaparece.
- [ ] Deben evitar ser comidos por los agentes carnívoros.
- [ ] Un agente que haya logrado sobrevivir toda la generación podrá reproducirse.
- [ ] Un agente que haya logrado comer al menos una vez a lo largo de la generación podrá reproducirse.

El comportamiento de los agentes carnívoros es el siguiente:

- [ ] Se pueden mover a razón de dos casillas por turno.
- [ ] Deben ir a la casilla donde haya un agente herbívoro.
- [ ] Si el agente carnívoro comienza un turno en la misma casilla que un agente herbívoro, el agente herbívoro sufre daño. Si un agente herbívoro sufre daño dos veces a lo largo de la generación éste muere y el agente carnívoro pasa un turno en esa casilla comiendo. En la casilla donde murió el agente herbívoro queda un cadáver.
- [ ] Un agente que haya logrado comer al menos una vez a lo largo de la generación podrá reproducirse.

El comportamiento de los agentes carroñeros es el siguiente:

- [ ] Se mueven libremente por el mapa a razón de una velocidad fija por turno, pero no pueden detenerse.
- [ ] Deben decidir si moverse recto o doblar hacia la izquierda o a la derecha.
- [ ] Deben estar a menos de una distancia del ancho de cuatro casillas durante veinte turnos de un cadáver de un agente herbívoro. El cadáver de un agente herbívoro desaparece después de que un agente carroñero haya comenzado un turno treinta veces a menos de cuatro casillas de distancia de él.
- [ ] Un agente que haya logrado comer al menos una vez a lo largo de la generación podrá reproducirse.

- [ ] La ejecución de las redes neuronales funcionan en ECS.

- [ ] Los comportamientos de los agentes deben estar codificados en una FSM, y las condiciones de transición deben darse por outputs de redes neuronales.

- [ ] Todo aquello que pueda ser paralelizable, debe ser paralelizado.

- [ ] Los agentes carroñeros deben aprender a no superponerse utilizando flocking, el output de una red neuronal deberá ser el multiplicador de los parámetros de alignment, cohesion, separation y direction.

- [ ] Toda la lógica de la simulación debe realizarse sin dependencias al engine en una dll aparte. El engine solo actúa como renderizador, lectura de inputs, marcador de deltatime y demás funciones que solo puede desempeñar el mismo.

- [ ] Si alguna especie se extingue, se tomará un save de genomas anteriores y se creará una nueva generación cruzando esos genomas, pero con una probabilidad y ratio de mutación mayores.

  

Condición mínima para promoción (4 - 7)

- [ ] Al inicio de la generación, se crea un diagrama de voronoi con las plantas en escena, desde la cual se le da la información a los agentes herbívoros de que planta tienen más cerca. Cuando una planta desaparece el diagrama se recalcula.

- [ ] Todos los agentes y entidades en escena se renderizan utilizando llamadas directas a GPU, no por componentes de renderer.

- [ ] Ante la detección de un estancamiento del fitness promedio de una especie de agentes a lo largo de las generaciones, la red neuronal puede crecer tanto en capas como en neuronas por capa.

  

Examen completo (7 - 10)

- [ ] Tras cada turno, el diagrama de voronoi tiene en cuenta cuántos agentes carnívoros hay en cada área para recalcular los límites.

- [ ] Todos los comportamientos de los agentes funcionan con ECS, pero manteniendo la separación de estados de la FSM.

- [ ] Los agentes deberán aprender a dejar comida si ya comió lo que necesita para sobrevivir/reproducirse, dejándola para los demás miembros de su especie.

  

  

Cosas a tener en cuenta:

El examen es largo, y los tiempos que van a necesitar para entrenar las redes neuronales van a ser más. Les recomiendo hacer la serialización de genomas lo antes posible para poder entrenar a sus agentes todo el tiempo que puedan, si incluso implementan una especie de "auto-save" cada un cierto número de generaciones mejor para estar cubiertos ante cualquier imprevisto mas que mejor, pero no es obligatorio.

Pueden usar la información que quieran para pasar como input a la red neuronal, elijan sabiamente. 

Pueden hacer que un agente haga todo su comportamiento con solo una red neuronal o con múltiples, elijan sabiamente.

Pueden decidir el tipo de estructura de red neuronal y el método de cruce de genomas que consideren más conveniente para cada red neuronal, elijan sabiamente.

No se extrañen si toma MUCHAS generaciones en ver progresos significativos, es un comportamiento relativamente complejo el buscado.

Si entrenan a sus agentes con una versión compilada del proyecto el entrenamiento será más rápido al no estar vinculado a cuestiones de Debug/Editor.