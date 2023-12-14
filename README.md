<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Age Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }

        #calculator {
            text-align: center;
        }

        input {
            padding: 8px;
            margin: 5px;
        }

        button {
            padding: 8px 15px;
            background-color: #4caf50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        #result {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

<div id="calculator">
    <h2>Age Calculator</h2>
    <label for="dob">Date of Birth:</label>
    <input type="number" id="dob" placeholder="Day" min="1" max="31" required>
    <input type="number" id="mob" placeholder="Month" min="1" max="12" required>
    <input type="number" id="yob" placeholder="Year" min="1900" required>

    <button onclick="calculateAge()">Calculate Age</button>

    <div id="result"></div>
</div>

<script>
    function calculateAge() {
        var dob = document.getElementById("dob").value;
        var mob = document.getElementById("mob").value;
        var yob = document.getElementById("yob").value;

        var today = new Date();
        var birthDate = new Date(yob, mob - 1, dob);

        var age = today.getFullYear() - birthDate.getFullYear();
        var monthDiff = today.getMonth() - birthDate.getMonth();

        if (monthDiff < 0 || (monthDiff === 0 && today.getDate() < birthDate.getDate())) {
            age--;
        }

        document.getElementById("result").innerHTML = "Your Age: " + age + " years";
    }
</script>

</body>
</html>
