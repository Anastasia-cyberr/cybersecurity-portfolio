# HTB - Appointment

- Platform: Hack The Box - Starting Point
- OS: Kali Linux
- Difficulty: Very Easy
- Date: 28.11.2026

## Recon

Started with a TCP port scan using Nmap:

`nmap -sT 10.129.X.X`

The scan revealed one open port:

`PORT   STATE SERVICE
80/tcp open  http`

Next, performed a service version scan:

`nmap -sV -p 80 10.129.X.X`

The scan identified the following service:

`PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.38 ((Debian))`

## Enumeration

Visited the website and discovered a login page.
<img width="1100" height="695" alt="image" src="https://github.com/user-attachments/assets/4724fa7e-4b1c-41f2-a868-3fe9f87ffc38" />

## Exploitation

Intercepted the login request using Burp Suite and tested the username parameter for SQL injection.

Used the following payload in the username field:

`admin'#`

The injection allowed me to bypass the login page and access the application without knowing the administrator's password.

## Key Takeaways

Learned how SQL injection can be used to bypass authentication.

Practiced intercepting and modifying HTTP POST requests with Burp Suite.

Learned how SQL quotes and comments can affect query execution.
