* * *
Для создания и запуска веб-приложения на Spring, вы можете следовать следующим шагам:

### 1. Настройка проекта

Создайте новый проект Maven или Gradle. Убедитесь, что у вас установлены необходимые зависимости в `pom.xml` (для Maven) или `build.gradle` (для Gradle). Пример зависимостей для Maven:

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-webmvc</artifactId>
        <version>5.3.10</version> <!-- Убедитесь, что версия актуальна -->
    </dependency>
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>4.0.1</version>
        <scope>provided</scope>
    </dependency>
    <dependency>
        <groupId>org.apache.tomcat.embed</groupId>
        <artifactId>tomcat-embed-core</artifactId>
        <version>9.0.50</version>
    </dependency>
    <!-- Добавьте другие зависимости, такие как Spring Data JPA, Hibernate и драйверы баз данных -->
</dependencies>
```

### 2. Создание конфигурации

Вы можете использовать JavaConfig для настройки вашего приложения. Создайте класс конфигурации:

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.EnableWebMvc;
import org.springframework.web.servlet.view.InternalResourceViewResolver;

@Configuration
@EnableWebMvc
@ComponentScan(basePackages = "com.example") // Укажите ваш базовый пакет
public class WebConfig {

    @Bean
    public InternalResourceViewResolver viewResolver() {
        InternalResourceViewResolver resolver = new InternalResourceViewResolver();
        resolver.setPrefix("/WEB-INF/views/");
        resolver.setSuffix(".jsp");
        return resolver;
    }
}
```

### 3. Создание контроллера

Создайте контроллер для обработки запросов:

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

### 4. Создание представления

Создайте JSP файл в папке `WEB-INF/views/`, например `home.jsp`:

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

### 5. Настройка `web.xml`

Настройте `DispatcherServlet` в вашем `web.xml`:

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

<context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>/WEB-INF/spring-config.xml</param-value> <!-- если используете XML -->
</context-param>

<listener>
    <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
</listener>
```

### 6. Запуск приложения

Теперь вы можете запустить ваше приложение на сервере, таком как Apache Tomcat. При переходе по адресу `http://localhost:8080/` вы должны увидеть сообщение "Hello, World!".

### Заключение

Следуя этим шагам, вы сможете создать и запустить простое веб-приложение на Spring с использованием MVC структуры. Вы можете расширять функциональность, добавляя больше контроллеров, моделей и представлений, а также интегрируя другие технологии, такие как Spring Data JPA для работы с базами данных.

* * *
#java  