# MyTournamentPal

## Validación de juego de rol en clase

![Fotografia_juego_rol](media/tarjeta_cliente_desarrollador.jpeg)

## ¿Cuál es el problema?

Soy un jugador del wargame de mesa Warhammer 40k que participa en una liga con su grupo de amigos. En esta liga los jugadores se enfrentan entre ellos en diversas partidas a lo largo de una serie de meses. Cada mes se realizan nuevos emparejamientos, cada jugador debe jugar 2 partidas con dos personas distintas con las que haya sido emparejado. 

Al hacer esta liga, la organización es bastante rudimentaria y desorganizada. Los pairings y enfrentamientos se realizan de forma totalmente aleatoria y sin tener en cuenta el nivel de los jugadores, lo que lleva a que dos personas con un nivel muy distinto entre si jueguen o los jugadores repitan varias veces partida con el mismo rival, haciendo que algunas personas dejen de participar o directamente se nieguen por miedo a no poder disfrutar de la liga.

El problema por tanto, sería que actualmente no existe ninguna herramienta o plataforma para poder realizar estos emparejamientos de forma justa y teniendo en cuenta el nivel y puntuación de los usuarios en el contexto de la liga.

## ¿Que datos hay disponibles?

Los datos necesarios para realizar estos emparejamientos son las puntuaciones que se obtienen tras cada partida de cada una de las rondas de la liga. Se encuentran de forma desorganizada en un grupo de WhatsApp o guardados por los propios participantes. Al acabar una partida, uno de los dos jugadores envía sus respectivas puntuaciones. Estos datos pueden ser perfectamente extraidos y dispuestos para su uso en la resolución del problema. 

## Lógica de Negocio

El producto resultante deberá calcular y generar los nuevos enfrentamientos en base a las partidas de la ronda anterior. Los jugadores deberán ser clasificados y sus resultados previos analizados para que se pueda resolver el problema correctamente y teniendo en cuenta las restricciones que originan el problema en primer lugar. Es decir, la falta de criterio a la hora de generar los emparejamientos y el relegar la tarea a una simple asignación aleatoria. 


## Referencias 

- [Documentacion complementaria](documentacion_extra.md): documentación complementaria en la que se muestra la configuración previa de git. 