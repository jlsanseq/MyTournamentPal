# MyTournamentPal

## Validación de juego de rol en clase

![Fotografia_juego_rol](media/tarjeta_cliente_desarrollador.jpeg)

## ¿Cuál es el problema?

Soy un jugador de Warhammer 40k y un problema que muchos jugadores viven en cada partida, independientemente de cuanto tiempo lleven en este juego, es que muchas veces no saben cuando merece la pena enfrentar una unidad con otra durante el transcurso de la partida por no saber que resultados esperar de dicho enfrentamiento. 

Este juego funciona mediante ejércitos compuestos por unidades de miniaturas. Todas las unidades de un ejército en el juego tienen unas características para las miniaturas que pertenecen a ellas. Para cada unidad, sus miniaturas tienen disponibles unos perfiles de armas que utilizarán para atacar a otras unidades. 

Las características de la unidad que intervienen en el combate son las siguientes:
- Resistencia (T).
- Salvación (Sv).
- Heridas (W).

Por parte de los perfiles de armas:
- Ataques (A).
- Habilidad para Impactar (BS).
- Fuerza (S).
- Penetración (AP). 
- Daño (D).

Teniendo en cuenta estos datos, un combate se resuelve de la siguiente manera:
- Se selecciona una unidad propia atacante y otra del rival como objetivo. De esta unidad atacante se elegiran que perfiles de armas atacarán al rival. De la unidad objetivo, se tendrán en cuanta sus características propias.  
- **Impactar**: se tiran tantos dados como indique el valor de Ataques (A) del perfil de armas teniendo en cuenta la Habilidad para Impactar (BS). Por ejemplo, si indica 4+, solo serán validos los resultados mayores o iguales a 4. Los dados que cumplan esto, se consideran impactos y válidos para tirarse en la fase de herir.
- **Herir**: se compara la Fuerza (S) del perfil de armas con la Resistencia (T) de la unidad objetivo. Si ambas son iguales, se necesita un 4+; si la Fuerza es mayor, un 3+ o 2+ si es dos veces mayor o más; de forma inversa, si la Fuerza (S) es menor, será necesario 5+ o 6+ en caso de ser dos veces menor o menos. 
- **Salvacion**: los dados que hayan logrado herir, podrán ser detenidos por la unidad objetivo usando la Salvación (Sv). Este valor se verá modificado por la característica de Penetración (AP) del perfil de armas de la unidad atacante. Por ejemplo, si una unidad tiene Salvación 4+ y el perfil de armas del atacante AP -1, tendrá que obtener un 5+ en vez del 4+ de base. 
- **Daño**: aquellos dados para herir que no hayan sido eliminados durante la Salvación, pasan a hacer daño. Este valor se resta a las Heridas (W) de la unidad objetivo, pudiendo provocar la eliminación de una o más miniaturas e incluso de la unidad al completo si no quedan más miniaturas restantes. 

Esto se hace para todos los perfiles de armas que intervienen en el combate. 

Estas habilidades de base pueden verse modificadas por reglas especiales contenidas en las llamadas "claves", que se encuentran o en los perfiles de armas o en las propias unidades. Tienen varios efectos y pueden cambiar el desenlace de un enfrentamiento. Debido a estos factores y a la propia aleatoriedad del juego al funcionar con dados, es complicado saber que resultado esperar de cada enfrentamiento.  

Actualmente para realizar esta secuencia y estimar como puede suceder un combate, un aficionado tiene que buscar la información de cada unidad y simular los combates él mismo manualmente, lo que impide saber realmente las posibilidades que esperar de un enfrentamiento y valorar si va a ser favorable para el. Esto dificulta probar de forma rápida diferentes enfrentamientos entre unidades que se pueden suceder en el transcurso de una partida, lo que es determinante en el juego. 

## ¿Qué datos hay disponibles?

Para poder resolver un enfrentamiento son necesarios los datos tanto de la unidad que ataca como la objetivo que se defiende, además del número de miniaturas que se incluyen en cada una de las dos unidades.

De la unidad atacante necesitaremos conocer sus perfiles de armas, que cómo recordemos contienen:
- **Perfiles de armas:** Ataques (A), Habilidad para Impactar (BS), Fuerza (S), Penetración (AP) y Daño (D).

Por parte de la unidad objetivo que se defiende, necesitaremos sus características propias: 
- **Características de las unidades:** Resistencia (T), Salvación (Sv) y Heridas (W).

Además, será necesario disponer de las reglas y habilidades especiales, las claves, que están asociadas a cada Perfil de armas y a las características propias de cada unidad. 

Estos datos se encuentran de forma estructurada en los ficheros .csv de Wahapedia.ru, que ofrece de forma estructurada y de forma libre para su uso en el siguiente enlace: https://wahapedia.ru/wh40k11ed/Export%20Data%20Specs.xlsx?v=20260817b. 

El producto utilizará esta fuente como origen de los datos. La extracción y almacenaemiento de la información contenida en los datos se realizará mediante el uso de código propio para el proyecto. 

## Lógica de negocio

Debido a las diferentes características de las unidades, los perfiles de armas y las reglas especiales que intervienen, un mismo enfrentamiento puede producir multiples resultados. 

La lógica de negocio tendrá que analizar estos posibles resultados para evaluar hacia cúal de las dos partes resulta más favorable el combate y así poder dar una respuesta al problema planteado.

## Referencias 

- [Documentacion complementaria](documentacion_extra.md): documentación complementaria en la que se muestra la configuración previa de git. 