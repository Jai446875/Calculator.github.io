<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grade Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 50px;
        }
        h1 {
            color: #333;
        }
        input, button {
            margin: 10px 0;
        }
        .message {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

<h1>Grade Calculator</h1>

<form id="gradeForm">
        <label>Prelim Grade:</label>
        <input type="text" id="prelim" placeholder="Enter your Prelim grade">
        <button>Calculate</button>
    </form>

<div id="resultMessage" class="message"></div>

<script>
        document.getElementById('gradeForm').onsubmit = function(event) {
            event.preventDefault();

            var prelimGrade = document.getElementById('prelim').value;
            var message = "";

            if (isNaN(prelimGrade) || prelimGrade < 0 || prelimGrade > 100) {
                message = "Please enter a valid grade between 0 and 100.";
            } else if (prelimGrade > 90) {
                message = "You've already passed with your Prelim grade! Edi Wow:)";
            } else if (prelimGrade < 75) {
                message = "Unfortunately, you can't pass.";
            } else {
                var required = (225 - prelimGrade) / 2;
                if (required > 100) {
                    message = "You need more than 100 in Midterms/Finals to pass.";
                } else {
                    message = "You need at least " + required.toFixed(2) + " in Midterms and Finals.";
                }
            }

            document.getElementById('resultMessage').innerText = message;
        };
    </script>

</body>
</html>
