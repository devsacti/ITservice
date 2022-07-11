# Overview of WEB-APP
* Intro
* Analysis of Front and Back
* URL and HTTP
* Implementation

# Intro
![webapp_electronic_vending_machine](./imgs/1.png)

(TO ME) Web Service is 'Electroic Vending Machine'

I think WEB-APP can be figuratively mapped with 'Electronic Vending machine'.

The Electronic vending machine you encounter has __'Front and Back'__.

It is waiting for calls of client that canbe human's actions, or more specifically calls of web browser like 'chrome'.

Clients call the WEB-APP(Web service Application) by __URL__.

## Analysis of Front and back

WEB-APP = Front + Back (= Front-End + Back-End)

Front = ((html + css) + javascript) ; (index.jsp), (index.mustache), ...

Back = ( (API of WEB-APP + Server) + Database )

; ( (config and controller.java of JAVA-APP + AWS Linux Server) + mybatis-OracleDB ), ...

*Server = ( OS + HW ), and Server has at least 2 kinds ; Web Server, Application Server, etc.

#### Flow between Front and Back

Let's assume that you input the primary url and WEB-APP returns the index page,

and it can be regarded as "Menu of Web Service".

Generally, Menu of Web Service provides choices of buttens mapped with other urls.

And those urls is mapped with functions of back-end of Electronic Vending Machine

So, you can access the functions that control the resources of Web Service.

this conception of flow canbe described at the perspective of back-oriented as 'Controller'.

# URL and HTTP

## URL : Uniform Resource Locater
(ex)https://www.google.com

Generally, if human user clicks or inserts the certain URL,

then, URL(or 'internet address') calls the function of WEB-APP.

And function provides html documents which is, in other words, Front-End.

more specifically, "index page"  like index.jsp, index.mustache, ...

### the related : URL vs URI
(To be supplemented later)


# Implementation of WEB-APP

In my Github, basic framework is 'Spring (boot)'

In this perspective, Spring Framework is a core joint of Front-End tool like jsp, Persitence-Framework like myBatis, Server that has runtime like AWS Linux

(ex)

　　　　　　　　　　　　　　　　　:arrow_upper_right: config of jsp and index.jsp

Spring Framework with Build Tool　　:arrow_right: config and controller.java of JAVA-APP + config of myBatis

　　　　　　　　　　　　　　　　　:arrow_lower_right: config of AWS and AWS Linux Server

　　　　　　　　　　　　　　　　　:arrow_lower_right:  config of AWS RDS and MariaDB of AWS RDS)

## the related : CRUD
Categories of functions based on processing resources like data of DB, ...

1. Create
Button send url, generally inserts the new data into the DB of WEB-APP.

2. Read
Button sends url that requires the infomations user want to see.

3. Update
Button sends url that requires change the data of DB, generally based on sub part of url.

4. Delete
Button sends url that requires remove the data of DB, generally based on sub part of url.

### Story of CRUD
Click the 'sign in' button of site,and do something(Create)

Click the 'see the detail of account' button after log in,and see the infomations of your account,(Read)

Click the 'change the nikckname' button, and do something,(Update)

Click the 'Withdrawal from site' button,(Delete)

## the related : RestFul
Simplely, I think it can also mean 'optimized Menu that can represent the sources enough' 

(To be supplemented later)


## Implementations of API
[JAVA-APP](https://github.com/devsacti/JAVA-APP)

[PYTHON-APP](https://github.com/devsacti/PYTHON-APP)


### The Relates

[Server](https://github.com/devsacti/Server)

[Server ; Cloud-Server](https://github.com/devsacti/Cloud-Server-and-Extensions)

# Rererences
1. Image of Front-End and Back-End - https://blog.dalso.org/language/web/6523