import turtle
# Настройка Turtle
turtle.speed(0)
turtle.hideturtle() #скрываем черепаху
turtle.bgcolor("white")
def draw_hangman(attempts_left):
    turtle.penup()  # Поднимаем перо, чтобы переместить черепаху
    turtle.goto(-150, -100)  # Позиционируем черепаху для рисования
    turtle.pensize(5)
    # Рисуем виселицу
    if attempts_left == 6:
        turtle.pendown()
        turtle.forward(200)  # Перекладина
        turtle.left(90)
        turtle.forward(300)  # Столб
        turtle.left(90)
        turtle.forward(100)  # Основание
        turtle.left(90)
        turtle.forward(50)
        turtle.penup()

   # Рисуем части тела по мере уменьшения попыток
    if attempts_left == 5:
        # Голова
        turtle.goto(-50, 100)
        turtle.setheading(0)
        turtle.pendown()
        turtle.circle(25)
        turtle.penup()

    if attempts_left == 4:
        # Тело
        turtle.goto(-50, 100)
        turtle.setheading(270)
        turtle.pendown()
        turtle.forward(100)
        turtle.penup()

    if attempts_left == 3:
        # Правая рука
        turtle.goto(-50, 75)
        turtle.setheading(45)
        turtle.pendown()
        turtle.forward(50)
        turtle.penup()

    if attempts_left == 2:
        # Левая рука
        turtle.goto(-50, 75)
        turtle.setheading(135)
        turtle.pendown()
        turtle.forward(50)
        turtle.penup()

    if attempts_left == 1:
        # Правая нога
        turtle.goto(-50, 0)
        turtle.setheading(225)
        turtle.pendown()
        turtle.forward(50)
        turtle.penup()

    if attempts_left == 0:
        # Левая нога
        turtle.goto(-50, 0)
        turtle.setheading(315)
        turtle.pendown()
        turtle.forward(50)
        turtle.penup()
        #GAME OVER
        turtle.bgcolor("black")  # Черный фон
        turtle.color("red")  # Красный цвет текста
        turtle.write("GAME OVER", align="center", font=("Arial", 24, "normal")) # Пишем "GAME OVER" в центре экрана
        turtle.done()
