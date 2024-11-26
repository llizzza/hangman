# Viseliza
Game
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
