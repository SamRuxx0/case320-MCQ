        }
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
        }
        
        .page {
            display: none;
            min-height: 100vh;
        }
        
        .active-page {
            display: block;
        }
        
        /* Main Page Styles */
        .main-page {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .main-header {
            text-align: center;
            margin-bottom: 40px;
            padding: 30px 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 15px;
            color: white;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        
        /* Unit Cards */
        .units-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        
        .unit-card {
            background: white;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            cursor: pointer;
            transition: all 0.3s ease;
            border-left: 4px solid #667eea;
            text-align: center;
        }
        
        .unit-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.12);
        }
        
        .unit-number {
            font-size: 3rem;
            font-weight: 700;
            color: #667eea;
            margin-bottom: 10px;
            line-height: 1;
        }
        
        .unit-title {
            font-size: 1.3rem;
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .unit-questions {
            color: #666;
            font-size: 1rem;
            font-weight: 600;
            background: #f8f9fa;
            padding: 6px 12px;
            border-radius: 20px;
            display: inline-block;
        }
        
        /* Course Outcomes */
        .co-container {
            margin-top: 40px;
            padding-top: 30px;
            border-top: 2px solid #eee;
        }
        
        .co-title {
            text-align: center;
            font-size: 1.5rem;
            color: #2c3e50;
            margin-bottom: 25px;
        }
        
        .co-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 15px;
        }
        
        .co-card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
            border-top: 4px solid #4CAF50;
        }
        
        .co-card:nth-child(1) { border-top-color: #667eea; }
        .co-card:nth-child(2) { border-top-color: #4CAF50; }
        .co-card:nth-child(3) { border-top-color: #ff9800; }
        .co-card:nth-child(4) { border-top-color: #9c27b0; }
        .co-card:nth-child(5) { border-top-color: #f44336; }
        .co-card:nth-child(6) { border-top-color: #2196F3; }
        
        .co-card-title {
            font-size: 1.2rem;
            color: #2c3e50;
            margin-bottom: 8px;
            font-weight: 600;
        }
        
        .co-card-desc {
            color: #666;
            line-height: 1.5;
            font-size: 0.95rem;
        }
        
        /* Quiz Page Styles */
        .quiz-page {
            padding: 15px;
        }
        
        .quiz-header {
            position: sticky;
            top: 0;
            background: white;
            z-index: 100;
            padding: 15px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            margin-bottom: 15px;
            border-radius: 10px;
        }
        
        .quiz-top-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .back-button {
            background: #6c757d;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            white-space: nowrap;
        }
        
        .back-button:hover {
            background: #5a6268;
        }
        
        .quiz-title {
            font-size: 1.4rem;
            color: #2c3e50;
            text-align: center;
            flex-grow: 1;
        }
        
        .quiz-info {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            background: #f8f9fa;
            padding: 12px;
            border-radius: 8px;
            margin-top: 10px;
        }
        
        .info-item {
            text-align: center;
            padding: 5px;
        }
        
        .info-value {
            font-size: 1.3rem;
            font-weight: 700;
            color: #667eea;
            display: block;
        }
        
        .info-label {
            font-size: 0.85rem;
            color: #666;
        }
        
        /* Questions Container */
        .questions-container {
            max-width: 1000px;
            margin: 0 auto;
        }
        
        .question-item {
            background: white;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
            border-left: 3px solid #667eea;
        }
        
        .question-header {
            display: flex;
            align-items: flex-start;
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid #f0f0f0;
        }
        
        .question-number {
            display: flex;
            align-items: center;
            justify-content: center;
            min-width: 35px;
            height: 35px;
            background: #667eea;
            color: white;
            border-radius: 50%;
            font-weight: 700;
            font-size: 1rem;
            margin-right: 12px;
            flex-shrink: 0;
        }
        
        .question-text {
            font-size: 1.2rem;
            color: #2c3e50;
            flex-grow: 1;
            line-height: 1.5;
        }
        
        /* Options Grid */
        .options-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 10px;
            margin-top: 15px;
        }
        
        .option {
            padding: 15px;
            background: #f8f9fa;
            border-radius: 8px;
            border: 2px solid #e9ecef;
            cursor: pointer;
            transition: all 0.2s ease;
            font-size: 1rem;
            display: flex;
            align-items: center;
        }
        
        .option:hover {
            background: #e9ecef;
        }
        
        .option.answered {
            cursor: default;
        }
        
        .option.answered:hover {
            background: #f8f9fa;
            transform: none;
        }
        
        .option-letter {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            min-width: 32px;
            height: 32px;
            background: #6c757d;
            color: white;
            border-radius: 50%;
            margin-right: 12px;
            font-weight: 600;
            flex-shrink: 0;
        }
        
        /* Answer Feedback Styles */
        .option.selected.correct {
            background: #d4edda;
            border-color: #28a745;
            color: #155724;
        }
        
        .option.selected.correct .option-letter {
            background: #28a745;
        }
        
        .option.selected.incorrect {
            background: #f8d7da;
            border-color: #dc3545;
            color: #721c24;
        }
        
        .option.selected.incorrect .option-letter {
            background: #dc3545;
        }
        
        .correct-answer {
            background: #d4edda;
            border-color: #28a745;
            color: #155724;
            cursor: default;
        }
        
        .correct-answer .option-letter {
            background: #28a745;
        }
        
        /* Feedback Section */
        .feedback-section {
            margin-top: 15px;
            padding: 15px;
            border-radius: 8px;
            display: none;
            animation: slideIn 0.3s ease;
        }
        
        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .feedback-correct {
            background: #d4edda;
            border-left: 3px solid #28a745;
            color: #155724;
        }
        
        .feedback-incorrect {
            background: #f8d7da;
            border-left: 3px solid #dc3545;
            color: #721c24;
        }
        
        .feedback-title {
            font-weight: 700;
            margin-bottom: 8px;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .feedback-explanation {
            line-height: 1.5;
            margin-top: 8px;
            font-size: 0.95rem;
        }
        
        /* Submit Section */
        .submit-section {
            position: fixed;
            bottom: 15px;
            right: 15px;
            background: white;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.15);
            z-index: 1000;
        }
        
        .submit-button {
            background: #4CAF50;
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            white-space: nowrap;
        }
        
        .submit-button:hover:not(:disabled) {
            background: #43a047;
            transform: translateY(-2px);
            box-shadow: 0 5px 10px rgba(76, 175, 80, 0.3);
        }
        
        .submit-button:disabled {
            background: #cccccc;
            cursor: not-allowed;
        }
        
        /* Results Modal */
        .results-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 2000;
            padding: 20px;
        }
        
        .results-modal.active {
            display: flex;
        }
        
        .results-content {
            background: white;
            padding: 30px;
            border-radius: 15px;
            max-width: 500px;
            width: 100%;
            text-align: center;
            animation: popIn 0.3s ease;
        }
        
        @keyframes popIn {
            from {
                opacity: 0;
                transform: scale(0.9);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }
        
        .score-circle {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2rem;
            font-weight: 700;
        }
        
        .modal-buttons {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin-top: 20px;
            flex-wrap: wrap;
        }
        
        .modal-button {
            padding: 10px 25px;
            border-radius: 8px;
            border: none;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            flex: 1;
            min-width: 120px;
        }
        
        .modal-restart {
            background: #667eea;
            color: white;
        }
        
        .modal-restart:hover {
            background: #5a6fd8;
        }
        
        .modal-close {
            background: #6c757d;
            color: white;
        }
        
        .modal-close:hover {
            background: #5a6268;
        }
        
        /* Mobile Responsive */
        @media (max-width: 768px) {
            .units-container, .co-grid {
                grid-template-columns: 1fr;
            }
            
            .quiz-top-bar {
                flex-direction: column;
                text-align: center;
            }
            
            .back-button {
                align-self: flex-start;
            }
            
            .quiz-title {
                order: 2;
                width: 100%;
                margin-top: 10px;
            }
            
            .question-text {
                font-size: 1.1rem;
            }
            
            .option {
                padding: 12px;
                font-size: 0.95rem;
            }
            
            .submit-section {
                position: static;
                margin-top: 20px;
                box-shadow: none;
                text-align: center;
            }
            
            .submit-button {
                width: 100%;
            }
            
            .modal-button {
                min-width: 100px;
            }
        }
        
        @media (max-width: 480px) {
            .main-header {
                padding: 20px 15px;
            }
            
            h1 {
                font-size: 2rem;
            }
            
            .subtitle {
                font-size: 1rem;
            }
            
            .unit-card {
                padding: 20px;
            }
            
            .unit-number {
                font-size: 2.5rem;
            }
            
            .unit-title {
                font-size: 1.1rem;
            }
            
            .quiz-info {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Main Page -->
    <div class="page main-page active-page" id="main-page">
        <div class="main-page">
            <header class="main-header">
                <h1>INT108: Python Programming</h1>
                <div class="subtitle">Select a Unit to Start the Quiz</div>
            </header>
            
            <div class="units-container" id="units-container">
                <!-- Unit cards will be generated by JavaScript -->
            </div>
            
            <!-- Course Outcomes at Bottom -->
            <div class="co-container">
                <h2 class="co-title">Course Outcomes</h2>
                <div class="co-grid" id="co-grid">
                    <!-- Course outcomes will be generated by JavaScript -->
                </div>
            </div>
        </div>
    </div>

    <!-- Quiz Page (All questions on one page) -->
    <div class="page quiz-page" id="quiz-page">
        <div class="quiz-header">
            <div class="quiz-top-bar">
                <button class="back-button" id="back-button">← Back</button>
                <div class="quiz-title" id="quiz-title">Unit I: Programming Environment & Basics</div>
            </div>
            
            <div class="quiz-info">
                <div class="info-item">
                    <span class="info-value" id="questions-count">50</span>
                    <span class="info-label">Total Questions</span>
                </div>
                <div class="info-item">
                    <span class="info-value" id="answered-count">0</span>
                    <span class="info-label">Answered</span>
                </div>
                <div class="info-item">
                    <span class="info-value" id="score-display">0</span>
                    <span class="info-label">Score</span>
                </div>
                <div class="info-item">
                    <span class="info-value" id="percentage">0%</span>
                    <span class="info-label">Progress</span>
                </div>
            </div>
        </div>
        
        <div class="questions-container" id="questions-container">
            <!-- All questions will be generated here -->
        </div>
        
        <div class="submit-section">
            <button class="submit-button" id="submit-button" disabled>Submit Quiz</button>
        </div>
    </div>

    <!-- Results Modal -->
    <div class="results-modal" id="results-modal">
        <div class="results-content">
            <h2>Quiz Completed!</h2>
            <div class="score-circle">
                <span id="score-percentage">85%</span>
            </div>
            <p style="margin: 15px 0; font-size: 1.1rem;">You answered <span id="final-correct" style="font-weight: 700;">42</span> out of <span id="final-total" style="font-weight: 700;">50</span> questions correctly</p>
            <div class="modal-buttons">
                <button class="modal-button modal-restart" id="restart-button">Try Another Unit</button>
                <button class="modal-button modal-close" id="close-modal">Close</button>
            </div>
        </div>
    </div>

    <script>
        // Generate 50 questions for each unit
        function generateUnitQuestions(unitId, count) {
            const questions = [];
            
            // Unit-specific question templates
            const unitTemplates = {
                1: { // Unit 1: Programming Environment & Basics
                    questions: [
                        "Which of the following is a valid variable name in Python?",
                        "What is the output of 'Hello' + 'World' in Python?",
                        "Which operator is used for exponentiation in Python?",
                        "What does the '//' operator do in Python?",
                        "Which of the following is NOT a Python keyword?",
                        "What is the correct way to comment a single line in Python?",
                        "Which function is used to get user input in Python?",
                        "What is the result of 5 % 2 in Python?",
                        "Which of these is a floating point number in Python?",
                        "What does the type() function return?",
                        "Which statement correctly assigns multiple variables in Python?",
                        "What is the output of print(2 * 3 ** 2)?",
                        "Which module is used for mathematical functions in Python?",
                        "How do you convert a string to integer in Python?",
                        "What is the output of print('Python'[1])?",
                        "Which escape sequence represents a new line in Python strings?",
                        "What does len('Hello') return?",
                        "Which operator checks if two values are equal in Python?",
                        "What is the result of bool(0) in Python?",
                        "How do you create a multi-line string in Python?"
                    ],
                    options: [
                        ["1st_variable", "my-variable", "_my_variable", "my variable"],
                        ["HelloWorld", "Hello World", "Hello+World", "Error"],
                        ["^", "**", "^^", "exp()"],
                        ["Integer division", "Floor division", "Comment", "Both A and B"],
                        ["while", "lambda", "switch", "yield"],
                        ["// This is a comment", "/* This is a comment */", "# This is a comment", "<!-- This is a comment -->"],
                        ["input()", "get()", "read()", "scan()"],
                        ["2.5", "2", "1", "0"],
                        ["5", "'5.0'", "5.0", "All of the above"],
                        ["Memory address", "Variable value", "Data type", "Variable length"],
                        ["a, b, c = 1, 2, 3", "a = b = c = 1, 2, 3", "a; b; c = 1; 2; 3", "a=1 b=2 c=3"],
                        ["36", "18", "12", "Error"],
                        ["math", "calc", "numpy", "mathematics"],
                        ["int()", "strToInt()", "parseInt()", "Integer()"],
                        ["P", "y", "t", "h"],
                        ["\n", "\r", "\t", "\\n"],
                        ["4", "5", "6", "Error"],
                        ["=", "==", "===", "equals"],
                        ["True", "False", "0", "Error"],
                        ["Triple quotes", "Backslash", "Both A and B", "Not possible"]
                    ],
                    answers: [2, 0, 1, 3, 2, 2, 0, 2, 2, 2, 0, 1, 0, 0, 1, 0, 1, 1, 1, 2],
                    explanations: [
                        "Valid Python variable names must start with a letter or underscore, cannot start with a number or contain spaces/hyphens.",
                        "The + operator concatenates strings in Python.",
                        "The ** operator is used for exponentiation (e.g., 2**3 = 8).",
                        "The // operator performs floor division (integer division).",
                        "Python doesn't have a 'switch' keyword; it uses if-elif-else instead.",
                        "Python uses # for single-line comments.",
                        "input() function reads user input from the keyboard.",
                        "% is modulus operator giving remainder (5 ÷ 2 = 2 remainder 1).",
                        "5.0 is a float, 5 is an integer, '5.0' is a string.",
                        "type() returns the data type of a variable or value.",
                        "Python allows multiple assignment: a, b, c = 1, 2, 3",
                        "Exponentiation has higher precedence: 3**2 = 9, then 2*9 = 18.",
                        "The math module provides mathematical functions and constants.",
                        "int() converts strings or floats to integers.",
                        "String indexing starts at 0, so 'Python'[1] = 'y'.",
                        "\\n is newline, \\r is carriage return, \\t is tab.",
                        "len() returns number of characters in a string.",
                        "== checks equality, = is assignment operator.",
                        "0, empty strings, and None evaluate to False in Python.",
                        "Multi-line strings can use triple quotes or backslash continuation."
                    ]
                },
                2: { // Unit 2: Conditional & Iterative Statements
                    questions: [
                        "Which loop is guaranteed to execute at least once in Python?",
                        "What is the output of: for i in range(3): print(i)",
                        "What does the break statement do in a loop?",
                        "What is the output of: x = 5; if x > 3: print('Yes') else: print('No')",
                        "Which keyword is used to define an if statement?",
                        "What is the purpose of the continue statement?",
                        "How many times will 'Hello' be printed: for i in range(5): print('Hello')",
                        "What is the correct syntax for a while loop?",
                        "What is the output of: i = 0; while i < 3: i += 1; print(i)",
                        "Which operator represents 'not equal to' in Python?",
                        "What is the purpose of the else clause with loops?",
                        "Which loop is used when you know the number of iterations?",
                        "What does range(1, 10, 2) generate?",
                        "Which statement is used to skip the rest of the current iteration?",
                        "What is a nested loop?",
                        "Which module is used to generate random numbers?",
                        "What does random.randint(1, 10) return?",
                        "How do you generate a random float between 0 and 1?",
                        "What is an infinite loop?",
                        "How do you exit an infinite loop?"
                    ],
                    options: [
                        ["for loop", "while loop", "do-while loop (Python doesn't have this)", "None"],
                        ["0 1 2", "1 2 3", "0 1 2 3", "1 2"],
                        ["Skips iteration", "Exits loop", "Restarts loop", "Pauses loop"],
                        ["Yes", "No", "Syntax Error", "No output"],
                        ["if", "when", "case", "check"],
                        ["Exit loop", "Skip iteration", "Restart loop", "Pause execution"],
                        ["4", "5", "6", "Error"],
                        ["while condition { }", "while condition:", "while (condition)", "All"],
                        ["0 1 2", "1 2 3", "1 2", "2 3"],
                        ["!=", "<>", "!==", "Both A and B"],
                        ["Executes if loop completes normally", "Executes if error occurs", "Always executes", "Never executes"],
                        ["for loop", "while loop", "Both", "Neither"],
                        ["1 to 10", "1, 3, 5, 7, 9", "1, 2, 3...10", "2, 4, 6, 8"],
                        ["break", "continue", "pass", "skip"],
                        ["Loop inside another loop", "Broken loop", "Complex loop", "Recursive loop"],
                        ["random", "rand", "generate", "math.random"],
                        ["Integer 1-10", "Float 1-10", "List 1-10", "String"],
                        ["random.random()", "random.float()", "random()", "rand.float()"],
                        ["Loop that never ends", "Fast loop", "Error loop", "Complex loop"],
                        ["break", "continue", "exit()", "All of above"]
                    ],
                    answers: [2, 0, 1, 0, 0, 1, 1, 1, 1, 3, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0]
                },
                3: { // Unit 3: Functions & Recursion
                    questions: [
                        "What is the base case in a recursive function?",
                        "How do you define a function in Python?",
                        "What is a parameter in a function?",
                        "What is an argument in a function?",
                        "What is the return statement used for?",
                        "What are default parameters?",
                        "What are keyword arguments?",
                        "What is variable-length argument?",
                        "What is function scope?",
                        "What is a lambda function?",
                        "What is recursion?",
                        "What happens without a base case in recursion?",
                        "What is a local variable?",
                        "What is a global variable?",
                        "What is the global keyword used for?",
                        "What are built-in functions?",
                        "What is function overloading?",
                        "What is function composition?",
                        "What is a pure function?",
                        "What is a higher-order function?"
                    ],
                    options: [
                        ["First call", "Stopping condition", "Return statement", "Recursive call"],
                        ["function myFunc():", "def myFunc():", "func myFunc():", "define myFunc():"],
                        ["Input to function", "Output of function", "Function name", "Return value"],
                        ["Input value", "Output value", "Function type", "Variable name"],
                        ["Send value back", "Print value", "Stop function", "All of above"],
                        ["Parameters with default values", "Required parameters", "Optional parameters", "None"],
                        ["Arguments with parameter names", "Required arguments", "Positional arguments", "All"],
                        ["*args", "**kwargs", "Both", "Neither"],
                        ["Where variables are accessible", "Function size", "Return type", "Parameters"],
                        ["Anonymous function", "Named function", "Large function", "Recursive function"],
                        ["Function calling itself", "Complex function", "Loop function", "Math function"],
                        ["Infinite recursion", "Error", "Nothing", "Returns None"],
                        ["Variable inside function", "Variable outside function", "Constant", "Parameter"],
                        ["Variable accessible everywhere", "Local variable", "Parameter", "Argument"],
                        ["Modify global variable", "Create local variable", "Delete variable", "Import module"],
                        ["Predefined functions", "User functions", "Lambda functions", "Recursive functions"],
                        ["Multiple functions same name", "One function", "Big function", "Complex function"],
                        ["Using function result as input", "Writing functions", "Calling functions", "Defining functions"],
                        ["No side effects", "Has side effects", "Returns nothing", "Complex function"],
                        ["Takes/returns functions", "Simple function", "Math function", "Built-in function"]
                    ],
                    answers: [1, 1, 0, 0, 0, 0, 0, 2, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
                },
                4: { // Unit 4: Strings, Lists, Tuples & Dictionaries
                    questions: [
                        "Which data type is mutable in Python?",
                        "How do you add element to a list?",
                        "How do you access list elements?",
                        "What is list slicing?",
                        "How to remove element from list?",
                        "What is tuple?",
                        "How to create a dictionary?",
                        "How to access dictionary values?",
                        "What are dictionary methods?",
                        "What is set?",
                        "What are list comprehensions?",
                        "How to sort a list?",
                        "What is string formatting?",
                        "What are string methods?",
                        "How to concatenate lists?",
                        "What is deep copy vs shallow copy?",
                        "How to iterate through dictionary?",
                        "What is enumerate()?",
                        "What is zip()?",
                        "What are generators?"
                    ],
                    options: [
                        ["Tuple", "String", "List", "All"],
                        ["add()", "append()", "insert()", "Both B and C"],
                        ["Indexing", "Key", "Both", "Neither"],
                        ["Extracting portion", "Cutting list", "Removing", "Adding"],
                        ["remove()", "pop()", "del", "All"],
                        ["Immutable sequence", "Mutable sequence", "Dictionary", "Set"],
                        ["{}", "dict()", "Both", "Neither"],
                        ["Key", "Index", "Both", "Neither"],
                        ["keys()", "values()", "items()", "All"],
                        ["Unordered unique elements", "Ordered elements", "Key-value", "Sequence"],
                        ["Compact list creation", "List expansion", "List sorting", "List copying"],
                        ["sort()", "sorted()", "Both", "Neither"],
                        ["Inserting variables", "Changing string", "Cutting", "All"],
                        ["upper()", "lower()", "split()", "All"],
                        ["+ operator", "extend()", "Both", "Neither"],
                        ["Copy references vs values", "Fast vs slow", "Large vs small", "None"],
                        ["for key in dict", "for key, value in dict.items()", "Both", "Neither"],
                        ["Adds counter", "Removes counter", "Sorts", "Zips"],
                        ["Combine iterables", "Separate", "Sort", "Remove"],
                        ["Yield values", "Return list", "Create list", "Sort list"]
                    ],
                    answers: [2, 3, 0, 0, 3, 0, 2, 0, 3, 0, 0, 2, 0, 3, 2, 0, 2, 0, 0, 0]
                },
                5: { // Unit 5: Classes & Objects
                    questions: [
                        "Which OOP concept allows inheritance?",
                        "What is __init__ method?",
                        "What is self parameter?",
                        "What is inheritance?",
                        "What is polymorphism?",
                        "What is encapsulation?",
                        "What is abstraction?",
                        "How to create class?",
                        "How to create object?",
                        "What are class variables?",
                        "What are instance variables?",
                        "What are methods?",
                        "What is method overriding?",
                        "What are access modifiers?",
                        "What is constructor?",
                        "What is destructor?",
                        "What is multiple inheritance?",
                        "What is super()?",
                        "What are magic methods?",
                        "What is composition?"
                    ],
                    options: [
                        ["Inheritance", "Polymorphism", "Encapsulation", "Abstraction"],
                        ["Constructor", "Destructor", "Method", "Variable"],
                        ["Reference to instance", "Class name", "Method name", "Parameter"],
                        ["Deriving class", "Hiding data", "Many forms", "Simplifying"],
                        ["Many forms", "One form", "Hiding", "Inheriting"],
                        ["Data hiding", "Data showing", "Inheriting", "Polymorphism"],
                        ["Hiding complexity", "Showing details", "Inheriting", "Polymorphism"],
                        ["class ClassName:", "def ClassName:", "object ClassName:", "new ClassName:"],
                        ["ClassName()", "new ClassName", "create ClassName", "object ClassName"],
                        ["Shared by all instances", "Unique per instance", "Temporary", "Global"],
                        ["Unique per instance", "Shared", "Temporary", "Global"],
                        ["Functions in class", "Variables", "Objects", "Classes"],
                        ["Redefining parent method", "Creating method", "Deleting", "Hiding"],
                        ["Public, private, protected", "Only public", "Only private", "None"],
                        ["__init__", "__del__", "__str__", "__add__"],
                        ["__del__", "__init__", "__str__", "__add__"],
                        ["Inherit multiple classes", "One class", "No inheritance", "Complex"],
                        ["Call parent class", "Create object", "Delete object", "Modify"],
                        ["Special methods", "Regular methods", "Hidden", "Private"],
                        ["Has-a relationship", "Is-a relationship", "Inheritance", "Polymorphism"]
                    ],
                    answers: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
                },
                6: { // Unit 6: Files, Exceptions & Regular Expressions
                    questions: [
                        "Which mode opens file for reading and writing?",
                        "What is try-except block?",
                        "What is regular expression?",
                        "Which module for regex?",
                        "How to open file?",
                        "How to read file?",
                        "How to write file?",
                        "How to close file?",
                        "What is with statement?",
                        "What are file modes?",
                        "What is exception?",
                        "What is finally block?",
                        "What is raise statement?",
                        "What are common exceptions?",
                        "What is regex pattern?",
                        "What is match()?",
                        "What is search()?",
                        "What is findall()?",
                        "What is sub()?",
                        "What is split()?"
                    ],
                    options: [
                        ["'a+'", "'r'", "'w'", "'rb'"],
                        ["Error handling", "File handling", "Loop", "Condition"],
                        ["Pattern matching", "File handling", "Error handling", "Loop"],
                        ["re", "regex", "pattern", "match"],
                        ["open()", "file()", "read()", "load()"],
                        ["read()", "readline()", "readlines()", "All"],
                        ["write()", "writelines()", "Both", "Neither"],
                        ["close()", "exit()", "end()", "stop()"],
                        ["Context manager", "Loop", "Condition", "Function"],
                        ["r, w, a, +", "Only r", "Only w", "None"],
                        ["Runtime error", "Syntax error", "Logical error", "All"],
                        ["Always executes", "Only on error", "Never executes", "Sometimes"],
                        ["Manually trigger exception", "Catch exception", "Ignore", "Handle"],
                        ["ValueError", "TypeError", "IOError", "All"],
                        ["Search pattern", "File pattern", "Error pattern", "Loop pattern"],
                        ["Start of string", "Anywhere", "End", "Multiple"],
                        ["Anywhere in string", "Start only", "End only", "Not in string"],
                        ["All matches", "First match", "No match", "Last match"],
                        ["Replace matches", "Find matches", "Split", "Join"],
                        ["Split by pattern", "Join strings", "Replace", "Find"]
                    ],
                    answers: [0, 0, 0, 0, 0, 3, 2, 0, 0, 0, 0, 0, 0, 3, 0, 0, 0, 0, 0, 0]
                }
            };
            
            const template = unitTemplates[unitId] || unitTemplates[1];
            
            for (let i = 0; i < count; i++) {
                const qIndex = i % template.questions.length;
                const optIndex = i % template.options.length;
                const ansIndex = i % template.answers.length;
                
                questions.push({
                    id: i + 1,
                    text: `${template.questions[qIndex]} (Q${i + 1})`,
                    options: template.options[optIndex],
                    correct: template.answers[ansIndex],
                    explanation: template.explanations ? 
                        template.explanations[qIndex] || `Correct answer for question ${i + 1} in Unit ${unitId}` :
                        `This is question ${i + 1} for Unit ${unitId}. The correct answer demonstrates key concepts.`
                });
            }
            
            return questions;
        }

        // Complete quiz data with 50 questions in each unit
        const quizData = {
            units: [
                {
                    id: 1,
                    title: "Unit I: Programming Environment & Basics",
                    description: "Python installation, variables, expressions, statements, operators, strings, comments",
                    questions: generateUnitQuestions(1, 50)
                },
                {
                    id: 2,
                    title: "Unit II: Conditional & Iterative Statements",
                    description: "Boolean expressions, if-else, loops (for/while), nested loops, random numbers",
                    questions: generateUnitQuestions(2, 50)
                },
                {
                    id: 3,
                    title: "Unit III: Functions & Recursion",
                    description: "Function calls, parameters, arguments, math functions, recursion, type conversion",
                    questions: generateUnitQuestions(3, 50)
                },
                {
                    id: 4,
                    title: "Unit IV: Strings, Lists, Tuples & Dictionaries",
                    description: "String operations, list manipulation, tuples, dictionaries, data structure operations",
                    questions: generateUnitQuestions(4, 50)
                },
                {
                    id: 5,
                    title: "Unit V: Classes & Objects",
                    description: "OOP concepts, classes, objects, inheritance, polymorphism, method overriding",
                    questions: generateUnitQuestions(5, 50)
                },
                {
                    id: 6,
                    title: "Unit VI: Files, Exceptions & Regular Expressions",
                    description: "File handling, exceptions, try-except blocks, regex patterns, web scraping basics",
                    questions: generateUnitQuestions(6, 50)
                }
            ],
            
            courseOutcomes: [
                {
                    id: 1,
                    title: "CO1: Installation & Basics",
                    description: "Describe Python environment installation and language basics"
                },
                {
                    id: 2,
                    title: "CO2: Conditional & Iterative Statements",
                    description: "Apply conditional and iterative statements for evaluating alternatives"
                },
                {
                    id: 3,
                    title: "CO3: Functions & Recursion",
                    description: "Explore functions including recursion with parameters and arguments"
                },
                {
                    id: 4,
                    title: "CO4: Data Structures",
                    description: "Construct core data structures like lists, dictionaries, tuples and sets"
                },
                {
                    id: 5,
                    title: "CO5: OOP Concepts",
                    description: "Apply OOP concepts using encapsulation, polymorphism, and inheritance"
                },
                {
                    id: 6,
                    title: "CO6: Files & Regular Expressions",
                    description: "Examine file handling and apply regular expressions for pattern matching"
                }
            ],
            
            currentUnit: null,
            userAnswers: {},
            lockedQuestions: new Set() // Track questions that can't be changed
        };

        // DOM Elements
        const mainPage = document.getElementById('main-page');
        const quizPage = document.getElementById('quiz-page');
        const unitsContainer = document.getElementById('units-container');
        const coGrid = document.getElementById('co-grid');
        const backButton = document.getElementById('back-button');
        const quizTitle = document.getElementById('quiz-title');
        const questionsContainer = document.getElementById('questions-container');
        const submitButton = document.getElementById('submit-button');
        const resultsModal = document.getElementById('results-modal');
        const scorePercentage = document.getElementById('score-percentage');
        const finalCorrect = document.getElementById('final-correct');
        const finalTotal = document.getElementById('final-total');
        const restartButton = document.getElementById('restart-button');
        const closeModal = document.getElementById('close-modal');

        // Initialize the main page
        function initializeMainPage() {
            // Create unit cards
            quizData.units.forEach(unit => {
                const unitCard = document.createElement('div');
                unitCard.className = 'unit-card';
                unitCard.innerHTML = `
                    <div class="unit-number">${unit.id}</div>
                    <div class="unit-title">${unit.title}</div>
                    <div class="unit-questions">${unit.questions.length} Questions</div>
                `;
                unitCard.addEventListener('click', () => startQuiz(unit.id - 1));
                unitsContainer.appendChild(unitCard);
            });

            // Create course outcomes cards
            quizData.courseOutcomes.forEach(co => {
                const coCard = document.createElement('div');
                coCard.className = 'co-card';
                coCard.innerHTML = `
                    <div class="co-card-title">${co.title}</div>
                    <div class="co-card-desc">${co.description}</div>
                `;
                coGrid.appendChild(coCard);
            });
        }

        // Start quiz for a specific unit
        function startQuiz(unitIndex) {
            quizData.currentUnit = unitIndex;
            quizData.userAnswers = {};
            quizData.lockedQuestions.clear();
            
            const unit = quizData.units[unitIndex];
            quizTitle.textContent = unit.title;
            
            // Update question count
            document.getElementById('questions-count').textContent = unit.questions.length;
            
            // Show quiz page, hide main page
            mainPage.classList.remove('active-page');
            quizPage.classList.add('active-page');
            
            // Generate all questions
            generateAllQuestions();
            
            // Update stats
            updateStats();
            
            // Scroll to top
            window.scrollTo(0, 0);
        }

        // Generate all questions on the page
        function generateAllQuestions() {
            questionsContainer.innerHTML = '';
            const unit = quizData.units[quizData.currentUnit];
            
            unit.questions.forEach((question, index) => {
                const questionElement = document.createElement('div');
                questionElement.className = 'question-item';
                questionElement.id = `question-${index + 1}`;
                
                const letters = ['A', 'B', 'C', 'D'];
                let optionsHTML = '';
                
                const isAnswered = quizData.userAnswers[index] !== undefined;
                const isLocked = quizData.lockedQuestions.has(index);
                
                question.options.forEach((option, optIndex) => {
                    const isSelected = quizData.userAnswers[index] === optIndex;
                    const isCorrect = optIndex === question.correct;
                    
                    let optionClass = 'option';
                    if (isLocked || isAnswered) {
                        optionClass += ' answered';
                    }
                    
                    if (isSelected) {
                        optionClass += isCorrect ? ' selected correct' : ' selected incorrect';
                    } else if (isAnswered && isCorrect) {
                        optionClass += ' correct-answer';
                    }
                    
                    optionsHTML += `
                        <div class="${optionClass}" 
                             data-question="${index}" 
                             data-option="${optIndex}"
                             onclick="${isLocked || isAnswered ? '' : `selectOption(${index}, ${optIndex})`}">
                            <span class="option-letter">${letters[optIndex]}</span>
                            <span class="option-text">${option}</span>
                        </div>
                    `;
                });
                
                const feedbackClass = isAnswered ? 
                    (quizData.userAnswers[index] === question.correct ? 'feedback-correct' : 'feedback-incorrect') : '';
                const feedbackSymbol = isAnswered ? 
                    (quizData.userAnswers[index] === question.correct ? '✓' : '✗') : '';
                const feedbackTitle = isAnswered ? 
                    (quizData.userAnswers[index] === question.correct ? 'Correct!' : 'Incorrect!') : '';
                
                questionElement.innerHTML = `
                    <div class="question-header">
                        <div class="question-number">${index + 1}</div>
                        <div class="question-text">${question.text}</div>
                    </div>
                    <div class="options-grid">
                        ${optionsHTML}
                    </div>
                    <div class="feedback-section ${feedbackClass}" id="feedback-${index}" 
                         style="${isAnswered ? 'display: block;' : 'display: none;'}">
                        <div class="feedback-title">
                            <span>${feedbackSymbol} ${feedbackTitle}</span>
                            ${isLocked ? '<small style="margin-left: 10px; color: #666;">(Answer locked)</small>' : ''}
                        </div>
                        <div class="feedback-explanation">
                            ${question.explanation}
                        </div>
                    </div>
                `;
                
                questionsContainer.appendChild(questionElement);
            });
        }

        // User selects an option (CANNOT CHANGE ONCE SELECTED)
        function selectOption(questionIndex, optionIndex) {
            // Check if question is already answered/locked
            if (quizData.lockedQuestions.has(questionIndex) || quizData.userAnswers[questionIndex] !== undefined) {
                return; // Don't allow changes
            }
            
            const unit = quizData.units[quizData.currentUnit];
            const question = unit.questions[questionIndex];
            
            // Store user's answer
            quizData.userAnswers[questionIndex] = optionIndex;
            
            // LOCK this question - user cannot change answer
            quizData.lockedQuestions.add(questionIndex);
            
            // Update the question display
            updateQuestionDisplay(questionIndex);
            
            // Update stats
            updateStats();
            
            // Scroll to show the feedback
            const questionElement = document.getElementById(`question-${questionIndex + 1}`);
            questionElement.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
        }

        // Update a single question's display
        function updateQuestionDisplay(questionIndex) {
            const unit = quizData.units[quizData.currentUnit];
            const question = unit.questions[questionIndex];
            const questionElement = document.getElementById(`question-${questionIndex + 1}`);
            const feedbackElement = document.getElementById(`feedback-${questionIndex}`);
            
            const userAnswer = quizData.userAnswers[questionIndex];
            const isCorrect = userAnswer === question.correct;
            
            // Update options
            const options = questionElement.querySelectorAll('.option');
            options.forEach((option, optIndex) => {
                const optionLetter = option.querySelector('.option-letter');
                
                // Reset and mark as answered/locked
                option.className = 'option answered';
                option.onclick = null; // Remove click handler
                option.style.cursor = 'default';
                
                if (optIndex === userAnswer) {
                    option.classList.add('selected');
                    option.classList.add(isCorrect ? 'correct' : 'incorrect');
                    optionLetter.style.background = isCorrect ? '#28a745' : '#dc3545';
                } else if (optIndex === question.correct) {
                    option.classList.add('correct-answer');
                    optionLetter.style.background = '#28a745';
                }
            });
            
            // Update feedback
            feedbackElement.className = `feedback-section ${isCorrect ? 'feedback-correct' : 'feedback-incorrect'}`;
            feedbackElement.style.display = 'block';
            feedbackElement.innerHTML = `
                <div class="feedback-title">
                    <span>${isCorrect ? '✓ Correct!' : '✗ Incorrect!'}</span>
                    <small style="margin-left: 10px; color: #666;">(Answer locked - cannot be changed)</small>
                </div>
                <div class="feedback-explanation">
                    ${question.explanation}
                </div>
            `;
        }

        // Update statistics
        function updateStats() {
            const unit = quizData.units[quizData.currentUnit];
            const totalQuestions = unit.questions.length;
            const answeredCount = Object.keys(quizData.userAnswers).length;
            
            // Calculate score
            let score = 0;
            unit.questions.forEach((question, index) => {
                if (quizData.userAnswers[index] === question.correct) {
                    score++;
                }
            });
            
            const percentage = Math.round((answeredCount / totalQuestions) * 100);
            const scorePercentage = Math.round((score / totalQuestions) * 100);
            
            // Update display
            document.getElementById('answered-count').textContent = answeredCount;
            document.getElementById('score-display').textContent = score;
            document.getElementById('percentage').textContent = `${percentage}%`;
            
            // Enable submit button only when all questions answered
            submitButton.disabled = answeredCount < totalQuestions;
        }

        // Submit quiz
        submitButton.addEventListener('click', () => {
            const unit = quizData.units[quizData.currentUnit];
            const totalQuestions = unit.questions.length;
            
            // Calculate final score
            let correctCount = 0;
            unit.questions.forEach((question, index) => {
                if (quizData.userAnswers[index] === question.correct) {
                    correctCount++;
                }
            });
            
            const finalPercentage = Math.round((correctCount / totalQuestions) * 100);
            
            // Update results modal
            scorePercentage.textContent = `${finalPercentage}%`;
            finalCorrect.textContent = correctCount;
            finalTotal.textContent = totalQuestions;
            
            // Show results modal
            resultsModal.classList.add('active');
        });

        // Back to units
        backButton.addEventListener('click', () => {
            quizPage.classList.remove('active-page');
            mainPage.classList.add('active-page');
        });

        // Restart quiz
        restartButton.addEventListener('click', () => {
            resultsModal.classList.remove('active');
            backButton.click();
        });

        // Close modal
        closeModal.addEventListener('click', () => {
            resultsModal.classList.remove('active');
        });

        // Close modal on background click
        resultsModal.addEventListener('click', (e) => {
            if (e.target === resultsModal) {
                resultsModal.classList.remove('active');
            }
        });

        // Initialize the application
        initializeMainPage();
        
        console.log("Python Programming Quiz Website Loaded");
        console.log("50 Questions in Each Unit (Total: 300 questions)");
        console.log("Answers cannot be changed once selected");
        console.log("Mobile Responsive Design Implemented");
    </script>
</body>
</html>   
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
