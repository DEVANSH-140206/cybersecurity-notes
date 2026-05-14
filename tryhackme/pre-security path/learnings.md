# MODULE 1

---

## IP Address
- Identifies a device on a network.
- Types:
  - Public IP → visible on internet.
  - Private IP → used inside local networks.
- IPv4 example:
```bash
192.168.1.1
```

### Important
- Devices in same network usually have similar starting numbers.
- IP addresses can change (dynamic IPs).

---

## MAC Address
- Unique hardware address of a device.
- Works at Layer 2 (Data Link Layer).
- Example:
```bash
00:1A:2B:3C:4D:5E
```

### Important
- Used for communication inside local network.
- Usually permanent.
- Can be spoofed/changed.

---

## IP vs MAC Address

| IP Address | MAC Address |
|---|---|
| Logical address | Physical hardware address |
| Can change | Usually fixed |
| Used across networks/internet | Used inside local network |
| Layer 3 | Layer 2 |

---

## MAC Spoofing
- Changing visible MAC address of a device.
- Used for:
  - Privacy
  - Security testing
  - Bypassing MAC filters

### Note
- Can also be abused maliciously.

---

## Ping Command
Used to test connectivity between devices.

### Basic Usage
```bash
ping google.com
```

### Important Things
- Checks if target is reachable.
- Shows latency (response time).
- Detects packet loss.

### Terms
- `TTL` → Time To Live
- `time=` → response speed in milliseconds

### Useful Command
```bash
ping -c 4 google.com
```

---

## ifconfig Command
Used to view network interface information in Linux.

### Basic Usage
```bash
ifconfig
```

### Important Fields
- `inet` → IPv4 address
- `ether` → MAC address
- `RX packets` → received data
- `TX packets` → transmitted data
- `netmask` → network range
- `broadcast` → sends data to all devices in network

### What I Practiced
- Checked real IP address.
- Checked real MAC address.
- Understood sections of `ifconfig` output.
- Used `ping` for connectivity testing.

---

## Commands To Remember
```bash
ifconfig
ping google.com
ping -c 4 google.com
```

---

## Quick Revision
- IP = identifies device on network.
- MAC = identifies hardware.
- Ping = tests connectivity.
- ifconfig = shows network details.
- MAC spoofing = changing visible MAC address.






# Module 2 - DNS

---

## DNS (Domain Name System)
- DNS gives names to IP addresses.
- Makes websites easier for humans to remember.

Example:
```text
142.x.x.x → google.com
```

### Important
- Without DNS, we would need to remember IP addresses.
- DNS helps connect domain names to IP addresses.

---

## Domain Structure

Example:
```text
sub.example.com
```

### Parts
- `.com` → Top Level Domain (TLD)
- `example` → Second Level Domain
- `sub` → Subdomain

---

## Top Level Domain (TLD)
- Last part of domain name.

Examples:
```text
.com
.org
.net
.edu
```

---

## Second Level Domain
- Main name of website.

Example:
```text
google
```

---

## Subdomain
- Small section added before main domain.

Examples:
```text
mail.google.com
blog.website.com
```

---

## DNS Record Types

### A Record
- Connects domain to IPv4 address.

---

### AAAA Record
- Connects domain to IPv6 address.

---

### MX Record
- Used for mail servers.

---

### CNAME Record
- Alias for another domain.

---

### TXT Record
- Stores text information in DNS.

---

## TTL (Time To Live)
- Shows how long DNS information is stored before refreshing.

---

## dig Command
Used to get DNS information.

### Commands Practiced
```bash
dig google.com
dig +short google.com
dig google.com A
dig google.com MX
dig google.com CNAME
```

### What I Practiced
- Extracted DNS records.
- Used `+short` for shorter output.
- Viewed TTL values.

---

## nslookup Command
Used for DNS lookups.

### Commands Practiced
```bash
nslookup google.com
nslookup 8.8.8.8
nslookup -type=MX google.com
```

### What I Practiced
- Converted domain → IP.
- Converted IP → domain.
- Checked DNS record types.

---

## Quick Revision
- DNS gives names to IP addresses.
- TLD = `.com`, `.org`, etc.
- Subdomain comes before main domain.
- A = IPv4
- AAAA = IPv6
- MX = mail server
- CNAME = alias
- TXT = text information
- dig = DNS info tool
- nslookup = DNS lookup tool
- TTL = DNS cache time


# HTTP IN DETAIL


