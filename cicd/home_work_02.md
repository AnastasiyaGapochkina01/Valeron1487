# Часть 1 - работа с артефактами
дан простой скрипт, который конвертирует markdown в pdf
```
import argparse
from markdown_pdf import MarkdownPdf, Section

def convert_markdown_to_pdf(input_file, output_file):
    pdf = MarkdownPdf(toc_level=2)

    with open(input_file, 'r', encoding='utf-8') as file:
        markdown_content = file.read()

    pdf.add_section(Section(markdown_content))
    pdf.save(output_file)
    print(f"PDF файл создан: {output_file}")

if __name__ == "__main__":
    parser = argparse.ArgumentParser(description='Конвертировать Markdown в PDF')
    parser.add_argument('-i', '--input', help='Входной файл Markdown', required=True)
    parser.add_argument('-o', '--output', help='Выходной файл PDF', required=True)
    args = parser.parse_args()

    convert_markdown_to_pdf(args.input, args.output)
```
ему требуется библиотека markdown-pdf

Нужно написать пайплайн, который
- будет прогонять линтер для самого скрипта на python
- будет прогонять линтер для article.md
- будет генерировать из файла article.md в репозитории проекта файл article-ff336b23.pdf, где ff336b23 - это CI_COMMIT_SHORT_SHA и сохранять его в артефактах
- заливать созданный файл article-ff336b23.pdf на ftp-сервер (ftp-сервер поднять самостоятельно)

# Часть 2 - docker
Дан код на python\
app.py
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
Необходимо
1) упаковать его в docker
2) написать пайплайн который
- прогонит линтеры для кода и Dockerfile
- соберет docker image
- запушит его в docker hub
- задеплоит собранный image по ssh на удаленный хост
