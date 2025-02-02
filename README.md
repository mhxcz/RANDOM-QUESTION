# RANDOM-QUESTION
find it out yourself
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine Question</title>
    <style>
        body { text-align: center; font-family: Arial, sans-serif; }
        .container { margin-top: 20%; }
        button { font-size: 20px; margin: 10px; padding: 10px; cursor: pointer; }
        #yesGif, #noGif { display: none; margin-top: 20px; }
    </style>
</head>
<body>
    <div class="container">
        <h2 id="question">Will you be my Valentine?</h2>
        <button onclick="sendResponse('Yes')">Yes</button>
        <button onclick="askAgain()">No</button>
        <img id="yesGif" src="https://media.giphy.com/media/l0MYGBilzF3vE2B5G/giphy.gif" alt="Heart GIF">
        <img id="noGif" src="https://media.giphy.com/media/9J7tdYltWyXIY/giphy.gif" alt="Crying Cat GIF">
    </div>

    <script>
        let attempts = 0;
        let messages = [
            "Why not? 🥺", "You sure? 😢", "Please say yes! 🥹", "I'm gonna cry 😭",
            "Don't break my heart 💔", "Think about it again! 🙏", "You're making me sad 😞",
            "You have no heart?! 😭", "I’ll ask again… 🤨", "One last chance? 😣",
            "Pretty please? 🥺👉👈", "Don’t be so cold 🥶", "Say yes, I’ll be happy! 😊",
            "You're testing my patience 🤔", "Okay, last time... 🤞", "I'm not giving up 😤",
            "What if I cry? 😢", "Okay fine... but think again!", "This is your final No? 👀"
        ];

        function sendResponse(answer) {
            fetch('https://formspree.io/f/YOUR_FORM_ID', { // Replace with your Formspree ID
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ response: answer })
            }).then(() => {
                document.getElementById("question").innerText = "Yay! Happy Valentine's 💖";
                document.querySelector("button").style.display = "none";
                document.querySelectorAll("button")[1].style.display = "none";
                document.getElementById("yesGif").style.display = "block"; // Show heart GIF
            }).catch(() => alert('Error sending response.'));
        }

        function askAgain() {
            if (attempts < messages.length) {
                document.getElementById("question").innerText = messages[attempts];
                attempts++;
            } else {
                document.getElementById("question").innerText = "Fine... I won't ask again 😔";
                document.querySelector("button").style.display = "none";
                document.querySelectorAll("button")[1].style.display = "none";
                document.getElementById("noGif").style.display = "block"; // Show crying cat GIF
            }
        }
    </script>
</body>
</html>
