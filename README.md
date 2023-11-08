 ```
# app.py

from flask import Flask, request, render_template

app = Flask(__name__)

@app.route('/', methods=['GET', 'POST'])
def index():
    if request.method == 'POST':
        full_name = request.form.get('full_name')
        first_name, last_name = full_name.split(' ')
        return render_template('index.html', first_name=first_name, last_name=last_name)
    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True)
```

```
# index.html

<!DOCTYPE html>
<html>
<head>
    <title>Split Name</title>
</head>
<body>
    <h1>Split Name</h1>
    <form action="/" method="post">
        <input type="text" name="full_name" placeholder="Enter your full name">
        <input type="submit" value="Split">
    </form>
    {% if first_name and last_name %}
        <p>First Name: {{ first_name }}</p>
        <p>Last Name: {{ last_name }}</p>
    {% endif %}
</body>
</html>
```