# 1. HTTP & HTTPS

## HTTP
HTTP (HyperText Transfer Protocol) is the protocol used for communication between a browser and a web server.

- Used to send requests and receive responses
- Data is usually sent in plain text
- Default Port: `80`

Example:
```http
http://example.com
```

---

## HTTPS
HTTPS = HTTP + Encryption using SSL/TLS

- Encrypts communication between client and server
- Protects passwords, cookies, and sensitive data
- Default Port: `443`
- Uses SSL/TLS certificates

Example:
```http
https://example.com
```

### Important
- HTTP = Not secure
- HTTPS = Secure & encrypted

---

# 2. URL (Uniform Resource Locator)

A URL is the address of a resource on the internet.

Example:
```http
https://tryhackme.com/login
```

## URL Structure

| Part | Meaning |
|---|---|
| `https://` | Protocol |
| `tryhackme.com` | Domain / Host |
| `/login` | Path / Resource |

---

# 3. HTTP Request Basics

Client sends a request → Server sends a response

Example:
```http
GET / HTTP/1.1
Host: example.com
```

---

# 4. HTTP Methods

| Method | Purpose |
|---|---|
| `GET` | Retrieve data |
| `POST` | Send/Create data |
| `PUT` | Update/Replace data |
| `DELETE` | Delete data |

---

## GET
Used to request data from a server.

Example:
```http
GET /profile HTTP/1.1
```

### Important
- Data often visible in URL
- Mainly used for fetching data
- Should not send passwords

---

## POST
Used to send data to the server.

Example:
```http
POST /login HTTP/1.1
```

### Important
- Data sent inside request body
- Used for logins, uploads, account creation

---

## PUT
Used to update existing resources.

Example:
```http
PUT /user/1 HTTP/1.1
```

---

## DELETE
Used to delete resources.

Example:
```http
DELETE /post/10 HTTP/1.1
```

---

# 5. HTTP Status Codes

Status codes tell whether a request succeeded or failed.

---

## Status Code Categories

| Range | Meaning |
|---|---|
| `100-199` | Informational Responses |
| `200-299` | Success |
| `300-399` | Redirection |
| `400-499` | Client Errors |
| `500-599` | Server Errors |

---

# 6. Important Status Codes

| Code | Meaning |
|---|---|
| `200` | OK |
| `201` | Created |
| `301` | Moved Permanently |
| `302` | Found / Temporary Redirect |
| `400` | Bad Request |
| `401` | Unauthorized |
| `403` | Forbidden |
| `404` | Page Not Found |
| `405` | Method Not Allowed |
| `500` | Internal Server Error |
| `503` | Service Unavailable |

---

# 7. Easy Status Code Memory Trick

## 2xx → Success
"Everything worked."

## 3xx → Redirect
"Go somewhere else."

## 4xx → Client Error
"You messed up the request."

## 5xx → Server Error
"Server failed."

---

# 8. HTTP Headers

Headers = Extra information attached to requests and responses.

Think of headers as:
> "Instructions & metadata"

---

# 9. Request Headers (Client → Server)

## Host
Tells the server which website you want.

```http
Host: tryhackme.com
```

### Important
One server can host multiple websites.

---

## User-Agent
Identifies browser/device.

```http
User-Agent: Mozilla/5.0
```

### Cybersecurity Importance
- Can be spoofed/faked
- Used for fingerprinting
- Used in bypass attempts

---

## Content-Length
Size of data being sent.

```http
Content-Length: 45
```

### Used In
- Uploads
- Login forms
- File transfers

---

## Accept-Encoding
Compression formats browser supports.

```http
Accept-Encoding: gzip, br
```

### Why Important
Makes websites load faster.

---

# 10. Response Headers (Server → Client)

## Set-Cookie
Server gives browser a session ID/cookie.

```http
Set-Cookie: sessionID=abc123
```

### Important
Used to remember logged-in users.

---

## Content-Type
Tells browser what file/data type was received.

```http
Content-Type: text/html
```

Examples:
```http
text/html
image/png
application/json
```

---

## Cache-Control
Controls browser caching.

```http
Cache-Control: max-age=3600
```

### Why Important
Makes websites faster by storing temporary copies.

---

# 11. Cookies

Cookies are small pieces of data stored in the browser.

Used for:
- Login sessions
- User preferences
- Tracking users

Example:
```http
Cookie: sessionID=abc123
```

---

# 12. Why Headers Matter In Cybersecurity

