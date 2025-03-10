# RabbitMQ Project 🐇

## Описание

Этот проект демонстрирует использование RabbitMQ в качестве брокера сообщений в приложении на Java Spring. Проект включает в себя примеры создания, отправки и получения сообщений через RabbitMQ.

## Основные функции 🛠️

- **Создание очередей**: Создание и управление очередями сообщений.
- **Отправка сообщений**: Отправка сообщений в очереди.
- **Получение сообщений**: Получение и обработка сообщений из очередей.
- **Настройка RabbitMQ**: Настройка и конфигурация RabbitMQ в Spring Boot приложении.

## Установка и запуск 🚀

### Требования ⚙️

- Java 21 или выше
- Maven 3.6.3 или выше
- RabbitMQ сервер
- Git

### Установка 📥

1. **Клонируйте репозиторий:**

    ```sh
    git clone https://github.com/DKAVrZoV65F/rabbitmq-project-1.git
    cd rabbitmq-project-1
    ```

2. **Установите зависимости:**

    ```sh
    mvn clean install
    ```

### Запуск🚀

1. **Запуск RabbitMQ сервера:**

    Убедитесь, что RabbitMQ сервер запущен на вашем компьютере или удаленном сервере.

2. **Запуск приложения:**

    ```sh
    mvn spring-boot:run
    ```

## Примеры использования

### Пример 1: Отправка сообщения

```java
// Пример кода на Java для отправки сообщения
import lombok.Setter;
import org.springframework.amqp.core.AmqpTemplate;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Service;

@Setter
@Service
public class MessageSender {

    @Value("${queue.name}")
    private String queueName;

    @Autowired
    private AmqpTemplate amqpTemplate;

    public void send(String message) {
        amqpTemplate.convertAndSend(queueName, message);
    }
}
```

### Пример 2: Получение сообщения

```java
// Пример кода на Java для получения сообщения
import lombok.extern.slf4j.Slf4j;
import org.springframework.amqp.rabbit.annotation.RabbitListener;
import org.springframework.stereotype.Service;

@Service
@Slf4j
public class RabbitReceiver {

    @RabbitListener(queues = {"FourthQueue"})
    public void receive(String message) {
        log.info((message + " - received from queue"));
    }
}
```
