# StarWars-Game-using-Python

```
Editor: Pavan Ananth Sharma
co-contributor: Oliver Shmikele & Siddarth Raj
```
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Introduction

In this turtle game tutorial, we will be learning how to build a simple star wars game with python turtle, where we will be able to destroy starships.For this game, we will use the turtle, random, and the math module. By the end of this tutorial, you will clear all your concepts regarding python turtle from basics to advanced topics. Many advanced turtle “methods” are used for this game too.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 1:

Import the modules “turtle,” “math,” and “random.” Set a turtle screen in the “window” variable. Set the screen up as “width=600, height=600”. Then, declare the background color of the screens as black.
If you do not have the turtle module then use then python package manager and install it code: ``` pip install turtle ```
So the code will look similar:

``` python
#importing important modules 
import turtle
import math
import random

#initilise the window screen
window = turtle.Screen()
#setting the width and height(2D)of the game screen
window.setup(width=600, height=600)
#set the title of the game
window.title("Star Wars Game")
#setting the backround color of the screen
window.bgcolor("black")
```
Set the tracer to 0. Likewise, set the vertices as “(0,15),(-15,0),(-18,5),(-18,-5),(0,0),(18,-5),(18, 5),(15, 0)” in the “vertex” variable. Similarly, register the shape as “player” and the vertex variable from above.

``` python
window.tracer(0)
vertex = ((0,15),(-15,0),(-18,5),(-18,-5),(0,0),(18,-5),(18, 5),(15, 0))
window.register_shape("player", vertex)
asVertex = ((0, 10), (5, 7), (3,3), (10,0), (7, 4), (8, -6), (0, -10), (-5, -5), (-7, -7), (-10, 0), (-5, 4), (-1, 8))
window.register_shape("chattan", asVertex)
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 2:
Inherit the “Turtle” from the “turtle” module into a class named “SharMAX”. Initialize with the function __init__(self). Then, set the initializer as the turtle. Likewise, set the speed to 0 and pick the pen up as we are not ready to draw.

``` python
class SharMAX(turtle.Turtle):
    def __init__(self):
        turtle.Turtle.__init__(self)

        self.speed(0)
        self.penup()
```

Coming out of the function, create a function(ankur1) with the parameters “t1” and “t2”. Inside this function, set the current x coordinate into the variable x1 and the y coordinate into y1. Then, do the same with the t2 and “x2”, “y2”. Similarly, set the arctangent of “y1-y2” and “x1-x2” into “taauko” with the math module. Again, multiply the “taauko” with “180.0 / 3.14159” and return “taauko”.

``` python
def SharMAX1(t1, t2):
    x1 = t1.xcor()
    y1 = t1.ycor()
    
    x2 = t2.xcor()
    y2 = t2.ycor()
    
    taauko = math.atan2(y1 - y2, x1 - x2)
    taauko = taauko * 180.0 / 3.14159
    
    return taauko
```
Create an object named “player” from the SharMAX() class. Then, set the color to white and the shape to “player”. Declare the score of the player object to 0.

``` python
player = SharMAX()
player.color("white")
player.shape("player")
player.score = 0
```
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 3:

Create an empty list named “missiles”. Then, create a for loop with the range of 3. Inside this loop, create an object from SharMAX() named “missile”. Likewise, set the color of the missile to red, shape as an arrow. Then, declare the speed of the missile to 1 and state it as “ready”. Similarly, hide the turtle and append the current missile into the “missiles” list.

``` python
missiles = []
for _ in range(3):
    missile = SharMAX()
    missile.color("red")
    missile.shape("arrow")
    missile.speed = 1
    missile.state = "ready"
    missile.hideturtle()
    missiles.append(missile)
```

Now, coming out of the loop, create another object from SharMAX() as “pen”. Set the color of this turtle object as white and hide the turtle. Then, position the turtle to (0, 250). After that, we will display the score with the code below.

``` python
pen = SharMAX()
pen.color("white")
pen.hideturtle()
pen.goto(0, 250)
pen.write("Score: 0", False, align = "center", font = ("Arial", 24, "normal"))
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

>Step 4:

Create an empty list with the variable “chattans”.These will be used as asteroids. Then, create a for loop with the range of 5. Inside this loop, create an object from SharMAX() as “chattan” and set the color of the chattan as brown and shape as an arrow. Now, we will set the speed of the chattan as a random integer from the following code.

``` python
chattans = []

for _ in range(5):   
    chattan = SharMAX()
    chattan.color("brown")
    chattan.shape("arrow")
```

Inside the loop itself, position the chattan to the origin. Set another variable named “taauko” and a random integer value from 0 to 260. Again, create another variable “distance” and set the random value as an integer from 300 to 400. Likewise, set the heading of the chattan as “taauko” and move the chattan forward at the “distance” unit. Similarly, add the current value of “chattan” into the list “chattans”

``` python
chattan.speed  = random.randint(2, 3)/50
    chattan.goto(0, 0)
    taauko = random.randint(0, 260)
    distance = random.randint(300, 400)
    chattan.setheading(taauko)
    chattan.fd(distance)
    chattan.setheading(ankur1(player, chattan))
    chattans.append(chattan)
```
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Defense functions :

