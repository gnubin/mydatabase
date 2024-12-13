Класс `Optional<T>` в Java был введен в версии 8 для упрощения обработки значений, которые могут отсутствовать (т.е. для предотвращения `NullPointerException`). Он предоставляет несколько методов, которые позволяют удобно работать с такими значениями. Вот основные методы класса `Optional<T>`:

## Основные методы класса `Optional<T>`

1. **`static <T> Optional<T> empty()`**:
   - Возвращает пустой экземпляр `Optional`, который не содержит значения.
   ```java
   Optional<String> emptyOptional = Optional.empty();
   ```

2. **`static <T> Optional<T> of(T value)`**:
   - Возвращает `Optional`, содержащий заданное ненулевое значение. Если значение равно `null`, выбрасывается `NullPointerException`.
   ```java
   Optional<String> nonNullOptional = Optional.of("Hello");
   ```

3. **`static <T> Optional<T> ofNullable(T value)`**:
   - Возвращает `Optional`, содержащий заданное значение, если оно ненулевое; в противном случае возвращает пустой `Optional`.
   ```java
   Optional<String> nullableOptional = Optional.ofNullable(null); // Вернет пустой Optional
   ```

4. **`boolean isPresent()`**:
   - Возвращает `true`, если значение присутствует, и `false`, если отсутствует.
   ```java
   boolean hasValue = optional.isPresent();
   ```

5. **`void ifPresent(Consumer<? super T> action)`**:
   - Выполняет заданное действие, если значение присутствует.
   ```java
   optional.ifPresent(value -> System.out.println(value));
   ```

6. **`T get()`**:
   - Возвращает значение, если оно присутствует; в противном случае выбрасывает `NoSuchElementException`. Рекомендуется использовать этот метод только после проверки наличия значения.
   ```java
   String value = optional.get();
   ```

7. **`T orElse(T other)`**:
   - Возвращает значение, если оно присутствует; в противном случае возвращает заданное значение по умолчанию.
   ```java
   String value = optional.orElse("Default Value");
   ```

8. **`T orElseGet(Supplier<? extends T> other)`**:
   - Возвращает значение, если оно присутствует; в противном случае вызывает предоставленный метод и возвращает его результат.
   ```java
   String value = optional.orElseGet(() -> "Generated Value");
   ```

9. **`T orElseThrow(Supplier<? extends X> exceptionSupplier)`**:
   - Возвращает значение, если оно присутствует; в противном случае выбрасывает исключение, создаваемое предоставленным методом.
   ```java
   String value = optional.orElseThrow(() -> new IllegalArgumentException("Value not present"));
   ```

10. **`Optional<T> filter(Predicate<? super T> predicate)`**:
    - Если значение присутствует и соответствует заданному предикату, возвращает его; в противном случае возвращает пустой `Optional`.
    ```java
    Optional<String> filtered = optional.filter(value -> value.length() > 5);
    ```

11. **`<U> Optional<U> map(Function<? super T,? extends U> mapper)`**:
    - Если значение присутствует, применяет функцию к нему и возвращает результат в новом `Optional`; если отсутствует — возвращает пустой `Optional`.
    ```java
    Optional<Integer> length = optional.map(String::length);
    ```

12. **`<U> Optional<U> flatMap(Function<? super T,Optional<U>> mapper)`**:
    - Аналогично методу `map`, но ожидает, что функция вернет другой `Optional`.
    ```java
    Optional<String> upperCase = optional.flatMap(value -> Optional.of(value.toUpperCase()));
    ```

13. **`void ifPresentOrElse(Consumer<? super T> action, Runnable emptyAction)`**:
    - Выполняет действие, если значение присутствует; если отсутствует — выполняет другое действие.
    ```java
    optional.ifPresentOrElse(
        value -> System.out.println(value),
        () -> System.out.println("Value not present")
    );
    ```

Эти методы делают работу с потенциально отсутствующими значениями более безопасной и удобной, уменьшая вероятность возникновения ошибок из-за отсутствия проверки на null.
