---
  layout: post
  title: JavaScript - Linking documents with the script tag
  language: javascript
---
# What You Will Learn:
+ Save JavaScript code to a .js file
+ Use script tags to add JS scripts to an html doc
+ Understand the connection between HTML, CSS, and JS as discrete parts of the front end of a web page that work together
+ Understand why it is useful to maintain Separation of Concerns

# Why This is Important:
We’ve been using the console to play around and test JavaScript core concepts. What if we want to create JavaScript that we can save for later, or use to add dynamic interaction to our HTML/CSS website?

# Saving and Linking JavaScript
Well, first off, we can save our JavaScript as a text file with a .js extension. Go ahead and create a `my_script.js` file and open it up in Atom.

Let's create a basic program so that we can test that everything is working.

```
console.log("Hello, World");
```

Console logging is a way to print strings of text to the JavaScript console. If we aren't in the console itself, we'll use console.log() to print out strings.

Save the file in the same directory as the html and css files for your website. Now, how do we run it?

Here is where we bring all three different front end coding languages together. In order for us to link and run the JavaScript on our html web page, we need to tell the browser where our script is. This is done with the `<script>` element in our html page. Remember when we linked to our .css file yesterday to add style to our .html? We do the same for our .js file by adding the `<script>` element to the `<body>` of our .html doc.

```
...
The rest of the html
...
<script src="my_script.js"></script>
</body>
```

You can add as many different scripts as you like. The `src` property is versatile - you can give it the name of a file in the same folder as the html, or the path to a file in another folder, or even the url of a script that exists somewhere else.

After adding the script tag, save the html file and load it up in the browser. Check your console, and see your message printed out!

# Separation of Concerns
HTML, CSS, and JavaScript work together to create the dynamic web pages we see on the web today. We keep each in their own files, but linked together provide structure, style and dynamic interactivity to the page.

In the early wild west days of the internet, it was common to see HTML, CSS, JavaScript together in one document. Browsers will still support this behavior - many examples and introductions you'll see online use inline styles and scripts. Having everything in one file made the code nearly indecipherable, a jumbled mess that was hard to understand and update when there were problems. HTML, CSS, and JavaScript play different roles, and keeping them in separate docs helps you and anyone who has to read your code understand what is happening.

Maintaining a separation between HTML(structure), CSS(style) and JS(logic) docs is referred to as separation of concerns. Keeping different roles separate helps coders on all kinds of projects, on the web or otherwise. Great developers don't just know how to solve problems with code - they keep their projects organized so they are easy to understand later. We'll use best practices from the start, so that you get to practice doing things the 'real' way.
