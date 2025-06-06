<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BrightSpot - Share Positivity</title>
    <style>
        :root {
            --primary: #4e54c8;
            --secondary: #8f94fb;
            --light: #f8f9fa;
            --dark: #212529;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            min-height: 100vh;
            padding: 20px;
            color: var(--light);
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            color: white;
            text-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            max-width: 600px;
            margin: 0 auto;
        }
        
        .card {
            background: rgba(255, 255, 255, 0.15);
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 25px;
            transition: transform 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-5px);
        }
        
        h2 {
            margin-bottom: 15px;
            color: white;
        }
        
        textarea {
            width: 100%;
            padding: 15px;
            border-radius: 10px;
            border: none;
            background: rgba(255, 255, 255, 0.9);
            resize: vertical;
            min-height: 120px;
            font-size: 1rem;
            margin-bottom: 15px;
        }
        
        button {
            background: white;
            color: var(--primary);
            border: none;
            padding: 12px 25px;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        button:hover {
            background: #e6e7ff;
            transform: scale(1.05);
        }
        
        .message {
            background: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 15px;
        }
        
        .message p {
            margin-bottom: 10px;
            line-height: 1.5;
        }
        
        .timestamp {
            font-size: 0.8rem;
            opacity: 0.7;
            text-align: right;
        }
        
        .guidelines {
            margin-top: 30px;
            padding: 20px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 15px;
        }
        
        .guidelines h3 {
            margin-bottom: 10px;
        }
        
        .guidelines ul {
            padding-left: 20px;
        }
        
        .guidelines li {
            margin-bottom: 8px;
        }
        
        footer {
            text-align: center;
            margin-top: 30px;
            opacity: 0.8;
            font-size: 0.9rem;
        }
        
        @media (max-width: 600px) {
            .container {
                padding: 15px;
            }
            
            h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>BrightSpot</h1>
            <p class="subtitle">Share anonymous compliments and positive messages to brighten someone's day</p>
        </header>
        
        <main>
            <div class="card">
                <h2>Spread Kindness</h2>
                <p>Write something positive that might make someone smile:</p>
                <textarea id="messageInput" placeholder="Your kind message here..."></textarea>
                <button id="submitBtn">Share Positivity</button>
            </div>
            
            <div class="card">
                <h2>Recent BrightSpots</h2>
                <div id="messagesContainer">
                    <!-- Messages will appear here -->
                </div>
            </div>
            
            <div class="guidelines">
                <h3>Community Guidelines</h3>
                <ul>
                    <li>Share only positive and uplifting messages</li>
                    <li>Never target specific individuals</li>
                    <li>No personal information or identifiers</li>
                    <li>Be kind - this is a positivity zone</li>
                    <li>Report any inappropriate content</li>
                </ul>
            </div>
        </main>
        
        <footer>
            <p>BrightSpot &copy; 2023 | Designed to spread kindness</p>
        </footer>
    </div>

    <script>
        // Sample initial messages
        const initialMessages = [
            "You have the power to make someone's day better!",
            "Your kindness matters more than you know",
            "The world is better with you in it",
            "Someone out there appreciates you exactly as you are"
        ];

        const messagesContainer = document.getElementById('messagesContainer');
        const messageInput = document.getElementById('messageInput');
        const submitBtn = document.getElementById('submitBtn');

        // Display initial messages
        initialMessages.forEach(msg => {
            addMessageToPage(msg);
        });

        // Submit new message
        submitBtn.addEventListener('click', () => {
            const message = messageInput.value.trim();
            
            if (message) {
                if (validateMessage(message)) {
                    addMessageToPage(message);
                    messageInput.value = '';
                } else {
                    alert('Please keep messages positive and non-targeted');
                }
            }
        });

        // Add message to page
        function addMessageToPage(text) {
            const messageEl = document.createElement('div');
            messageEl.className = 'message';
            
            const now = new Date();
            const
