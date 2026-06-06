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
<img width="799" height="775" alt="Screenshot 2026-06-06 224123" src="https://github.com/user-attachments/assets/8d30f2e0-3181-4af9-bde7-1ba366105a53" />
<img width="784" height="226" alt="Screenshot 2026-06-06 223144" src="https://github.com/user-attachments/assets/47dbafec-50f7-4569-9492-4871ac45ee5d" />


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
<img width="799" height="775" alt="Screenshot 2026-06-06 224123" src="https://github.com/user-attachments/assets/b284b208-eada-4f05-abde-136373498c63" />




Example:

Set-Cookie: sessionid=abc123

Session management is an important component of web application security.

## **Making Requests:**

***Make a GET request to /room page :***   
***Ans: THM{YOU'RE\_IN\_THE\_ROOM}***  
<img width="822" height="634" alt="Screenshot 2026-06-06 230414" src="https://github.com/user-attachments/assets/655e5f74-02c6-4c64-9f94-8af17710ea56" />



***Make a GET request to /blog page and set the id parameter to 1***   
***Ans: THM{YOU\_FOUND\_THE\_BLOG}***  

<img width="597" height="638" alt="Screenshot 2026-06-06 230729" src="https://github.com/user-attachments/assets/631565dc-640a-4837-91f5-fe35cbe724ec" />


***Make a DELETE request to /user/1 page***  
***Ans: THM{USER\_IS\_DELETED}***  
<img width="811" height="658" alt="Screenshot 2026-06-06 230857" src="https://github.com/user-attachments/assets/570177de-bc85-45c8-9c36-d1a15702ea5b" />


***Make a PUT request to /user/2 page with the username parameter set to admin***   
***Ans: THM{USER\_HAS\_UPDATED}***  
<img width="762" height="719" alt="Screenshot 2026-06-06 231349" src="https://github.com/user-attachments/assets/3dd4d688-f6a8-4588-802b-b05cebf131e0" />


***Make a POST request to /login page with the username of thm and a password of letmein*** 

***Ans: THM{HTTP\_REQUEST\_MASTER}***  

<img width="750" height="704" alt="Screenshot 2026-06-06 231630" src="https://github.com/user-attachments/assets/fb435ed8-339f-45b1-9301-3ff9a5b21782" />

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


