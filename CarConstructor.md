# Машина: конструктор с тремя параметрами

Это второй пример по конструкторам.  
Я создаю класс `Car` с конструктором, который принимает марку, модель и год выпуска, и методом `getInfo()` для вывода информации.

---

## Код

```java
class Car {
    String brand;
    String model;
    int year;

    public Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }

    public String getInfo() {
        return brand + " - " + model + " (" + year + ")";
    }
}
```
Класс CarMain (создание объектов)
```java
public class CarMain {
    public static void main(String[] args) {
        Car car1 = new Car("Toyota", "Camry", 2020);
        Car car2 = new Car("BMW", "X5", 2022);
        Car car3 = new Car("Honda", "Civic", 2019);
        System.out.println(car1.getInfo());
        System.out.println(car2.getInfo());
        System.out.println(car3.getInfo());
    }
}
```
**Вывод в консоли**
```
Toyota - Camry (2020)
BMW - X5 (2022)
Honda - Civic (2019)
```
**Как это работает**
1. Конструктор принимает три параметра: `brand`, `model`, `year`
2. `this.brand = brand` — сохраняет переданное значение в поле объекта
3. `getInfo()` — возвращает строку с информацией о машине

| Student | Car |
|---------|-----|
| 2 параметра (name, age) | 3 параметра (brand, model, year) |
| Метод `introd()` | Метод `getInfo()` |
| Вывод с текстом | Вывод в формате "марка - модель (год)" |

---

## Мои заметки
- Конструктор может принимать любое количество параметров
- В конструкторе можно инициализировать все поля объекта
- `getInfo()` — универсальное имя для метода, который возвращает информацию об объекте
- Конструктор упрощает создание множества объектов с разными данными

---

⭐ Теперь я умею создавать конструкторы с тремя параметрами и форматировать вывод информации о машине.
