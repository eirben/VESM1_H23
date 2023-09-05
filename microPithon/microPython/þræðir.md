
``` python
import _thread as th
import time
from machine import Pin
blink1_running = True
blink2_running = True
buzzer_running = True

buzzer = Pin(12,Pin.OUT) # buzzer í pinna 12 og GND
led1 = Pin(13, Pin.OUT) #led1 í pinna 13 og GND
led2 = Pin(14, Pin.OUT) #led2 í pinna 14 og GND
buzzer.value(0)

def blink1(delay):
     while blink1_running:
         led1.value(not led1.value())
         time.sleep(delay)
     led1.value(0)

def blink2(delay):
     while blink2_running:
         led2.value(not led2.value())
         time.sleep(delay)
     led2.value(0)

def buzz(delay):
    while buzzer_running:
        buzzer.value(not buzzer.value())
        time.sleep(delay)
    buzzer.value(0)

print("Byrja þráðavinnslu..")
th.start_new_thread(blink1, (0.5,))
th.start_new_thread(blink2, (0.25,))
th.start_new_thread(buzz,(0.25,))

count = 0
while True:
  print("Ljósa sýning og óhljóð... " + str(count))
  count += 1
  if count >= 10:
    break
  time.sleep(1)

print("Enda ljósasýningu...")
blink1_running = False
blink2_running = False
buzzer_running = False
```

