```Python
from machine import Pin
from time import sleep_ms
from random import randint

button = Pin(2, Pin.IN, Pin.PULL_UP)

def rollDise():
    for i in range(9,15):
        led = Pin(i,Pin.OUT)
        led.value(1)
        sleep_ms(500)
        led.value(0)
    led.value(0)
    sleep_ms(1000)
    pinNum = randint(9,14)
    led = Pin(pinNum,Pin.OUT)
    led.value(1)
    sleep_ms(3000)
    led.value(0)
        
while True:
    if not button.value():
        rollDise() 
```
