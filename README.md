# ESTUDIO DE EMISIONES DE DIÓXIDO DE CARBONO POR EL TRANSPORTE DE LIBROS A LAS PALMAS DE GRAN CANARIA

## 1. La protección del clima y la huella de carbono de la logística
El transporte en logística se refiere al traslado de mercancías de un punto a otro y es esencial para proveer a compañías e individuos de materias primas y productos. Según el Observatorio del Transporte y la Logística en España (OTLE), a pesar de las limitaciones de movilidad consecuencia de la COVID-19, en España el transporte es el sector con mayor consumo energético, representando un 36,0% de la energía total en 2020 (Figura 1). Este valor se encuentra ocho puntos por encima de la media de los países de la UE-27. El modo de transporte con mayor cuota en el consumo energético total del sector es la carretera (93,8%) (OTLE, 2023). Por lo tanto, en base a estos datos, la gestión y la reducción del consumo de energía derivado del transporte son piezas clave para luchar contra el cambio climático y asegurar la seguridad del abastecimiento.

La huella de carbono se refiere a “la totalidad de gases de efecto invernadero, en adelante GEI, producidos de forma directa o indirecta por un individuo, organización, evento o producto” (MITECO, 2023). El análisis de huella de carbono proporciona un dato que puede ser utilizado como indicador ambiental global de una actividad y se configura como punto de referencia básico para el inicio de actuaciones de reducción del consumo de energía y para la utilización de recursos y materiales con mejor comportamiento medioambiental.

En logística las emisiones de GEI generalmente se crean por el consumo de combustibles o electricidad. y se pueden calcular a partir del consumo utilizando factores de emisión fijados.

El dióxido de carbono (CO2) es el GEI con mayor efecto sobre el calentamiento global. No obstante, existen otros GEI de gran importancia debido a su mayor potencial de calentamiento global (Global Warming Potential, GWP) comparado con el del CO2. Los estándares actuales demandan la determinación de la emisión de todos los GEI porque cantidades similares de algunos gases tienen la capacidad de calentar la atmósfera mucho más que el CO2. Así, este trabajo muestra las cantidades totales en la forma de equivalentes de CO2 (CO2e ).

Existen emisiones de GEI directas e indirectas. Las emisiones de GEI no tienen lugar únicamente durante el uso final del combustible, sino que se debe considerar todo su ciclo de vida. En este sentido el estándar UNE-EN 16258 estipula que el consumo indirecto de energía, así como las emisiones derivadas deben ser tenidas en cuenta. Se diferencian los siguientes conceptos:
- Fuente a depósito (Well-to-tank, WTT). Procesos energéticos. Considera el consumo energético y todas las emisiones indirectas derivadas del combustible de la fuente al depósito del vehículo. Aquí el consumo incluye las pérdidas durante la producción de la energía.
- Depósito a ruedas (Tank-to-wheels, TTW). Procesos de los vehículos. Considera todas las emisiones directas de la operación del vehículo. Aquí el consumo se refiere a la energía final consumida.
- Fuente a ruedas (Well-to-wheels, WTW). Procesos energéticos y de vehículos. Es la suma de los dos anteriores, es decir, emisiones indirectas y directas.
    - WTW=WTT+TTW


## 2. Objeto y alcance del estudio
Este trabajo analiza la huella de carbono derivada del transporte de cinco tipos de libros impresos en distintos centros urbanos españoles y llevados a un punto de despacho en Las Palmas de Gran Canaria. El alcance del estudio considera únicamente las emisiones de GEI derivadas de los viajes de ida, no los de retorno. Tampoco se investiga el ciclo de vida de materiales y recursos empleados en la impresión.


