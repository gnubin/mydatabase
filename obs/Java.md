* * *
1. [[Чем отличается объект от примитива? Какие типы данных в Java существуют?]]
2. [[В чем разница передачи параметров по ссылке и по значению?]]
3. [[Что такое JVM, JDK, JRE?]]
4. Зачем используют JVM?
5. [[Что такое bytecode?]]
6. [[Что такое стек?]]
7. [[Назовите все методы класса object.]]
8. [[Что такое конструкторы? Какие типы знаете?]]
9. [[Что такое аннотации в Java?]]
10. [[Классы обертки для примитивов и String? Зачем нужны? Как объединяются строки?]]
 11. [[Зачем нужны методы equals() и hashCode()?]]
 12. [[Из чего состоит класс? Что такое POJO в Java?]]
 13. [[Что такое массивы? Что такое коллекции, какие есть в Java? Разница ArrayList и LinkedList?]]
 14. [[Что такое HashMap? ]]
 15. [[4 принципа ООП? Приведите пример каждого из них]]
 16. [[Что такое дженерики?]]
 17. [[Что такое stream? Какие у него есть операторы?]]
 18. [[Что такое Hibernate? Зачем используется?]]
 19. [[Что такое Entity? Как поля класса мапятся на базу данных? Какие аннотации используются? Что такое кэш первого уровня?]]
 20. [[Зачем нужен Spring? Что такое MVC структура и REST?]]
 21. [[Основные аннотации в спринге?]]
 22. [[Как построить mvc структуру с помощью спринг?]]
 23. [[Как создать и запустить веб-приложение на Spring?]]
 24. [[Что такое JSON? Его структура?]]
 25. [[Работа с файлом application.yml? Зачем и для чего?]]

[[темы на потом]]

### Optional\<T\>
- Либо значение (не null), либо его отсутствие
- Optional.of(obj)
- Optional.ofNullable(obj)
- Optional.empty(obj)

```java
static Optional<Integer> toInteger(String opt) {
	try {
		return Optional.of(Integer.valueOf(opt));
	}
	catch (NumberFormatException ex) {
		return Optional.empty();
	}
}
```
 [[Optional<T> methods]]

### Stream API (java.util.stream)
- поток однотипных данных
- источник создаёт ленивый стрим
- промежуточные операции описывают рецепт обработки, но ничего не делают
- вся работа производится при вызове терминальной операции
- может потребить не все элементы
- может быть бесконечным и завершиться за конечное время

Специализации
- java.util.stream.Stream
- java.util.stream.IntStream
- java.util.stream.LongStream
- java.util.stream.DoubleStream

Источники
- Strem.empty()
- Stream.of(x, y, z)
- Stream.generate(Math::random)
- Stream.iterate(val, x -> x+1)
- collection.stream
- Arrays.stream(array) (int/long/double/Object)
- Random.ints()
- String.chars()
- Pattern.splitAsStream()

Промежуточные операции (intermediate)
- map (mapToInt/mapToLong/mapToDouble/mapToObj)
- filter
- flatMap (flatMapToInt/flatMapToLong/flatMapToDouble)
- mapMulti (mapMultiToInt/mapMultiToLong/mapMultiToDouble) (java 16)
- distinct
- sorted
- limit
- skip
- peek
- takeWhile
- dropWhile
- boxed/asLongStream/asDoubleStream (примитивы)

Терминальные операции (terminal)
- count
- findFirst/findAny -> Optional
- anyMatch/noneMatch/allMatch
- forEach/forEachOrdered
- max/min -> Optional
- reduce
- collect
- toArray
- toList
- sum/average/summaryStatistics (Примитивы)


### Collector
- Рецепт терминальной опирации (способ комьинирования элементов в едушое целое)
- Предопределёные коллекторы в классе Collectors
- Некоторые коллекторы можно комбинировать
- Можно написать свой коллектор с нуля 
Collectors
- toList()
- toSet
- toCollection(supplier)
- toMap(KeyMapper, valueMapper\[, merger\[, mapSuplplier]])
- joining(\[separator\[,prefix, suffix]])
- groupingBy(classifier\[\[m mapSupplier], downstreem])
- partitioningBy(predicate\[, downstreem])
- 

### Ввод - вывод
Потоковый ввод вывод
- inputStream - читать байты
- OutputStream - писать байты
- Reader -читать символы
- Writer - писать символы

#### inputStream
- int read() -> -1 или 0..255
- long skip(long n)
- int available() количество байт, доступных без блокировки
- void mark(int readlimit)
- void reset()
- boolean markSupported()

java.io.File (классика)
-

java.nio.file.Path\/Paths.Files

Path (Comparable)
Files

### Многопоточность

Доступ к разделяемую ресурсу
- Блокировка (mutec, mutual exclusion)
- Неблокирующий доступ:
	- Lock-free: гарантируется общий прогресс
	- Wait-free: гарантируется прогресс в каждом потоке
Блокирующий доступ
- Для блокировки испольщуется монитор или лок
- Один и тот же ресурс должен блокироваться одним и тем же монитором
- Блокировать надо как чтение так и запись

synhronized
- synhronized(obj){...}: монитор - obj
- synhronized void method():{};

потоконебезопастные коллекции


java memory model

Атормарность

правила happens before

volatile

singleton
 























* * *
#java