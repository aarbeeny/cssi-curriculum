---
  layout: post
  title: Template Variables
  language: app-engine
---

###  Using Variables in Templates
In Jinja, the syntax for interpolating strings is to put the expression between mustaches, like this: {{ variable }}.

In hello.html, instead of Hello World, write Hello {{ name }}. Now our page will change to greet anyone whose name is stored in the variable 'name'.

###  Passing Variables to the Template
In order for Jinja to have access to the variable when it renders the template, we need to pass the variable 'name' from our controller, helloworld.py and pass it to the template, hello.html.

In our helloworld.py:

```python
class HelloHandler(webapp2.RequestHandler):
  def get(self):
    template_vars = {"name": "CSSI Chicago"}
    template = jinja_environment.get_template('templates/hello.html')
    self.response.out.write(template.render(template_vars))
```
Every time we call render(), we can pass it a dictionary of values as an argument. The variables in the dictionary are passed to the template, and are then available in the template.

##  Getting Data from the Request
We’ve made our HelloWorld app a little smarter, because we can pass it a dictionary of key-value pairs and use them in the template. But right now that key:value pair is hardcoded in our handler. Instead, let's get the data from the user.

###  Data in HTTP GET requests
We know that the user will be sending a GET request, and our app will route the request to a handler and respond with a page. GET requests can contain data! For instance, Facebook uses a URL parameter called login_attempt to keep track of how many times you have tried to login.

`https://www.facebook.com/login.php?login_attempt=1`

Everything after the ? in a url is called the query string. Everything before the ? is the route that is matched, and the data in the query string is available in the handler.

####  The Query String
Query strings are almost always a set of paired parameter names and values, separated by ampersands (&). A complex url might look like this:

`http://api.umd.io/v0/courses?dept_id=CMSC&semester=201501&credits=3&department=Computer%20Science&grading_method=Audit`

The protocol is specified in `http://`

The route is `api.umd.io/v0/courses`

The url parameters are:

| parameter       | value        |
| -------------   |-------------|
| dept_id         | CMSC        |
| semester        | 20150       |
| credits         | 3           |
| department      | Computer Science   |
| grading_method  | Audit       |



###  Accessing the URL Parameters
In your handler, you can use self.request.get() to access the url parameters.

Here's an updated HelloWorld Handler in helloworld.py that gets the 'name' parameter from the url and passes it into the template.

```python
class HelloHandler(webapp2.RequestHandler):
  def get(self):
    template_vars = {'name': self.request.get('name')}
    template = jinja_environment.get_template('templates/hello.html')
    self.response.out.write(template.render(template_vars))
```
Notice that in this handler, we are defining how to respond to a GET request (`def get(self):`). This handler is perfect for getting data from the URL.

# Conclusion
Template variables are passed from the handler to the template as an argument in the render() function. The variables can either be a dictionary or a list. To get variables from a url, use `self.request.get()`.