## 3. Datos de partida
### 3.1 Coordenadas
-	Coordenadas de centros urbanos. Se ha obtenido de GitHubGist jhernandez-stratio/spain-ciudades.geojson (https://gist.github.com/jhernandez-stratio/dd6159c04f14a5078681e369dcd8aea6). De aquí se han seleccionado las ciudades de la península con más de 50.000 habitantes y los núcleos urbanos de Canarias más con mayor población.
-	Coordenadas de puertos. Obtenidas a de la página web de MarineTraffic (www.marinetraffic.com).
-	Coordenadas del punto de llegada. Punto de despacho/entrega (almacén): Cabildo de Gran Canaria, Archivo General Insular, Carretera General del Centro, s/n, 35015 (km 3,7). Latitud-Longitud = 28°05'11.5N, 15°26'05.3W [28.086528, -15.434806].

### 3.2 Masa de la carga
|                    Título                    |      ISBN         | Dimensiones, cm | Páginas | Masa ud., g | Masa 500 uds., t |
|:--------------------------------------------:|:-----------------:|:---------------:|:-------:|:-----------:|:----------------:|
| Niebla de sueño                              | 978-84-1353-114-4 | 13x19x1.2       | 162     | 250         | 0.15             |
| La isla de los canarios. Volumen 6           | 978-84-1353-115-1 | 21x23x0.8       | 92      | 400         | 0.225            |
| El mundo del libro en Canarias               | 84-8103-396-0     | 15x21x3.1       | 532     | 780         | 0.415            |
| Historia del Cabildo insular de Gran Canaria | 84-8103-067-8     | 17x24xx3.9      | 748     | 1240        | 0.645            |
| Flora de Gran Canaria 1                      | 978-84-8103-741   | 27x34 x3        | 238     | 2280        | 1.165            |

### 3.3	Distancias
La distancia es otro factor imprescindible para el cálculo de las emisiones de GEI.
- Distancias por carretera. Se ha determinado la distancia más corta entre los puntos a unir utilizando la Distance Matrix API de Google Maps Platform (https://developers.google.com/maps).
- Distancias por mar. Distancias entre diferentes puertos de salida españoles y el puerto de Las Palmas de Gran Canaria.
    - Puertos de salida en España peninsular. Se ha utilizado el cuadro de distancias interportuarias de Puertos del Estado (https://www.puertos.es/Documents/Cuadro distancias.pdf).
    - Puertos de salida canarios. Las distancias se han obtenido de la Armada española (https://armada.defensa.gob.es/ihm/Aplicaciones/Distancia/Index_Distancia_xml.htm).


## 4. Pasos para el cálculo de la huella
La estandarización es una herramienta importante para el cálculo de emisiones de GEI porque permite mejorar la precisión, transparencia y consistencia de los resultados. Esto también permite comparar los resultados producto de diferentes estudios, o al menos comprender mejor si éstos difieren. Las emisiones de GEI por el transporte de libros se ha calculado en base a dos metodologías ampliamente utilizadas:
- Para el transporte por carretera se ha seguido el estándar UNE-EN 16258 “Metodología para el cálculo y la declaración del consumo de energía y de las emisiones de gases de efecto invernadero en los servicios de transporte (transporte de mercancías y de pasajeros)” (AENOR, 2013). Aquí, es importante destacar que este estudio se ha apoyado en el estándar, pero que no se ajusta a él por completo ya que:
    - Se han calculado únicamente las emisiones del viaje de ida, y no de ida y vuelta.
    - Este informe no presenta datos de consumos energéticos.
    - Este informe no presenta datos de GEI desagregados por tipo de gas.
- Para el transporte por mar se ha seguido la metodología de Clean Cargo Working Group (CCWG, 2015).

Este estudio se estructura en base a las etapas establecidas en la norma EN 16258. Por otro lado, los cálculos se han desarrollado en lenguaje Python y son accesibles a través del repositorio GitHub bererei/Huella-carbono-transporte-editorial (https://github.com/bererei/Huella-carbono-transporte-editorial). Paralelamente, los resultados se presentan en mapas interactivos alojados en https://bererei.github.io/Huella-carbono-transporte-editorial/.

Las etapas aquí enumeradas se desarrollan en el código:
1. Etapa 1: identificación de los diferentes trayectos de los servicios de transporte.
2. Etapa 2: cálculo del consumo de energía y de emisiones de GEI de cada trayecto y servicio de transporte
3. Etapa 3: suma de los resultados de cada trayecto


## 5. Referencias
- AENOR. (2013). UNE-EN 16258 Metodología para el cálculo y la declaración del consumo de energía y de las emisiones de gases de efecto invernader en los servicios de transporte (transporte de mercancías y de pasajeros). https://www.une.org/encuentra-tu-norma/busca-tu-norma/norma?c=N0051329
- CCWG. (2015). Clean Cargo Working Group Emissions Accounting Methodology (Número June). www.bsr.org
- Clean Cargo. (2021). 2020 Global Container Shipping Trade Lane Emissions Factors (Número October). https://www.bsr.org/files/clean-cargo/BSR-Clean-Cargo-Emissions-Report-2021.pdf
- EcoTransIT World. (2023). Environmental Methodology and Data Update 2023. EcoTransIT World Initiative (EWI), 141. https://www.ecotransit.org/en/
- MITECO. (2023). Guía para el cálculo de la huella de carbono y para la elaboración de un plan de mejora de una organización. https://www.miteco.gob.es/es/cambio-climatico/temas/mitigacion-politicas-y-medidas/
- OTLE. (2023). Informe Anual del Observatorio del Transporte y la Logísitica en España (2022). Ministerio de Transportes, Movilidad y Agenda Urbana. https://observatoriotransporte.mitma.es/inform/es/2022/indice
- Schmied, M. y Knörr, W. (2012). Calculating GHG emissions for freight forwarding and logistics services in accordance with EN 16258 – Terms , Methods , Examples. https://www.clecat.org/media/CLECAT_Guide_on_Calculating_GHG_emissions_for_freight_forwarding_and_logistics_services.pdf (Accessed 22.10.2019)



