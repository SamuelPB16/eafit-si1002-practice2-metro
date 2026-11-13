# eafit-si1002-practice2-metro
Integrantes: Samuel David Plata Burgos


¿Por qué una clase abstracta con funciones virtuales puras es preferible a un enum más un switch?
utilizando el polimorfismo dinámico en c++ se guardan objetos de clases hijas dentro de punteros de la clase padre.
La clase Network tiene un vector de punteros inteligentes: std::vector<std::unique_ptr<TransportMode>> modes_.
Cuando el programa termina o cuando network sale de su ambito en el main, cada std:unique_ptr ejecuta automáticamente delete
sobre el puntero interno que guarda, el cual es del tipo TransportMode*.
En el caso que ~TransportMode() no sea virtual, el compilador usa enlace estático.

¿Por qué una clase abstracta con funciones virtuales puras es preferible a un enum más un switch?
El enunciado menciona que este problema es un diagnostico de diseño orientado a objetos. La calidad del código no se mide solo
por si arroja los numeros correctos, si no por cuantos archivos o funciones hay que modificar cuando cambia una regla.
Si se hubiese creado un enum ModeType { METRO, TRAM, CABLE, TOURIST_CABLE, FEEDER };. para calcular las tarifas, se 
tendría un switch (mode.type) en computerFare(). Para saber si abre ventana de integración, se tendría otro switch para 
cada método involucrado. esto causaría que si se quiere añadir un nuevo proyecto del metro, se tendría que abrir el proyecto y buscar cada switch disperso 
y modificarlo uno por uno, volviéndose mas propenso a error humano. 
