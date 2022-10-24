# Engineering_4_Notebook

&nbsp;
### My Table of Contents Never Works:(
&nbsp;

## Launch_Pad_Part_1_(Countdown)

### Assignment Description

Today Ellen and I wrote code to make a countdown from 10 on the serial monitor. We had to write code to import the pico correctly and ensure we had all the downloaded extensions. We did this to incorporate it into our final python assignment later. 

### Evidence 

![evidence](images/Launchpad1GIF.gif)  

### Code
```
import time    #time variable
for x in range(10,0,-1):  #counting range of numbers
    print(x)         #says each number
    time.sleep (1)   #rest 1 sec for a pause
print("LAUNCHY")     #say this at the end of 10s
```

### Reflection

We had some difficulty getting the countdown to count down from ten as opposed to counting up from 1, but other than that, this task was pretty straightforward. Another minor issue was figuring out the best way to run the pico, as this was our first assignment. Thankfully there was no wiring, and we could get this assignment done relatively quickly.

## Launch Pad Part 2 (Lights)

### Assignment Description

Today Ellen and I created code to make a red light flash as the serial monitor counts down from ten and then flashes a red light when the word 'launch' is printed. We wrote this code as a part of our 4pt python assignment. This will be useful later in the year if we need LEDs for our project or something that functions similarly through code or practice.

### Evidence 

![Lights+Countdown](images/Launchpad2.gif)  

### Code

```
import time #Imports variables
import board
import digitalio 

led1 = digitalio.DigitalInOut(board.GP13) #says that the first led is at pin 13
led1.direction = digitalio.Direction.OUTPUT #gives direcction
led2 = digitalio.DigitalInOut(board.GP18) #says the second led is at pin 18
led2.direction = digitalio.Direction.OUTPUT #gives direction

for x in reversed(range(11)): 
    led1.value = True #turns light on
    time.sleep(0.5) #wait time
    print(x) #tells it what to say
    led1.value = False #turns led off
    time.sleep(0.5) #wait time
while True:
    print("liftoff!") #says liftoff
    led2.value = True #turns red light on
    time.sleep(0.5) #tells it when to sleep
```
### Wiring

[Diagram](images/Wiringdiagram1.jpg)

### Reflection

We struggled to get the correct light to light up during the countdown. We eventually figured out the problem was that we had misidentified our LEDs, so it's important to label things because it makes things more organized and easier to use or understand later. This assignment will be helpful in the following two launch pad assignments along with our pi in the sky project.

## Launch Pad Part 3 (Button)

### Assignment Description

This is for our 4 part python assignment. Today Ellen and I created code to make the countdown and lights start when we press a button. We did this to mimic a realistic countdown that is started with an ignition.

### Evidence 

![Button](images/butt1.gif)  

### Code

```
import time #imports
import board
import digitalio

led1 = digitalio.DigitalInOut(board.GP13) #pins 
led1.direction = digitalio.Direction.OUTPUT
led2 = digitalio.DigitalInOut(board.GP18)
led2.direction = digitalio.Direction.OUTPUT
button = digitalio.DigitalInOut(board.GP16) #adds in the button
button.direction = digitalio.Direction.INPUT
button.pull = digitalio.Pull.UP #incorperates the button into the circuit

while True: #if the button is pressed this will happen
     if button.value == False:
          for x in reversed(range(11)):
               led1.value = True #light on
               time.sleep(0.5) #light rest
               print(x)
               led1.value = False #light off
               time.sleep(0.5)
          while True:
               print("liftoff!") #prints liftoff
               led2.value = True
               time.sleep(0.5)
```

### Wiring

[Wiring Diagram](images/B2891F05-A75D-4551-ACE8-1FF7697E1B06.jpeg)

### Reflection

So as a group with minimal experience and a strong dislike for coding, this took a lot of questioning and thinking. We were adding to our previous code and wiring, but we have never used a button, much less coded for it, so that was new. Our main issue was that we didn't know where to put the new code (again). We had to figure out how to use the correct imports in order to print the correct code.

