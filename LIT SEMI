<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LIVING IN THE IT ERA SEMIFINAL EXAM</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f7f9;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }
        .quiz-card {
            background-color: #ffffff;
            border-radius: 1rem;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            padding: 2rem;
            margin-bottom: 1.5rem;
            transition: transform 0.3s ease;
        }
        .quiz-card:hover {
            transform: translateY(-2px);
        }
        .option-button {
            width: 100%;
            text-align: left;
            padding: 0.75rem 1rem;
            margin-bottom: 0.5rem;
            border-radius: 0.5rem;
            border: 2px solid #e5e7eb;
            transition: all 0.2s ease;
            cursor: pointer;
            font-weight: 500;
        }
        .option-button:hover:not(.disabled):not(.correct):not(.incorrect) {
            background-color: #eff6ff;
            border-color: #60a5fa;
        }
        .option-button.correct {
            background-color: #d1fae5;
            border-color: #10b981;
            font-weight: 700;
            color: #065f46;
        }
        .option-button.incorrect {
            background-color: #fee2e2;
            border-color: #ef4444;
            color: #991b1b;
        }
        .disabled {
            pointer-events: none;
        }
        .progress-bar {
            height: 10px;
            background-color: #e5e7eb;
            border-radius: 9999px;
            overflow: hidden;
            margin-top: 0.5rem;
        }
        .progress-fill {
            height: 100%;
            background-color: #10b981;
            transition: width 0.3s ease;
        }
        .sticky-header {
            position: sticky;
            top: 0;
            z-index: 10;
            background-color: #1f2937;
            color: white;
            padding: 1rem 0;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }
        .welcome-card {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 60vh;
            text-align: center;
        }
    </style>
</head>
<body>

<div class="sticky-header">
    <div class="container flex justify-between items-center">
        <h1 class="text-2xl font-bold">LIVING IN THE IT ERA SEMIFINAL EXAM</h1>
        <div class="flex space-x-4 text-lg font-semibold">
            <span id="score-display" class="bg-blue-600 px-3 py-1 rounded-full">Score: 0/30</span>
            <span id="timer-display" class="bg-red-600 px-3 py-1 rounded-full">Time: --:--</span>
        </div>
    </div>
</div>

<div class="container">
    <!-- Welcome/Start Screen -->
    <div id="welcome-area" class="quiz-card welcome-card">
        <h2 class="text-4xl font-extrabold text-gray-800 mb-6">Welcome to the Exam!</h2>
        <p class="text-xl text-gray-600 mb-8">Please enter your name to begin the Living in the IT Era Semifinal Exam.</p>
        <div class="w-full max-w-sm">
            <label for="student-name" class="block text-left text-sm font-medium text-gray-700 mb-2">Student Name:</label>
            <input type="text" id="student-name" placeholder="E.g., Juan Dela Cruz" class="w-full p-3 border-2 border-gray-300 rounded-lg focus:outline-none focus:border-indigo-500 mb-6">
            <button id="start-exam-button" class="w-full bg-indigo-600 text-white px-6 py-3 rounded-lg font-semibold text-lg hover:bg-indigo-700 transition duration-150 shadow-md disabled:opacity-50" disabled>
                Start Exam
            </button>
        </div>
    </div>

    <!-- Quiz Area (Hidden by default) -->
    <div id="quiz-area" class="hidden">
        <!-- Questions will be rendered here -->
    </div>

    <!-- Results Area (Hidden by default) -->
    <div id="results-area" class="hidden quiz-card text-center">
        <h2 class="text-4xl font-extrabold text-blue-600 mb-4">Exam Complete!</h2>
        <p class="text-xl mb-2 text-gray-700">Student: <span id="student-name-result" class="font-bold text-indigo-600"></span></p>
        <p class="text-xl mb-6">Thank you for completing the objective exam.</p>
        <div class="bg-gray-100 p-6 rounded-lg">
            <p class="text-3xl font-bold text-gray-800">Final Score: <span id="final-score" class="text-green-600"></span></p>
            <p id="final-time" class="text-lg text-gray-600 mt-2"></p>
        </div>
        <button id="restart-button" class="mt-8 bg-indigo-600 text-white px-6 py-3 rounded-lg font-semibold hover:bg-indigo-700 transition duration-150">
            Start New Exam
        </button>
    </div>
</div>

