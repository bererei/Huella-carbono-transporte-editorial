# Etapas del cálculo de consumo de energía y de emisiones de GEI de un servicio de transporte
Disclaimer: Este trabajo está apoyado en metodologías publicadas y ampliamente utilizadas en el sector. Toma parte de su metodología de la norma AENOR EN 16258, pero no se acoge totalmente a ella.


## Etapa 1: identificación de los diferentes trayectos de este servicio de transporte
Las coordenadas y las distancias han sido obtenidas de:
- spain-cities: 
    - https://gist.github.com/jhernandez-stratio/dd6159c04f14a5078681e369dcd8aea6

- Cuadros Distancias Puertos (distancias interportuarias):
    - CuadroDistancias_PuertosPeninsula (Península) (https://www.puertos.es/Documents/Cuadro%20distancias.pdf)
    - CuadroDistancias_PuertosCanarias (Islas Canarias) (https://armada.defensa.gob.es/ihm/Aplicaciones/Distancia/Index_Distancia_xml.htm)
- CoordenadasPuertos (www.marinetraffic.com)

Ruta A - Península y Canarias:
- Trayecto 1. De punto de salida (S) a puerto de carga (C).
- Trayecto 2. De puerto de carga a puerto de descarga (D).
- Trayecto 3. De puerto de descarga a punto de llegada (L)

Ruta B - Gran Canaria:
- Trayecto 1. De Punto de salida a punto de llegada.


## Etapa 2: cálculo de las emisiones de CO2 equivalentes de cada trayecto

### Subetapa 2.1: establecimiento del sistema de operación de los vehículos para cada trayecto
 Como un requisito mínimo el VOS se refiere al conjunto coherente de operaciones de vehículo relativas al trayecto que se está calculando.
 
 Cuando se establezca el VOS, se deben tener en consideración los factores que afectan a la escala y composición del VOS, tales como:
 - Número y tipo de vehículos a incluir
 - Periodo de tiempo de actividad de estos vehículos

 En todos los casos el VOS debe incluir los viajes en vacío relativos a las operaciones del vehículo.


### Subetapa 2.2: cálculo de las emisiones totales para cada trayecto
WTW = WTT + TTW

Se van a seguir diferentes metodologías según el trayecto y tipo de transporte.
1. **De punto de salida a puerto de carga**
    0. EcoTransIT World
    1. Cuantificación del consumo total de combustible para el VOS
        - Se hará utilizando las categorías de valores indicadas en el apartado 5.4 (AENOR2013).
    2. Cálculo del consumo total d energía y de emisiones de GEI para este VOS
        (AENOR2013)
        - ![Alt text](/img/image-19.png)
        - ![Alt text](/img/image-20.png)

        (Schmied2012)
        - ![Alt text](/img/image-21.png)
        - ![Alt text](/img/image-22.png)

        Conversión del consumo total de combustible para el VOS en cantidades de consumo de E y en emisiones de GEI. Fórmulas:
        - ![Alt text](/img/image.png)
        - ![Alt text](/img/image-1.png)

        VOS - Sistema de Operación de un Vehículo. Conjunto de operaciones de un vehículo.

        Cálculos deben generar los siguientes resultados:

        Well-to-Wheel (WTW) = Well-to-Tank (WTT) + Tank-to-Wheel (TTW)
        - WTW. Fuente a  ruedas. Evaluación relativa al vehículo (funcionamiento del motor o motores que tiene) y a los procesos energéticos. Consumo de energía y emisiones de fuente a ruedas (Ew, Gw).
        - WTT. Fuente a depósito. Evaluación relativa a los procesos energéticos.
        - TTW. Depósito a ruedas. Consumo de energía y emisiones de depósito a ruedas (Et, Gt).
    3. Asignación de este trayecto a una porción del consumo total de energía y de emisiones 
        - ![Alt text](/img/image-2.png)
        - ![Alt text](/img/image-3.png)

2. **De puerto de carga a puerto de descarga**
    0. Clean Cargo Working Group
    1. Cálculo de las emisiones de CO2 equivalentes para el VOS
    2. Asignación de este trayecto a una porción de las emisiones

3. **De puerto de descarga a punto de llegada**
    0. EcoTransIT World. Igual que 'De punto de salida a puerto de carga'.

#### DATOS GENERALES
(Schmied2012). EN 16258 Distance-based approach.
- ![Alt text](/img/image-4.png)


#### SUPOSICIONES QUE TOMÉ DE ECOTRANSIT WORLD
Truck/Lorry (defaults)
-	Vehicle type: 12-20 t (config) Creo que lo he configurado al ponerlo en RoRo.
    - Lorry type (load capacity) (c. methodology report ch. 6.1.1)
	- Default: 26-40t
-	Fuel type: diesel (default)
	- Sets the fuel type for trucks. Diesel is the default fuel type. Alternative fuel types include CNG (compressed natural gas), LNG (liquefied natural gas), LNG-diesel (a dual-fuel engine with an average ratio of 40% diesel and 60% LNG in energy consumption) and BEV (battery electric vehicle). Note: Alternative fuel types require dedicated refuelling facilities. The availability is restricted and may differ by region.
-	Emission standard: EURO 5 (default)
	- Sets the emission standard for the selected lorry type. Standard values vary per region (EURO for Europe and other countries, EPA for the US and Canada and JP for Japan). (c. methodology report ch. 6.1.3)
-	Load factor: 60% (default)
	- The load factor determines how much of the load capacity of the selected transport vehicle is utilised. The load factor is 100% if the maximum load weight capacity of the vehicle or the load carrier (e.g. container) is used. (c. methodology report ch.)
-	ETF: 20% (default)
	- Additional distance that the vehicle or load carrier has to travel empty related to the transport distance. The share of empty trips varies depending on the selected transport mode and cargo type. (c. methodology report ch. 4.2.3).
-	Cooling Unit: No


#### SUPOSICIONES Y DATOS DEL TRANSPORTE POR CARRETERA
- Medio de transporte (tipo de camión). EcoTransITWorld2023, pg. 60 indica que en EU 28 (without SE) el transporte por defecto es Truck > 26-40t. Yo voy a tomar un camión de 12-20 tonnes.
- Combustible. Diesel. No biofuel.
- Capacidad de carga de los camiones y factores de corrección carreteras urbanas:
    - ![Alt text](/img/image-5.png)
- Specific energy consumption. Consumo energético específico.
    - (Schmied2012)
        - ![Alt text](/img/image-6.png)


#### SUPOSICIONES Y DATOS DEL TRANSPORTE POR MAR
V**Metodología de Clean Cargo**
- (CCWG2015)
- (CleanCargo2021)
    - ![Alt text](/img/image-24.png)
    - ![Alt text](/img/image-23.png) 



## Etapa 3: suma de los resultados de cada trayecto