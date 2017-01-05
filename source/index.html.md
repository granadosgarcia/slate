---
title: API Reference

language_tabs:
  - shell
  - javascript

toc_footers:

search: true
---

# Introducción

Bienvenido a la API de Controlpack. Esta API se usa para tener acceso a las ordenes y permite interactuar con nuestro sistema para realizar ordenes o checar el estado de las que ya están en proceso.

Tenemos ejemplos de uso en Shell, Ruby, Python y JS Con ejemplos de código para integrarlo rápidamente con tu sistema.  

Para acceder a la API se usa la siguiente URL:
[https://api.packandpack.com/v1/](https://api.packandpack.com/v1/)

# Órdenes

## Ver todas las órdenes

```shell
curl "https://api.packandpack.com/v1/orders"
```

```javascript
(con JQuery)
$.getJSON("https://api.packandpack.com/v1/orders", function(response){
        //Las ordenes están listas
        console.log(response.orders)
});
```

> El comando regresa un JSON que tiene esta forma:

```json
{
  "status": "success",
  "orders": [
    {
      "_id": "586cf9eeafa05d617ab63a51",
      "eta": "2017-01-05T06:56:30.000Z",
      "cost": 5000,
      "requestedDate": "2017-01-05T06:12:37.763Z",
      "possible": true,
      "__v": 0,
      "status": 20,
      "places": {
        "pickup": {
          "contactName": "ullamco tempor fugiat consequat elit",
          "contactPhone": "68937108",
          "address": "Oxxo de la esquina",
          "coordinates": {
            "lat": 19.0355907,
            "lng": -98.2245167
          }
        },
        "delivery": {
          "contactName": "Juan Pérez",
          "contactPhone": "2223988299",
          "address": "Anzures, Puebla",
          "coordinates": {
            "lat": 19.1037467,
            "lng": -98.2497827
          }
        }
      }
    },
    {
      "_id": "58640ca9e86fbfb723984424",
      "eta": "2016-12-28T19:12:51.000Z",
      "cost": 3000,
      "requestedDate": "2016-12-28T19:04:08.779Z",
      "possible": true,
      "__v": 0,
      "places": {
        "pickup": {
          "contactName": "Otro tipo",
          "contactPhone": "5553987875",
          "address": "Av. Bla bla bla, col. bla bla bla, del bla bla bla"
        },
        "delivery": {
          "contactName": "Prueba",
          "contactPhone": "5553987875",
          "address": "Av. Bla bla bla, col. bla bla bla, del bla bla bla"
        }
      }
    }
  ]
}
```

Este endpoint regresa todas las órdenes relacionadas

### HTTP Request

`GET https://api.packandpack.com/v1/orders`


<aside class="success">
Se necesita estar autenticado para poder ver órdenes
</aside>

## Crear una Orden

```shell
curl -H "Content-Type: application/json" -X POST -d '{
    "pickup": {
    "contactName": "Pruebas",
    "contactPhone": "68937101",
    "address": "Sin calle",
    "coordinates": {
        "lat": 19.0355901,
        "lng": -98.2245161
        }
    },
    "delivery": {
    "contactName": "Super sith",
    "contactPhone": "92051031",
    "address": "velit in minim eu",
    "coordinates": {
        "lat": 19.1037464,
        "lng": -98.2497824
        }
    }
}'
https://api.packandpack.com/v1/orders
```

```javascript
(con JQUERY)
$.ajax({
  url: 'https://api.packandpack.com/v1/orders',
  type: 'POST',
  data: {
    "pickup": {
    "contactName": "Pruebas",
    "contactPhone": "68937101",
    "address": "Sin calle",
    "coordinates": {
        "lat": 19.0355901,
        "lng": -98.2245161
        }
    },
    "delivery": {
    "contactName": "Super sith",
    "contactPhone": "92051031",
    "address": "velit in minim eu",
    "coordinates": {
        "lat": 19.1037464,
        "lng": -98.2497824
        }
    }
}
});
```

> El comando regresa un JSON que luce así:

```json
{
  "status": "success",
  "order": {
    "__v": 0,
    "eta": "2017-01-05T09:12:42.000Z",
    "cost": 5000,
    "requestedDate": "2017-01-05T08:29:26.366Z",
    "possible": true,
    "status": 10,
    "_id": "586e03e624a74500049d0a8f",
    "places": {
      "delivery": {
        "contactName": "Super sith",
        "contactPhone": "92051031",
        "address": "velit in minim eu",
        "coordinates": {
          "lat": 19.1037464,
          "lng": -98.2497824
        }
      },
      "pickup": {
        "contactName": "Pruebas",
        "contactPhone": "68937101",
        "address": "Sin calle",
        "coordinates": {
          "lat": 19.0355901,
          "lng": -98.2245161
        }
      }
    }
  }
}
```
En este endpoint se crea una orden.

### HTTP Request

`POST https://api.packandpack.com/v1/orders`

### Body Request

Se necesita mandar en el body un JSON con la siguiente información del envío que se va a crear

<code>
{  
    "pickup": {  
        "contactName": "Pruebas",  
        "contactPhone": "68937101",  
        "address": "Sin calle",  
        "coordinates": {  
            "lat": 19.0355901,  
            "lng": -98.2245161  
        }  
    },  
    "delivery": {  
            "contactName": "Super sith",  
            "contactPhone": "92051031",  
            "address": "velit in minim eu",  
            "coordinates": {  
                "lat": 19.1037464,  
                "lng": -98.2497824  
            }  
    }  
}  
</code>

## Ver una orden específica


```shell
curl "https://api.packandpack.com/v1/orders/586cff2fb1ffb06a3df2db41"
```

```javascript
(con JQuery)
$.getJSON("https://api.packandpack.com/v1/orders/586cff2fb1ffb06a3df2db41", function(response){
        //La orden está lista
        console.log(response.orden)
});
```
> Este comando regresa un JSON que se ve así:

```json
{
  "status": "success",
  "order": {
    "_id": "586cff2fb1ffb06a3df2db41",
    "eta": "2017-01-05T00:22:35.000Z",
    "cost": 5000,
    "requestedDate": "2017-01-04T23:34:47.900Z",
    "possible": true,
    "__v": 0,
    "status": 299,
    "places": {
      "pickup": {
        "contactName": "Juanito",
        "contactPhone": "68937101",
        "address": "Sin calle",
        "coordinates": {
          "lat": 19.0355901,
          "lng": -98.2245161
        }
      },
      "delivery": {
        "contactName": "occaecat sit",
        "contactPhone": "92051031",
        "address": "velit in minim eu",
        "coordinates": {
          "lat": 19.1037464,
          "lng": -98.2497824
        }
      }
    }
  }
}
```

Este endpoint regresa una orden específica

### HTTP Request

`GET https://api.packandpack.com/v1/orders/<ID>`

### Parámetros de URL

Parameter | Description
--------- | -----------
ID | El ID de la órden que se va a revisar

## Actualizar una Orden

```shell
curl -H "Content-Type: application/json" -X PUT -d '{
    "pickup": {
      "contactName": "eli",
      "contactPhone": 34315086,
      "address": "pariatur"
    },
    "status": 6
}'
https://api.packandpack.com/v1/orders
```

```javascript
(con JQUERY)
$.ajax({
  url: 'https://api.packandpack.com/v1/orders/586cff2fb1ffb06a3df2db41',
  type: 'PUT',
  data: {  
    "pickup": {
      "contactName": "eli",
      "contactPhone": 34315086,
      "address": "pariatur"
    },
    "status": 6
}
});
```

> El comando regresa un JSON que luce así:

```json
{
  "status": "success",
  "order": {
    "__v": 0,
    "eta": "2017-01-05T09:12:42.000Z",
    "cost": 5000,
    "requestedDate": "2017-01-05T08:29:26.366Z",
    "possible": true,
    "status": 10,
    "_id": "586e03e624a74500049d0a8f",
    "places": {
      "delivery": {
        "contactName": "Super sith",
        "contactPhone": "92051031",
        "address": "velit in minim eu",
        "coordinates": {
          "lat": 19.1037464,
          "lng": -98.2497824
        }
      },
      "pickup": {
        "contactName": "Pruebas",
        "contactPhone": "68937101",
        "address": "Sin calle",
        "coordinates": {
          "lat": 19.0355901,
          "lng": -98.2245161
        }
      }
    }
  }
}
```
En este endpoint se actualiza la información de una orden.

### HTTP Request

`PUT https://api.packandpack.com/v1/orders/<ID>`

### Parámetros de URL

Parameter | Description
--------- | -----------
ID | El ID de la órden que se va a actualizar

### Body Request

Se necesita mandar en el body un JSON con la información que se le va a actualizar a la orden

<code>
{  
  "pickup": {
    "contactName": "eli",
    "contactPhone": 34315086,
    "address": "pariatur"
  },
  "status": 6
}

</code>