* Here, create a function baanya() where you will set the turtle left at an angle of 20 degrees.
Likewise, create another function daanya() where the turtle will be set right at an angle of 20 degrees.

``` python
def baanya():
    player.lt(20)
    
def daanya():
    player.rt(20)
```
* Likewise, create a function fire_missile(). Inside this function, create a for loop which will loop through the “missiles” list and set the values in “missile”. Again, inside this function check if the state of the missile “ready”. Then, position the missile to (0, 0) and show the turtle which was hidden before with the method hideturtle(). Set the heading of the missile the same as the “player” turtle. Change the state of the missile to “fire” and break the loop.

``` python
def fire_missile():
    for missile in missiles:
        if missile.state == "ready":
            missile.goto(0, 0)
            missile.showturtle()
            missile.setheading(player.heading())
            missile.state = "fire"
            break
```
* After the functions, call the listen() method and call the onkey method on the “Left” key with the baanya function. Do the same with the other two functions as in the code below.

``` python
window.listen()
window.onkey(baanya, "Left")
window.onkey(daanya, "Right")
window.onkey(fire_missile, "space")
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Functions of the code - Part 1:

* Here, create an infinite loop of “while True:”. Now, update the turtle GUI and position the player turtle to the origin.

``` python
sakkyo = False
while True:

    window.update()
    player.goto(0, 0)
```

* Then, create a for loop which will loop through the “missiles” list. Inside this list, check if the state if the current value of “missiles” is “fire” and move the missile forward at a distance equal to the speed. Again, check if “missile.xcor() > 300 or missile.xcor() < -300 or missile.ycor() > 300 or missile.ycor() < -300”. If so, hide the turtle and set the state to “ready”.

``` python
for missile in missiles:
        if missile.state == "fire":
            missile.fd(missile.speed)
        
        if missile.xcor() > 300 or missile.xcor() < -300 or missile.ycor() > 300 or missile.ycor() < -300:
            missile.hideturtle()
            missile.state = "ready"
```

* Create another for loop that will loop through the “chattans” list. Here, move the turtle forward at a distance same as the speed of the current value of “chattan”

``` python
    for chattan in chattans:    
        chattan.fd(chattan.speed)
```

* Again, inside this list, create another loop that will loop through the “missiles” list. Here, see if the distance from chattan to the missile is less than 20.
If so, then declare a variable named “taauko” and “distance” and set the value as a random integer from 0 to 260 and a random integer from 600 to 800 respectively. Set the heading of the “chattan to “taauko” and move it forward at a distance of “distance”.

``` python
for missile in missiles:
            if chattan.distance(missile) < 20:
                taauko = random.randint(0, 260)
                distance = random.randint(600, 800)
                chattan.setheading(taauko)
                chattan.fd(distance)
```

* Again, set the heading of the “chattan” turtle as the function ankur1() and send the parameters “player1, chattan”. Likewise, change the speed of the “chattan” where 0.01 will be added as in the code below.

``` python
    chattan.setheading(SharMAX1(player, chattan))
                chattan.speed += 0.01
```

* Now, position the “missile” turtle to (600, 600), hide the turtle and set the state of the “missile” to “ready”.

``` python
                missile.goto(600, 600)
                missile.hideturtle()
                missile.state = "ready"
```

* After that, add 10 to the “player.score” and clear the turtle pen. Now, write the score on the screen with the code below.

``` python
                player.score += 10
                pen.clear()
                pen.write("Score: {}".format(player.score), False, align = "center", font = ("Arial", 24, "normal"))
```

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Functions of the code - Part 2:

* Continuing, check if the distance from “chattan” to the “player” is less than 20. If so, declare a variable “taauko” and set the value as a random integer from 0 to 260. Again, declare another variable “distance” and set the value as a random integer from 600 to 800.

``` python 
if chattan.distance(player) < 20:
            taauko = random.randint(0, 260)
            distance = random.randint(600, 800)
```

* Now, set the heading of the “chattan” as “taauko” and move the turtle forward at a unit of “distance” from above.

``` python
            chattan.setheading(taauko)
            chattan.fd(distance)
```
* Likewise, again, set the heading of the chattan as the function SharMAX1() and send the arguments “player1, chattan”. Similarly, add 0.005 to the speed of the “chattan”. Accordingly, declare a variable “sakkyo” and set the value as “True”.

``` python
            chattan.setheading(SharMAX(player, chattan))
            chattan.speed += 0.005
            sakkyo = True
```
* Then, decrease the score of the player by 30. and clear the pen. Again, write the score of the “player” with the code below.

``` python
            player.score -= 30
            pen.clear()
            pen.write("Score: {}".format(player.score), False, align = "center", font = ("Arial", 24, "normal"))
```

* Lastly, check if “sakkyo” is “True”. Here, hide all the turtles of “player” and missile. Now, create a for loop which will loop through the list “chattans” and hide all the turtles in that loop. Clear the pen and break the loop. Close the GUI with the mainloop().

``` python
if sakkyo == True:
        player.hideturtle()
        missile.hideturtle()
        for a in chattans:
            a.hideturtle()
        pen.clear()
        break

window.mainloop()
```
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
>Credits : ```https://copyassignment.com/```

Lets hope you enjoyed this tutorial and please make sure you follow me on GitHub and also on my Instagram.

## Thankyou!!

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
