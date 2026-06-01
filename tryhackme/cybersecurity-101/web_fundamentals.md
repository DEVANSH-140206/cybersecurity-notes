# Web Application Fundamentals (The "Post Office" Analogy)

> TryHackMe — Quick Revision Notes

---

# 1. The Big Picture (Frontend vs Backend)

Imagine a restaurant:

| Frontend | Backend |
|-----------|----------|
| Dining Room | Kitchen |
| What customers see | What customers don't see |
| HTML, CSS, JavaScript | Databases, Storage, APIs, Firewalls |

---

## Frontend (Client Side)

What the user interacts with:

- Buttons
- Forms
- Images
- Menus
- Web pages

Main Technologies:

```text
HTML → Structure
CSS → Appearance
JavaScript → Interactivity
```

---

## Backend (Server Side)

Handles:

- Logins
- Databases
- File storage
- Security checks
- Business logic

Think:

```text
Frontend = Taking the order

Backend = Cooking the food
```

---

# 2. Anatomy of a URL (The Mailing Address)

Example:

```text
https://tryhackme.com:443/room/web?level=easy#section1
```

---

| URL Part | Example | Analogy |
|-----------|---------|----------|
| Scheme | https:// | Delivery method |
| Host | tryhackme.com | Building address |
| Port | :443 | Which door to enter |
| Path | /room/web | Specific room |
| Query String | ?level=easy | Special instructions |
| Fragment | #section1 | Exact paragraph/page |

---

## Port Examples

| Port | Purpose |
|--------|---------|
| 80 | HTTP |
| 443 | HTTPS |

---

## Query String Example

```text
?user=alice&id=5
```

Think:

```text
Extra instructions attached to the request
```

---

## Fragment Example

```text
#comments
```

Think:

```text
Open the page directly at the comments section
```

---

## Security Warning: Typosquatting

Attackers register look-alike domains.

Example:

```text
google.com      ← Real
gooogle.com     ← Fake
g00gle.com      ← Fake
```

Purpose:

```text
Trick users into visiting malicious websites
```

---

# 3. HTTP Requests & Responses (The Conversation)

The web is simply:

```text
Browser asks
↓
Server replies
```

---

## Request

```text
"Can I have this page?"
```

---

## Response

```text
"Sure, here it is."
```

---

# 4. HTTP Methods (The Verbs)

| Method | Meaning | Simple Action | Security Tip |
|----------|----------|---------------|--------------|
| GET | Retrieve data | Look at something | Never put passwords in URL |
| POST | Create/send data | Create something | Common in login forms |
| PUT | Replace data | Replace something | Can modify resources |
| DELETE | Remove data | Destroy something | Dangerous if access control fails |
| PATCH | Modify part of data | Edit something | Often used in APIs |
| HEAD | Get headers only | Peek without opening | Useful for reconnaissance |
| OPTIONS | Ask what is allowed | Check the rules | Shows supported methods |
| CONNECT | Create tunnel | Open secure channel | Used by proxies |

---

# Easy Memory Trick

```text
GET    → Read
POST   → Create
PUT    → Replace
PATCH  → Edit
DELETE → Remove
```

---

# 5. Request Headers (The Passport Control)

Headers are:

```text
Extra information attached to requests
```

Think:

```text
Passport details attached to a traveler
```

---

## Host

```http
Host: tryhackme.com
```

Meaning:

```text
Who is this request for?
```

---

## User-Agent

```http
User-Agent: Chrome
```

Meaning:

```text
What device/browser am I using?
```

---

## Referer

```http
Referer: https://google.com
```

Meaning:

```text
Where did I come from?
```

---

## Cookie

```http
Cookie: sessionid=abc123
```

Meaning:

```text
My digital nametag
```

Used for:

- Sessions
- Logins
- User tracking

---

# 6. Response Status Codes (The Quick Answers)

---

## 1xx → Hold On...

```text
"Wait, I'm still processing."
```

Example:

```text
100 Continue
```

---

## 2xx → Success!

```text
Everything worked
```

Example:

```text
200 OK
201 Created
```

---

## 3xx → Go Over There Instead

```text
Resource moved
```

Example:

```text
301 Moved Permanently
302 Found
```

---

## 4xx → You Messed Up

```text
Problem with the request
```

Examples:

```text
401 Unauthorized
403 Forbidden
404 Not Found
```

---

## 5xx → The Server Messed Up

```text
Problem on the server side
```

Examples:

```text
500 Internal Server Error
503 Service Unavailable
```

---

# Easy Memory Trick

```text
1xx = Hold On

2xx = Success

3xx = Redirect

4xx = Client Error

5xx = Server Error
```

---

# 7. Security Headers (The Bouncers)

Think of a castle protected by security guards.

These headers help defend websites.

---

## Content-Security-Policy (CSP)

### The Guest List

Controls:

```text
Which websites are allowed
to provide code, scripts, and content
```

Purpose:

```text
Blocks many XSS attacks
```

---

## Strict-Transport-Security (HSTS)

### The Armored Car Rule

Forces:

```text
HTTPS only
```

Even if the user tries HTTP.

Purpose:

```text
Prevents downgrade attacks
```

---

## X-Content-Type-Options: nosniff

### Stop Guessing!

Browser must:

```text
Trust the file label
```

Not guess the content type.

Purpose:

```text
Prevents file-type confusion attacks
```

---

## Referrer-Policy

### Don't Gossip

Controls:

```text
How much information about
the previous page gets shared
```

Purpose:

```text
Protect user privacy
```

---

# 8. MOST IMPORTANT THINGS TO REMEMBER

```text
Frontend = What users see
Backend = What servers do

URL:
Scheme → Host → Port → Path → Query → Fragment

GET = Read
POST = Create
PUT = Replace
PATCH = Edit
DELETE = Remove

Cookie = Digital nametag

2xx = Success
4xx = Client error
5xx = Server error

CSP = Guest list
HSTS = HTTPS only
nosniff = Stop guessing
Referrer-Policy = Don't gossip
```

---

# 9. 30 Second Revision

```text
Frontend = HTML, CSS, JavaScript

Backend = Database, Storage, Security

Browser sends Request
Server sends Response

GET → Read
POST → Create
DELETE → Remove

Host → Destination
Cookie → Identity

200 → Success
404 → Not Found
500 → Server Error

CSP → Allowed code
HSTS → Force HTTPS
```