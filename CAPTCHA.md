
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CAPTCHA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <style>
        .captcha-container {
            text-align: center;
        }
        #captcha {
            font-size: 24px;
            margin-bottom: 10px;
        }
        #captcha-input {
            margin-bottom: 10px;
        }
        #result {
            font-weight: bold;
        }
    </style>
</head>
<body style ="background-color:powderblue;">
    <div class="container">
        <div class="row">
            <div class="col-md-6 offset-md-3">
                <div class="captcha-container">
                    <p>Enter the characters exactly as they appear:</p>
                    <p id="captcha"></p>
                    <input type="text" id="captcha-input" class="form-control" placeholder="Enter CAPTCHA">
                    <button id="verify-btn" class="btn btn-primary">Verify</button>
                    <p id="result"></p>
                    <button id="refresh-btn" class="btn btn-secondary" style="background-color: #FF0000; /* Red */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;">Refresh CAPTCHA</button> 
                </div>
            </div>
        </div>
    </div>

    <script>
        // Function to generate a random CAPTCHA
        function generateCaptcha() {
            var chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
            var captcha = '';
            for (var i = 0; i < 6; i++) {
                captcha += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            return captcha;
        }

        // Function to refresh CAPTCHA
        function refreshCaptcha() {
            var captcha = generateCaptcha();
            document.getElementById('captcha').textContent = captcha;
            document.getElementById('captcha-input').value = '';
            document.getElementById('result').textContent = '';
        }

        // Event listener for refresh button
        document.getElementById('refresh-btn').addEventListener('click', function() {
            refreshCaptcha();
        });

        // Event listener for verify button
        document.getElementById('verify-btn').addEventListener('click', function() {
            var captchaText = document.getElementById('captcha').textContent;
            var userInput = document.getElementById('captcha-input').value;
            if (userInput === captchaText) {
                document.getElementById('result').textContent = 'CAPTCHA verification successful!';
            } else {
                document.getElementById('result').textContent = 'CAPTCHA verification failed. Please try again.';
            }
        });

        // Initial CAPTCHA generation
        refreshCaptcha();
    </script>
</body>
</html>
