# HTML Fundamentals for Cybersecurity

> TryHackMe — Quick Revision Notes

---

# What is HTML?

**HTML (HyperText Markup Language)** is the language used to structure web pages.

Think:

```text
HTML = Skeleton
CSS = Appearance
JavaScript = Behavior
```

---

# Basic HTML Structure

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Page</title>
</head>
<body>
    Content goes here
</body>
</html>
```

---

# Most Important Tags

| Tag | Purpose |
|-------|---------|
| `<html>` | Root of webpage |
| `<head>` | Metadata/settings |
| `<title>` | Browser tab title |
| `<body>` | Visible content |
| `<h1>` - `<h6>` | Headings |
| `<p>` | Paragraph |
| `<a>` | Hyperlink |
| `<img>` | Image |
| `<div>` | Generic container |
| `<span>` | Inline container |
| `<br>` | Line break |

---

# Hyperlinks

```html
<a href="https://example.com">Visit Site</a>
```

### Important Attribute

```html
href
```

Specifies destination URL.

### Cybersecurity Relevance

```text
Check links for:
- Phishing
- Malicious redirects
- Typosquatting
```

---

# Images

```html
<img src="image.png" alt="Profile Picture">
```

### Important Attributes

| Attribute | Purpose |
|------------|---------|
| `src` | Image location |
| `alt` | Alternative text |

---

# Attributes

Attributes provide extra information to HTML elements.

Example:

```html
<a href="https://tryhackme.com">
```

Here:

```text
href = Attribute
https://tryhackme.com = Value
```

---

# Common Attributes

| Attribute | Purpose |
|------------|---------|
| `id` | Unique identifier |
| `class` | Group elements |
| `href` | Link destination |
| `src` | File source |
| `name` | Form field name |
| `value` | Stored value |
| `type` | Input type |

---

# Forms (Very Important)

Forms collect user input.

```html
<form>
</form>
```

Examples:

- Login forms
- Registration forms
- Search bars

---

# Input Fields

```html
<input type="text">
```

---

## Common Input Types

| Type | Purpose |
|--------|---------|
| `text` | Text input |
| `password` | Password field |
| `email` | Email address |
| `number` | Numbers |
| `submit` | Submit form |
| `checkbox` | Tick box |
| `radio` | Single choice |

---

# Buttons

```html
<button>Login</button>
```

Used to:

- Submit forms
- Trigger actions
- Run JavaScript

---

# Form Submission

```html
<form action="/login" method="POST">
```

### Important Attributes

| Attribute | Purpose |
|------------|---------|
| `action` | Where data is sent |
| `method` | How data is sent |

---

## Methods

### GET

```html
method="GET"
```

Data appears in URL.

Example:

```text
site.com/search?q=linux
```

---

### POST

```html
method="POST"
```

Data sent in request body.

Used for:

```text
Logins
Registration
Sensitive data
```

---

# Lists

## Unordered List

```html
<ul>
    <li>Item</li>
</ul>
```

---

## Ordered List

```html
<ol>
    <li>Item</li>
</ol>
```

---

# Tables

```html
<table>
<tr>
    <th>Name</th>
</tr>
<tr>
    <td>Yami</td>
</tr>
</table>
```

Used to organize data into rows and columns.

---

# Comments

```html
<!-- Secret Note -->
```

### Cybersecurity Tip

Always check page source.

Sometimes developers accidentally expose:

```text
- API Keys
- Passwords
- Internal URLs
- Hidden Notes
```

---

# View Page Source

Browser:

```text
Right Click → View Page Source
```

Useful for:

```text
Information Gathering
Finding Hidden Content
Discovering Endpoints
```

---

# HTML Injection

Occurs when user-controlled HTML is inserted into a webpage.

Example:

```html
<b>Hello</b>
```

May change page content.

Can sometimes lead to:

```text
Cross-Site Scripting (XSS)
```

---

# Most Important Cybersecurity Notes

```text
Always inspect page source.

Check comments for hidden information.

Understand forms:
- action
- method
- input fields

GET = Data in URL
POST = Data in request body

Look for:
- Hidden fields
- Hidden links
- Developer comments

HTML Injection can lead to XSS.
```

---

# 30-Second Revision

```text
HTML = Structure of webpage

Important Tags:
html
head
title
body
a
img
div
form
input
button

Attributes:
href
src
id
class
name
value

Forms:
action = destination
method = GET or POST

Security:
View Source
Check Comments
Look For Hidden Data
Understand HTML Injection
```