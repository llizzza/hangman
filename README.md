# Viseliza
Game
import random
import turtle

# Список слов для игры
words = ['собака', 'кошка', 'машина', 'птица', 'дерево', 'река', 'телевизор', 'книга', 'учитель']

# Настройка Turtle
turtle.speed(0)
turtle.hideturtle() #скрываем черепаху
turtle.bgcolor("white")

# Функция для рисования виселицы
def draw_hangman(attempts_left):
    turtle.penup()  # Поднимаем перо, чтобы переместить черепаху
    turtle.goto(-150, -100)  # Позиционируем черепаху для рисования
    turtle.pensize(5)
    # Рисуем виселицу
    if attempts_left == 6:
        turtle.pendown()

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

# Функция для игры в виселицу
def hangman():
    # Выбираем случайное слово
    word = random.choice(words)
    # Создаем строку для отображения прогресса игрока(в зависимости от длины слова)
    hidden_word = ['_'] * len(word)#сколько букв столько черточек
    guessed_letters = set()  # Множество для хранения угаданных букв
    attempts = 6  # Количество попыток

    print("Добро пожаловать в игру 'Виселица'!")
    print("Угадайте слово!")

    # Рисуем виселицу
    draw_hangman(attempts)

    #Цикл игры
    while attempts > 0:
        # Показываем текущее состояние слова
        print("Слово: " + ' '.join(hidden_word))
        print(f"Осталось попыток: {attempts}")
        print("Угаданные буквы:", ', '.join(sorted(guessed_letters)))

        # Просим пользователя ввести букву
        guess = input("Введите букву: ").lower()

        # Проверяем, что введена только одна буква и это буква из русского алфавита
        if len(guess) != 1 or not guess.isalpha() or guess not in 'абвгдеёжзийклмнопрстуфхцчшщыэюя':
            print("Пожалуйста, введите одну букву русского алфавита.")
            continue

        # Проверяем, не была ли буква уже угадана
        if guess in guessed_letters:
            print("Вы уже угадали эту букву.")
            continue

        # Добавляем букву в множество угаданных букв
        guessed_letters.add(guess)

        # Если буква есть в слове, обновляем скрытое слово
        if guess in word:
            for i in range(len(word)):
                if word[i] == guess:
                    hidden_word[i] = guess
            print("Правильно!")
        else:
            attempts -= 1
            print("Неправильно!")

        # Рисуем виселицу с учётом оставшихся попыток
        draw_hangman(attempts)

        # Проверяем, выиграл ли игрок(Если в скрытом слове больше нет подчеркиваний, значит, игрок угадал слово.)
        if '_' not in hidden_word:
            print("Поздравляю! Вы угадали слово:", word)
            break
    else:
        print("Вы проиграли. Загаданное слово было:", word)

    turtle.done()  # Завершаем рисование

# Запуск игры
hangman()