---

## Information Gathering

Headers may reveal server details.

Example:
```http
Server: Apache/2.4.41 (Ubuntu)
```

### Why Important
Attackers search for vulnerabilities in specific versions.

---

## Bypassing Filters

Attackers may modify:
- User-Agent
- Host
- Custom headers

to trick applications/security systems.

---

## Cookie Theft / Session Hijacking

If attackers steal session cookies:
- They may access accounts without passwords.

---

# 13. MOST IMPORTANT THINGS TO REMEMBER

## HTTP Flow
```text
Client Request → Server Response
```

---

## HTTPS
```text
HTTP + Encryption = HTTPS
```

---

## Main HTTP Methods
```text
GET    → Retrieve data
POST   → Send/Create data
PUT    → Update data
DELETE → Remove data
```

---

## Main Status Codes
```text
200 → Success
301/302 → Redirect
401 → Unauthorized
403 → Forbidden
404 → Not Found
500 → Server Error
503 → Service Unavailable
```

---

## Important Request Headers
```text
Host
User-Agent
Content-Length
Accept-Encoding
```

---

## Important Response Headers
```text
Set-Cookie
Content-Type
Cache-Control
```

---

# 14. Cybersecurity Focus

You should understand:
- Difference between HTTP & HTTPS
- Request vs Response
- GET vs POST
- Common status codes
- What headers do
- How cookies work
- Why headers matter in reconnaissance and attacks

---

# 15. 30 Second Revision

```text
HTTP = communication protocol
HTTPS = encrypted HTTP

GET = retrieve data
POST = send data
PUT = update
DELETE = remove

200 = success
404 = not found
403 = forbidden
500 = server error

Headers = metadata/instructions

Cookies = session tracking

Cybersecurity:
- Headers leak information
- User-Agent can be spoofed
- Cookies can be stolen
```

---



# HOW WEBSITES WORK

> TryHackMe — Pre Security Path  
> Fast Revision Notes

---

# 1. How Websites Work

A website works using:

```text
Client (Browser) ↔ Server
```

## Basic Flow
1. User enters a URL
2. Browser sends HTTP/HTTPS request
3. Server processes request
4. Server sends response
5. Browser displays website

---

# 2. Frontend vs Backend

| Frontend | Backend |
|---|---|
| What users see | Server-side logic |
| Runs in browser | Runs on server |
| UI / Design | Database & processing |
| HTML, CSS, JS | PHP, Python, Node.js, Java, etc |

---

# 3. Frontend

Frontend = Everything visible to the user.

Includes:
- Text
- Buttons
- Images
- Forms
- Animations

Main Technologies:
```text
HTML → Structure
CSS → Styling
JavaScript → Functionality
```

---

# 4. Backend

Backend handles:
- Authentication
- Databases
- Server logic
- User accounts
- Processing requests

Backend communicates with:
```text
Frontend ↔ Backend ↔ Database
```

---

# 5. HTML (HyperText Markup Language)

HTML creates the structure of a webpage.

Example:
```html
<h1>Hello</h1>
<p>This is a webpage</p>
```

### HTML Is Used For
- Headings
- Paragraphs
- Forms
- Buttons
- Links
- Images

---

# 6. JavaScript

JavaScript adds functionality and interactivity to websites.

Example Uses:
- Popups
- Animations
- Form validation
- Dynamic content
- Button actions

Example:
```javascript
alert("Hello")
```

---

# 7. View Page Source

Browsers allow viewing website source code.

Shortcut:
```text
CTRL + U
```

or:
```text
Right Click → View Page Source
```

---

# 8. Why View Source Is Important In Cybersecurity

Sensitive information may accidentally be exposed inside HTML source code.

Examples:
- Comments
- Hidden links
- API keys
- Developer notes
- Hidden pages
- Credentials (bad security practice)

Example:
```html
<!-- Admin Panel: /admin -->
```

---

# 9. Important Cybersecurity Habit

ALWAYS check:
```text
View Page Source
```

because developers sometimes leave sensitive information exposed.

---

# 10. HTML Injection

HTML Injection = Injecting HTML code into a webpage input.

Example:
```html
<h1>Hacked</h1>
```

If website improperly handles user input:
- Injected HTML may appear on webpage
- Can modify displayed content

---

# 11. Why HTML Injection Matters

Can be used to:
- Change webpage appearance
- Mislead users
- Test input handling
- Sometimes lead to bigger vulnerabilities

