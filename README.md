# Sv24K
The24K
{
  "$esquema": "http://json-schema.org/draft-07/schema#",
  "$id": "https://uniswap.org/tokenlist.schema.json",
  "title": "Lista de tokens de Uniswap",
  "description": "Esquema para listas de tokens compatibles con la Interfaz Uniswap",
  "definiciones": {
    "Versión": {
      "tipo": "objeto",
      "description": "La versión de la lista, utilizada en la detección de cambios",
      "ejemplos": [
        {
          "principal": 1,
          "menor": 0,
          "parche": 0
        }
      ],
      "Propiedades adicionales": falso,
      "propiedades": {
        "importante": {
          "tipo": "entero",
          "description": "La versión principal de la lista. Debe incrementarse cuando se eliminan tokens de la lista o se cambian las direcciones de tokens".,
          "mínimo": 0,
          "ejemplos": [
            1,
            2
          ]
        },
        "menor": {
          "tipo": "entero",
          "description": "La versión menor de la lista. Debe incrementarse cuando se agregan tokens a la lista.",
          "mínimo": 0,
          "ejemplos": [
            0,
            1
          ]
        },
        "parche": {
          "tipo": "entero",
          "description": "La versión del parche de la lista. Debe incrementarse para cualquier cambio en la lista.",
          "mínimo": 0,
          "ejemplos": [
            0,
            1
          ]
        }
      },
      "requerido": [
        "importante",
        "menor",
        "parche"
      ]
    },
    "Identificador de etiqueta": {
      "tipo": "cadena",
      "description": "El identificador único de una etiqueta",
      "longitud mínima": 1,
      "longitud máxima": 10,
      "patrón": "^[\\w]+$",
      "ejemplos": [
        "compuesto",
        "moneda estable"
      ]
    },
    "ExtensionIdentifier": {
      "tipo": "cadena",
      "description": "El nombre de una propiedad de extensión de token",
      "longitud mínima": 1,
      "longitud máxima": 40,
      "patrón": "^[\\w]+$",
      "ejemplos": [
        "color",
        "es_tarifa_en_transferencia",
        "alias"
      ]
    },
    "Mapa de extensión": {
      "tipo": "objeto",
      "description": "Un objeto que contiene cualquier metadato de token arbitrario o específico del proveedor",
      "maxProperties": 10,
      "nombres de propiedad": {
        "$ref": "#/definiciones/ExtensionIdentifier"
      },
      "Propiedadesadicionales": {
        "$ref": "#/definiciones/ExtensionValue"
      },
      "ejemplos": [
        {
          "color": "#000000",
          "es_verificado_por_mi": verdadero
        },
        {
          "x-direcciones-puenteadas-por-cadena": {
            "1": {
              "dirección del puente": "0x42000000000000000000000000000000000000010",
              "tokenAddress": "0x42000000000000000000000000000000000000010"
            }
          }
        }
      ]
    },
    "ExtensiónPrimitiveValue": {
      "cualquiera de": [
        {
          "tipo": "cadena",
          "longitud mínima": 1,
          "longitud máxima": 42,
          "ejemplos": [
            "#00000"
          ]
        },
        {
          "tipo": "booleano",
          "ejemplos": [
            verdadero
          ]
        },
        {
          "teclea un número",
          "ejemplos": [
            15
          ]
        },
        {
          "tipo": "nulo"
        }
      ]
    },
    "Valor de extensión": {
      "cualquiera de": [
        {
          "$ref": "#/definiciones/ExtensionPrimitiveValue"
        },
        {
          "tipo": "objeto",
          "maxProperties": 10,
          "nombres de propiedad": {
            "$ref": "#/definiciones/ExtensionIdentifier"
          },
          "Propiedadesadicionales": {
            "$ref": "#/definiciones/ExtensionValueInner0"
          }
        }
      ]
    },
    "ExtensionValueInner0": {
      "cualquiera de": [
        {
          "$ref": "#/definiciones/ExtensionPrimitiveValue"
        },
        {
          "tipo": "objeto",
          "maxProperties": 10,
          "nombres de propiedad": {
            "$ref": "#/definiciones/ExtensionIdentifier"
          },
          "Propiedadesadicionales": {
            "$ref": "#/definiciones/ExtensionValueInner1"
          }
        }
      ]
    },
    "ExtensionValueInner1": {
      "cualquiera de": [
        {
          "$ref": "#/definiciones/ExtensionPrimitiveValue"
        }
      ]
    },
    "Definición de etiqueta": {
      "tipo": "objeto",
      "description": "Definición de una etiqueta que se puede asociar con un token a través de su identificador",
      "Propiedades adicionales": falso,
      "propiedades": {
        "nombre": {
          "tipo": "cadena",
          "description": "El nombre de la etiqueta",
          "patrón": "^[ \\w]+$",
          "longitud mínima": 1,
          "longitud máxima": 20
        },
        "descripción": {
          "tipo": "cadena",
          "description": "Una descripción fácil de usar de la etiqueta",
          "patrón": "^[ \\w\\.,:]+$",
          "longitud mínima": 1,
          "longitud máxima": 200
        }
      },
      "requerido": [
        "nombre",
        "descripción"
      ],
      "ejemplos": [
        {
          "nombre": "Moneda estable",
          "description": "Un token con valor vinculado a otro activo"
        }
      ]
    },
    "TokenInfo": {
      "tipo": "objeto",
      "description": "Metadatos para un solo token en una lista de tokens",
      "Propiedades adicionales": falso,
      "propiedades": {
        "id de cadena": {
          "tipo": "entero",
          "description": "El ID de la cadena de la red Ethereum donde se implementa este token",
          "mínimo": 1,
          "ejemplos": [
            1,
            42
          ]
        },
        "Dirección": {
          "tipo": "cadena",
          "description": "La dirección de suma de verificación del token en el ID de cadena especificado",
          "patrón": "^0x[a-fA-F0-9]{40}$",
          "ejemplos": [
            "0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48"
          ]
        },
        "decimales": {
          "tipo": "entero",
          "description": "El número de decimales para el saldo del token",
          "mínimo": 0,
          "máximo": 255,
          "ejemplos": [
            18
          ]
        },
        "nombre": {
          "tipo": "cadena",
          "description": "El nombre del token",
          "longitud mínima": 1,
          "longitud máxima": 40,
          "patrón": "^[ \\w.'+\\-%/À-ÖØ-öø-ÿ:&\\[\\]\\(\\)]+$",
          "ejemplos": [
            "Moneda USD"
          ]
        },
        "símbolo": {
          "tipo": "cadena",
          "description": "El símbolo del token; debe ser alfanumérico",
          "patrón": "^[a-zA-Z0-9+\\-%/$.]+$",
          "longitud mínima": 1,
          "longitud máxima": 20,
          "ejemplos": [
            "USDC"
          ]
        },
        "logoURI": {
          "tipo": "cadena",
          "description": "Un URI para el activo del logotipo del token; si no se configura, la interfaz intentará encontrar un logotipo basado en la dirección del token; sugiere SVG o PNG de tamaño 64x64",
          "formato": "uri",
          "ejemplos": [
            "ipfs://QmXfzKRvjZz3u5JRgC4v5mGVbm9ahrUiB4DgzHBsnWbTMM"
          ]
        },
        "etiquetas": {
          "tipo": "matriz",
          "description": "Una matriz de identificadores de etiqueta asociados con el token; las etiquetas se definen en el nivel de lista",
          "elementos": {
            "$ref": "#/definiciones/Identificador de etiqueta"
          },
          "elementos máximos": 10,
          "ejemplos": [
            "moneda estable",
            "compuesto"
          ]
        },
        "extensiones": {
          "$ref": "#/definiciones/ExtensionMap"
        }
      },
      "requerido": [
        "cadenaId",
        "Dirección",
        "decimales",
        "nombre",
        "símbolo"
      ]
    }
  },
  "tipo": "objeto",
  "Propiedades adicionales": falso,
  "propiedades": {
    "nombre": {
      "tipo": "cadena",
      "description": "El nombre de la lista de tokens",
      "longitud mínima": 1,
      "longitud máxima": 20,
      "patrón": "^[\\w ]+$",
      "ejemplos": [
        "Mi lista de fichas"
      ]
    },
    "marca de tiempo": {
      "tipo": "cadena",
      "formato": "fecha-hora",
      "description": "La marca de tiempo de esta versión de la lista; es decir, cuándo se creó esta versión inmutable de la lista"
    },
    "versión": {
      "$ref": "#/definiciones/Versión"
    },
    "fichas": {
      "tipo": "matriz",
      "description": "La lista de tokens incluidos en la lista",
      "elementos": {
        "$ref": "#/definiciones/TokenInfo"
      },
      "elementos mínimos": 1,
      "maxItems": 10000
    },
    "palabras clave": {
      "tipo": "matriz",
      "description": "Palabras clave asociadas con el contenido de la lista; se pueden usar en la visibilidad de la lista",
      "elementos": {
        "tipo": "cadena",
        "description": "Una palabra clave para describir el contenido de la lista",
        "longitud mínima": 1,
        "longitud máxima": 20,
        "patrón": "^[\\w ]+$",
        "ejemplos": [
          "compuesto",
          "préstamo",
          "fichas personales"
        ]
      },
      "elementos máximos": 20,
      "elementos únicos": verdadero
    },
    "etiquetas": {
      "tipo": "objeto",
      "description": "Un mapeo de identificadores de etiqueta a su nombre y descripción",
      "nombres de propiedad": {
        "$ref": "#/definiciones/Identificador de etiqueta"
      },
      "Propiedadesadicionales": {
        "$ref": "#/definiciones/Definición de etiqueta"
      },
      "maxProperties": 20,
      "ejemplos": [
        {
          "moneda estable": {
            "nombre": "Moneda estable",
            "description": "Un token con valor vinculado a otro activo"
          }
        }
      ]
    },
    "logoURI": {
      "tipo": "cadena",
      "description": "Un URI para el logo de la lista de tokens; prefiera SVG o PNG de tamaño 256x256",
      "formato": "uri",
      "ejemplos": [
        "ipfs://QmXfzKRvjZz3u5JRgC4v5mGVbm9ahrUiB4DgzHBsnWbTMM"
      ]
    }
  },
  "requerido": [
    "nombre",
    "marca de tiempo",
    "versión",
    "fichas"
  ]
}
