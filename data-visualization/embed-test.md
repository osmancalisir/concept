<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
    <title>Embedded Observable notebook</title>
    
  </head>
  <body>
    <div class="wrapper">
      <div class="title">TEST</div>
      <div id="labels"></div>
      <div id="output"></div>
    </div>

    <script type="module">
      import {Inspector, Runtime} from "https://unpkg.com/@observablehq/notebook-runtime@1.0.1?module";
      import notebook from "https://observablehq.com/d/87de48220ae3faec";
      const renders = {
        "viewof value": "#labels",
        "output": "#output",
      };
      Runtime.load(notebook, (variable) => {
        const selector = renders[variable.name];
        if (selector) {
          return new Inspector(document.querySelector(selector));
        } else {
          return true;
        }
      });
    </script>
  </body>
</html>