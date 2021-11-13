# QueVotaron (datos recopilados)
Repositorio de datos obtenidos con la herramienta QueVotaron

QueVotaron es un proyecto destinado a visibilizar las votaciones realizadas en la Cámara de Diputados del Congreso chileno por medio de visualizaciones autogeneradas.

Todas las visualizaciones son también publicadas en nuestro Twitter:
<p align="center">
    <a href="https://twitter.com/quevotaron"><img src="https://imgur.com/hIXMqsE.png"> <b>@quevotaron</b></a>
</p>

## Estructura de archivos

### Descripción de las carpetas:

- **html:** Contiene los archivos con la información sin procesar de las votaciones, todo en formato HTML.

- **json:** Contiene los archivos con la información ya procesada de las votaciones, siguiente el formato JSON definido más abajo.
  
- **visualizaciones:** Contiene las visualizaciones generadas en formato PNG, para cada votación se generan dos archivos: `[ID_VOTACIÓN]_coaliciones.png` y `[ID_VOTACIÓN]_partidos.png`.


### Formato JSON:

🚧  🚨 **TODO:** Sección desactualizada. Los archivos JSON actuales siguien conteniendo las llaves aquí mencionadas, pero falta agregar información que ha sido agregada con posterioridad. 🚧 

Los archivos JSON generados tienen el formato presentado en este ejemplo:

```json
{
    "id": 36403,
    "titulo": "Modifica la Carta Fundamental para restablecer el voto obligatorio en las elecciones populares",
    "subtitulo": "En votación particular el artículo primero propuesto por la Comisión de Gobierno",
    "proyecto": "13212-07",
    "fecha": [2021, 6, 15],
    "sesion": "Sesión n°96, Ordinaria del 04 Nov 2021 a las 09:00hrs.",
    "tramite": "Primer Trámite / Segundo Informe",
    "tipo": "Proyecto Ley",
    "resultado": "Aprobado",
    "quorum": "3/5 del total",
    "nquorum": 93,
    "votos_por_partido": [
        {
            "A favor": {
                "IND": 18, "EVOP": 5, "PS": 17, "DC": 12, "PC": 7, "RN": 16, "PL": 2, "RD": 5, "PPD": 7,
                "PEV": 1, "PR": 4, "PH": 1, "CO": 2, "FRVS": 3, "CS": 4
            },
            "Abstienen": {"UDI": 1, "RN": 6, "PLR": 1},
            "En contra": {"UDI": 21, "EVOP": 1, "RN": 9, "IND": 2}
        },
        {"Ausentes": {"RN": 2, "PC": 1, "UDI": 3}},
        [["RN", "PC"], ["UDI", "RD"]]
    ],
    "votos_por_coalicion": [
        {
            "A favor": {
                "UC": 48, "CV": 23, "SC": 9, "AD": 24
            }, 
            "Abstienen": {"CV": 8},
            "En contra": {"CV": 33}
        },
        {"Ausentes": {"CV": 5, "AD": 1}},
        [["CV", "AD"], ["CV", "AD"]]
    ],
    "votos_por_diputado": [
        {
            "A favor": [
                803, 1010, 968, 925, 1012, 971, 1013, 1014, 1015, 1016, 973, 931, 1020, 975, 1023, 1025, 1027,
                1028, 1029, 837, 981, 982, 1030, 984, 936, 1034, 848, 986, 1038, 987, 1039, 856, 1041, 1042, 1044,
                1046, 1047, 1048, 660, 1049, 991, 1051, 1052, 869, 872, 1054, 74, 993, 994, 1056, 1057, 1058, 879,
                1059, 1061, 885, 1062, 1063, 1064, 1067, 1000, 1069, 1070, 1071, 893, 950, 1001, 1073, 953, 920,
                897, 1076, 898, 1002, 956, 1078, 957, 1081, 1006, 1083, 961, 913, 1084, 963, 1077, 1074, 1068,
                1036, 1088, 1018, 1085, 1008, 1092, 1091, 1093, 855, 866, 1087, 1086, 1037, 972, 827, 862, 1080
            ], 
            "Abstienen": [811, 1019, 1022, 989, 946, 952, 1075, 908],
            "En contra": [
                1009, 923, 926, 815, 976, 1024, 1031, 985, 1032, 843, 850, 940, 1040, 942, 1050, 945, 1055, 875,
                1060, 995, 1065, 999, 1066, 1072, 1079, 1003, 1005, 959, 917, 1090, 1011, 1017, 1094
            ]
        },
        {"Ausentes": [1021, 1043, 1045, 1053, 1089, 1095]},
        [[172, 1035], [1082, 810]]
    ]
}
```

- Tanto `votos_por_partido` como `votos_por_coalicion` siguen la siguiente subestructura:
    ```
    [OPCIONES_DESPLEGADAS_EN_HORIZONTAL, OPCIONES_DESPLEGADAS_EN_VERTICAL, PAREOS]
    ```

    Que en detalle se definen como:

    - `OPCIONES_DESPLEGADAS_EN_HORIZONTAL`:
    ```
    Un conjunto de opciones destinadas a ser desplegadas en horizontal. Tiene la siguiente forma:
        {
            <opcion1>: {<grupo1>: n, <grupo2>: n, ..., <grupoN>: n},
            <opcion2>: {<grupo1>: n, <grupo2>: n, ..., <grupoN>: n},
            ...,
            <opcionN>: {<grupo1>: n, <grupo2>: n, ..., <grupoN>: n}
        }

       Estas opciones serán incluídas en la visualización de la forma:
             ------------------------------------------------------------------
            |    votos option1    |   votos option2   |...|   votos optionN    |
             ------------------------------------------------------------------
    ```

    - `OPCIONES_DESPLEGADAS_EN_VERTICAL`:
    ```
    Un conjunto de opciones destinadas a ser desplegadas en vertical. Tiene la siguiente forma:
        {
            <opcion1>: {<grupo1>: n, <grupo2>: n, ..., <grupoN>: n},
            <opcion2>: {<grupo1>: n, <grupo2>: n, ..., <grupoN>: n},
            ...,
            <opcionN>: {<grupo1>: n, <grupo2>: n, ..., <grupoN>: n}
        }

        Estas opciones serán incluídas en la visualización de la forma:
                             --------------------
                            |    votos option1   |
                             --------------------
                            |    votos option2   |
                             --------------------
                                      ...
                             --------------------
                            |    votos optionN   |
                             --------------------
    ```

    - `PAREOS`:
    ```
    Una lista de los pareos con la forma:
        [(<grupo1>, <grupo2>), (<grupo3>, <grupo4>), ...]
    ```

- Además, `votos_por_diputado` incluye una estructura similar al caso anterior, con la diferencia de que los diccionarios son reemplazados por listas que contienen los ids de todos los diputados que votaron la respectiva opción.

Finalmente, se aclara que este formato está optimizado para la realización de las visualizaciones, no para ser usados como descriptor genérico de las votaciones. Por esta razón, no se incluye información detallada de qué votó cada diputado o diputada.
