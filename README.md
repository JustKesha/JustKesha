<!--
<h1> Hello ✌ Name's Ilya </h1>

📌 Based in Russia<br>
🎓 Just got my bachelor's degree<br>
📧 Contact me at: <a href="mailto:sazonovilya03@mail.ru">sazonovilya03@mail.ru</a> or in <a href="https://t.me/MangoAvocadoSalad">telegram</a><br>

<br>
<div>
  <img width="15px" src="images/smol.png" />
  <img alt="Back" src="https://skillicons.dev/icons?i=python,nodejs,git" />
  <img width="15px" src="images/smol.png" />
  <img alt="Front" src="https://skillicons.dev/icons?i=js,html,css,figma" />
  <img width="15px" src="images/smol.png" />
  <img alt="Game dev" src="https://skillicons.dev/icons?i=cs,lua,godot" />
</div>

<img alt="Contributions Snake" width="100%" style="background: transparent;" src="https://github.com/JustKesha/JustKesha/blob/output/github-contribution-grid-snake.svg" />

<div>
  <img width="15px" src="images/smol.png" />
  <a href="https://discord.gg/mh6ZwSSPcy"><img alt="Discord" height="24px" src="https://img.shields.io/badge/kesha__2293-5865F2?style=flat&logo=discord&logoColor=white" /></a>
  <img width="1px" src="images/smol.png" />
  <a href="https://t.me/MangoAvocadoSalad"><img alt="Telegram" height="24px" src="https://img.shields.io/badge/MangoAvocadoSalad-229ED9?style=flat&logo=telegram&logoColor=white" /></a>
  <img width="1px" src="images/smol.png" />
  <a href="mailto:sazonovilya03@mail.ru"><img alt="Email" height="24px" src="https://img.shields.io/badge/sazonovilya03%40mail.ru-d14836?style=flat&logo=gmail&logoColor=white" /></a>
</div>
-->

# Подготовка к защите лабораторной работы по Java (ООП)

