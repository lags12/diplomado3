FORMAT: 1A
HOST: http://polls.apiblueprint.org/

# Diplomado Unidad 3

SISTEMA DE CONTROL DE TRAFICO URBANO

## Envio de datos [/Usuarios/{id}]
Recurso Datos

Atributos Obligatorios: 

- `id`          Asignado
- `transmision_estadistica_trafico`
- `nego_param`
- `alarmas`

+ Parameters
    + id (required, int) ... PK Datos

+ Model (application/hal+json)

    + Body

            {
                "id": 1,
                "transmision_estadistica_trafico":"informacion de trafico",
                "nego_param":"negociacion de paarmetros",
                "alarmas":" genera y transmite alarmas",
                                    
            }

## Lista Informacion de trafico [GET]

+ Response 200

        [Envio de datos][Usuarios]
        

## Videos [/videos/{id}]
Recurso_videos

Atributos Obligatorios: 

- `id`          Asignado
- `i_transmision`


+ Parameters
    + id (required, int) ... PK video

+ Model (application/hal+json)

    + Body

            {
                "id": 1,
                "i_transmision": "12-09-2015 11:00",
                "fin_transmision": "13-09-2015 12:00",
                "tamano_video": "2 GB",
                
            }
            
## Buscar Video [GET]

+ Response 200

    [Videos][]

+ Response 404 (application/json)

        { 
            "error": "Recurso no se encuentra" 
        }

+ Response 404

        { 
            "error": "Recurso no disponible"
        }

+ Response 400

        { 
            "error": "Fallo al modificar el Recurso"
        }

## Eliminar Video [DELETE]

+ Response 200

        { 
            "result": True,
            "message": "Video eliminado "
        }

        [Videos][]
    

# Lista de videos [/videos]
Obtener todos los videos

+ Model (application/hal+json)

    + Body

            {
                "videos": [
                    {
                        "id": 1,
                        "i_transmision": "12-09-2015 11:00",
                        "fin_transmision": "13-09-2015 12:00",
                        "tamano_video": "2 GB",
                                            },
                    {
                        "id": 2,
                        "i_transmision": "12-09-2015 11:00",
                        "fin_transmision": "13-09-2015 12:00",
                        "tamano_video": "2 GB",
                                            },{
                        "id": 3,
                        "i_transmision": "12-09-2015 11:00",
                        "fin_transmision": "12-09-2015 12:00",
                        "tamano_video": "2 GB",
                                            }
                ]
            }


## Obtener lista de videos [GET]

+ Response 200

    [Lista de videos][]


# Reproducir Video [/videos/{id}/reproducir]
Reproducir video 

+ Model (application/hal+json)

    + Body

            {
                "id": 3,
                "status": "offline",
                "i_transmision": "12-09-2015 11:00",
                "fin_transmision":"13-09-2015 22:00"
            }


## Buscar y reproducir video [GET]

+ Response 200

    [Reproducir Video][]


## Camaras [/camaras/{id}]
Recurso Cámaras 

Atributos Obligatorios: 

- `id`          Asignado
- `marca`
- `brillo`
- `calidad`
- `color`
- `contraste`
- `ip`
- `coordenadas`


+ Parameters
    + id (required, int) ... PK Cámara

+ Model (application/hal+json)

    + Body

            {
                "id": 1,
                "marca":"Camara Sony",
                "fecha_add":"05-09-2015",
                "ip":"192.168.1.100",
                "latitud":"-33.000101",
                "longitud":"-77.01212",
                "configuración":{
                    "brillo": 10,
                    "calidad": "720p",
                    "color":"rgba(0,0,0)",
                                    }
            }
            
## Buscar Cámara [GET]

+ Response 200

    [Camaras][]
    
+ Response 404 (application/json)

        { 
            "error": "Recurso no se encuentra" 
        }
    
### Editar Cámara [PATCH]

+ Request (application/json)

        {
            "brillo": 20,
                    }

+ Response 200
    
    [Camaras][]

+ Response 404

        { 
            "error": "Recurso no disponible"
        }

+ Response 400

        { 
            "error": "Fallo al modificar el Recurso"
        }

## Eliminar Cámara [DELETE]

+ Response 200

        { 
            "result": True,
            "message": "Cámara eliminada con éxito"
        }

## Nueva Cámara [POST]

+ Request (application/json)

        {
            "marca":"Camara Sony",
            "fecha_add":"05-09-2015",
            "brillo": 10,
            "calidad": "720p",
            "color":"rgba(0,0,0)",
                    }

+ Response 201

    [Camaras][]
    
+ Response 400

        { 
            "error": "Error al crear cámara"
        }

# Lista de camaras [/camaras]
Obtener todas las cámaras registradas

+ Model (application/hal+json)

    + Body

            {
                "camaras": [
                    {
                        "id": 1,
                        "marca":"Camara Sony",
                        "fecha_add":"12-09-2015",
                        "ip":"192.168.1.150",
                        "latitud":"-33.000101",
                        "longitud":"-77.01212",
                        "configuración":{
                            "brillo": 10,
                            "calidad": "720p",
                            "color":"rgba(0,0,0)",
                                                    }
                    },{
                        "id": 1,
                        "marca":"Camara Sony",
                        "fecha_add":"12-09-2015",
                        "ip":"192.168.1.151",
                        "latitud":"-33.000101",
                        "longitud":"-77.01212",
                        "configuración":{
                            "brillo": 10,
                            "calidad": "720p",
                            "color":"rgba(0,0,0)",
                                                    }
                    }
                ]
            }


## Obtener lista de cámaras [GET]

+ Response 200

    [Lista de camaras][]

# Transmitir video [/camaras/{id}/transmitir]
Transmitir video

+ Model (application/hal+json)

    + Body

            {
                "id": 1,
                "marca":"Camara Sony",
                "fecha_add":"12-09-2015",
                "ip":"192.168.1.150",
                "latitud":"-33.000101",
                "longitud":"-77.01212",
                "configuración":{
                    "brillo": 10,
                    "calidad": "720p",
                    "color":"rgba(0,0,0)",
                                    },
                "Video":{
                    "id": 1,
                                    },
                "broadcast":{
                    "id": 1,
                    "inicio_broadcast":"12-09-2015 18:00",
                    "descripción": "Descripción video tiempo real",
                    "fps":30
                }
            }


## Buscar y transmitir video [GET]

+ Response 200

    [Transmitir video][]
    
## Mapa Metereologico [/Mapa/{id}]
Recurso Mapa

Atributos Obligatorios: 

- `id`          Asignado
- `localizacion`
- `hora`
- `condiciones_clima`

+ Parameters
    + id (required, int) ... PK Mapa

+ Model (application/hal+json)

    + Body

            {
                "id": 1,
                "localizacion":"lugar del mapa",
                "fecha_hora":"01-01-2015 00:01",
                "condiciones_clima`":" clima",
                                    
            }

## Lista un mapa [GET]

+ Response 200

        [Mapa Metereologico][Mapa]
        
## Borra un mapa [DELETE]

+ Response 200

        { 
            "result": True
        }   
        
