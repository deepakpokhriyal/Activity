# Activity

Step1.) Build Nginx Image

[root@server opstree]# docker build -t nginxproxy nginx/

Step2.) Build Node Js Image

[root@server opstree]# docker build -t hello-world node/

Step3.) Start all containers

[root@server opstree]# docker-compose up -d

Step4.) Update /etc/hosts file


192.168.33.60      app1.opstree.com  app1
192.168.33.60      app2.opstree.com  app2
192.168.33.60      app3.opstree.com  app3

Step5.) Hurray !! All Done Now Check 

-------------------------------------------------------------

**[root@server opstree]# curl app1.opstree.com:80**

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


---------------------------------------------------------------

**[root@server opstree]# curl app2.opstree.com:80**

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
[root@server opstree]#

----------------------------------------------------------------------- 

**[root@server opstree]# curl app3.opstree.com:80**
Hello World!
[root@server opstree]#
