# Практическая работа 3: Циклы и массивы
**Студент:** Паринова Ксения Николаевна
**Группа:** 1зб_ИВТ(ускор.)/25
**Дата:** 02 апреля 2026 г.
---
## Задание 3.1: Таблица синусов
### Постановка задачи
Напишите программу, которая выводит таблицу значений sin(x) от 0 до 2π с шагом 0.1.
### Математическая модель
Значения синуса вычисляются по формуле:
sin(x)=sum((-1)^n/(2n+1)! * x^2n+1
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| pi | double | Число π (3.14159) |
| step | double | Шаг изменения x (0.1) |
| x | double | Текущее значение аргумента |
### Код программы
```c
#include <stdio.h>
#include <math.h>

int main(void) {
    double pi = 3.14159;
    double step = 0.1;
    
    printf("Table of sin(x) from 0 to 2π:\n");
    
    for (double x = 0; x <= 2 * pi + step/2; x += step) {
        printf("x = %.2f, sin(x) = %.4f\n", x, sin(x));
    }
    
    return 0;
}
```
### Результаты работы
![Результат](practice-3/screenshots/task3-1.png)
---
## Задание 3.2: Сумма ряда
### Постановка задачи
Напишите программу, которая вычислит сумму гармонического ряда:
S=1+1/2+1/3+...+1/n 
### Математическая модель
Гармонический ряд:
Hn=sum(k=1,n)1/k
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| n | int | Количество членов ряда |
| sum | double | Сумма ряда |
| i | int | Счётчик цикла |
### Код программы
```c
#include <stdio.h>

int main(void) {
    int n;
    double sum = 0.0;
    
    printf("Enter n: ");
    scanf("%d", &n);
    
    for (int i = 1; i <= n; i++) {
        sum += 1.0 / i;
    }
    
    printf("S = 1 + 1/2 + 1/3 + ... + 1/%d = %.4f\n", n, sum);
    
    return 0;
}
```
### Результаты работы
![Результат](practice-3/screenshots/task3-2.png)
---
## Задание 3.3: Числа Фибоначчи
### Постановка задачи
Напишите программу, которая выведет первые N чисел Фибоначчи. 
### Математическая модель
Последовательность Фибоначчи определяется:
F(0)=0, F(1)=1, F(n)=F(n-1)+F(n-2)
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| n | int | Количество чисел для вывода |
| prev2 | long long | F(n-2) |
| prev1 | long long | F(n-1) |
| current | long long | Текущее число Фибоначчи |
### Код программы
```c
#include <stdio.h>

int main(void) {
    int n;
    
    printf("Enter N: ");
    scanf("%d", &n);
    
    if (n <= 0) {
        printf("Invalid input\n");
        return 1;
    }
    
    printf("Fibonacci: ");
    
    if (n >= 1) {
        printf("0 ");
    }
    if (n >= 2) {
        printf("1 ");
    }
    
    long long prev2 = 0, prev1 = 1, current;
    
    for (int i = 3; i <= n; i++) {
        current = prev1 + prev2;
        printf("%lld ", current);
        prev2 = prev1;
        prev1 = current;
    }
    
    printf("\n");
    
    return 0;
}
```
### Результаты работы
![Результат](practice-3/screenshots/task3-3.png)
---
## Задание 3.4: Среднее арифметическое
### Постановка задачи
Напишите программу, которая запрашивает 5 чисел, сохраняет их в массив и вычисляет среднее арифметическое. 
### Математическая модель
Среднее арифметическое:
xср = 1/n * sum(i=1,n)xi
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| arr | int[5] | Массив из 5 целых чисел |
| sum | int | Сумма элементов массива |
| average | double | Среднее арифметическое |
### Код программы
```c
#include <stdio.h>

int main(void) {
    int arr[5];
    int sum = 0;
    
    printf("Enter 5 numbers: ");
    
    for (int i = 0; i < 5; i++) {
        scanf("%d", &arr[i]);
        sum += arr[i];
    }
    
    double average = (double)sum / 5;
    
    printf("Average: %.2f\n", average);
    
    return 0;
}
```
### Результаты работы
![Результат](practice-3/screenshots/task3-4.png)
---
## Задание 3.5: Минимум и максимум
### Постановка задачи
Напишите программу, которая находит минимальный и максимальный элементы массива из 10 чисел, введённых с клавиатуры. 
### Математическая модель
min(x1, x2​,..., xn​)=наименьшее значение среди xi​	 
max⁡(x1, x2,...,xn)=наибольшее значение среди xi
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| arr | int[10] | Массив из 10 целых чисел |
| min | int | Минимальный элемент |
| max | int | Максимальный элемент |
### Код программы
```c
#include <stdio.h>

int main(void) {
    int arr[10];
    
    printf("Enter 10 numbers: ");
    
    for (int i = 0; i < 10; i++) {
        scanf("%d", &arr[i]);
    }
    
    int min = arr[0];
    int max = arr[0];
    
    for (int i = 1; i < 10; i++) {
        if (arr[i] < min) {
            min = arr[i];
        }
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    
    printf("Minimum: %d\n", min);
    printf("Maximum: %d\n", max);
    
    return 0;
}
```
### Результаты работы
![Результат](practice-3/screenshots/task3-5.png)
---
## Задание 3.6: Реверс массива
### Постановка задачи
Напишите программу, которая переворачивает массив "на месте".
### Математическая модель
Реверс массива:
для i=0 до [n/2]-1: обменять arr[i] и arr[n-1-i]
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| n | int | Размер массива |
| arr | int[n] | Массив целых чисел |
| temp | int | Временная переменная для обмена |
### Код программы
```c
#include <stdio.h>

int main(void) {
    int n;
    
    printf("Enter size of array: ");
    scanf("%d", &n);
    
    int arr[n];
    
    printf("Enter %d numbers: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("Original: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    for (int i = 0; i < n / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[n - 1 - i];
        arr[n - 1 - i] = temp;
    }
    
    printf("Reversed: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```
### Результаты работы
![Результат](practice-3/screenshots/task3-6.png)
