<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Age Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f9;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      text-align: center;
      background-color: #fff;
      padding: 20px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      border-radius: 8px;
    }

    h1 {
      font-size: 2em;
      margin-bottom: 20px;
    }

    label {
      font-size: 1.2em;
    }

    input[type="date"] {
      padding: 10px;
      font-size: 1em;
      margin-top: 10px;
    }

    button {
      padding: 10px 20px;
      font-size: 1.2em;
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
      margin-top: 15px;
    }

    button:hover {
      background-color: #45a049;
    }

    #result {
      margin-top: 20px;
      font-size: 1.5em;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Age Calculator</h1>
    <form id="ageForm">
      <label for="dob">Enter Your Date of Birth:</label>
      <input type="date" id="dob" name="dob" required>
      <button type="submit">Calculate Age</button>
    </form>

    <div id="result">
      <p id="age"></p>
    </div>
  </div>

  <script>
    document.getElementById('ageForm').addEventListener('submit', function(event) {
      event.preventDefault();

      // Get the input date of birth value
      let dob = document.getElementById('dob').value;

      // If date of birth is not entered, return
      if (!dob) {
        alert("Please enter a valid date of birth.");
        return;
      }

      // Convert DOB into a Date object
      let birthDate = new Date(dob);
      
      // Get the current date
      let currentDate = new Date();
      
      // Calculate the difference in years
      let age = currentDate.getFullYear() - birthDate.getFullYear();
      let month = currentDate.getMonth() - birthDate.getMonth();

      // Adjust age if the birthday hasn't happened yet this year
      if (month < 0 || (month === 0 && currentDate.getDate() < birthDate.getDate())) {
        age--;
      }

      // Display the result
      document.getElementById('age').textContent = `Your age is: ${age} years old.`;
    });
  </script>
</body>
</html>