## Содержание
1. [Введение в проект](#введение-в-проект)
2. [Основные концепции ООП в проекте](#основные-концепции-ооп-в-проекте)
3. [Архитектура классов](#архитектура-классов)
4. [Ключевые интерфейсы](#ключевые-интерфейсы)
5. [Реализации табулированных функций](#реализации-табулированных-функций)
6. [Математические функции](#математические-функции)
7. [Специальные алгоритмы](#специальные-алгоритмы)
8. [Тестирование](#тестирование)
9. [Работа с инструментами](#работа-с-инструментами)
10. [Вопросы по проекту](#вопросы-по-проекту)
11. [Вопросы по Java](#вопросы-по-java)
12. [Ответы на вопросы](#краткие-ответы-для-подготовки)

## Введение в проект

### Что такое табулирование функций?
Представьте, что у вас есть математическая функция, например f(x) = x². Табулирование - это процесс создания таблицы значений этой функции для разных x. Например:
- x = 0 → f(0) = 0
- x = 1 → f(1) = 1
- x = 2 → f(2) = 4
- и т.д.

### Зачем это нужно?
Когда функция сложная или мы хотим с ней работать в программе, иногда проще хранить ее в виде таблицы значений, а не в виде формулы. Это особенно полезно когда:
- Функция очень сложная для вычисления
- Мы хотим быстро получать значения без вычислений
- Нужно работать с экспериментальными данными

### Основные задачи проекта:
1. **Хранение функций** в табличном виде
2. **Вычисление значений** между известными точками (интерполяция)
3. **Вычисление значений** за пределами известных точек (экстраполяция)
4. **Комбинирование функций** (композиция)
5. **Модификация функций** (добавление/удаление точек)

## Основные концепции ООП в проекте
<br>

#### 1. Абстракция (Abstraction)
Мы скрываем сложные детали реализации и показываем только важные функции. Например, класс `AbstractTabulatedFunction` скрывает как именно хранятся данные (в массиве или списке), но предоставляет общие методы для работы.
<br><br>

#### 2. Инкапсуляция (Encapsulation)
Каждый класс "запечатывает" свои данные и методы. Например:
- Данные массива `xValues` и `yValues` скрыты в `ArrayTabulatedFunction`
- Внутренняя структура узлов скрыта в `LinkedListTabulatedFunction`
<br><br>

#### 3. Наследование (Inheritance)
Классы наследуют поведение от родительских классов:
- `ArrayTabulatedFunction` и `LinkedListTabulatedFunction` наследуют от `AbstractTabulatedFunction`
- `AbstractTabulatedFunction` реализует `TabulatedFunction`
<br><br>

#### 4. Полиморфизм (Polymorphism)
Разные классы могут использоваться одинаково:
- Мы можем работать с `ArrayTabulatedFunction` и `LinkedListTabulatedFunction` через интерфейс `TabulatedFunction`
- Метод `apply()` работает по-разному для разных реализаций, но вызывается одинаково
<br><br>

## Архитектура классов
<br>

### Иерархия классов (от общего к частному):

    MathFunction (интерфейс) - самая общая концепция "функция"
        ↑
    TabulatedFunction (интерфейс) - функция в табличном виде  
        ↑
    AbstractTabulatedFunction (абстрактный класс) - общая логика для табличных функций
        ↑
    ArrayTabulatedFunction    LinkedListTabulatedFunction (конкретные реализации)

<br>

### Пояснение иерархии:

**MathFunction** - как бы говорит: "Я любая функция, которая может принимать число x и возвращать число y"

**TabulatedFunction** - говорит: "Я тоже функция, но я храню свои значения в таблице (набор точек x,y)"

**AbstractTabulatedFunction** - реализует общую логику для ВСЕХ табличных функций (как вычислять значения между точками и т.д.)

**ArrayTabulatedFunction** и **LinkedListTabulatedFunction** - конкретные способы хранения таблицы данных

<br>

## Ключевые интерфейсы

<br>

### Интерфейс MathFunction

```java
public interface MathFunction {
    double apply(double x);
    default CompositeFunction andThen(MathFunction afterFunction) {
        return new CompositeFunction(this, afterFunction);
    }
}
```

**Что это делает?**
- `apply(double x)` - основной метод: дайте мне x, я верну y
- `andThen()` - метод для создания цепочки функций: f(g(x))

**Пример использования:**
```java
MathFunction square = x -> x * x; // лямбда-выражение
double result = square.apply(5); // вернет 25.0`
```

### Интерфейс TabulatedFunction

Расширяет MathFunction, добавляя методы для работы с таблицей:

```java
public interface TabulatedFunction extends MathFunction {
    int getCount();                    // сколько точек в таблице
    double getX(int index);           // получить x по индексу
    double getY(int index);           // получить y по индексу  
    void setY(int index, double value); // изменить y по индексу
    int indexOfX(double x);           // найти индекс для данного x
    int indexOfY(double y);           // найти индекс для данного y
    double leftBound();               // самый маленький x
    double rightBound();              // самый большой x
}
```

### Интерфейсы Insertable и Removable

```java
public interface Insertable {
    void insert(double x, double y);  // добавить новую точку
}

public interface Removable {
    void remove(int index);           // удалить точку по индексу
}
```

Эти интерфейсы позволяют модифицировать табличные функции.

<br>

## Реализации табулированных функций

<br>

### Абстрактный класс AbstractTabulatedFunction

Это "мозг" всей системы - здесь реализована основная логика работы с табличными функциями.

<br>

**Ключевые защищенные (protected) методы:**

1. `floorIndexOfX(double x)` - найти индекс точки, которая находится "полом" для x (ближайшая слева)
2. `extrapolateLeft(double x)` - вычислить значение слева от известных точек
3. `extrapolateRight(double x)` - вычислить значение справа от известных точек  
4. `interpolate(double x, int floorIndex)` - вычислить значение между точками


<br>

**Важный публичный метод apply():**

```java
public double apply(double x) {
    if (x < leftBound()) {
        return extrapolateLeft(x);      // если x слева - экстраполяция слева
    } else if (x > rightBound()) {
        return extrapolateRight(x);     // если x справа - экстраполяция справа
    } else {
        int index = indexOfX(x);
        if (index != -1) {
            return getY(index);         // если x точно совпадает с существующей точкой
        } else {
            int floorIndex = floorIndexOfX(x);
            return interpolate(x, floorIndex); // если x между точками - интерполяция
        }
    }
}
```

**Метод интерполяции:**

```java
protected double interpolate(double x, double leftX, double rightX, double leftY, double rightY) {
    return leftY + (rightY - leftY) * (x - leftX) / (rightX - leftX);
}
```

Это формула линейной интерполяции - мы проводим прямую линию между двумя точками и находим значение на этой линии.


<br>

### Класс ArrayTabulatedFunction

**Хранение данных:** в двух параллельных массивах
- `xValues` - массив координат x
- `yValues` - массив соответствующих координат y

**Конструкторы:**
1. Из массивов - просто копируем переданные массивы
2. Из функции - создаем равномерную сетку точек

**Преимущества:**
- Быстрый доступ к элементу по индексу - O(1)
- Простая реализация

**Недостатки:**
- Медленная вставка/удаление - O(n) (нужно копировать массивы)
- Фиксированный размер (нужно создавать новые массивы при изменении размера)

**Пример создания:**
```java
double[] x = {1, 2, 3, 4};
double[] y = {1, 4, 9, 16};
ArrayTabulatedFunction func = new ArrayTabulatedFunction(x, y);
```

<br>

### Класс LinkedListTabulatedFunction

**Хранение данных:** в двусвязном циклическом списке

**Внутренний класс Node:**
```java
private static class Node {
    public Node next;  // ссылка на следующий узел
    public Node prev;  // ссылка на предыдущий узел  
    public double x;   // координата x
    public double y;   // координата y
}
```

**Структура списка:**
- Каждый узел содержит точку (x,y)
- Узлы связаны в кольцо: последний узел ссылается на первый
- Есть ссылка `head` на первый узел

**Преимущества:**
- Быстрая вставка/удаление - O(1) после нахождения позиции
- Динамический размер

**Недостатки:**
- Медленный доступ по индексу - O(n)
- Более сложная реализация

**Метод addNode():**
Добавляет новый узел в конец списка, поддерживая циклическую структуру.

<br>

## Математические функции

<br>

#### IdentityFunction (Тождественная функция)
Самая простая функция: `f(x) = x`
```java
public class IdentityFunction implements MathFunction {
    public double apply(double x) {
        return x;  // просто возвращаем то, что получили
    }
}
```


<br>



#### SqrFunction (Квадратичная функция)  
`f(x) = x²`
```java
public class SqrFunction implements MathFunction {
    public double apply(double x) {
        return Math.pow(x, 2);  // используем стандартную математическую функцию
    }
}
```


<br>


#### CompositeFunction (Композиция функций)
Реализует операцию `f(g(x))` - сначала применяем одну функцию, потом другую.

**Конструктор:** принимает две функции<br>
**Метод apply():** применяет функции последовательно

```java
public class CompositeFunction implements MathFunction {
    private final MathFunction firstFunction;
    private final MathFunction secondFunction;

    public CompositeFunction(MathFunction firstFunction, MathFunction secondFunction) {
        this.firstFunction = firstFunction;
        this.secondFunction = secondFunction;
    }

    public double apply(double x) {
        return secondFunction.apply(firstFunction.apply(x));
    }
}
```

**Пример использования:**
```java
MathFunction square = new SqrFunction();      // f(x) = x²
MathFunction increment = x -> x + 1;         // g(x) = x + 1 (лямбда)
CompositeFunction complex = new CompositeFunction(square, increment); // g(f(x)) = x² + 1
double result = complex.apply(3); // (3²) + 1 = 10`
```

## Специальные алгоритмы

### BSpline (B-сплайны)
B-сплайны - это специальные функции, используемые в компьютерной графике и моделировании для создания гладких кривых.

**Рекурсивная формула Кокса-де Бура:**
- Базовый случай (степень 0): функция равна 1 на интервале между узлами, иначе 0
- Рекурсивный случай: линейная комбинация сплайнов меньшей степени

**Параметры:**
- `i` - индекс базисной функции
- `k` - степень сплайна  
- `t` - точка, в которой вычисляем
- `knots` - узловой вектор (массив узлов)

**Пример использования:**
`double[] knots = {0, 1, 2, 3};
double value = BSpline.apply(0, 1, 1.5, knots);`


<br>


### NewtonMethod (Метод Ньютона)
Численный метод для нахождения корней уравнений (где f(x) = 0).

**Алгоритм:**
1. Начинаем с начального приближения x₀
2. Вычисляем новое приближение: x₁ = x₀ - f(x₀)/f'(x₀)
3. Повторяем пока не достигнем нужной точности

**Параметры:**
- `f` - функция, корень которой ищем
- `df` - производная функции  
- `x0` - начальное приближение
- `eps` - точность
- `maxIterations` - максимальное число итераций


<br>


## Тестирование


### Зачем нужно тестирование?
- Убедиться, что код работает правильно
- Обнаружить ошибки раньше
- Упростить изменение кода без страха что-то сломать


<br>


### JUnit Framework
Стандартная библиотека для тестирования в Java.

**Основные аннотации:**
- `@Test` -标记 метод как тест
- `@BeforeEach` - выполняется перед каждым тестом
- `@AfterEach` - выполняется после каждого теста

**Основные assertions (проверки):**
- `assertEquals(expected, actual)` - проверка равенства
- `assertTrue(condition)` - проверка истинности
- `assertFalse(condition)` - проверка ложности
- `assertNull(object)` - проверка на null

### Пример теста из проекта:

```java
@Test
void testConstructorArrays() {
    double[] x = {1, 2, 3};
    double[] y = {4, 5, 6};
    ArrayTabulatedFunction f = new ArrayTabulatedFunction(x, y);

    assertEquals(3, f.getCount());      // проверяем количество точек
    assertEquals(1, f.getX(0));        // проверяем первую координату x
    assertEquals(6, f.getY(2));        // проверяем последнюю координату y
}
```

### Типы тестов в проекте:

1. **Unit-тесты** - тестирование отдельных классов
2. **Интеграционные тесты** - тестирование взаимодействия классов
3. **Тесты граничных случаев** - тестирование особых ситуаций


<br>


## Работа с инструментами

### GitHub и GitHub Desktop
**Git** - система контроля версий, позволяет:
- Сохранять историю изменений
- Работать в команде без конфликтов
- Откатываться к предыдущим версиям

**GitHub** - веб-платформа для хранения Git-репозиториев

**GitHub Desktop** - графический интерфейс для работы с Git


<br>


### Основные команды Git:
- `git clone` - скопировать репозиторий
- `git add` - добавить файлы в отслеживание  
- `git commit` - сохранить изменения
- `git push` - отправить изменения на сервер
- `git pull` - забрать изменения с сервера


<br>


### IntelliJ IDEA
Среда разработки (IDE) с мощными возможностями:
- Подсветка синтаксиса
- Автодополнение кода
- Отладка
- Интеграция с Git
- Запуск тестов


<br>

# Вопросы для подготовки

<br>

## Вопросы по проекту

1. **Какая основная цель вашего проекта?**
   - Что делает ваш проект и какие проблемы решает?

2. **В чем разница между ArrayTabulatedFunction и LinkedListTabulatedFunction?**
   - Какие преимущества и недостатки у каждой реализации?

3. **Как работает интерполяция в вашем проекте?**
   - Что происходит, когда нужно вычислить значение между известными точками?

4. **Что такое композиция функций и как она реализована?**
   - Как работает метод andThen() и класс CompositeFunction?

5. **Как вы тестировали свой проект?**
   - Какие типы тестов написали и что они проверяют?

## Вопросы по Java

1. **Что такое интерфейс в Java?**
   - Чем интерфейс отличается от обычного класса?

2. **Как работает наследование в Java?**
   - Что такое ключевые слова extends и implements?

3. **Что такое полиморфизм?**
   - Как он применяется в вашем проекте?

4. **Какие модификаторы доступа вы знаете?**
   - Где вы использовали private, protected, public?

5. **Что такое конструктор?**
   - Сколько конструкторов в ваших классах и зачем?

6. **Как работают массивы в Java?**
   - Где вы использовали массивы в проекте?

7. **Что такое статические методы?**
   - Какие статические методы есть в вашем проекте?

8. **Как организованы пакеты (packages) в вашем проекте?**
   - Зачем нужны пакеты?

9. **Что такое исключения (exceptions)?**
   - Какие исключения могут возникнуть в вашем проекте?

10. **Что такое JUnit и как вы его использовали?**
    - Как вы тестировали свои классы?

<br>

## Краткие ответы для подготовки

### По проекту:
1. **Цель** - работа с математическими функциями: хранение в таблицах, интерполяция, композиция
2. **Array vs LinkedList** - массивы быстрее для чтения, список быстрее для изменений
3. **Интерполяция** - линейное вычисление значений между точками по формуле
4. **Композиция** - последовательное применение функций: f(g(x))
5. **Тестирование** - unit-тесты для каждого класса, проверка граничных случаев

### По Java:
1. **Интерфейс** - контракт без реализации, класс реализует интерфейс
2. **Наследование** - класс наследует от родителя, реализует интерфейсы
3. **Полиморфизм** - работа с разными классами через общий интерфейс
4. **Модификаторы** - private (внутри класса), protected (наследники), public (везде)
5. **Конструктор** - создает объект, у нас по 2 конструктора на класс
6. **Массивы** - в ArrayTabulatedFunction для хранения точек
7. **Статические методы** - BSpline.apply() и NewtonMethod.apply()
8. **Пакеты** - все классы в package functions для организации
9. **Исключения** - могут быть при неверных индексах массива/списка
10. **JUnit** - фреймворк для тестов, аннотация @Test, проверки assertEquals
