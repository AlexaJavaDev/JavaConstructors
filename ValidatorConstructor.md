# Валидатор пароля: конструктор и методы проверки

Это третий пример по конструкторам.  
Я создаю класс `Validator`, который принимает пароль и проверяет его на длину и наличие цифр.

---

## Код

```java
class Validator {
    String password;

    public Validator(String password) {
        this.password = password;
    }

    public void setPassword(String p) {
        this.password = p;
    }

    public String getPassword() {
        return password + " " + isValid() + " " + hashDigit();
    }

    public boolean isValid() {
        return password.length() > 8;
    }

    public boolean hashDigit() {
        for (int i = 0; i < password.length(); i++) {
            if (Character.isDigit(password.charAt(i))) {
                return true;
            }
        }
        return false;
    }
}
```
Класс ValidatorMain (создание объектов и проверка)
```java
public class ValidatorMain {
    public static void main(String[] args) {
        Validator val1 = new Validator("qwerty");
        Validator val2 = new Validator("secure1234");
        val1.isValid();
        val1.hashDigit();
        System.out.println(val1.getPassword());

        val2.isValid();
        val2.hashDigit();
        System.out.println(val2.getPassword());
    }
}
```
**Вывод в консоли**
```
qwerty false false
secure1234 true true
```
**Как это работает**
1. Конструктор:
`Validator(String password)` — принимает пароль и сохраняет его в поле
2. Методы:
- `isValid()` — проверяет, что длина пароля больше 8 символов  
- `hashDigit()` — проверяет, есть ли в пароле хотя бы одна цифра
- `getPassword()` — возвращает строку с паролем и результатами проверок
3. Цикл в `hashDigit()`:
- Проходит по каждому символу пароля
- `Character.isDigit()` — проверяет, является ли символ цифрой
- Если нашлась цифра — сразу возвращает `true`
- Если цифр нет — возвращает `false`

| Student | Car | Validator |
|---------|-----|-----------|
| 2 параметра | 3 параметра | 1 параметр |
| Метод вывода | Метод вывода | Методы проверки + вывод |
| Простое форматирование | Простое форматирование | Возвращает несколько значений в одной строке |

---

### Мои заметки
- В конструктор можно передавать не только данные, но и сразу начинать их обрабатывать
- `getPassword()` — возвращает не только пароль, но и результаты проверок
- `hashDigit()` — хороший пример метода, который проверяет символы в строке
- `Character.isDigit()` — полезный метод для проверки цифр

---

⭐ Теперь я умею создавать конструкторы с проверками и методы для валидации данных.
