<!DOCTYPE HTML>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>SageMathCell</title>
    <script src="https://sagecell.sagemath.org/static/embedded_sagecell.js"></script>
    <script>
function add_copy_button() {
        var eval_button = $('#mysagecell').find('.sagecell_evalButton');
        console.log(eval_button.text());
        var copy_button = $('<button class="ui-button ui-corner-all ui-widget">Copy input and output</button>');
        copy_button.click(function() {
            console.log('hello');
            var input_lines = $('#mysagecell .sagecell_input pre')
            var output_lines = $('#mysagecell .sagecell_output pre')
            var input = $.map(input_lines, function(element) { return $(element).text() }).join('\n');
            var output = $.map(output_lines, function(element) { return $(element).text() }).join('\n');
            $('#clipboard').val('Input:\n\n' + input + '\n\nOutput:\n\n' + output);
            $('#clipboard').show();
            $('#clipboard').select();
            document.execCommand('copy');
            $('#clipboard').hide();
        });
        eval_button.after(copy_button);
}
$(document).ready(function() {
        $('#clipboard').hide();
        sagecell.makeSagecell({inputLocation: '#mysagecell',
                           evalButtonText: 'Evaluate'});
        var buttonExists = setInterval(function() {
           if ($('#mysagecell .sagecell_evalButton').length) {
              add_copy_button();
              clearInterval(buttonExists);
           }
        }, 100);
    });
    </script>
</head>
<body>

<h2>Your own computations</h2>
Type your own Sage computation below and click “Evaluate”.
<div id="mysagecell"><script type="text/x-sage">print next_prime(7)
print next_prime(11)
print next_prime(13)</script></div>
<textarea id="clipboard"></textarea>
  </body>
</html>

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
