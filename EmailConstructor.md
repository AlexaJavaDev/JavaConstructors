# Email: конструктор и работа с доменом

Это четвёртый пример по конструкторам.  
Я создаю класс `Email`, который принимает адрес электронной почты и проверяет его на валидность, а также извлекает домен.

---

## Код

```java
class Email {
    String email;

    public Email(String email) {
        this.email = email;
    }

    public void setEmail(String e) {
        this.email = e;
    }

    public String getEmail() {
        return email + " " + getDomain() + " " + isValid();
    }

    public boolean isValid() {
        return email.contains("@") && email.contains(".");
    }

    public String getDomain() {
        return email.substring(email.indexOf("@") + 1);
    }
}
```
Класс EmailMain (создание объектов и проверка)
```java
public class EmailMain {
    public static void main(String[] args) {
        Email one = new Email("test@mail.ru");
        Email two = new Email("bad-email");
        System.out.println(one.getEmail());
        System.out.println(two.getEmail());

        System.out.println("Проверка: ");
        System.out.println("До: " + one.getEmail());
        one.setEmail("new@java.com");
        System.out.println("После: " + one.getEmail());
    }
}
```
**Вывод в консоли**
```
test@mail.ru mail.ru true
bad-email  false
Проверка: 
До: test@mail.ru mail.ru true
После: new@java.com java.com true
```
**Как это работает**
1. Конструктор:
- `Email(String email)` — принимает `email` и сохраняет его в поле
2. Методы:
- `isValid()` — проверяет, что в `email` есть **"@"** и **"."**
- `getDomain()` — извлекает домен (всё после **"@"**)
- `getEmail()` — возвращает `email`, домен и результат проверки

### Важные моменты:
- `indexOf("@")` — находит позицию символа `@`
- `substring(index + 1)` — берёт всё, что после `@`
- Если `@` нет, `indexOf()` вернёт `-1`, и программа упадёт с ошибкой
- Это пример того, как нужно проверять данные перед использованием

---

## Опасное место в коде
В методе `getDomain()` есть проблема:

```java
email.substring(email.indexOf("@") + 1)
```
Если в `email` нет `@`, программа упадёт. Чтобы это исправить, нужно сначала проверить:

```java
public String getDomain() {
    if (email.contains("@")) {
        return email.substring(email.indexOf("@") + 1);
    }
    return "Нет домена";
}
```
---

| Student | Car | Validator | Email |
|---------|-----|-----------|-------|
| Вывод текста | Вывод текста | Проверка пароля | Извлечение домена |
| Простой метод | Простой метод | Поиск цифр | Поиск @ |
| Нет опасных мест | Нет опасных мест | Нет опасных мест | Есть опасное место |

---
## Мои заметки
- `contains()` — проверяет, есть ли подстрока в строке
- `indexOf()` — возвращает позицию подстроки (или -1, если не найдена)
- `substring()` — вырезает часть строки
- Всегда нужно проверять данные перед использованием `indexOf()` и `substring()`
- `getDomain()` — хороший пример метода, который обрабатывает строку

---

⭐ Теперь я умею извлекать домен из email и проверять его на валидность.
