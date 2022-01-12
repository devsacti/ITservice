# Approaching to Web service Application on Network

I think WEB-APP can be figuratively 'Electric Vending machine'

waiting for clients that canbe human(or other calls of web service)

client like chrome human using calls the WEB-APP(Web service Application) by url

## URL
(ex)www.google.com

Generally, if human user clicks or inserts the certain url,

then, url(or internet address) calls the function of WEB-APP

and function provides html documents which is,in other words, Front-End

### the related : URL vs URI
abbr 

# communications between Front and Back

let's assume that you input the url and see the Front-End of WEB-APP

the Electric vending machine you encounter has functions on the 'back'

Generally, interface of Front-end provides choices of butten mappedn with other urls

so, you can access or the control the other resources of back web-service

## the related : CRUD
categories of button based on function

1. Create
button send url, generally inserts the new data into the DB of WEB-APP

2. Read
button sends url that requires the infomations user want to see

3. Update
button sends url that requires change the data of webapp, generally based on sub part of url

4. Delete
button sends url that requires remove the data of webapp, generally based on sub part of url

### Story of CRUD
click the 'sign in' button of site,and do something,

then you Create

click the 'see the detail of account' button after log in,and see the infomations of your account,

then you Read

click the 'change the nikckname' button, and do something,

then you Update

click the 'Withdrawal from site' button,

then you Delete

## the related : RestFul
abbr

simplely, i think it can also mean 'optimized interface that can represent the sources enough' 

## Analysis of Front and back
WEB-APP = Front-End + Back-End

Perspective1

![front-end_back-end_full-Stack](https://user-images.githubusercontent.com/88543657/149053803-39be2d86-6fe5-4d55-be00-99dde2ac8e7d.png)

[image reference](https://www.a-mean-blog.com/images/rqvbk2p56xjsis3ut1ta/front-end_back-end_full-Stack.png)

Perspective2

![perspective2_full-stack](https://user-images.githubusercontent.com/88543657/149053816-3ad0307c-11fb-4fb8-bc60-4311855cbe29.png)

[image reference](https://blog.dalso.org/language/web/6523)

## components of Front-end
html + css

js(javascript)

! js is mapped with Url which calls the API

## components of Back-end
API on Server like linux

DB

# Implementation of WEB-APP

there are many related frameworks(or tools like mybatis) that is utilized to webservice Implementation

at this point, i will upload the related frameworks that is useful to expand webservice


## Implementations LIST
[JAVA-APP](https://github.com/devsacti/JAVA-APP)

[PYTHON-APP](https://github.com/devsacti/WEB-APP/tree/main/PYTHON-APP)
*python-app has seperate repos per prj, so this directory is only media for prj links

[JS-APP](https://github.com/devsacti/JS-APP)
