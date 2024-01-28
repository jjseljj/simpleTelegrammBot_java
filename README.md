# TelegrammBot

TelegrammBot - это бот для Telegram, созданный с использованием фреймворка Spring
для демонстрации его возможностей. Бот предоставляет несколько команд для взаимодействия
с пользователями.

## Функциональность

- Регистрация пользователей
- Отправка сообщений всем зарегистрированным пользователям
- Встроенные команды, такие как /start, /help, /mydata

## Классы и методы

### TelegrammBot

Основной класс, наследуемый от `TelegramLongPollingBot`. Обрабатывает входящие обновления и реализует основную логику бота.

- `onUpdateReceived(Update update)`: Метод, вызываемый при получении нового обновления. Обрабатывает текстовые сообщения, команды и callback-запросы.
- `register(long chatId)`: Метод для регистрации пользователя.
- `registerUser(Message msg)`: Метод для регистрации пользователя в базе данных.
- `startCommandReceived(long chatId, String name)`: Метод, вызываемый при получении команды /start. Отправляет приветственное сообщение пользователю.
- `sendMassage(long chatId, String textToSend)`: Метод для отправки текстового сообщения с клавиатурой пользователю.
- `executeEditMessageText(String text, long chatId, long messageId)`: Метод для редактирования текста сообщения.
- `executeMessage(SendMessage message)`: Метод для выполнения операции отправки сообщения с обработкой исключений.
- `prepareAndMessage(long chatId, String textToSend)`: Метод для подготовки и отправки сообщения.
- `sendAds()`: Метод, вызываемый по расписанию, для отправки рекламных сообщений пользователям.

## Конфигурация и инициализация

### BotConfig

Класс, содержащий конфигурацию бота, такую как имя бота и токен.

## Репозитории

### AdsRepository

Интерфейс репозитория для взаимодействия с базой данных для объявлений.

### UserRepository

Интерфейс репозитория для взаимодействия с базой данных для пользователей.

## Расписание

`@Scheduled(cron = "* * * * * *")`: 
Аннотация для выполнения метода `sendAds()` по расписанию.

## Зависимости

- Java 17
- Spring Boot
- Lombok
- Библиотека TelegramBots для Java
- Spring Boot Starter Web
- Spring Boot Starter Test
- Spring Boot Starter Data JPA
- MySQL Connector/J
- JAXB API
- Библиотека Emoji для Java
- ...

## Запуск

Для успешного запуска проекта, выполните следующие шаги:

1. Убедитесь, что у вас установлена Java.

2. Склонируйте репозиторий:

    ```bash
    git clone https://github.com/jjseljj/simpleTelegrammBot_java.git
    ``` 

3. Перейдите в каталог проекта:

    ```bash
    cd ваш_репозиторий
    ```

4. Запустите сборку проекта с помощью Maven Wrapper:

    ```bash
    ./mvnw clean install
    ```

5. Заполните файл конфигурации `application.properties` или `application.yml`. Пример файла `application.yml`:

    ```yaml
    # application.yml

    spring:
      datasource:
        url: jdbc:mysql://localhost:3306/ваша_база_данных
        username: ваш_пользователь
        password: ваш_пароль
      jpa:
        hibernate:
          ddl-auto: update
        show-sql: true
    telegram:
      token: ваш_токен_бота
    ```

   Замените `ваша_база_данных`, `ваш_пользователь`, `ваш_пароль` и `ваш_токен_бота` на актуальные значения.

6. Запустите приложение:

    ```bash
    java -jar target/ваш-проект.jar
    ```

Теперь вы можете успешно запустить ваш Telegram бот. 
Замените все placeholder'ы на фактическую информацию вашего проекта.

