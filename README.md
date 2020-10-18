# Hands On Activity On Docker

create a utility which will accept a property file and deploy the applications as per provided in the property file on a single node. Port 80 of node should accept all the connections and route the content according to the Domain provided in the property file to the respective applications. Rest of the ports should not be exposed on the host. PFB the sample of property file
APP_NAMES=APP1,APP2,App3
APP1_IMAGE=nginx:1.7.9
APP1_DOMAIN=app1.opstree.com
APP1_PORT=80
APP1_NAME=web1
APP2_IMAGE=tomcat
APP2_DOMAIN=app2.opstree.com
APP2_PORT=8080
APP2_NAME=app2
APP3_IMAGE=node
APP3_DOMAIN=app3.opstree.com
APP3_PORT=9000
APP3_NAME=app3
For eg the following curl request must be served by App2
curl --header ""Host: app2.opstree.com"" http://NODE_IP:80/
Or if triggered from with-in the host
curl --header ""Host: app2.opstree.com"" http://localhost:80/"

## Step1.) Build Nginx Image

```bash
[root@server opstree]# docker build -t nginxproxy nginx/
```
## Step2.) Build Node Js Image

```bash
[root@server opstree]# docker build -t hello-world node/
```

## Step3.) Start all containers

```bash
[root@server opstree]# docker-compose up -d
```
## Step4.) Update /etc/hosts file

```bash

192.168.33.60      app1.opstree.com  app1
192.168.33.60      app2.opstree.com  app2
192.168.33.60      app3.opstree.com  app3

```
## Step5.) Hurray !! All Done 
### Check app1.opstree.com:80

```bash
[root@server opstree]# curl app1.opstree.com:80

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
[root@server opstree]#

```


### Check app2.opstree.com:80

```bash
[root@server opstree]# curl app2.opstree.com:80
<html>
<head>
<title>Sample "Hello, World" Application</title>
</head>
<body bgcolor=white>

<table border="0">
<tr>
<td>
<img src="images/tomcat.gif">
</td>
<td>
<h1>Sample "Hello, World" Application</h1>
<p>This is the home page for a sample application used to illustrate the
source directory organization of a web application utilizing the principles
outlined in the Application Developer's Guide.
</td>
</tr>
</table>

<p>To prove that they work, you can execute either of the following links:
<ul>
<li>To a <a href="hello.jsp">JSP page</a>.
<li>To a <a href="hello">servlet</a>.
</ul>

</body>
</html>
[root@server opstree]#<html>
<head>
<title>Sample "Hello, World" Application</title>
</head>
<body bgcolor=white>

<table border="0">
<tr>
<td>
<img src="images/tomcat.gif">
</td>
<td>
<h1>Sample "Hello, World" Application</h1>
<p>This is the home page for a sample application used to illustrate the
source directory organization of a web application utilizing the principles
outlined in the Application Developer's Guide.
</td>
</tr>
</table>

<p>To prove that they work, you can execute either of the following links:
<ul>
<li>To a <a href="hello.jsp">JSP page</a>.
<li>To a <a href="hello">servlet</a>.
</ul>

</body>
</html>
[root@server opstree]#
```

 
### Check app3.opstree.com:80
``` bash
[root@server opstree]# curl app3.opstree.com:80
Hello World!
```


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.
