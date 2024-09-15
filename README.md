<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grade Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            padding: 20px;
        }
        h1 {
            color: #333;
        }
        form {
            margin-bottom: 20px;
        }
        input[type="text"] {
            padding: 8px;
            font-size: 16px;
            margin-right: 10px;
        }
        button {
            padding: 8px 16px;
            font-size: 16px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .message {
            font-size: 18px;
            color: #333;
            margin-top: 20px;
        }
    </style>
</head>
<body>

  <h1>Grade Calculator</h1>
    <form id="gradeForm">
        <label for="prelim">Enter Prelim Grade:</label>
        <input type="text" id="prelim" name="prelim">
        <button type="submit">Calculate</button>
    </form>

  <p class="message" id="message"></p>

   <script>
        document.getElementById('gradeForm').addEventListener('submit', function(event) {
            event.preventDefault();

            let prelim = document.getElementById('prelim').value;
            let messageElement = document.getElementById('message');
            let passingGrade = 75;

            if (isNaN(prelim) || prelim === '') {
                messageElement.textContent = 'Invalid input. Please enter a valid numerical Prelim grade.';
                return;
            }

            prelim = parseFloat(prelim);
            let requiredMidtermFinal = passingGrade - (prelim * 0.30);

            if (requiredMidtermFinal < 0) {
                messageElement.textContent = "You've already passed with your Prelim grade!";
            } else if (requiredMidtermFinal > 100) {
                messageElement.textContent = "Unfortunately, it's impossible to pass the subject.";
            } else {
                messageElement.textContent = `To pass, you need a combined Midterm and Final score of at least ${requiredMidtermFinal.toFixed(2)}.`;
            }
        });
    </script>

</body>
</html>
