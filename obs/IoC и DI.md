### [[Bean scope]]
### [[Life cycle]]

***
## Inversion of Control
### Основные функции, которые выполняет Spring Container:
- IоС — инверсия управления - это создание и управление объектами
	IoC — аутсорсинг создания и управления объектами. Т.е. передача программистом прав на создание и управление объектами Spring-y.

Spring Веаn -  это объект, который создаётся и управляется Spring Container
### Способы конфигурации Spring Container:
- XML file (устаревший способ)
- Annotations + XML file (современный способ)
- Java code (современный способ)

Конфигурация XML файла:
```java
ClassPathXmlApplicationContext context =  
        new ClassPathXmlApplicationContext("applicationContext.xml");
///Создание контекста
```
```xml
<bean id = "myPet"  
      class = "com.mytest.introduction.Dog">  
</bean>
```
<bean id = "myPet"
class —
" ioc . Cat" >
</bean>
- id - идентификатор бина
- class - полное имя класса
## Dependency lnjection
- DI — Dependency lnjection- это внедрение зависимостей
	Dl — аутсорсинг добавления/внедрения зависимостей. Он делает объекты нашего приложения слабо зависимыми друг от друга. 
### Способы внедрения зависимостей:
- С помощью конструктора
```xml
<bean id = "myPerson"  
      class="com.mytest.introduction.Person">  
    <constructor-arg ref="myPet"/>  
</bean>
```
- С помощью сеттеров
```xml
<bean id = "myPerson"  
      class="com.mytest.introduction.Person">  
    <property name="pet" ref="myPet"/>  
    <property name="name" value="Babich"/>  
	<property name="age" value="22"/>
	<property name="age" value="${person.age}"/> //через file.properties
</bean>

/// Указание файла
<context:property-placeholder location="classpath:myApp.properties"/>
```


- @Autowired
	- В конструкторе
		```java
@Autowired  
public Person(Pet pet) {  
this.pet = pet;  
}
```
	- В сеттере (в любом методе)
```java
@Autowired  
public void setPet(Pet pet) {  
    System.out.println("Class Person: setPet");  
    this.pet = pet;  
}
```
- Для поля

### Конфигурация при помощи аннотации

Аннотации - это метаданные, которые нужны для передачи определенной информации.
```xml
<context:component-scan base-package="com.mytest.introduction"/>
```

@Component("beanId") - создает бин

Процесс состоит из 2 этапов:
1. Сканирование классов и поиск аннотаций @Component
2. Создание (регистрация) бина в Spring Container

@Autowired
 \- внедряет зависимости  
 Процесс внедрения зависимостей:
 1. Сканирование пакета, поиск классов с аннотацией @Component
 2. При наличии аннотации @Autowired начинается поиск по типу бина

 Можно использовать в:
 - конструкторе
 - сеттер
 - поле

@Qualifire - указывает конкретный бин когда их несколько
- для конструктора пишется как параметр


@Value - внедряет значение полю (напрямую или через file.properties)
@Scope - задает scope для бина
@PostConstruct - метод выполняется после создания бина
@PreDestroy - метод выполняется после закрытия контекста

@Configuration - указывает что класс конфиг 
@ComponentScan("путь к файлу") - указываем какой пакет сканировать
@PropertySource("путь к файлу") - указывает на file.properties

@Bean - создает бин в конфиг классе




***
#java #spring 

