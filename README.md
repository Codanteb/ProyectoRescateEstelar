# ProyectoRescateEstelar
Trabajo práctico AyP 1. Nave espacial autónoma que esquiva obstáculos y recoge ítem aleatorios dispersos en el escenario. También recoge combustible y entrega el reporte del contenido de su bodega.

Documentación del Diseño – Proyecto “Nave de Rescate” 

1- Decisiones de diseño tomadas 
El diseño del sistema se organizó en torno a una nave autónoma que recorre distintos 
mundos, evita obstáculos y recoge recursos. Las decisiones principales fueron: 
Modelo orientado a actores (Greenfoot): Cada entidad del escenario (nave, 
contenedores, balizas, asteroides) se implementa como una clase independiente que 
extiende Actor o clases base del proyecto. 
Responsabilidad única por clase: 
NaveDeRescate gestiona movimiento, búsqueda, recolección y reporte final. 
ContenedorRecurso encapsula créditos y código de manifiesto. 
BalizaDeRescate entrega combustible y se elimina del mundo. 
ItemDeCombustible provee combustible fijo. 
Los mundos (Mundo00, Mundo01, Mundo02) definen el mapa, ítems y obstáculos. 
Uso de composición: La nave contiene una bodega interna (ContenedorRecurso[]) y 
consulta al mundo para obtener información de visitas y obstáculos, evitando 
acoplamiento fuerte. 
Cada clase contiene los contratos de los métodos que contiene, con las pre y post 
condiciones correspondiente. 
Movimiento basado en heurística simple: La nave elige rumbo evaluando: 
• distancia Manhattan al contenedor más cercano, 
• cantidad de visitas previas al sector, 
• posibilidad de avanzar según obstáculos. 
Control de estado y finalización: La simulación se detiene cuando: 
• se queda sin combustible, 
• queda inmovilizada, 
• acumula 4 movimientos bloqueados, 
• no puede actuar. 

2. Modificaciones y criterios aplicados 
A partir del código final se observan las siguientes decisiones de ajuste: 
Normalización de valores constantes: Combustible máximo, consumo, capacidad de 
bodega y radio de búsqueda se definen como static final, facilitando cambios globales. 
Separación de lógica de recolección:  
recogerObjetosDelSector() distingue entre contenedores y balizas, aplicando acciones 
diferentes. 
Registro de visitas: La nave delega en MundoBase la matriz de visitas, manteniendo la 
lógica de exploración fuera de la clase principal. 
Heurística de movimiento refinada: Se prioriza avanzar hacia el contenedor más 
cercano, pero también se penalizan sectores ya visitados para evitar loops. 
Reporte final estructurado: Se imprime: 
• balance económico, 
• espacios vacíos, 
• recurso más valioso, 
• presencia de recurso OMEGA, 
• matriz completa de sectores visitados.

3. Detalle de los mapas creados 
Mundo00 – Mapa chico 
Dimensiones: 9×7. 
Obstáculos simples y pocos recursos. 
La nave inicia en (1,1). 
Objetivo: mostrar un escenario introductorio donde la nave rescata rápido y enfrenta 
bloqueos mínimos. 
Mundo01 – Mapa mediano con corredor 
Dimensiones: 12×8. 
Contenedores distribuidos en zonas separadas. 
Asteroides definidos mediante matriz booleana. 
Objetivo: mostrar navegación por corredores y decisiones de ruta más complejas. 
Mundo02 – Mapa grande y denso 
Dimensiones: 20×12. 
Gran cantidad de asteroides formando “islas” y paredes. 
Recursos variados y un único contenedor OMEGA estratégico. 
Objetivo: evaluar la heurística de la nave en un entorno amplio, con múltiples desvíos y 
rutas posibles.

4. Qué busca mostrar cada mapa 
Mundo00: 
Comportamiento básico de la nave, detección de contenedores cercanos y uso de baliza. 
Mundo01: 
Cómo la nave evita corredores bloqueados, prioriza recursos y gestiona múltiples rutas 
posibles. 
Mundo02 
Capacidad de exploración en un entorno complejo, interacción con asteroides densos y 
búsqueda del recurso OMEGA.

5. Conclusión 
El diseño final combina exploración autónoma, recolección de recursos y registro de 
visitas para generar un comportamiento coherente dentro de distintos escenarios. Las 
clases están organizadas de forma modular y cada mapa permite observar un aspecto 
distinto de la lógica de navegación y rescate.
