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
<div id="mysagecell"><script type="text/x-sage">
A = matrix([[1,2,3],
            [4,5,6],
            [7,8,9]])
A.rref() </script></div>
<textarea id="clipboard"></textarea>
  </body>
</html>

