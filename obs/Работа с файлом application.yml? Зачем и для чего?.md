Файл `application.yml` в Spring Boot используется для хранения конфигурационных параметров приложения. Он позволяет задавать настройки, которые могут варьироваться в зависимости от среды (например, разработка, тестирование, продакшн) и упрощает управление этими настройками.

### Зачем нужен `application.yml`?

1. **Управление конфигурацией**: `application.yml` позволяет централизованно управлять настройками приложения, такими как параметры подключения к базе данных, порты сервера и другие свойства.

2. **Читаемость**: Формат YAML более удобочитаем по сравнению с традиционным форматом `.properties`. Он поддерживает иерархическую структуру, что делает конфигурацию более понятной.

3. **Поддержка профилей**: Spring Boot позволяет использовать разные файлы конфигурации для различных сред с помощью профилей. Например, вы можете создать `application-dev.yml` для разработки и `application-prod.yml` для продакшена.

4. **Использование переменных окружения**: В `application.yml` можно использовать переменные окружения, что позволяет гибко настраивать приложение без изменения кода. Например:
   ```yaml
   server:
     port: ${PORT:8080}
   ```
   Здесь переменная `${PORT}` будет использоваться, если она определена в окружении; в противном случае будет использовано значение по умолчанию — `8080`.

### Структура файла `application.yml`

Файл имеет иерархическую структуру, где параметры задаются в виде ключ-значение. Пример структуры:

```yaml
spring:
  application:
    name: my-app
  datasource:
    url: jdbc:mysql://localhost:3306/mydb
    username: user
    password: pass
  server:
    port: 8080
```

### Основные аннотации для работы с `application.yml`

1. **@Value**: Позволяет внедрять значения из конфигурационного файла непосредственно в поля классов.
   ```java
   @Value("${spring.application.name}")
   private String appName;
   ```

2. **@ConfigurationProperties**: Используется для группировки связанных параметров в один класс.
   ```java
   @ConfigurationProperties(prefix = "datasource")
   public class DataSourceConfig {
       private String url;
       private String username;
       private String password;
       // геттеры и сеттеры
   }
   ```

### Кэш первого уровня

Кэш первого уровня (или сессии) в Spring управляет состоянием объектов, загруженных из базы данных, на уровне текущей сессии. Это позволяет избежать повторных запросов к базе данных для уже загруженных объектов, что значительно повышает производительность.

### Заключение

Файл `application.yml` является важным инструментом для управления конфигурацией приложений на Spring Boot. Он упрощает процесс настройки и делает код более гибким и удобным для поддержки.

Citations:
[1] https://sky.pro/wiki/java/ispolzovanie-peremennykh-okruzheniya-v-fayle-application-yml/
[2] https://habr.com/ru/articles/740802/
[3] https://devmark.ru/article/spring-boot-config
[4] https://habr.com/ru/companies/otus/articles/576910/
[5] https://ru.stackoverflow.com/questions/758038/spring-boot-yml-%D0%BF%D1%80%D0%BE%D0%B8%D0%B7%D0%B2%D0%BE%D0%BB%D1%8C%D0%BD%D1%8B%D0%B5-%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B0%D1%86%D0%B8%D0%B8
[6] https://for-each.dev/lessons/b/-spring-boot-yaml-vs-properties
[7] https://www.uiscom.ru/blog/chto-takoe-yml-fayl-i-kak-ego-sozdat/
[8] https://www.youtube.com/watch?v=A4iCQYoI4Cs