# Quick and Simple github pages

This is a quick and dirty method of hosting markdown pages on github pages without any framework.

## 1. Create a index.html

Create a `index.html` file with the following content:

```
<!DOCTYPE >
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/showdown/1.9.1/showdown.min.js"></script>
    <style>
      #container {
        border: 1px solid red;
      }
    </style>
  </head>
  <body>
    <h1>SBland Dev Snippets</h1>
    <h2></h2>
    <div id="container"></div>
  </body>
  <script>
    fetch("./example.md")
      .then((response) => response.text())
      .then((data) => {
        console.log(data);
        var converter = new showdown.Converter(),
          html = converter.makeHtml(data);
        document.getElementById("container").innerHTML = html;
      });
  </script>
</html>

```

In the script tag we load `showdown` which can convert our markdown files to html.
https://github.com/showdownjs/showdown
