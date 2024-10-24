Для построения MVC структуры с использованием Spring необходимо следовать определённой архитектуре, которая включает в себя создание контроллеров, моделей и представлений. Вот основные шаги для создания MVC приложения на Spring.

### 1. Настройка проекта

Создайте новый проект Spring, используя Maven или Gradle. Убедитесь, что у вас есть необходимые зависимости в `pom.xml` (для Maven) или `build.gradle` (для Gradle). Основные зависимости для Spring MVC:

```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.3.10</version> <!-- Убедитесь, что версия актуальна -->
</dependency>
```

### 2. Конфигурация `web.xml`

Вам нужно настроить `DispatcherServlet`, который будет действовать как фронт-контроллер для обработки всех запросов.

```xml
<servlet>
    <servlet-name>dispatcher</servlet-name>
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <load-on-startup>1</load-on-startup>
</servlet>

<servlet-mapping>
    <servlet-name>dispatcher</servlet-name>
    <url-pattern>/</url-pattern>
</servlet-mapping>
```

### 3. Создание контроллера

Создайте класс контроллера, который будет обрабатывать HTTP-запросы. Используйте аннотации `@Controller` и `@RequestMapping`.

```java
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HomeController {

    @GetMapping("/")
    public String home(Model model) {
        model.addAttribute("message", "Hello, World!");
        return "home"; // имя представления
    }
}
```

### 4. Настройка представлений

Создайте JSP или HTML файлы для представлений. Например, создайте файл `home.jsp` в папке `WEB-INF/views/`.

```jsp
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
    <title>Home Page</title>
</head>
<body>
    <h1>${message}</h1>
</body>
</html>
```

### 5. Настройка `InternalResourceViewResolver`

Добавьте конфигурацию для разрешения представлений в вашем конфигурационном файле Spring (например, в `dispatcher-servlet.xml`).

```xml
<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
    <property name="prefix" value="/WEB-INF/views/" />
    <property name="suffix" value=".jsp" />
</bean>

<context:component-scan base-package="com.example.controller" />
```

### 6. Запуск приложения

Теперь вы можете запустить ваше приложение. При переходе по адресу `http://localhost:8080/` вы должны увидеть сообщение "Hello, World!".

### Заключение

Эти шаги описывают базовую настройку MVC структуры с использованием Spring. Вы можете расширять функциональность, добавляя больше контроллеров, моделей и представлений, а также использовать другие аннотации Spring для обработки данных и управления транзакциями.

Citations:
[1] https://docs.spring.io/spring-framework/reference/web/webmvc/mvc-controller.html
[2] https://www.techferry.com/articles/spring-annotations.html
[3] https://www.javaguides.net/2018/11/spring-web-mvc-annotations.html
[4] https://www.digitalocean.com/community/tutorials/spring-mvc-example
[5] https://www.javacodegeeks.com/2019/05/spring-mvc-annotations.html
[6] https://www.javatpoint.com/spring-mvc-tutorial
[7] https://spring.io/guides/gs/serving-web-content/
[8] https://www.digitalocean.com/community/tutorials/spring-controller-spring-mvc-controller