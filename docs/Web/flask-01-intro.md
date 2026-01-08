# Flask: Intro

## 1. What Is Flask?

**Flask** is a lightweight **Python web framework** used to build web applications and APIs.

Key features:

-   Simple and easy to learn
-   Minimal and flexible (micro-framework)
-   Uses Python
-   Perfect for small projects, APIs, and learning web development

Flask does **not** force a project structure or many dependencies—you add only what you need.

------

## 2. Prerequisites

Before learning Flask, you should know:

-   Basic Python (functions, variables, imports)
-   How to use the terminal
-   Basic HTTP concepts (URL, request, response)

Check Python version:

```bash
python3 --version
```

Recommended: **Python 3.8+**

------

## 3. Installing Flask

It’s best to use a **virtual environment**.

### 3.1 Create a virtual environment

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

### 3.2 Install Flask

```bash
pip install flask
```

Verify installation:

```bash
python -c "import flask; print(flask.__version__)"
```

------

## 4. Your First Flask App (Hello World)

Create a file named **`app.py`**:

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello, Flask!"

if __name__ == "__main__":
    app.run(debug=True)
```

Run the app:

```bash
python app.py
```

Open your browser:

```
http://127.0.0.1:5000/
```

You should see:

```
Hello, Flask!
```

------

## 5. Understanding the Code

```python
from flask import Flask
```

Imports the Flask class.

```python
app = Flask(__name__)
```

Creates a Flask application instance.

```python
@app.route("/")
```

Defines a **route** (URL path).

```python
def hello():
    return "Hello, Flask!"
```

Function that handles requests to `/`.

```python
app.run(debug=True)
```

Starts the development server.

-   `debug=True` enables auto-reload and error messages.

------

## 6. Routing (URLs)

### 6.1 Basic Routes

```python
@app.route("/about")
def about():
    return "About Page"
```

Visit:

```
/about
```

------

### 6.2 Dynamic Routes

```python
@app.route("/user/<name>")
def user(name):
    return f"Hello, {name}!"
```

Example:

```
/user/Alice
/user/Bob
```

------

### 6.3 Route with Type

```python
@app.route("/post/<int:post_id>")
def post(post_id):
    return f"Post ID: {post_id}"
```

Common converters:

-   `int`
-   `float`
-   `string`
-   `path`

------

## 7. HTTP Methods (GET, POST)

By default, Flask routes accept **GET** only.

### 7.1 GET and POST Example

```python
from flask import request

@app.route("/login", methods=["GET", "POST"])
def login():
    if request.method == "POST":
        return "Logging in..."
    return "Login Page"
```

------

## 8. Templates (HTML with Jinja2)

Flask uses **Jinja2** for templates.

### 8.1 Project Structure

```
project/
│── app.py
└── templates/
    └── index.html
```

------

### 8.2 HTML Template (`templates/index.html`)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Flask</title>
</head>
<body>
    <h1>Hello {{ name }}</h1>
</body>
</html>
```

------

### 8.3 Render Template in Flask

```python
from flask import render_template

@app.route("/")
def home():
    return render_template("index.html", name="Flask")
```

------

## 9. Static Files (CSS, JS, Images)

### 9.1 Structure

```
project/
│── app.py
│── templates/
│── static/
    └── style.css
```

### 9.2 CSS File (`static/style.css`)

```css
body {
    background-color: #f4f4f4;
}
```

### 9.3 Use in HTML

```html
<link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
```

------

## 10. Handling Form Data

### 10.1 HTML Form

```html
<form method="post">
    <input type="text" name="username">
    <button type="submit">Submit</button>
</form>
```

### 10.2 Flask Code

```python
from flask import request

@app.route("/submit", methods=["GET", "POST"])
def submit():
    if request.method == "POST":
        username = request.form["username"]
        return f"Hello, {username}"
    return render_template("form.html")
```

------

## 11. Returning JSON (API)

Flask is great for APIs.

```python
from flask import jsonify

@app.route("/api/user")
def api_user():
    return jsonify({
        "name": "Alice",
        "age": 20
    })
```

------

## 12. Error Handling

### 12.1 Custom 404 Page

```python
@app.errorhandler(404)
def not_found(error):
    return "Page not found", 404
```

------

## 13. Project Structure (Recommended)

```
project/
│── app.py
│── templates/
│── static/
│── venv/
│── requirements.txt
```

Generate dependencies:

```bash
pip freeze > requirements.txt
```

------

## 14. Flask vs Django (Brief)

| Feature        | Flask            | Django         |
| -------------- | ---------------- | -------------- |
| Complexity     | Simple           | Full-featured  |
| Flexibility    | High             | Opinionated    |
| Learning Curve | Easy             | Steeper        |
| Use Case       | Small apps, APIs | Large web apps |

------

## 15. What to Learn Next

After Flask basics:

-   Blueprints
-   Flask-SQLAlchemy (database)
-   Flask-Login (authentication)
-   RESTful APIs
-   Deployment (Gunicorn, Nginx, Docker)

------

## 16. Summary

-   Flask is a lightweight Python web framework
-   Easy to start, powerful when extended
-   Perfect for beginners and APIs
-   Grows with your project