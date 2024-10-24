HashMap в Java — это структура данных, которая позволяет хранить и быстро извлекать данные в виде пар "ключ-значение". Основные характеристики и функциональность HashMap включают:

## Основные характеристики HashMap

1. **Хранение пар "ключ-значение"**:
   - HashMap использует уникальные ключи для сопоставления с определенными значениями. Например, можно использовать строку в качестве ключа и целое число в качестве значения: `HashMap<String, Integer>`.

2. **Отсутствие порядка**:
   - HashMap не гарантирует порядок хранения элементов. При итерации по элементам порядок может отличаться от порядка их добавления.

3. **Допустимость null**:
   - HashMap допускает один null-ключ и любое количество null-значений.

4. **Не синхронизирован**:
   - HashMap не является потокобезопасным, что означает, что его следует использовать с осторожностью в многопоточных средах.

5. **Эффективность**:
   - Операции добавления, удаления и поиска выполняются за среднее время O(1), благодаря использованию хеширования.

## Основные методы HashMap

- **`put(key, value)`**: добавляет пару "ключ-значение" в HashMap.
- **`get(key)`**: возвращает значение, связанное с указанным ключом.
- **`remove(key)`**: удаляет пару по указанному ключу.
- **`size()`**: возвращает количество элементов в HashMap.
- **`keySet()`**: возвращает набор всех ключей.
- **`values()`**: возвращает коллекцию всех значений.

## Пример использования HashMap

```java
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        HashMap<String, String> capitalCities = new HashMap<>();
        
        // Добавление элементов
        capitalCities.put("England", "London");
        capitalCities.put("Germany", "Berlin");
        capitalCities.put("Norway", "Oslo");
        
        // Получение значения по ключу
        String capitalOfEngland = capitalCities.get("England");
        System.out.println("Capital of England: " + capitalOfEngland);
        
        // Удаление элемента
        capitalCities.remove("Germany");
        
        // Итерация по ключам
        for (String country : capitalCities.keySet()) {
            System.out.println("Country: " + country + ", Capital: " + capitalCities.get(country));
        }
    }
}
```

В этом примере создается `HashMap`, который хранит названия стран и их столицы. Показаны основные операции добавления, получения и удаления элементов.

Таким образом, HashMap является мощным инструментом для работы с данными в Java, обеспечивая эффективное хранение и доступ к данным по ключам.

Citations:
[1] https://www.w3schools.com/java/java_hashmap.asp
[2] https://www.javatpoint.com/java-hashmap
[3] https://www.programiz.com/java-programming/hashmap
[4] https://www.digitalocean.com/community/tutorials/java-hashmap
[5] https://dev.to/suresh02/understanding-basics-of-hashmaps-in-java-10mj
[6] https://www.freecodecamp.org/news/how-java-hashmaps-work-internal-mechanics-explained/
[7] https://www.youtube.com/watch?v=H62Jfv1DJlU
[8] https://foxminded.ua/ru/kollekcii-java/