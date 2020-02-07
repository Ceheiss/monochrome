---
title: Learning by induction
description: Observe a couple of examples, look at the specific characteristics, extract what is common.
header: Learning by induction
---

Imagine you are an early scientist an you are manage to get to an island nobody has ever seen. While there, you get exposed to this strange animals you haven't seen before, you see an eagle roaming high, you see a hummingbird next to a flower, some seagulls cracking shells in the coast, and an occational pidgeon moving from tree to tree. All of these creatures are certainly not equal, but they certainly look different to the animals you have at home, you can extract some common patterns enough to make a cathegory. The all have beacks, feathers, wings, and lay eggs. You call them birds.

You might be thinking, why are we talking about birds? Is because I think there is some value from this approach to learn different things, in my case for example, was about templating engines. I'm currently diving into the backend (NodeJS), I learned how to route to different static files and that is cool, but how about using dinamic information? If I want to display the name of the user that logged in my page, how do I do that? I went with EJS.

So I set `app.set("view engine", "ejs");` up in my `app.js` file. Then imagine I have a simple route:

```javascript
app.get("/subsection/:name", function(req, res) {
  const sectionName = req.params.name;
  res.render("section.ejs", { sectionName: sectionName });
});
```

So now for some strange reason I want to print five times th name of the section on `section.ejs`. Oh, and I also have some nice header and footer I want to include (as I do in all of my pages) and I end up with this:

```javascript
<% include partials/header %>
<h1>Welcome to...:</h1>
<% for(let i=0); i < 5; i++ {
  <h2> <%= sectionName %=> </h2>
<% } %>
<%include partials/footer%>
```

But is EJS, the only qway of doing this? Is it a must in a Node? Sometimes when you only use one tool you might subconsciously thinking of it as mandatory, so let's experiment with **hbs**, the Express templating engine for **Handlebars**.

We set it like this: `app.set("view engine", "hbs");`. My route to the sections looks like this:
```javascript
app.get("/subsection/:name", function(req, res) {
  const sectionName = req.params.name;
  res.render("section.ejs", { sectionName: sectionName });
});
```
 and my file would look like this:
 ```javascript
 {{>header}}
 <h1>Welcome to...:</h1>
 {{#repeater}}
  <h2>{{sectionName}}</h2>
{{/repeater}}
 {{>footer}}
 ```
