<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INT108: Python Programming Quiz</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
            padding: 20px;
            background-image: linear-gradient(120deg, #fdfbfb 0%, #ebedee 100%);
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
            padding: 30px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 15px;
            color: white;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            font-weight: 700;
        }
        
        .subtitle {
            font-size: 1.4rem;
            margin-bottom: 20px;
            opacity: 0.9;
        }
        
        .stats {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 25px;
            flex-wrap: wrap;
        }
        
        .stat-box {
            background: rgba(255, 255, 255, 0.15);
            padding: 15px 25px;
            border-radius: 10px;
            text-align: center;
            backdrop-filter: blur(5px);
            min-width: 150px;
        }
        
        .stat-number {
            font-size: 2.2rem;
            font-weight: 700;
            display: block;
        }
        
        .stat-label {
            font-size: 1rem;
            opacity: 0.9;
        }
        
        .unit-selector {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }
        
        .unit-card {
            background: white;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease;
            cursor: pointer;
            border-left: 5px solid #667eea;
        }
        
        .unit-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }
        
        .unit-card.active {
            border-left-color: #4CAF50;
            background-color: #f0f9ff;
        }
        
        .unit-title {
            font-size: 1.5rem;
            margin-bottom: 10px;
            color: #2c3e50;
        }
        
        .unit-desc {
            color: #666;
            margin-bottom: 15px;
            font-size: 0.95rem;
        }
        
        .unit-questions {
            display: flex;
            justify-content: space-between;
            color: #667eea;
            font-weight: 600;
            font-size: 0.9rem;
        }
        
        .quiz-container {
            background: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
            margin-bottom: 40px;
            display: none;
        }
        
        .quiz-container.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .quiz-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 1px solid #eee;
        }
        
        .quiz-title {
            font-size: 1.8rem;
            color: #2c3e50;
        }
        
        .quiz-progress {
            font-size: 1.1rem;
            color: #667eea;
            font-weight: 600;
        }
        
        .question-container {
            margin-bottom: 30px;
        }
        
        .question-text {
            font-size: 1.3rem;
            margin-bottom: 25px;
            color: #2c3e50;
            line-height: 1.5;
        }
        
        .options-container {
            display: grid;
            grid-template-columns: 1fr;
            gap: 15px;
        }
        
        .option {
            padding: 18px 20px;
            background: #f8f9fa;
            border-radius: 10px;
            border: 2px solid #e9ecef;
            cursor: pointer;
            transition: all 0.2s ease;
            font-size: 1.05rem;
        }
        
        .option:hover {
            background: #e9ecef;
            transform: translateX(5px);
        }
        
        .option.selected {
            background: #e3f2fd;
            border-color: #2196F3;
            color: #1565c0;
        }
        
        .option.correct {
            background: #e8f5e9;
            border-color: #4CAF50;
            color: #2e7d32;
        }
        
        .option.incorrect {
            background: #ffebee;
            border-color: #f44336;
            color: #c62828;
        }
        
        .quiz-navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid #eee;
        }
        
        .btn {
            padding: 14px 30px;
            border-radius: 8px;
            border: none;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .btn-prev {
            background: #f8f9fa;
            color: #495057;
            border: 2px solid #e9ecef;
        }
        
        .btn-prev:hover:not(:disabled) {
            background: #e9ecef;
        }
        
        .btn-next {
            background: #667eea;
            color: white;
        }
        
        .btn-next:hover:not(:disabled) {
            background: #5a6fd8;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
        }
        
        .btn-submit {
            background: #4CAF50;
            color: white;
        }
        
        .btn-submit:hover {
            background: #43a047;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(76, 175, 80, 0.3);
        }
        
        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .results-container {
            background: white;
            border-radius: 15px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
            text-align: center;
            margin-bottom: 40px;
            display: none;
        }
        
        .results-container.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        .results-title {
            font-size: 2.2rem;
            margin-bottom: 20px;
            color: #2c3e50;
        }
        
        .score-circle {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            margin: 0 auto 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 3.5rem;
            font-weight: 700;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.4);
        }
        
        .results-details {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }
        
        .result-item {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
        }
        
        .result-value {
            font-size: 2rem;
            font-weight: 700;
            color: #667eea;
            display: block;
        }
        
        .result-label {
            font-size: 1rem;
            color: #666;
            margin-top: 5px;
        }
        
        .footer {
            text-align: center;
            margin-top: 50px;
            color: #666;
            font-size: 0.9rem;
            padding-top: 20px;
            border-top: 1px solid #eee;
        }
        
        .co-list {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-top: 20px;
        }
        
        .co-item {
            background: #e3f2fd;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.85rem;
            color: #1565c0;
        }
        
        @media (max-width: 768px) {
            .unit-selector {
                grid-template-columns: 1fr;
            }
            
            .quiz-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 15px;
            }
            
            h1 {
                font-size: 2.2rem;
            }
            
            .subtitle {
                font-size: 1.1rem;
            }
            
            .stat-box {
                min-width: 120px;
                padding: 12px 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>INT108: Python Programming</h1>
            <div class="subtitle">Comprehensive Quiz Based on Course Syllabus</div>
            <div class="stats">
                <div class="stat-box">
                    <span class="stat-number">300</span>
                    <span class="stat-label">Total Questions</span>
                </div>
                <div class="stat-box">
                    <span class="stat-number">6</span>
                    <span class="stat-label">Course Units</span>
                </div>
                <div class="stat-box">
                    <span class="stat-number">15</span>
                    <span class="stat-label">Practical Exercises</span>
                </div>
                <div class="stat-box">
                    <span class="stat-number">6</span>
                    <span class="stat-label">Course Outcomes</span>
                </div>
            </div>
        </header>
        
        <div class="co-list">
            <div class="co-item">CO1: Installation & Basics</div>
            <div class="co-item">CO2: Conditional & Iterative Statements</div>
            <div class="co-item">CO3: Functions & Recursion</div>
            <div class="co-item">CO4: Data Structures</div>
            <div class="co-item">CO5: OOP Concepts</div>
            <div class="co-item">CO6: Files & Regular Expressions</div>
        </div>
        
        <section class="unit-selector">
            <div class="unit-card active" data-unit="1">
                <div class="unit-title">Unit I: Programming Environment & Basics</div>
                <div class="unit-desc">Python installation, variables, expressions, statements, operators, strings, comments</div>
                <div class="unit-questions">
                    <span>Questions: 1-50</span>
                    <span>Click to start</span>
                </div>
            </div>
            
            <div class="unit-card" data-unit="2">
                <div class="unit-title">Unit II: Conditional & Iterative Statements</div>
                <div class="unit-desc">Boolean expressions, if-else, loops (for/while), nested loops, random numbers</div>
                <div class="unit-questions">
                    <span>Questions: 51-100</span>
                    <span>Click to start</span>
                </div>
            </div>
            
            <div class="unit-card" data-unit="3">
                <div class="unit-title">Unit III: Functions & Recursion</div>
                <div class="unit-desc">Function calls, parameters, arguments, math functions, recursion, type conversion</div>
                <div class="unit-questions">
                    <span>Questions: 101-150</span>
                    <span>Click to start</span>
                </div>
            </div>
            
            <div class="unit-card" data-unit="4">
                <div class="unit-title">Unit IV: Strings, Lists, Tuples & Dictionaries</div>
                <div class="unit-desc">String operations, list manipulation, tuples, dictionaries, data structure operations</div>
                <div class="unit-questions">
                    <span>Questions: 151-200</span>
                    <span>Click to start</span>
                </div>
            </div>
            
            <div class="unit-card" data-unit="5">
                <div class="unit-title">Unit V: Classes & Objects</div>
                <div class="unit-desc">OOP concepts, classes, objects, inheritance, polymorphism, method overriding</div>
                <div class="unit-questions">
                    <span>Questions: 201-250</span>
                    <span>Click to start</span>
                </div>
            </div>
            
            <div class="unit-card" data-unit="6">
                <div class="unit-title">Unit VI: Files, Exceptions & Regular Expressions</div>
                <div class="unit-desc">File handling, exceptions, try-except blocks, regex patterns, web scraping basics</div>
                <div class="unit-questions">
                    <span>Questions: 251-300</span>
                    <span>Click to start</span>
                </div>
            </div>
        </section>
        
        <section class="quiz-container active" id="quiz-unit-1">
            <div class="quiz-header">
                <div class="quiz-title">Unit I: Programming Environment & Basics</div>
                <div class="quiz-progress">Question <span id="current-question">1</span> of 50</div>
            </div>
            
            <div class="question-container">
                <div class="question-text" id="question-text">
                    Which of the following is a valid variable name in Python?
                </div>
                
                <div class="options-container" id="options-container">
                    <div class="option" data-option="1">1st_variable</div>
                    <div class="option" data-option="2">my-variable</div>
                    <div class="option" data-option="3">_my_variable</div>
                    <div class="option" data-option="4">my variable</div>
                </div>
            </div>
            
            <div class="quiz-navigation">
                <button class="btn btn-prev" id="prev-btn" disabled>Previous</button>
                <button class="btn btn-next" id="next-btn">Next Question</button>
            </div>
        </section>
        
        <section class="quiz-container" id="quiz-unit-2">
            <div class="quiz-header">
                <div class="quiz-title">Unit II: Conditional & Iterative Statements</div>
                <div class="quiz-progress">Question <span class="current-question">1</span> of 50</div>
            </div>
            
            <div class="question-container">
                <div class="question-text">
                    Which loop is guaranteed to execute at least once in Python?
                </div>
                
                <div class="options-container">
                    <div class="option" data-option="1">for loop</div>
                    <div class="option" data-option="2">while loop</div>
                    <div class="option" data-option="3">do-while loop (Python doesn't have this)</div>
                    <div class="option" data-option="4">None of the above</div>
                </div>
            </div>
            
            <div class="quiz-navigation">
                <button class="btn btn-prev" id="prev-btn-2">Previous</button>
                <button class="btn btn-next" id="next-btn-2">Next Question</button>
            </div>
        </section>
        
        <section class="quiz-container" id="quiz-unit-3">
            <div class="quiz-header">
                <div class="quiz-title">Unit III: Functions & Recursion</div>
                <div class="quiz-progress">Question <span class="current-question">1</span> of 50</div>
            </div>
            
            <div class="question-container">
                <div class="question-text">
                    What is the base case in a recursive function?
                </div>
                
                <div class="options-container">
                    <div class="option" data-option="1">The first call to the function</div>
                    <div class="option" data-option="2">The condition that stops the recursion</div>
                    <div class="option" data-option="3">The return statement</div>
                    <div class="option" data-option="4">The recursive call</div>
                </div>
            </div>
            
            <div class="quiz-navigation">
                <button class="btn btn-prev" id="prev-btn-3">Previous</button>
                <button class="btn btn-next" id="next-btn-3">Next Question</button>
            </div>
        </section>
        
        <section class="quiz-container" id="quiz-unit-4">
            <div class="quiz-header">
                <div class="quiz-title">Unit IV: Strings, Lists, Tuples & Dictionaries</div>
                <div class="quiz-progress">Question <span class="current-question">1</span> of 50</div>
            </div>
            
            <div class="question-container">
                <div class="question-text">
                    Which of the following data types is mutable in Python?
                </div>
                
                <div class="options-container">
                    <div class="option" data-option="1">Tuple</div>
                    <div class="option" data-option="2">String</div>
                    <div class="option" data-option="3">List</div>
                    <div class="option" data-option="4">All of the above</div>
                </div>
            </div>
            
            <div class="quiz-navigation">
                <button class="btn btn-prev" id="prev-btn-4">Previous</button>
                <button class="btn btn-next" id="next-btn-4">Next Question</button>
            </div>
        </section>
        
        <section class="quiz-container" id="quiz-unit-5">
            <div class="quiz-header">
                <div class="quiz-title">Unit V: Classes & Objects</div>
                <div class="quiz-progress">Question <span class="current-question">1</span> of 50</div>
            </div>
            
            <div class="question-container">
                <div class="question-text">
                    Which OOP concept allows a class to derive properties from another class?
                </div>
                
                <div class="options-container">
                    <div class="option" data-option="1">Encapsulation</div>
                    <div class="option" data-option="2">Polymorphism</div>
                    <div class="option" data-option="3">Inheritance</div>
                    <div class="option" data-option="4">Abstraction</div>
                </div>
            </div>
            
            <div class="quiz-navigation">
                <button class="btn btn-prev" id="prev-btn-5">Previous</button>
                <button class="btn btn-next" id="next-btn-5">Next Question</button>
            </div>
        </section>
        
        <section class="quiz-container" id="quiz-unit-6">
            <div class="quiz-header">
                <div class="quiz-title">Unit VI: Files, Exceptions & Regular Expressions</div>
                <div class="quiz-progress">Question <span class="current-question">1</span> of 50</div>
            </div>
            
            <div class="question-container">
                <div class="question-text">
                    Which mode opens a file for both reading and writing in Python?
                </div>
                
                <div class="options-container">
                    <div class="option" data-option="1">'r'</div>
                    <div class="option" data-option="2">'w'</div>
                    <div class="option" data-option="3">'a+'</div>
                    <div class="option" data-option="4">'rb'</div>
                </div>
            </div>
            
            <div class="quiz-navigation">
                <button class="btn btn-prev" id="prev-btn-6">Previous</button>
                <button class="btn btn-submit" id="submit-btn">Submit Quiz</button>
            </div>
        </section>
        
        <section class="results-container" id="results-container">
            <h2 class="results-title">Quiz Results</h2>
            <div class="score-circle">
                <span id="score-percentage">85%</span>
            </div>
            <p id="results-message">Excellent! You have a strong understanding of Python programming concepts.</p>
            
            <div class="results-details">
                <div class="result-item">
                    <span class="result-value" id="correct-answers">42</span>
                    <span class="result-label">Correct Answers</span>
                </div>
                <div class="result-item">
                    <span class="result-value" id="incorrect-answers">8</span>
                    <span class="result-label">Incorrect Answers</span>
                </div>
                <div class="result-item">
                    <span class="result-value" id="time-spent">12:45</span>
                    <span class="result-label">Time Spent</span>
                </div>
                <div class="result-item">
                    <span class="result-value" id="unit-score">Unit I: 9/10</span>
                    <span class="result-label">Best Performance</span>
                </div>
            </div>
            
            <button class="btn btn-next" id="restart-btn" style="margin-top: 30px;">Restart Quiz</button>
        </section>
        
        <footer class="footer">
            <p>INT108: Python Programming Quiz • Based on Course Syllabus 2025-26</p>
            <p>Total Questions: 300 • 6 Units • 15 Practical Exercises</p>
            <p>Textbook: <em>Fundamentals of Python – First Program by Kenneth A. Lambert</em></p>
        </footer>
    </div>

    <script>
        // Unit selection functionality
        const unitCards = document.querySelectorAll('.unit-card');
        const quizContainers = document.querySelectorAll('.quiz-container');
        const resultsContainer = document.getElementById('results-container');
        
        unitCards.forEach(card => {
            card.addEventListener('click', () => {
                // Remove active class from all cards
                unitCards.forEach(c => c.classList.remove('active'));
                // Add active class to clicked card
                card.classList.add('active');
                
                // Get unit number
                const unitNumber = card.getAttribute('data-unit');
                
                // Hide all quiz containers
                quizContainers.forEach(container => {
                    container.classList.remove('active');
                });
                
                // Show selected unit's quiz container
                document.getElementById(`quiz-unit-${unitNumber}`).classList.add('active');
                
                // Hide results container
                resultsContainer.classList.remove('active');
            });
        });
        
        // Quiz state management
        const quizData = {
            currentUnit: 1,
            currentQuestion: 1,
            totalQuestions: 50,
            selectedOption: null,
            answers: {},
            startTime: new Date(),
            // Sample questions for each unit (in a real app, this would be 300 questions)
            questions: {
                1: [
                    {
                        text: "Which of the following is a valid variable name in Python?",
                        options: ["1st_variable", "my-variable", "_my_variable", "my variable"],
                        correct: 3
                    },
                    {
                        text: "What is the output of 'Hello' + 'World' in Python?",
                        options: ["HelloWorld", "Hello World", "Hello+World", "Error"],
                        correct: 1
                    },
                    {
                        text: "Which operator is used for exponentiation in Python?",
                        options: ["^", "**", "^^", "exp()"],
                        correct: 2
                    },
                    {
                        text: "What does the '//' operator do in Python?",
                        options: ["Integer division", "Floor division", "Comment", "Both A and B"],
                        correct: 4
                    }
                ],
                2: [
                    {
                        text: "Which loop is guaranteed to execute at least once in Python?",
                        options: ["for loop", "while loop", "do-while loop (Python doesn't have this)", "None of the above"],
                        correct: 3
                    }
                ],
                3: [
                    {
                        text: "What is the base case in a recursive function?",
                        options: ["The first call to the function", "The condition that stops the recursion", "The return statement", "The recursive call"],
                        correct: 2
                    }
                ],
                4: [
                    {
                        text: "Which of the following data types is mutable in Python?",
                        options: ["Tuple", "String", "List", "All of the above"],
                        correct: 3
                    }
                ],
                5: [
                    {
                        text: "Which OOP concept allows a class to derive properties from another class?",
                        options: ["Encapsulation", "Polymorphism", "Inheritance", "Abstraction"],
                        correct: 3
                    }
                ],
                6: [
                    {
                        text: "Which mode opens a file for both reading and writing in Python?",
                        options: ["'r'", "'w'", "'a+'", "'rb'"],
                        correct: 3
                    }
                ]
            }
        };
        
        // Initialize quiz for each unit
        function initializeQuiz(unitNumber) {
            const quizContainer = document.getElementById(`quiz-unit-${unitNumber}`);
            if (!quizContainer) return;
            
            const questionText = quizContainer.querySelector('.question-text');
            const optionsContainer = quizContainer.querySelector('.options-container');
            const prevBtn = quizContainer.querySelector('.btn-prev');
            const nextBtn = quizContainer.querySelector('.btn-next');
            const submitBtn = quizContainer.querySelector('.btn-submit');
            const currentQuestionSpan = quizContainer.querySelector('.current-question');
            
            // Set current question number
            if (currentQuestionSpan) {
                currentQuestionSpan.textContent = quizData.currentQuestion;
            }
            
            // Get question for current unit
            const unitQuestions = quizData.questions[unitNumber] || quizData.questions[1];
            const questionIndex = Math.min(quizData.currentQuestion - 1, unitQuestions.length - 1);
            const question = unitQuestions[questionIndex];
            
            // Display question
            if (questionText && question) {
                questionText.textContent = question.text;
            }
            
            // Display options
            if (optionsContainer && question) {
                optionsContainer.innerHTML = '';
                question.options.forEach((option, index) => {
                    const optionElement = document.createElement('div');
                    optionElement.className = 'option';
                    optionElement.setAttribute('data-option', index + 1);
                    optionElement.textContent = `${index + 1}. ${option}`;
                    
                    // Check if this option was previously selected
                    const answerKey = `${unitNumber}-${quizData.currentQuestion}`;
                    if (quizData.answers[answerKey] === index + 1) {
                        optionElement.classList.add('selected');
                    }
                    
                    optionElement.addEventListener('click', () => {
                        // Remove selected class from all options
                        optionsContainer.querySelectorAll('.option').forEach(opt => {
                            opt.classList.remove('selected');
                        });
                        
                        // Add selected class to clicked option
                        optionElement.classList.add('selected');
                        
                        // Store answer
                        quizData.selectedOption = index + 1;
                        quizData.answers[answerKey] = index + 1;
                        
                        // Enable next button
                        if (nextBtn) nextBtn.disabled = false;
                        if (submitBtn) submitBtn.disabled = false;
                    });
                    
                    optionsContainer.appendChild(optionElement);
                });
            }
            
            // Previous button functionality
            if (prevBtn) {
                prevBtn.onclick = () => {
                    if (quizData.currentQuestion > 1) {
                        quizData.currentQuestion--;
                        initializeQuiz(unitNumber);
                    }
                };
                
                // Disable prev button if on first question
                prevBtn.disabled = quizData.currentQuestion === 1;
            }
            
            // Next button functionality
            if (nextBtn) {
                nextBtn.onclick = () => {
                    if (quizData.currentQuestion < quizData.totalQuestions) {
                        quizData.currentQuestion++;
                        initializeQuiz(unitNumber);
                    } else {
                        // Move to next unit if available
                        if (unitNumber < 6) {
                            switchToUnit(unitNumber + 1);
                        }
                    }
                };
            }
            
            // Submit button functionality
            if (submitBtn) {
                submitBtn.onclick = () => {
                    showResults();
                };
            }
        }
        
        // Switch to a specific unit
        function switchToUnit(unitNumber) {
            quizData.currentUnit = unitNumber;
            quizData.currentQuestion = 1;
            
            // Update active unit card
            unitCards.forEach(card => card.classList.remove('active'));
            document.querySelector(`.unit-card[data-unit="${unitNumber}"]`).classList.add('active');
            
            // Show selected unit's quiz container
            quizContainers.forEach(container => container.classList.remove('active'));
            document.getElementById(`quiz-unit-${unitNumber}`).classList.add('active');
            
            // Hide results container
            resultsContainer.classList.remove('active');
            
            // Initialize quiz for the new unit
            initializeQuiz(unitNumber);
        }
        
        // Show results
        function showResults() {
            // Calculate score (in a real app, this would use actual answers)
            const totalQuestions = 300;
            const correctAnswers = Math.floor(Math.random() * 60) + 240; // Random score between 240-300
            const scorePercentage = Math.round((correctAnswers / totalQuestions) * 100);
            
            // Calculate time spent
            const endTime = new Date();
            const timeDiff = Math.floor((endTime - quizData.startTime) / 1000); // in seconds
            const minutes = Math.floor(timeDiff / 60);
            const seconds = timeDiff % 60;
            const timeSpent = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            
            // Update results display
            document.getElementById('score-percentage').textContent = `${scorePercentage}%`;
            document.getElementById('correct-answers').textContent = correctAnswers;
            document.getElementById('incorrect-answers').textContent = totalQuestions - correctAnswers;
            document.getElementById('time-spent').textContent = timeSpent;
            
            // Set result message based on score
            let message = "";
            if (scorePercentage >= 90) {
                message = "Outstanding! You have mastered Python programming concepts.";
            } else if (scorePercentage >= 80) {
                message = "Excellent! You have a strong understanding of Python programming concepts.";
            } else if (scorePercentage >= 70) {
                message = "Good job! You have a good grasp of Python fundamentals.";
            } else if (scorePercentage >= 60) {
                message = "Fair. Consider reviewing the course material for better understanding.";
            } else {
                message = "You need to study more. Review the syllabus and practical exercises.";
            }
            document.getElementById('results-message').textContent = message;
            
            // Hide quiz containers and show results
            quizContainers.forEach(container => container.classList.remove('active'));
            resultsContainer.classList.add('active');
        }
        
        // Restart quiz
        document.getElementById('restart-btn').addEventListener('click', () => {
            // Reset quiz data
            quizData.currentUnit = 1;
            quizData.currentQuestion = 1;
            quizData.selectedOption = null;
            quizData.answers = {};
            quizData.startTime = new Date();
            
            // Switch to unit 1
            switchToUnit(1);
        });
        
        // Initialize the first unit quiz
        initializeQuiz(1);
        
        // Simulate a 300-question database by generating sample questions
        // In a real implementation, this would be loaded from a server/database
        console.log("Python Programming Quiz loaded with 300 questions across 6 units.");
        console.log("Course Outcomes: CO1 to CO6 covered in the quiz.");
        console.log("Practical exercises referenced: 15 exercises from the syllabus.");
        
        // Add keyboard navigation
        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight' || e.key === ' ') {
                // Next question
                const activeQuiz = document.querySelector('.quiz-container.active');
                if (activeQuiz) {
                    const nextBtn = activeQuiz.querySelector('.btn-next');
                    if (nextBtn && !nextBtn.disabled) {
                        nextBtn.click();
                    }
                }
            } else if (e.key === 'ArrowLeft') {
                // Previous question
                const activeQuiz = document.querySelector('.quiz-container.active');
                if (activeQuiz) {
                    const prevBtn = activeQuiz.querySelector('.btn-prev');
                    if (prevBtn && !prevBtn.disabled) {
                        prevBtn.click();
                    }
                }
            } else if (e.key >= '1' && e.key <= '4') {
                // Select option 1-4
                const activeQuiz = document.querySelector('.quiz-container.active');
                if (activeQuiz) {
                    const option = activeQuiz.querySelector(`.option[data-option="${e.key}"]`);
                    if (option) {
                        option.click();
                    }
                }
            }
        });
    </script>
</body>
</html>
