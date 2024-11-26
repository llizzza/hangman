# Viseliza
Game
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
