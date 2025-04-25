1) Создать репозиторий, содержащий три приложения
- golang-web
```
package main

import (
    "fmt"
    "log"
    "net/http"
    "time"
)

func helloHandler(w http.ResponseWriter, r *http.Request) {
    if r.URL.Path != "/" {
        http.Error(w, "404 Not Found", http.StatusNotFound)
        return
    }

    currentTime := time.Now().Format(time.RFC3339)
    greeting := "Hello!"

    fmt.Fprintf(w, "Current time: %s\n%s", currentTime, greeting)
}

func main() {
    http.HandleFunc("/", helloHandler)

    fmt.Println("Server started on 9100")
    log.Fatal(http.ListenAndServe(":9100", nil))
}
```
- flask-web
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
- nodejs-web
```
const http = require('http');

let requestCount = 0;

const server = http.createServer((req, res) => {
    requestCount++;
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end(`Количество запросов: ${requestCount}`);
});

server.listen(3000, () => {
    console.log('Сервер запущен на порту 3000');
});
```
2) Создать в репозитории 3 ветки с именами
- goapp
- flaskapp
- nodeapp
3) Завернуть приложения в докер (по отдельности, 3 разных Dockerfile)
4) Написать пайплайн, который будет собирать docker image для приложения в зависимости от ветки:
- если был коммит в ветку goapp, то собирать golang-web;
- если был коммит в ветку flaskapp - собирать flask-web
- если был коммит в ветку nodeapp - собирать nodejs-web

Прогонять линтеры для кода и Dockerfile только если в коммите были затронуты соответствующие файлы в ветке проекта или в main.\
Для golang реализовать отдельно компиляцию банрного файла для
- darwin, amd64
- freebsd, amd64
- linux, arm64 и amd64

сборку бинарника реализовать на parallel и закидывать результаты в releases (https://docs.gitlab.com/user/project/releases/release_cicd_examples/)
