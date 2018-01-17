## 7. Authentication and Authrization
### Authetication
* Authentication is a process of obtaining some sort of credentials from the users and to verify user's identity. For example when you try to enter into you college gate, you show your identy card. The card verifies your identity.
### Authorization
* Authrization is the process of allowing an authenticated user access to resources. For example, Students of first year can not enter into room of Third year students. Even if they are authenticated (from the gate, after showing cards), they are not authorized to enter into that room.
### Authentication Provides in ASP.NET
There are mainly three options for authentication:
* Windows Authentication  
This authenticates based on windows account. This optionn uses IIS to perform the authentication and then passes authenticated identity to you code.
* Forms Authentication  
It uses custom HTML forms to collect authentication information and lets you use your own logic to authenticate users. Users credentials are stored in a cookie for use during the session.
* ASP.NET Identity  
Authentication using social networking accounts like Facebook, Gmail, Twitter etc. is possible through ASP.NET Identity.

### References:
1. http://www.c-sharpcorner.com/article/authentication-and-authorization-in-Asp-Net/
2. https://docs.microsoft.com/en-us/aspnet/identity/overview/getting-started/introduction-to-aspnet-identity