## Launch Pad Part 4 (Servo)

### Assignment Description

Today Ellen and I created code to make the coundown and lights start when we press a button and at the end it will make a servo turn at 180 degrees. This is for our 4pt pyhton assignment.

### Evidence 

![Servo](images/this1.gif)  

### Code

```
import time    #importing stuff
import board
import digitalio
import pwmio 
from adafruit_motor import servo

led1 = digitalio.DigitalInOut(board.GP13)
led1.direction = digitalio.Direction.OUTPUT
led2 = digitalio.DigitalInOut(board.GP18)
led2.direction = digitalio.Direction.OUTPUT
button = digitalio.DigitalInOut(board.GP16)  #what stuff is going in vs out and where it's at
button.direction = digitalio.Direction.INPUT
button.pull = digitalio.Pull.UP
pwm_servo = pwmio.PWMOut(board.GP5, duty_cycle=2 ** 15, frequency=50)  #setting up servo
servo1 = servo.Servo(pwm_servo, min_pulse=500, max_pulse=2500)

servo1.angle = 0


while True: 
     if button.value == False:    #so when we aren't pressing it anymore
          for x in reversed(range(11)):
               led1.value = True
               time.sleep(0.5)     #rest a sec between counts
               print(x)
               led1.value = False
               time.sleep(0.5)
          while True:
               print("liftoff!")     #say liftoff
               led2.value = True
               servo1.angle = 180     #turn180
               time.sleep(0.5)
 ```

### Wiring

[Wiring Diagram](https://github.com/gdaless20/Engineering_4_Notebook/blob/main/images/605AF562-1631-4CA0-96F3-7A6D2509CADD.jpeg)

### Reflection

The servo code was given in the assignment, and you just had to add it to the end of the While True, so the assignment went pretty smoothly. I ignored the pin map, which was probably the disconnect. We were in the wrong pin because I thought the 7th pin down was GP7, but it was GP5, so once we had that figured out, the servo worked, and we were done.

## Crash Avoidance Part 1

### Assignment Description

Today Ellen and I created code to make an accelerometer that continuously reports x, y, and z acceleration values on our serial monitor.

### Evidence 

![Servo](https://github.com/gdaless20/Engineering_4_Notebook/blob/main/images/P1.gif)  

### Code

[Code](https://github.com/gdaless20/Engineering_4_Notebook/blob/main/raspberry-pi/Crashavoidance1)

### Wiring

[Wiring Diagram](https://github.com/gdaless20/Engineering_4_Notebook/blob/main/images/605AF562-1631-4CA0-96F3-7A6D2509CADD.jpeg)

### Reflection

This was fairly simple, once we had the right libraries moved into our circuitpy, we used the code from the assignment we were basically there.

## Crash Avoidance Part 2

### Assignment Description

We had to get an accelerometer working so that when it was 90 degrees an led would turn on.

### Evidence 

![Servo](https://github.com/gdaless20/Engineering_4_Notebook/blob/main/images/CA2.gif)  

### Code

[Code](https://github.com/gdaless20/Engineering_4_Notebook/blob/main/raspberry-pi/Crashavoidance2)

### Wiring

[Wiring Diagram](https://github.com/gdaless20/Engineering_4_Notebook/blob/main/images/605AF562-1631-4CA0-96F3-7A6D2509CADD.jpeg)

### Reflection

I messed up the led wiring and almost blew up an LED but after i fixed that issue our code worked well! We additionally had to retake our video a couple times because Ellen kept cussing in the video.

&nbsp;

## Media Test

Your readme will have various images and gifs on it. Upload a test image and test gif to make sure you've got the process figured out. Pick whatever image and gif you want!

### Test Link
[slay](https://github.com/gdaless20/Engineering_4_Notebook/blob/main/test.py)
### Test Image
![Walter](images/breaking-bad-chemistry.gif)  
### Test GIF
![Green](images/download.png)  