<script>
    const questions = [
        { id: 1, text: "The Digital Age is also commonly known as the:", options: ["Mechanical Era", "Industrial Revolution", "Information Age", "Agrarian Age"], answer: "Information Age" },
        { id: 2, text: "Digital technology is defined as electronic tools, devices, and systems that generate, store, and process what?", options: ["Machinery", "Culture", "Data", "Values"], answer: "Data" },
        { id: 3, text: "The internet and telecommunication industry changed the way we connect and exchange information in which decade?", options: ["1980s", "1990s", "2000s", "2010s"], answer: "1990s" },
        { id: 4, text: "What term refers to a transformation of culture and social organizations/structures over time, acknowledging that a modern society is never static?", options: ["Digitalization", "Technological Change", "Automation", "Social Change"], answer: "Social Change" },
        { id: 5, text: "Which is NOT explicitly listed as a category where the impact of the ICT and social change is discussed?", options: ["Business", "Agriculture", "Education", "Health"], answer: "Agriculture" },
        { id: 6, text: "In the context of business, the impact of ICT infrastructure on social businesses includes making social impact affordable and:", options: ["Profitable", "Convenient", "Scalable", "Traditional"], answer: "Scalable" },
        { id: 7, text: "Modern ICT tools replicate the formal learning experience via virtual learning through the use of what?", options: ["Physical classrooms", "Virtual classrooms", "Computer-assisted exams", "Textbooks"], answer: "Virtual classrooms" },
        { id: 8, text: "The digital economy fundamentally changes the nature of work by placing fewer physical demands on workers but more jobs placing a/an:", options: ["Financial burden", "Emotional strain", "Time constraint", "Physical strain"], answer: "Emotional strain" },
        { id: 9, text: "Digitalization can affect people's health through the emergence of new physical and mental health risks and through its impact on the:", options: ["Insurance system", "Health-care delivery system", "Pharmaceutical industry", "Medical education"], answer: "Health-care delivery system" },
        { id: 10, text: "Digital technologies have been found in some studies to have positive effects in computer-assisted learning, particularly in which two subjects?", options: ["English and History", "Arts and Philosophy", "Science and Mathematics", "Social Studies and Literature"], answer: "Science and Mathematics" },
        { id: 11, text: "Which theory posits that technological innovation is the *cause* of social progress and that technology has control over human actions, culture, and values?", options: ["Social Constructivism", "Cultural Relativism", "Technological Determinism", "Economic Determinism"], answer: "Technological Determinism" },
        { id: 12, text: "According to Technological Determinism, society is changing because of:", options: ["Politics", "Culture", "Technology", "Human Free Will"], answer: "Technology" },
        { id: 13, text: "Which theory is the opposite of Technological Determinism and believes that technology does *not* determine human action?", options: ["Digital Evolution", "Social Constructivism", "Social Darwinism", "Cultural Materialism"], answer: "Social Constructivism" },
        { id: 14, text: "Technological progress is comprised of the creation of skill, new means of production, new uses of raw materials, and widespread use of what?", options: ["Patents", "Machinery", "Capital", "Labor"], answer: "Machinery" },
        { id: 15, text: "In the context of a 'smart home,' connected gadgets are designed to liberate users from their:", options: ["Neighbors", "Chores", "Emotions", "Bills"], answer: "Chores" },
        { id: 16, text: "An IoT ecosystem consists of web-enabled smart devices that use what to collect, send, and act on data?", options: ["Operating systems", "Embedded systems", "Analog circuits", "Human intervention"], answer: "Embedded systems" },
        { id: 17, text: "When was the term 'internet of things' coined?", options: ["1989", "1999", "2004", "2014"], answer: "1999" },
        { id: 18, text: "What was the first internet-connected 'thing' mentioned in the material to make use of the new protocol?", options: ["Computer", "Mobile phone", "Toaster", "Television"], answer: "Toaster" },
        { id: 19, text: "What product did Amazon introduce in 2014 that helped demystify the IoT for consumers?", options: ["Fire Phone", "Kindle", "Echo", "Prime Video"], answer: "Echo" },
        { id: 20, text: "One of the common benefits of IoT for businesses is providing a real-time look into how their systems really work, delivering insights into everything from the performance of machines to supply chain and:", options: ["Human resources", "Logistics operations", "Marketing campaigns", "Customer satisfaction"], answer: "Logistics operations" },
        { id: 21, text: "A major advantage of IoT is that devices do most of the work without what, even though people can still interact with them?", options: ["Wi-Fi", "Human intervention", "Electricity", "Cloud storage"], answer: "Human intervention" },
        { id: 22, text: "Which of the following is listed as a *disadvantage* (con) of the Internet of Things?", options: ["Improved communication between connected electronic devices.", "The potential for a hacker to steal confidential information as the number of connected devices increases.", "The ability to access information from anywhere at any time.", "Automating tasks to improve the quality of a business’s services."], answer: "The potential for a hacker to steal confidential information as the number of connected devices increases." },
        { id: 23, text: "Smart buildings utilize IoT sensors primarily to achieve what goal?", options: ["Improve security protocols.", "Reduce energy costs.", "Enhance tenant entertainment.", "Increase building height."], answer: "Reduce energy costs." },
        { id: 24, text: "Which emerging technology refers to computer systems built to mimic human intelligence and perform tasks such as image recognition, speech, or patterns?", options: ["Augmented Reality (AR)", "Virtual Reality (VR)", "Artificial Intelligence (AI)", "5G"], answer: "Artificial Intelligence (AI)" },
        { id: 25, text: "In the context of Virtual Reality (VR), the illusion of 'being there' that is created by motion sensors adjusting the view in real-time is called:", options: ["Telepathy", "Immersion", "Telepresence", "Simulation"], answer: "Telepresence" },
        { id: 26, text: "Which emerging trend is described as a more versatile and practical version of VR because it does *not* fully immerse individuals in an experience, but rather enhances the real world with images and sounds?", options: ["5G", "Augmented Reality (AR)", "Artificial Intelligence (AI)", "Blockchain Data"], answer: "Augmented Reality (AR)" },
        { id: 27, text: "The mobile game cited as an example of how Augmented Reality has infiltrated everyday life is:", options: ["Candy Crush", "Angry Birds", "Pokémon Go", "Fortnite"], answer: "Pokémon Go" },
        { id: 28, text: "Which new global wireless standard, after 4G, is designed to connect virtually everyone and everything together with high speeds, superior reliability, and negligible latency?", options: ["Wi-Fi 6", "6G", "5G", "LTE-A"], answer: "5G" },
        { id: 29, text: "Design for social impact aims to define opportunities for change that give voice to those who have been marginalized or what by design?", options: ["Discriminated", "Ignored", "Disenfranchised", "Overlooked"], answer: "Disenfranchised" },
        { id: 30, text: "What is considered a 'fundamental asset of design' for social impact, bringing knowledge and insight in its wake and requiring designers to be comfortable with the 'messiness' of human society?", options: ["Profitability", "Failure", "Complexity", "Collaboration"], answer: "Failure" }
    ];

    let currentScore = 0;
    let quizState = {}; // To store user answers and lock state
    let studentName = '';
    let startTime;
    let timerInterval;

    const welcomeArea = document.getElementById('welcome-area');
    const studentNameInput = document.getElementById('student-name');
    const startExamButton = document.getElementById('start-exam-button');
    const quizArea = document.getElementById('quiz-area');
    const resultsArea = document.getElementById('results-area');
    const scoreDisplay = document.getElementById('score-display');
    const timerDisplay = document.getElementById('timer-display');
    const restartButton = document.getElementById('restart-button');
    const studentNameResult = document.getElementById('student-name-result');


    // Utility function to format time
    const formatTime = (totalSeconds) => {
        const minutes = Math.floor(totalSeconds / 60);
        const seconds = totalSeconds % 60;
        return `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
    };

    // Timer functions
    const startTimer = () => {
        startTime = Date.now();
        timerInterval = setInterval(() => {
            const elapsedTime = Math.floor((Date.now() - startTime) / 1000);
            timerDisplay.textContent = `Time: ${formatTime(elapsedTime)}`;
        }, 1000);
    };

    const stopTimer = () => {
        clearInterval(timerInterval);
        const elapsedTime = Math.floor((Date.now() - startTime) / 1000);
        return formatTime(elapsedTime);
    };

    // --- Core Logic ---

    const renderQuestions = () => {
        quizArea.innerHTML = ''; // Clear previous content

        questions.forEach((q, index) => {
            const questionElement = document.createElement('div');
            questionElement.className = 'quiz-card';
            questionElement.id = `q-${q.id}`;

            const qIndex = index + 1;
            const state = quizState[q.id] || { selected: null, locked: false };

            let html = `
                <div class="flex justify-between items-center mb-4">
                    <h3 class="text-lg font-semibold text-gray-700">Question ${qIndex} of ${questions.length}</h3>
                    <span class="text-sm font-medium text-gray-500">Topic: ${qIndex <= 10 ? 'I. Introduction' : (qIndex <= 14 ? 'II. Theories' : (qIndex <= 23 ? 'III. IoT' : 'IV/V. Trends/Design'))}</span>
                </div>
                <p class="text-xl font-bold mb-4 text-gray-900">${q.text}</p>
                <div class="options-container space-y-2">
            `;

            q.options.forEach(option => {
                let classes = 'option-button';
                let isAnswer = option === q.answer;

                if (state.locked) {
                    classes += ' disabled';
                    if (option === state.selected) {
                        classes += isAnswer ? ' correct' : ' incorrect';
                    } else if (isAnswer) {
                        classes += ' correct';
                    }
                } else if (option === state.selected) {
                    classes += ' bg-blue-50 border-blue-400'; // Pre-selected style before locking
                }

                html += `
                    <button
                        class="${classes}"
                        data-question-id="${q.id}"
                        data-option="${option.replace(/"/g, '&quot;')}"
                        onclick="handleAnswerClick(event, ${q.id}, '${option.replace(/'/g, "\\'")}')"
                    >
                        ${option}
                    </button>
                `;
            });

            html += `</div>`;
            questionElement.innerHTML = html;
            quizArea.appendChild(questionElement);
        });

        // Add a submit button at the end
        // Only show submit button if all questions have been attempted (are locked)
        const allAnswered = questions.every(q => quizState[q.id] && quizState[q.id].locked);

        if (allAnswered) {
             let submitButton = document.getElementById('submit-exam-button');
             if (!submitButton) {
                 submitButton = document.createElement('button');
                 submitButton.id = 'submit-exam-button';
                 submitButton.className = 'w-full mt-6 mb-12 bg-green-600 text-white px-6 py-4 rounded-lg font-semibold text-xl hover:bg-green-700 transition duration-150 shadow-lg';
                 submitButton.textContent = 'Submit Exam and View Results';
                 submitButton.onclick = finishExam;
                 quizArea.appendChild(submitButton);
             }
        } else {
            // Remove submit button if it exists and not all are answered
            const submitButton = document.getElementById('submit-exam-button');
            if (submitButton) {
                submitButton.remove();
            }
        }
    };

    const updateScore = () => {
        currentScore = questions.filter(q => quizState[q.id] && quizState[q.id].selected === q.answer).length;
        scoreDisplay.textContent = `Score: ${currentScore}/${questions.length}`;
    };

    window.handleAnswerClick = (event, questionId, selectedOption) => {
        const state = quizState[questionId] || { selected: null, locked: false };
        const container = event.target.closest('.options-container');

        if (state.locked) return;

        // Deselect previous
        container.querySelectorAll('.option-button').forEach(btn => {
            btn.classList.remove('bg-blue-50', 'border-blue-400');
        });

        // Select current
        event.target.classList.add('bg-blue-50', 'border-blue-400');
        state.selected = selectedOption;

        // Lock the answer immediately for this type of test (user cannot change mind after clicking)
        state.locked = true;

        quizState[questionId] = state;

        // Update appearance for locking
        const questionData = questions.find(q => q.id === questionId);
        container.querySelectorAll('.option-button').forEach(btn => {
            const option = btn.getAttribute('data-option');
            btn.classList.add('disabled');

            if (option === questionData.answer) {
                btn.classList.add('correct');
            }
            if (option === state.selected && option !== questionData.answer) {
                btn.classList.add('incorrect');
            }
        });

        updateScore();
        renderQuestions(); // Re-render to show submit button if all answered
    };

    const finishExam = () => {
        const finalTime = stopTimer();

        // Hide quiz, show results
        quizArea.classList.add('hidden');
        resultsArea.classList.remove('hidden');

        // Display results
        studentNameResult.textContent = studentName;
        document.getElementById('final-score').textContent = `${currentScore}/${questions.length}`;
        document.getElementById('final-time').textContent = `Time Taken: ${finalTime}`;
    };

    const initializeExam = () => {
        // Reset all states
        quizState = {};
        currentScore = 0;
        studentName = '';
        studentNameInput.value = '';
        scoreDisplay.textContent = `Score: 0/${questions.length}`;
        timerDisplay.textContent = `Time: --:--`;

        // Show welcome screen, hide others
        welcomeArea.classList.remove('hidden');
        quizArea.classList.add('hidden');
        resultsArea.classList.add('hidden');

        // Disable start button until name is entered
        startExamButton.disabled = true;
    };

    const startQuiz = () => {
        studentName = studentNameInput.value.trim();
        if (studentName) {
            welcomeArea.classList.add('hidden');
            quizArea.classList.remove('hidden');
            renderQuestions();
            startTimer();
        }
    };

    // Event listeners for name input and start button
    studentNameInput.addEventListener('input', () => {
        startExamButton.disabled = studentNameInput.value.trim() === '';
    });

    startExamButton.addEventListener('click', startQuiz);
    restartButton.addEventListener('click', initializeExam);


    // Initial setup when the page loads
    window.onload = initializeExam;

</script>

</body>
</html>
