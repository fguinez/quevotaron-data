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
    "fecha": [2021, 6, 15],
    "tipo": "Proyecto Ley",
    "resultado": "Aprobado",
    "quorum": "3/5 del total",
    "nquorum": 93,
    "info_por_partido": [
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
    "info_por_coalicion": [
        {
            "A favor": {"UC": 48, "CV": 23, "SC": 9, "AD": 24}, 
            "Abstienen": {"CV": 8},
            "En contra": {"CV": 33}
        },
        {"Ausentes": {"CV": 5, "AD": 1}},
        [["CV", "AD"], ["CV", "AD"]]
    ]
}
```

Tanto `info_por_partido` como `info_por_coalicion` siguen la siguiente subestructura:
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


Finalmente, se aclara que este formato está optimizado para la realización de las visualizaciones, no para ser usados como descriptor genérico de las votaciones. Por esta razón, no se incluye información detallada de qué votó cada diputado o diputada.
