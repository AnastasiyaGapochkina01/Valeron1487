1) Запустить свой gitlab-runner: проделать все те же шаги, что я делала на занятии, НО учесть, что я запускала раннер как просто процесс. Это неудобно и не совсем корректно, поэтому нужно написать к этому настроенному раннеру unit-файл и запустить его как демон
2) Создать репозиторий в gitlab, подключить к нему раннер; в репозитории создать два файла
- main.go
```
package main

import (
    "bufio"
    "fmt"
    "os"
    "strconv"
)

func main() {
    // Создаем новый сканер для чтения ввода пользователя
    scanner := bufio.NewScanner(os.Stdin)

    fmt.Println("Simple calculator")
    fmt.Println("1. addition")
    fmt.Println("2. subtraction")
    fmt.Println("3. multiplication")
    fmt.Println("4. division")

    // Запрашиваем у пользователя номер операции
    fmt.Print("Enter the operation number: ")
    scanner.Scan()
    operation, err := strconv.Atoi(scanner.Text())
    if err != nil {
        fmt.Println("Incorrect input")
        return
    }

    // Запрашиваем два числа
    fmt.Print("Enter first number: ")
    scanner.Scan()
    num1, err := strconv.ParseFloat(scanner.Text(), 64)
    if err != nil {
        fmt.Println("Incorrect input")
        return
    }

    fmt.Print("Enter second number: ")
    scanner.Scan()
    num2, err := strconv.ParseFloat(scanner.Text(), 64)
    if err != nil {
        fmt.Println("Incorrect input")
        return
    }

    // Выполняем операцию
    var result float64
    switch operation {
    case 1:
        result = num1 + num2
        fmt.Printf("%.2f + %.2f = %.2f\n", num1, num2, result)
    case 2:
        result = num1 - num2
        fmt.Printf("%.2f - %.2f = %.2f\n", num1, num2, result)
    case 3:
        result = num1 * num2
        fmt.Printf("%.2f * %.2f = %.2f\n", num1, num2, result)
    case 4:
        if num2 != 0 {
            result = num1 / num2
            fmt.Printf("%.2f / %.2f = %.2f\n", num1, num2, result)
        } else {
            fmt.Println("Division by zero!")
        }
    default:
        fmt.Println("Incorrect operation number")
    }
}
```
- app.py
```
package main

import (
    "bufio"
    "fmt"
    "os"
    "strconv"
)

func main() {
    // Создаем новый сканер для чтения ввода пользователя
    scanner := bufio.NewScanner(os.Stdin)

    fmt.Println("Simple calculator")
    fmt.Println("1. addition")
    fmt.Println("2. subtraction")
    fmt.Println("3. multiplication")
    fmt.Println("4. division")

    // Запрашиваем у пользователя номер операции
    fmt.Print("Enter the operation number: ")
    scanner.Scan()
    operation, err := strconv.Atoi(scanner.Text())
    if err != nil {
        fmt.Println("Incorrect input")
        return
    }

    // Запрашиваем два числа
    fmt.Print("Enter first number: ")
    scanner.Scan()
    num1, err := strconv.ParseFloat(scanner.Text(), 64)
    if err != nil {
        fmt.Println("Incorrect input")
        return
    }

    fmt.Print("Enter second number: ")
    scanner.Scan()
    num2, err := strconv.ParseFloat(scanner.Text(), 64)
    if err != nil {
        fmt.Println("Incorrect input")
        return
    }

    // Выполняем операцию
    var result float64
    switch operation {
    case 1:
        result = num1 + num2
        fmt.Printf("%.2f + %.2f = %.2f\n", num1, num2, result)
    case 2:
        result = num1 - num2
        fmt.Printf("%.2f - %.2f = %.2f\n", num1, num2, result)
    case 3:
        result = num1 * num2
        fmt.Printf("%.2f * %.2f = %.2f\n", num1, num2, result)
    case 4:
        if num2 != 0 {
            result = num1 / num2
            fmt.Printf("%.2f / %.2f = %.2f\n", num1, num2, result)
        } else {
            fmt.Println("Division by zero!")
        }
    default:
        fmt.Println("Incorrect operation number")
    }
}
```
3) Написать пайплайн, который будет прогонять линтеры для кода на go и python (две разные job) и собирает исполняемые файлы из кода (еще две разные job)
- для go это делается с помощью команды ```go build -o $res_file $src_file```, где $res_file и $src_file - это итоговый файл и исходный код соответсвтенно
- для python это делается с помощью библиотеки pyinstaller: ```pyinstaller --onefile app.py``` (соответственно перед выполнением команды надо установить pyinstaller)