---

# 12. Important Difference

| HTML Injection | JavaScript Injection |
|---|---|
| Injects HTML tags | Injects JavaScript code |
| Changes page structure | Executes scripts/code |
| Usually less dangerous | More dangerous |

---

# 13. MOST IMPORTANT THINGS TO REMEMBER

## Website Flow
```text
Browser ↔ Server
```

---

## Frontend
```text
HTML → Structure
CSS → Design
JavaScript → Functionality
```

---

## Backend
```text
Handles logic, databases, authentication, processing
```

---

## View Source
```text
CTRL + U
```

### Always Check For:
- Hidden comments
- Sensitive data
- Hidden endpoints
- Developer notes

---

## HTML Injection
```text
Injecting HTML into webpage inputs
```

---

# 14. Cybersecurity Focus

You should understand:
- Frontend vs Backend
- Purpose of HTML
- Purpose of JavaScript
- Why source code inspection matters
- Why hidden data exposure is dangerous
- Basic idea of HTML Injection

---

# 15. 30 Second Revision

```text
Frontend = What users see
Backend = Server-side processing

HTML → Structure
CSS → Styling
JavaScript → Functionality

CTRL + U → View page source

Always check source code for:
- Hidden comments
- API keys
- Hidden links
- Sensitive data

HTML Injection = Injecting HTML into webpage inputs
```


# WEB INFRASTRUCTURE BASICS

> TryHackMe — Pre Security Path  
> Fast Revision Notes

---

# 1. Web Server

A web server handles HTTP/HTTPS requests and serves website content to users.

Example Web Servers:
```text
Apache
Nginx
IIS
```

---

# 2. What A Web Server Does

- Receives requests from browsers
- Processes requests
- Sends responses
- Hosts websites/web applications

Flow:
```text
Browser → Web Server → Response
```

---

# 3. Static vs Dynamic Content

| Static Content | Dynamic Content |
|---|---|
| Same for every user | Changes depending on user/data |
| Fast/simple | Requires backend processing |
| HTML, CSS, images | Dashboard, login systems, feeds |

---

## Static Content Examples
```text
HTML files
CSS files
Images
Videos
```

---

## Dynamic Content Examples
```text
User profiles
Login systems
Comments
Dashboards
```

Dynamic content usually uses:
```text
Backend + Database
```

---

# 4. Virtual Hosts

Virtual Hosts allow one web server/IP address to host multiple websites.

Example:
```text
example1.com
example2.com
example3.com
```

All can run on:
```text
Same server
Same IP address
```

---

# 5. Why Virtual Hosts Matter In Cybersecurity

Sometimes hidden websites/subdomains exist on the same server.

Attackers may discover:
- Hidden admin panels
- Development sites
- Test environments

---

# 6. Load Balancers

Load Balancer distributes traffic across multiple servers.

Purpose:
- Prevent overload
- Improve speed
- Increase reliability

Flow:
```text
Users → Load Balancer → Multiple Servers
```

---

# 7. Round Robin Load Balancing

Requests are distributed equally between servers.

Example:
```text
Request 1 → Server A
Request 2 → Server B
Request 3 → Server C
```

Then repeats.

---

# 8. Weighted Load Balancing

Traffic distribution depends on server power/capacity.

Example:
```text
Strong server → More traffic
Weak server → Less traffic
```

---

# 9. Content Delivery Network (CDN)

CDN = Network of servers distributed globally.

Purpose:
- Deliver content faster
- Reduce latency
- Reduce server load

Examples:
```text
Cloudflare
Akamai
```

---

# 10. How CDN Works

Instead of loading content from one distant server:
```text
User gets data from nearest CDN server
```

Benefits:
- Faster websites
- Better performance
- DDoS protection

---

# 11. Databases

Databases store website/application data.

Examples:
```text
User accounts
Passwords
Posts
Messages
```

Popular Databases:
```text
MySQL
PostgreSQL
MongoDB
```

---

# 12. Backend & Database Connection

Flow:
```text
Frontend ↔ Backend ↔ Database
```

Example:
```text
Login form → Backend checks database → Access granted
```

---

# 13. Web Application Firewall (WAF)

WAF filters and monitors HTTP traffic.

Purpose:
- Block malicious requests
- Protect web applications

---

# 14. What WAF Can Block

Examples:
- SQL Injection
- XSS
- Malicious bots
- Suspicious traffic

---

