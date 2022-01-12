# Approaching to Web service Application on Network

I think WEB-APP can be figuratively mapped with 'Electronic Vending machine'

the Electronic vending machine you encounter has 'front' and 'back'

it is waiting for clients that canbe human(or other calls of web service)

client like chrome human are using calls the WEB-APP(Web service Application) by URL

## URL : Uniform Resource Locater
(ex)www.google.com

Generally, if human user clicks or inserts the certain URL,

then, URL(or 'internet address') calls the functions of WEB-APP

and function provides html documents which is, in other words, Front-End

### the related : URL vs URI
abbr 

# communications between Front and Back

let's assume that you input the primary url and WEB-APP returns the Front-End of its

Generally, interface of Front-end provides choices of butten mapped with other urls

and those urls is mapped with functions of back-side of Electronic Vending Machine

so, you can access or the control the functions or other resources of back of web-service

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
click the 'sign in' button of site,and do something(Create)

click the 'see the detail of account' button after log in,and see the infomations of your account,(Read)

click the 'change the nikckname' button, and do something,(Update)

click the 'Withdrawal from site' button,(Delete)

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

## components of Front-end, Back-end
Front = ((html + css) + javascript)
(ex) index.jsp, index.mustache, ...

Back = API on Server like linux + DB
(ex) controller.java, ...

* javascript(js) is connection point between Front and Back By URL

# Implementation of WEB-APP

In my Github, basic frameworks is 'Spring (boot)'

and, there are many related frameworks(like Django,Persitence Framework,...) that is utilized to webservice Implementation

i will expand implementations from spring to the other related frameworks 

## Implementations LIST
[JAVA-APP](https://github.com/devsacti/JAVA-APP)

[PYTHON-APP](https://github.com/devsacti/PYTHON-APP)

[JS-APP](https://github.com/devsacti/JS-APP)
