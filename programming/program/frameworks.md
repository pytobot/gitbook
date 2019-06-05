# Frameworks

## Framework

To strucure our program a framework is used. A framework provides you with the certainty that you are developing an application that is in full compliance with the business rules.

It allows developers to save time by re-using generic modules in order to focus on other areas. Without, however, ever being tied to the framework itself.

## Integration

In order to choose the best suited framework, a little research was done to see what framework filled the tasks we had. The main task is a good interaction with REST and API's. 

## NodeJS

NodeJS is a realy big framework, and the first framework that was tested before desiding to write the code in Python. The first reschearche was done in JavaScript. But because Javascript doesnt had the many libraries as Python on Hardware the choice went to go further into Python.

## Django

Django is one of the biggest frameworks in Python and has a good interaction with API's and hardware, Therefor was Django to most logitical framework to go for. 

Though Django is the most obvieus choice wasn't is the fastes way to have a quick demo.  
Therefor was the first Demo created With Flask

## Flask

Flask is a microframework for Python, Its one of the most easy's ways to setup a simple webserver 

The following code shows a simple web application that prints "Hello World!":

```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

if __name__ == "__main__":
    app.run()
```