# 15. Why WAF Matters In Cybersecurity

Attackers may try to:
- Bypass WAF rules
- Evade detection
- Modify payloads

---

# 16. MOST IMPORTANT THINGS TO REMEMBER

## Web Server
```text
Handles HTTP/HTTPS requests
Serves website content
```

---

## Static vs Dynamic
```text
Static → Same for everyone
Dynamic → Changes using backend/database
```

---

## Virtual Hosts
```text
One server can host multiple websites
```

---

## Load Balancer
```text
Distributes traffic across servers
```

### Round Robin
```text
Equal distribution
```

### Weighted
```text
More powerful server gets more traffic
```

---

## CDN
```text
Global servers delivering content faster
```

---

## Database
```text
Stores website data
```

---

## WAF
```text
Filters malicious web traffic
```

---

# 17. Cybersecurity Focus

You should understand:
- Purpose of web servers
- Difference between static & dynamic content
- How load balancers work
- Why CDNs exist
- Role of databases
- What WAF does
- Why virtual hosts matter in recon

---

# 18. 30 Second Revision

```text
Web Server → Handles requests

Static → Same content
Dynamic → Backend + database

Virtual Hosts → Multiple websites on one server

Load Balancer → Distributes traffic

Round Robin → Equal traffic
Weighted → Based on server power

CDN → Faster delivery using nearby servers

Database → Stores application data

WAF → Blocks malicious requests
```

# OPERATING SYSTEM & WINDOWS BASICS

> TryHackMe — Pre Security Path  
> Fast Revision Notes

---

# 1. Operating System (OS)

Operating System = Core software managing:
- Hardware
- Applications
- Memory
- System resources

Examples:
```text
Windows
Linux
macOS
```

---

# 2. Kernel Space vs User Space

| Kernel Space | User Space |
|---|---|
| Full hardware access | Limited permissions |
| Core OS functions | Regular applications |
| Highly privileged | Restricted for safety |

---

## Important
```text
Kernel = Highest privilege level
```

Compromising kernel access = Extremely dangerous.

---

# 3. GUI vs CLI

| GUI | CLI |
|---|---|
| Graphical interface | Text-based interface |
| Easier for beginners | Faster & more powerful |
| Uses windows/icons | Uses commands |

---

## Cybersecurity Importance

### GUI
Good for:
- General navigation
- Basic management

### CLI
Preferred in:
- Linux
- Hacking
- Automation
- Scripting
- Server management

---

# 4. File Explorer

Used to:
- Browse files/folders
- Manage directories
- View file structures

Cybersecurity use:
```text
Finding logs
Analyzing files
Navigating systems
```

---

# 5. Task Manager

Used to monitor:
- Running processes
- CPU/RAM usage
- Background applications

Shortcut:
```text
CTRL + SHIFT + ESC
```

---

## Cybersecurity Importance

Useful for:
- Detecting suspicious processes
- Checking malware activity
- Monitoring resource usage

---

# 6. Windows Security

Central dashboard for built-in Windows protection.

Includes:
- Antivirus
- Firewall
- Threat protection

---

# 7. Windows Defender Firewall

Filters incoming/outgoing network traffic.

Purpose:
```text
Block unauthorized access
```

---

## Firewall Importance In Cybersecurity

Firewalls help:
- Block malicious connections
- Restrict network access
- Protect devices from attacks

---

# 8. Windows Update

Keeps:
- OS
- Security patches
- System components

updated.

---

## Cybersecurity Importance

Updates patch:
- Vulnerabilities
- Exploits
- Security flaws

Outdated systems are common attack targets.

---

# 9. MOST IMPORTANT THINGS TO REMEMBER

## OS
```text
Manages hardware, software, and resources
```

---

## Kernel Space
```text
Highest privilege level
Direct hardware access
```

---

## User Space
```text
Regular applications run here
```

---

## CLI
```text
Important for cybersecurity & Linux
```

---

## Task Manager
```text
Monitor running processes
Detect suspicious activity
```

---

## Firewall
```text
Filters network traffic
Blocks unauthorized access
```

---

## Windows Updates
```text
Patch vulnerabilities & security flaws
```

---

# 10. 30 Second Revision

```text
OS → Manages system resources

Kernel Space → Highest privileges
User Space → Regular apps

GUI → Graphical
CLI → Command-based

Task Manager → Monitor processes

Firewall → Filters traffic

Windows Updates → Patch vulnerabilities
```


