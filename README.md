# Approaching to Web service Application on Network

I think WEB-APP can be figuratively mapped with 'Electronic Vending machine'

the Electronic vending machine you encounter has 'front' and 'back'

it is waiting for clients that canbe human(or other calls of web service like chrome you are using)

clients call the WEB-APP(Web service Application) by URL

## URL : Uniform Resource Locater
(ex)www.google.com

Generally, if human user clicks or inserts the certain URL,

then, URL(or 'internet address') calls the function of WEB-APP

and function provides html documents which is, in other words, Front-End

more specifically, "index page"  like index.jsp, index.mustache, ...

### the related : URL vs URI
abbr 

# communications between Front and Back

let's assume that you input the primary url and WEB-APP returns the index page,

and it can be regarded as "interface of Front-End"

Generally, interface of Front-end provides choices of butten mapped with other urls

and those urls is mapped with functions of back-end of Electronic Vending Machine

so, you can access the functions that control the resources of web-service

## the related : CRUD
categories of functions based on processing resources like data of DB, ...

1. Create
button send url, generally inserts the new data into the DB of WEB-APP

2. Read
button sends url that requires the infomations user want to see

3. Update
button sends url that requires change the data of DB, generally based on sub part of url

4. Delete
button sends url that requires remove the data of DB, generally based on sub part of url

### Story of CRUD
click the 'sign in' button of site,and do something(Create)

click the 'see the detail of account' button after log in,and see the infomations of your account,(Read)

click the 'change the nikckname' button, and do something,(Update)

click the 'Withdrawal from site' button,(Delete)

## the related : RestFul
simplely, i think it can also mean 'optimized interface that can represent the sources enough' 

To be supplemented later

## Analysis of Front and back
WEB-APP = Front-End + Back-End

Perspective1

![front-end_back-end_full-Stack](https://user-images.githubusercontent.com/88543657/149053803-39be2d86-6fe5-4d55-be00-99dde2ac8e7d.png)

[image reference](https://www.a-mean-blog.com/images/rqvbk2p56xjsis3ut1ta/front-end_back-end_full-Stack.png)

Perspective2

![perspective2_full-stack](https://user-images.githubusercontent.com/88543657/149053816-3ad0307c-11fb-4fb8-bc60-4311855cbe29.png)

[image reference](https://blog.dalso.org/language/web/6523)

## components of Front-end, Back-end
Front = ((html + css) + javascript)

(ex) (index.jsp), (index.mustache), ...

Back = ( (API of WEB-APP + Server) + Database )

(ex) ( (config and controller.java of JAVA-APP + AWS Linux Server) + mybatis-MySQL ), ...

* javascript(js) is the media point between Front and Back By URL

### Core
[API of WEB-APP](https://github.com/devsacti/WEB-APP#implementations)

[Server](https://github.com/devsacti/OperatingSystem)

[Database](https://github.com/devsacti/Query-and-Extensions)


# Implementation of WEB-APP

In my Github, basic framework is 'Spring (boot)'

In this perspective, Spring Framework is a core joint of Front-End tool like jsp, Persitence-Framework like myBatis, Server that has runtime like AWS Linux

(ex)

　　　　　　　　　　　　　　　　　:arrow_upper_right: cofig of jsp and index.jsp

Spring Framework with Build Tool　　:arrow_right: config and controller.java of JAVA-APP + config of myBatis

　　　　　　　　　　　　　　　　　:arrow_lower_right: config of AWS and AWS Linux Server

　　　　　　　　　　　　　　　　　:arrow_lower_right:  config of AWS RDS and MariaDB of AWS RDS)

## Implementations
[JAVA-APP](https://github.com/devsacti/JAVA-APP)

[PYTHON-APP](https://github.com/devsacti/PYTHON-APP)

[JS-APP](https://github.com/devsacti/JS-APP)
