# ESP32-con-pantalla-nombres
import time
from machine import Pin, I2C
import lcd

# Inicializar I2C
i2c = I2C(0, scl=Pin(22), sda=Pin(21), freq=400000)  # GPIO22 para SCL, GPIO21 para SDA

# Inicializar pantalla LCD (en este caso una LCD 16x2)
lcd = lcd.LCD(i2c)

# Configurar el LCD
lcd.clear()

# Lista de nombres
nombres = ["Juan", "Maria", "Pedro", "Ana", "Luis"]

# Contador para recorrer los nombres
index = 0

# Bucle para mostrar los nombres
while True:
    lcd.clear()  # Limpiar la pantalla antes de mostrar el nuevo nombre
    lcd.putstr("Nombre: " + nombres[index])  # Mostrar el nombre en la pantalla
    time.sleep(2)  # Esperar 2 segundos antes de mostrar el siguiente nombre
    
    # Incrementar el índice para mostrar el siguiente nombre
    index += 1
    
    # Si llegamos al final de la lista, volver al inicio
    if index >= len(nombres):
       
