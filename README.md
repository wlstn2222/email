<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Send an Email</title>
    <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
    <script>
        // EmailJS 초기화
        (function () {
            emailjs.init("_EydCcV_d5A88_IXm"); // EmailJS User ID
        })();

        function sendEmail(event) {
            event.preventDefault(); // submit 동작 차단

            const email = "wwlstn216@gmail.com"; // 고정된 이메일 주소
            const message = document.getElementById('message').value;

            if (message) {
                emailjs.send("_EydCcV_d5A88_IXm", "template_br102by", {
                    to_email: email,
                    message: message
                })
                .then(() => {
                    alert("Email sent successfully!");
                })
                .catch(error => {
                    alert("Failed to send email. Please try again.");
                    console.error("Error:", error);
                });
            } else {
                alert("Please fill in the message field.");
            }
        }
    </script>
</head>
<body>
    <h1>Send an Email</h1>
    <form onsubmit="sendEmail(event)">
        <label for="message">Your Message:</label><br>
        <textarea id="message" placeholder="Enter your message here"></textarea><br><br>
        <button type="submit">Send Email</button>
    </form>
</body>
</html>
