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
import http.server
import socket
import os
import getpass

# Получаем имя пользователя
username = getpass.getuser()

# Получаем версию ОС
os_version = f"{os.sys.platform} {os.sys.version}"

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.connect(("8.8.8.8", 80))
local_ip = s.getsockname()[0]
s.close()

greeting = f"Привет, {username}!"

class RequestHandler(http.server.BaseHTTPRequestHandler):
    def do_GET(self):
        if self.path != "/":
            self.send_response(404)
            self.send_header("Content-type", "text/plain")
            self.end_headers()
            self.wfile.write(b"404 Not Found")
            return

        self.send_response(200)
        self.send_header("Content-type", "text/plain")
        self.end_headers()

        response = f"Версия ОС: {os_version}\nПриветствие: {greeting}\nЛокальный IP: {local_ip}"
        self.wfile.write(response.encode())

def run_server():
    server_address = ('', 3000)
    httpd = http.server.HTTPServer(server_address, RequestHandler)
    print("Сервер запущен на порту 3000")
    httpd.serve_forever()

if __name__ == "__main__":
    run_server()
```
3) Написать пайплайн, который будет прогонять линтеры для кода на go и python (две разные job) и собирает исполняемые файлы из кода (еще две разные job)
- для go это делается с помощью команды ```go build -o $res_file $src_file```, где $res_file и $src_file - это итоговый файл и исходный код соответсвтенно
- для python это делается с помощью библиотеки pyinstaller: ```pyinstaller --onefile app.py``` (соответственно перед выполнением команды надо установить pyinstaller)
