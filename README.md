# Практическое задание

Протестировать задачу 2, 3, 4.

Первая задача приведена просто для контекста.

## Описание бота
Бот для повторения теории к экзамену

## Задача 1 (тестировать не надо)

Бот для прохождения тестов.
Пользователь отправляет первое сообщение командой /start. Бот приветствует пользователя и ждёт следующей команды. 
Когда поступает команда /test, то бот задаёт вопрос и ожидает ответа. Далее, когда ответ от пользователя получен, то со стороны бота приходит его оценка (верно/неверно)

*Пример:*    
User: /start  
Bot: Hello!  
User: /test  
Bot: [some question]  
User: [answer]    
Bot: Good job!   
Или   
Bot: Wrong answer.

## Задача 2

Реализовать алгоритм повторения тестов. Если пользователь неверно ответил на вопрос, то этот вопрос будет задан повторно для закрепления, когда тест будет пройден до конца, либо доступен по команде /repeat 

*Пример 1:* допустим, в тесте 2 вопроса, тогда  
User: /test  
Bot: [question1]    
User: [wrong answer]    
Bot: Ошибка, верный ответ: [верный ответ]    
User: /next  
Bot: [question2]    
User: [right answer]    
Bot: Верно!  
Bot: Вопросы закончились, если хотите выйти из режима теста введите /stop, иначе если хотите отработать вопросы с ошибкой, то введите /next  
User: /next  
Bot: [question1]    

User: [right answer]    
Bot: Верно! [вопрос удаляется из списка ошибочных]    
or  
User: [wrong answer]    
Bot: Ошибка! [оставляет вопрос в списке ошибочных]    

*Пример 2:*

Если пользователь после прохождения теста совершил ошибки и вышел из режима тестирования командой /stop, а позже решил отработать вопросы с ошибкой, то:  
 
User: /repeat  
Bot: [answer1]    

User: [right answer]    
Bot: Верно! [вопрос удаляется из списка ошибочных]    
or  
User: [wrong answer]    
Bot: Ошибка! [оставляет вопрос в списке ошибочных]    

*Пример 3:*  
Если при прохождении теста пользователем не было совершено ошибок или тест ещё не был пройден, то:  

User: /repeat  
Bot: Список вопросов для отработки пуст. Пройдите тест!  


## Задача 3

Возможность выбора учебного предмета и добавление кнопок для более удобного управления  
*Пример 1:*    
User: /start  
Bot: Привет! Давай выберем предмет  
[Список предметов в виде кнопок]    
    1. Математика (MATHS) 
    2. Английский язык (ENGLISH)
    3. Русский язык (RUSSIAN)
User: [нажимает на кнопку 1 (MATHS)]    
Bot: Вы выбрали предмет математика, хотите начать тест (/test)?  
User: [кнопка тест]  
Bot: Алгебра: [question1]  

Если пользователь захочет поменять предмет, то можно будет это сделать при помощи /back  
*Пример 2:*   
[user пользуется функционалом бота в выбранном разделе и решил его сменить]    
User: [кнопка назад (back)]    
Bot: [выдает сообщение и список предметов из примера 1]    


## Задача 4

Отправление пользователю сообщения-приглашения, если тот не пользовался функционалом бота фиксированное время с возможностью отказаться от рассылки уведомлений с помощью кнопки "Настройки"  

*Пример 1:*   
[пользователь в 23:37 совершил последнее действие и более не был активен]  
Bot: [через 24 часа] Вас давно не было видно. Хотите пройти тест? [кнопки с набором предметов и кнопка "меню"]  
  
*Пример 2:*  
User: /start  
Bot: Меню:  
[кнопки "настройки" и "выбор предмета"]  
User: [настройки]  
Bot: Хотите получать уведомления?  
[кнопки "да", "нет"]  
User: [да]  
Bot: Уведомления успешно включены [переход к меню]  

или  

User: /start  
Bot: Меню:  
[кнопки "настройки" и "выбор предмета"]  
User: [выбор предмета]  
Bot: Выберите предмет:  
[кнопки с названиями предметов и кнопка "меню"]

**Подсказка:**
Вам может пригодиться метод ru.urfu.TimerBehavior.setStandardDispatchTime()