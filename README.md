<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personal Information and IQ Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        label {
            display: block;
            margin-top: 10px;
        }
        input[type="text"] {
            margin-bottom: 10px;
            padding: 5px;
            width: 100%;
        }
        button {
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .result, .questions {
            margin-top: 20px;
        }
        .questions label {
            display: block;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <h1>Personal Information and IQ Generator</h1>
    <form id="infoForm">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required>
        
        <label for="age">Age:</label>
        <input type="text" id="age" name="age" required>
        
        <label for="height">Height (cm):</label>
        <input type="text" id="height" name="height" required>
        
        <label for="weight">Weight (kg):</label>
        <input type="text" id="weight" name="weight" required>
        
        <label for="topic">Choose a Topic:</label>
        <select id="topic" name="topic">
            <option value="football">Football</option>
            <option value="songs">Songs</option>
            <option value="cricket">Cricket</option>
            <option value="volleyball">Volleyball</option>
            <option value="geography">Geography</option>
            <option value="current_affairs">Current Affairs</option>
        </select>
        
        <button type="button" onclick="displayQuestions()">Get Questions</button>
    </form>
    
    <div class="questions" id="questions"></div>
    <button type="button" id="submitAnswers" style="display:none;" onclick="calculateIQ()">Submit Answers</button>
    
    <div class="result" id="result"></div>
    
    <script>
        const questions = {
            football: [
                "Who won the FIFA World Cup in 2018?",
                "Which club is known as the 'Red Devils'?",
                "Who is considered one of the greatest footballers of all time?",
                "What is the maximum number of players allowed on the field for one team in football?",
                "Which country is the birthplace of football?"
            ],
            songs: [
                "Who is known as the 'King of Pop'?",
                "Which song became famous for the lyric 'I will always love you'?",
                "Which band released the album 'Abbey Road'?",
                "Who is the lead singer of the band Coldplay?",
                "What genre of music is characterized by a strong rhythm and blues influences?"
            ],
            cricket: [
                "Which country won the first-ever Cricket World Cup?",
                "Who holds the record for the most runs in One Day Internationals (ODIs)?",
                "Which player is known as 'The Little Master'?",
                "What is the maximum number of overs in a One Day International match?",
                "Which country hosted the 2023 Cricket World Cup?"
            ],
            volleyball: [
                "How many players are there on a volleyball team?",
                "Which country is known as the birthplace of volleyball?",
                "What is the height of the net in women's volleyball?",
                "In which year was volleyball introduced to the Olympic Games?",
                "Which organization governs international volleyball competitions?"
            ],
            geography: [
                "What is the capital city of France?",
                "Which river is the longest in the world?",
                "Which continent is the Sahara Desert located on?",
                "What is the largest ocean on Earth?",
                "Which mountain range separates Europe and Asia?"
            ],
            current_affairs: [
                "Who is the current President of the United States?",
                "Which country recently hosted the Summer Olympics?",
                "What is the name of the latest Mars rover launched by NASA?",
                "Which international organization is known for addressing climate change?",
                "Who won the Nobel Peace Prize in the most recent year?"
            ]
        };
        
        function displayQuestions() {
            const topic = document.getElementById('topic').value;
            const questionDiv = document.getElementById('questions');
            const submitBtn = document.getElementById('submitAnswers');
            
            let questionsHTML = '<h2>Answer the following questions:</h2>';
            
            questions[topic].forEach((question, index) => {
                questionsHTML += `<label for="q${index}">${question}</label><input type="text" id="q${index}" name="q${index}" required>`;
            });
            
            questionDiv.innerHTML = questionsHTML;
            submitBtn.style.display = 'block';
        }
        
        function calculateIQ() {
            const name = document.getElementById('name').value;
            const age = document.getElementById('age').value;
            const height = document.getElementById('height').value;
            const weight = document.getElementById('weight').value;
            
            // Generate a random IQ score between 70 and 160
            const randomIQ = Math.floor(Math.random() * (160 - 70 + 1)) + 70;
            
            // Display the result
            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = `<h2>Hello, ${name}!</h2>
                                   <p>Your Age: ${age} years</p>
                                   <p>Your Height: ${height} cm</p>
                                   <p>Your Weight: ${weight} kg</p>
                                   <p>Your Random IQ Score (based on answers): ${randomIQ}</p>`;
        }
    </script>
</body>
</html>
