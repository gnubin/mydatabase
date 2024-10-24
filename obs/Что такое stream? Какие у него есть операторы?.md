Stream API в Java — это мощный инструмент, введенный в версии Java 8, который упрощает работу с коллекциями и позволяет выполнять операции над наборами данных в функциональном стиле. Потоки (streams) представляют собой последовательность элементов, которые могут быть обработаны различными операциями.

## Основные характеристики Stream API

- **Ленивые вычисления**: Операции над потоками не выполняются до тех пор, пока не будет вызвана терминальная операция.
- **Одноразовые**: Поток можно использовать только один раз; после завершения его нельзя повторно использовать.
- **Параллельная обработка**: Потоки могут быть обработаны параллельно, что позволяет улучшить производительность при работе с большими объемами данных.

## Операторы Stream API

Операторы Stream API делятся на два типа: **промежуточные** (intermediate) и **терминальные** (terminal).

### Промежуточные операторы
Промежуточные операторы обрабатывают элементы потока и возвращают новый поток. Они могут быть использованы последовательно для создания цепочки операций.

1. **filter(Predicate predicate)**: Фильтрует элементы потока по заданному условию.
   ```java
   List<String> filtered = list.stream()
                                .filter(s -> s.length() > 3)
                                .collect(Collectors.toList());
   ```

2. **map(Function mapper)**: Преобразует каждый элемент потока в другой объект.
   ```java
   List<Integer> lengths = list.stream()
                                .map(String::length)
                                .collect(Collectors.toList());
   ```

3. **distinct()**: Удаляет дубликаты из потока.
   ```java
   List<String> unique = list.stream()
                             .distinct()
                             .collect(Collectors.toList());
   ```

4. **sorted(Comparator comparator)**: Сортирует элементы потока.
   ```java
   List<String> sorted = list.stream()
                             .sorted()
                             .collect(Collectors.toList());
   ```

### Терминальные операторы
Терминальные операторы выполняют вычисления и возвращают результат, завершив работу потока.

1. **forEach(Consumer action)**: Применяет действие к каждому элементу потока.
   ```java
   list.stream().forEach(System.out::println);
   ```

2. **collect(Collector collector)**: Сбор элементов потока в коллекцию или другую структуру данных.
   ```java
   List<String> collected = list.stream()
                                 .collect(Collectors.toList());
   ```

3. **count()**: Возвращает количество элементов в потоке.
   ```java
   long count = list.stream().count();
   ```

4. **reduce(BinaryOperator accumulator)**: Сводит элементы потока к одному значению.
   ```java
   Optional<Integer> sum = numbers.stream()
                                   .reduce(Integer::sum);
   ```

5. **findFirst()**: Возвращает первый элемент потока, если он существует.
   ```java
   Optional<String> first = list.stream().findFirst();
   ```

## Заключение
Stream API предоставляет удобный и эффективный способ работы с данными в Java, позволяя разработчикам писать более чистый и читаемый код. Использование промежуточных и терминальных операторов позволяет легко обрабатывать данные, избегая громоздких циклов и условных конструкций.

Citations:
[1] https://struchkov.dev/blog/ru/java-stream-api/
[2] https://javarush.com/groups/posts/2203-stream-api
[3] https://metanit.com/java/tutorial/10.1.php
[4] https://devmark.ru/article/stream-api-terminal-opers
[5] https://annimon.com/article/2778
[6] https://javarush.com/groups/posts/3974-kofe-breyk-177-podrobnoe-rukovodstvo-po-java-stream-v-java-8
[7] https://habr.com/ru/articles/693666/
[8] https://devmark.ru/article/stream-api-intermediate-opers