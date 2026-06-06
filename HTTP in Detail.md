# **HTTP in Detail- TryHackMe writeup**

## **Overview**

The HTTP in Detail room explored the Hypertext Transfer Protocol (HTTP), the foundation of communication between web browsers and web servers. Understanding HTTP is essential for web security analysis, threat detection, and incident investigations.

## **Learning Objectives**

* Understand how HTTP works.  
* Learn common request methods.  
* Analyze HTTP responses.  
* Understand headers and cookies.  
* Explore authentication and session management.

## **Understanding HTTP**

HTTP follows a request-response model.

Client Request:

GET /index.html HTTP/1.1  
Host: example.com

Server Response:

HTTP/1.1 200 OK  
Content-Type: text/html

The client sends a request and the server returns a response.

![][image1]

**Example Response:**

HTTP/1.1 200 OK

Server: nginx/1.15.8

Date: Fri, 09 Apr 2021 13:34:03 GMT

Content-Type: text/html

Content-Length: 98

\<html\>

\<head\>

    \<title\>TryHackMe\</title\>

\</head\>

\<body\>

    Welcome To TryHackMe.com

\</body\>

\</html\>

![][image2]

## **HTTP Methods**

HTTP methods are a way for the client to show their intended action when making an HTTP request. There are a lot of HTTP methods but we'll cover the most common ones, although mostly you'll deal with the GET and POST method. 

### **GET**

Retrieves information from a server.

GET /products

**POST**Submits data to a server.  
POST /login

**PUT** Updates existing resources.

**DELETE** Removes resources.

## **Status Codes**

Common status codes covered include:

| Code | Meaning |
| ----- | ----- |
| 200 | OK |
| 301 | Moved Permanently |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

Understanding these codes helps analysts identify abnormal web activity.

***What response code might you receive if you've created a new user or blog post article?***  
***Ans: 201***

***What response code might you receive if you've tried to access a page that doesn't exist?***  
***Ans: 404***

***What response code might you receive if the web server cannot access its database and the application crashes?***  
***Ans: 503***

***What response code might you receive if you try to edit your profile without logging in first?***  
***Ans: 401***

## **Headers**

HTTP headers provide metadata about requests and responses.

HTTP request headers are sent by the client (browser) to provide information about the request and client capabilities.

* **Host** – Specifies the target website hosted on the server.  
* **User-Agent** – Identifies the browser and its version, helping servers deliver compatible content.  
* **Content-Length** – Indicates the size of data being sent in the request.  
* **Accept-Encoding** – Lists supported compression methods (e.g., gzip) to optimize data transfer.  
* **Cookie** – Stores user-related information and session data that is sent with requests.

Headers often contain valuable information during investigations.

***What header tells the web server what browser is being used?***  
***Ans: USER-AGENT***

***What header tells the browser what type of data is being returned?***  
***Ans: CONTENT-TYPE***

***What header tells the web server which website is being requested?***  
***Ans: HOST***

## **Cookies and Sessions**

Cookies allow websites to maintain user sessions.

![][image3]

Example:

Set-Cookie: sessionid=abc123

Session management is an important component of web application security.

## **Making Requests:**

***Make a GET request to /room page :***   
***Ans: THM{YOU'RE\_IN\_THE\_ROOM}***  
![][image4]

***Make a GET request to /blog page and set the id parameter to 1***   
***Ans: THM{YOU\_FOUND\_THE\_BLOG}***  
![][image5]

***Make a DELETE request to /user/1 page***  
***Ans: THM{USER\_IS\_DELETED}***  
![][image6]

***Make a PUT request to /user/2 page with the username parameter set to admin***   
***Ans: THM{USER\_HAS\_UPDATED}***  
![][image7]

***Make a POST request to /login page with the username of thm and a password of letmein*** 

***Ans: THM{HTTP\_REQUEST\_MASTER}***  
![][image8]

## **Security Relevance**

Understanding HTTP helps analysts investigate:

* Web attacks  
* Brute-force attempts  
* Session hijacking  
* Authentication abuse  
* Malicious user activity

## **Key Takeaways**

* HTTP forms the backbone of web communication.  
* Requests and responses contain critical forensic information.  
* Status codes provide insight into application behavior.  
* Cookies and headers are valuable during investigations.  
* Understanding HTTP improves web security analysis.


