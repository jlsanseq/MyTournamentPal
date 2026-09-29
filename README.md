# MyTournamentPal

## Validación de juego de rol en clase

![Fotografia_juego_rol](media/tarjeta_cliente_desarrollador.jpeg)

## ¿Cuál es el problema?

Soy un jugador de Warhammer 40k y un problema que muchos jugadores viven en cada partida, independientemente de cuanto tiempo lleven en este juego, es que muchas veces no saben cuando merece la pena enfrentar una unidad con otra durante el transcurso de la partida por no saber que resultados esperar de dicho enfrentamiento. 

Este juego funciona mediante ejércitos compuestos por unidades de miniaturas. Cada unidad de un ejército en el juego tiene unas características, unos perfiles de armas y coste en puntos. Estas estadísticas pueden verse modificadas por reglas extra, propias de cada unidad o del propio ejército que tiene un jugador. Debido a estos factores y de la propia aleatoriedad del juego al funcionar con dados, es complicado saber que resultado esperar de cada enfrentamiento.

Actualmente para realizar estas comparativas y estimar como puede suceder un combate, un aficionado tiene que buscar las fichas de cada unidad y compararlas el mismo manualmente. Esto dificulta comparar de forma rápida diferentes enfrentamientos y valorar que resultado esperar de ellos, por lo que no se puede hacer de forma inmediata, lo que es determinante enmedio de una partida. 

## ¿Que datos hay disponibles?

Los datos necesarios para realizar estas simulaciones se pueden encontrar de forma disponible para su descarga en diversas fuentes estructuradas y abiertas para su uso:

- Wahapedia.ru ofrece de forma abierta y para su uso por la comunidad de jugadores en formato .CSV toda la información pertinente de las unidades como sus perfiles, armamento y reglas y todas las reglas especiales de cada ejército a través del siguiente enlace: https://wahapedia.ru/wh40k11ed/Export%20Data%20Specs.xlsx?v=20260817b que se puede encontrar en la sección de 'Data export' dentro del propio Wahapedia.ru. Sobre los ficheros CSV y los datos de ínteres que contienen. Estas tablas están conectadas entre si por los identificadores de 'datasheet_id':  
    - `Factions.csv`: contiene los IDs de ejercitos del juego.     
    - `Datasheets.csv`: contiene todas las fichas de unidad.  
    - `Datasheets_models.csv`: contiene los datos referentes a las características de una unidad.
    - `Datasheet_keyword.csv`: contiene las claves que modifican una unidad y los efectos de sus perfiles de armas.
    - `Datasheet_wargear.csv`: contiene los perfiles de armas.
    - `Datasheet_model_cost.csv`: contiene los costes en pts de cada unidad. 

- El proyecto BSData proporciona también estos datos estructurados mediante archivos en formato .json en su repositorio de GitHub con licencia de uso MIT. 

El producto puede utilizar alguna de estas fuentes como origen de los datos que posteriormente serán almacenados y procesados por el sistema para realizar las simulaciones.

## Lógica de Negocio

El producto tendrá que calcular y simular el resultado de un enfrentamiento entre un perfil atacante y otro defensor, que hará de objetivo para el atacante, teniendo en cuenta las características de cada unidad y el perfil de armas seleccionado. 

Para esclarecer mejor que comportamiento debería seguir el producto, los combates en Warhammer 40k se resuelven mediante las siguientes fases: 
- Se selecciona una unidad atacante y un perfil de armas y como objetivo una unidad del rival. 
- **Impactar**: se tiran tantos dados como indique el valor de Ataques (A) del perfil de armas teniendo en cuenta la Habilidad para Impactar (BS). Por ejemplo, si indica 4+, solo serán validos los resultados mayores o iguales a 4. Los dados que cumplan esto, se consideran impactos y válidos para tirarse en la fase de herir.
- **Herir**: se compara la Fuerza (S) del perfil de armas con la Resistencia (T) de la unidad objetivo. Si ambas son iguales, se necesita un 4+; si la Fuerza es mayor, un 3+ o 2+ si es dos veces mayor; de forma inversa, si la Fuerza es menor, será necesario 5+ o 6+. 
- **Salvacion**: los dados que hayan logrado herir, podrán ser detenidos por la unidad objetivo usando la Salvación (Sv). Este valor puede modificarse por la característica de Penetración (AP) del perfil de armas de la unidad atacante. Por ejemplo, si una unidad tiene Salvación +4 y el perfil de armas del atacante AP -1, podrá eliminar los dados para herir con un 5+. 
- **Daño**: aquellos dados para herir que no hayan sido eliminados durante la Salvación, pasan a hacer daño. Este valor se resta a las Heridas (W) de la unidad objetivo, pudiendo provocar la eliminación de una o más miniaturas e incluso de la unidad al completo. 

Todos estos cálculos se pueden ver afectados por las diferentes habilidades y reglas especiales de las unidades, tales como repetir tiradas para herir, modificar alguno de los resultados u obtener otros efectos adicionales. 

## Referencias 

- [Documentacion complementaria](documentacion_extra.md): documentación complementaria en la que se muestra la configuración previa de git. 