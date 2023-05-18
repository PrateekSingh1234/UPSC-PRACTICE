# UPSC-PRACTICE
Practice UPSC questions here 
<!DOCTYPE html>
<html>
<head>
  <title>UPSC Exam Practice</title>
  <style>
    .question-container {
      margin-bottom: 20px;
    }
    .options-container {
      margin-top: 10px;
    }
    .explanation-container {
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <h1>UPSC Exam Practice</h1>
  
  <div id="questionContainer" class="question-container">
    <h2>Question:</h2>
    <p id="question"></p>
    <div id="optionsContainer" class="options-container">
      <input type="radio" name="option" id="option1" value="option1">
      <label for="option1" id="option1Label"></label><br>
      <input type="radio" name="option" id="option2" value="option2">
      <label for="option2" id="option2Label"></label><br>
      <input type="radio" name="option" id="option3" value="option3">
      <label for="option3" id="option3Label"></label><br>
      <input type="radio" name="option" id="option4" value="option4">
      <label for="option4" id="option4Label"></label>
    </div>
    <button id="submitAnswerBtn">Submit Answer</button>
  </div>
  
  <div id="explanationContainer" class="explanation-container">
    <h2>Explanation:</h2>
    <p id="explanation"></p>
  </div>
  
  <script>
    var questions = [
      {
        question: "Who is the President of India?",
        options: [
          "Narendra Modi",
          "Ram Nath Kovind",
          "Rahul Gandhi",
          "Amit Shah"
        ],
        correctAnswerIndex: 1,
        explanation: "Ram Nath Kovind is the current President of India."
      },
      {
        question: "What is the longest river in India?",
        options: [
          "Ganga",
          "Yamuna",
          "Godavari",
          "Brahmaputra"
        ],
        correctAnswerIndex: 0,
        explanation: "The Ganga is the longest river in India."
      },
      {
        question: "Who is the author of the book 'Discovery of India'?",
        options: [
          "Jawaharlal Nehru",
          "Rabindranath Tagore",
          "Vikram Seth",
          "Arundhati Roy"
        ],
        correctAnswerIndex: 0,
        explanation: "The book 'Discovery of India' was written by Jawaharlal Nehru."
      },
      // Add more questions here
    ];
    
    var currentQuestionIndex = 0;
    
    var questionElement = document.getElementById("question");
    var option1Label = document.getElementById("option1Label");
    var option2Label = document.getElementById("option2Label");
    var option3Label = document.getElementById("option3Label");
    var option4Label = document.getElementById("option4Label");
    var explanationElement = document.getElementById("explanation");
    
    function displayQuestion() {
      var currentQuestion = questions[currentQuestionIndex];
      
      questionElement.textContent = currentQuestion.question;
      option1Label.textContent = currentQuestion.options[0];
      option2Label.textContent = currentQuestion.options[1];
      option3Label.textContent = currentQuestion.options[2];
      option4Label.textContent = currentQuestion.options[3];
      
      clearSelectedOption();
      hideExplanation();
    }
    
    function clearSelectedOption() {
      var optionElements = document.getElementsByName("option");
      for (var i = 0; i < optionElements.length; i++) {
        optionElements[i].checked = false;
      }
    }
    
    function showExplanation(isCorrect) {
      var currentQuestion = questions[currentQuestionIndex];
      explanationElement.textContent = currentQuestion.explanation;
      
      if (isCorrect) {
        explanationElement.style.color = "green";
      } else {
        explanationElement.style.color = "red";
      }
    }
    
    function hideExplanation() {
      explanationElement.textContent = "";
    }
    
    function checkAnswer() {
      var selectedOption = document.querySelector('input[name="option"]:checked');
      
      if (selectedOption) {
        var selectedOptionIndex = parseInt(selectedOption.value);
        var currentQuestion = questions[currentQuestionIndex];
        
        if (selectedOptionIndex === currentQuestion.correctAnswerIndex) {
          showExplanation(true);
        } else {
          showExplanation(false);
        }
        
        currentQuestionIndex++;
        
        if (currentQuestionIndex < questions.length) {
          displayQuestion();
        } else {
          questionElement.textContent = "End of questions";
          clearSelectedOption();
          hideExplanation();
        }
      }
    }
    
    var submitAnswerBtn = document.getElementById("submitAnswerBtn");
    submitAnswerBtn.addEventListener("click", checkAnswer);
    
    displayQuestion();
  </script>
</body>
</html>
