<html>
   <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width">
      <title>Linear Algebra & Probbaility: SageMathCell</title>
      <script src="https://sagecell.sagemath.org/static/embedded_sagecell.js"></script>
      <script>
       // Make the div with id 'mycell' a Sage cell
       sagecell.makeSagecell({inputLocation:  '#mycell',
                             template:       sagecell.templates.minimal,
                             evalButtonText: 'Activate'});
       // Make *any* div with class 'compute' a Sage cell
       sagecell.makeSagecell({inputLocation: 'div.compute',
                              evalButtonText: 'Evaluate'});
       </script>
   </head>
   <body>
      <h1>Welcome to Linear Algebra & Probability</h1>
      <p>we'll try to set up a Sage cell here..</p>
      <h1>Embedded Sage Cells</h1>

      <h2>Your own computations</h2>
      Type your own Sage computation below and click &ldquo;Evaluate&rdquo;.
      <div class="compute"><script type="text/x-sage">plot(sin(x), (x, 0, 2*pi))</script></div>
         
   </body>
</html>
