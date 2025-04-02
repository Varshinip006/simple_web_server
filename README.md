# EX01 Developing a Simple Webserver

# Date:01:04:2025
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
```
views.py

from importlib.resources import contents
from django.shortcuts import render
from django.http import HttpResponse

content='''<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laptop Specifications</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: blanchedalmond;
          
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .specs-container {
            background-color:cyan;
            padding: 20px;
            border-radius: 10px;
            box-shadow: burlywood;
            width: 400px;
        }
        h1 {
            text-align: center;
            color:black;
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid rgb(165, 158, 158);
        }
        th {
            background-color: blue;
        }
    </style>
</head>
<body>
    <div class="specs-container">
        <h1>Laptop Specifications</h1>
        <table>
            <tr>
                <th>Specification</th>
                <th>Details</th>
            </tr>
            <tr>
                <td>Brand</td>
                <td>LENOVO</td>
            </tr>
            <tr>
                <td>Model</td>
                <td>ThinkPad E16 Gen 1</td>
            </tr>
            <tr>
                <td>Processor</td>
                <td>13th Gen Intel(R) Core(TM) i5-1335U   1.30 GHz</td>
            </tr>
            <tr>
                <td>RAM</td>
                <td>16 GB (15.7 GB usable)</td>
            </tr>
            <tr>
                <td>Storage</td>
                <td>350.8 GB</td>
            </tr>
            <tr>
                <td>Graphics</td>
                <td>NVIDIA GeForce GTX 1650</td>
            </tr>
            <tr>
                <td>Display</td>
                <td>16inch Full HD</td>
            </tr>
            <tr>
                <td>Battery Life</td>
                <td>Up to 48 hours</td>
            </tr>
            <tr>
                <td>Operating System</td>
                <td>Windows 11</td>
            </tr>
            <tr>
                <td>Price</td>
                <td>69000 INR</td>
            </tr>
        </table>
    </div>
</body>
</html>
'''

def app(request):
    return HttpResponse("Hello India")
from http.server import HTTPServer,BaseHTTPRequestHandler
class MyServer(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(content.encode())
print("This is my webserver")
server_address =('',8000)
httpd = HTTPServer(server_address,MyServer)
httpd.serve_forever()

urls.py

from tempfile import template
from django.contrib import admin
from django.urls import path
from app.views import MyServer

urlpatterns = [
    path('admin/', admin.site.urls),
    path('server/',MyServer.as_view())
]
```
# OUTPUT:
![Screenshot 2025-04-02 102907](https://github.com/user-attachments/assets/f4e84264-9279-4057-aa47-dee3e49af92b)

![Screenshot 2025-04-02 103122](https://github.com/user-attachments/assets/77aff5f9-83ee-4d90-869c-aa8d6ebe59ed)


# RESULT:
The program for implementing simple webserver is executed successfully.
