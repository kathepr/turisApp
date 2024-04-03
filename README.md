# CHEAT-SHEET JSON Y PYTHON

1. ***“Invocar” PUERTO/URL local/remota JSON Server***
    
    ejemplo: json-server storage/gama_producto.json -b 5502
    

1. ***JSON:***

**get:** 

peticion1 = requests.get(f"[http://154.38.171.54:5503/activos?id={id}](http://154.38.171.54:5503/activos?id=%7Bid%7D)")
data1 = json.loads(peticion1.text)
datosActuales = data1[0]

**put:**

url = f"[http://154.38.171.54:5503/activos/{id}](http://154.38.171.54:5503/activos/%7Bid%7D)"
data2 = json.dumps(activoActualizado)
peticion2 = requests.put(url, data2)

**post:**

url = "http://154.38.171.54:5503/activos"
data = json.dumps(activoNuevo)
peticion = requests.post(url, data)

**patch:**

activo["historialActivos"].append(registroHistorialRetorno) #Aquí agrego el nuevo registro al historial del activo
url = f"[http://154.38.171.54:5503/activos/{id}](http://154.38.171.54:5503/activos/%7Bid%7D)"
dataHistorial = json.dumps(activo,default=str) #aquí envío el activo con ese nuevo registro de historial a la base de datos remota
peticionHistorial = requests.patch(url, dataHistorial)

1. **FUNCIÓN PARA VALIDAR EXPRESIONES REGULARES:**
    
    Import re
    
    #Expresiones regulares para los datos ingresado
    
    ```
    NroSerialR = re.compile(r'^[A-Z0-9\\-]+$') #Solo permite números y letras mayusculas y guiones
    
    ```
    
    #Obtener los datos del usuario
    
    ```
    NroSerial = pe.validar_input(NroSerialR, "Ingrese el número del serial: ")
    
    ```
    
    ```
    def validar_input(patron, mensaje):
    
    while True:
        entrada = input(mensaje)
        if patron.match(entrada):
            confirmacion = input(f"¿Confirma el ingreso de este dato '{entrada}'? (S/N) ").strip().lower()
            if confirmacion == "s":
                return entrada
        else:
            print("El dato no cumple con los parametros establecidos. Vuelva a intentarlo.")
    
    ```
    
    1. **Configuración de códigos aleatorios:**
        
        import random
        
        import shortuuid
        
        nuevoNroItem =''.join(random.choices('0123456789', k=5)) #con random creo una secuencia aleatoria de elementos, join me ayuda a convertir la lista en caracteres
        
        nuevoNroFormulario =  shortuuid.random(length=4) #uuid me ayuda a generar un id unico y aleatorio
