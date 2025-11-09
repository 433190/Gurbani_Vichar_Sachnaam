<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sikh History Quiz</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        #quiz-container {
            background: #fff;
            padding: 20px 40px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            width: 500px;
        }
        h2 {
            margin-bottom: 20px;
        }
        .option {
            background: #e0e0e0;
            padding: 10px;
            margin: 8px 0;
            border-radius: 5px;
            cursor: pointer;
        }
        .option:hover {
            background: #d0d0d0;
        }
        #score {
            font-weight: bold;
            margin-top: 20px;
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            border: none;
            background: #4CAF50;
            color: white;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background: #45a049;
        }
    </style>
</head>
<body>

<div id="quiz-container">
    <h2 id="question">Question text</h2>
    <div id="options"></div>
    <div id="score"></div>
    <button id="next-btn">Next Question</button>
</div>

<script>
const quiz = [
    {
         question: "What is Naam?",
        options: ["Sound of God", "Space", "Written words given by someone", "i dont know"],
        answer: "Sound of God",
        marks: 1
    },
    {
        question: "In which year was Guru Nanak Dev Ji born?",
        options: ["1469", "1499", "1505", "1450"],
        answer: "1469",
        marks: 1
    },
    {
        question: "Which Guru compiled the Adi Granth?",
        options: ["Guru Arjan Dev Ji", "Guru Gobind Singh Ji", "Guru Nanak Dev Ji", "Guru Ram Das Ji"],
        answer: "Guru Arjan Dev Ji",
        marks: 1
    },
    {
        question: "What is the significance of Vaisakhi in Sikhism?",
        options: ["Formation of Khalsa in 1699", "Birth of Guru Nanak", "Start of Langar", "Guru Granth Sahib completion"],
        answer: "Formation of Khalsa in 1699",
        marks: 1
    },
    {
        question: "Who was the 10th Sikh Guru?",
        options: ["Guru Gobind Singh Ji", "Guru Arjan Dev Ji", "Guru Nanak Dev Ji", "Guru Tegh Bahadur Ji"],
        answer: "Guru Gobind Singh Ji",
        marks: 1
    },
    {
        question: "What are the five Ks of Sikhism?",
        options: ["Kesh, Kangha, Kara, Kachera, Kirpan", "Kangha, Kara, Langar, Kirpan, Kachera", "Kesh, Kara, Langar, Kirpan, Kachera", "Kara, Kesh, Kangha, Kirpan, Langar"],
        answer: "Kesh, Kangha, Kara, Kachera, Kirpan",
        marks: 1
    },
    {
        question: "Which battle is Guru Gobind Singh Ji famous for?",
        options: ["Battle of Chamkaur", "Battle of Panipat", "Battle of Kurukshetra", "Battle of Sirhind"],
        answer: "Battle of Chamkaur",
        marks: 1
    },
    {
        question: "Who was the first Sikh martyr?",
        options: ["Guru Arjan Dev Ji", "Guru Tegh Bahadur Ji", "Guru Gobind Singh Ji", "Guru Nanak Dev Ji"],
        answer: "Guru Arjan Dev Ji",
        marks: 1
    },
    {
        question: "Where is the Golden Temple located?",
        options: ["Amritsar, Punjab, India", "Delhi, India", "Chandigarh, India", "Lahore, Pakistan"],
        answer: "Amritsar, Punjab, India",
        marks: 1
    },
    {
        question: "Which Guru introduced the concept of Langar?",
        options: ["Guru Nanak Dev Ji", "Guru Arjan Dev Ji", "Guru Gobind Singh Ji", "Guru Tegh Bahadur Ji"],
        answer: "Guru Nanak Dev Ji",
        marks: 1
    }
];

let currentQuestion = 0;
let score = 0;

const questionEl = document.getElementById("question");
const optionsEl = document.getElementById("options");
const scoreEl = document.getElementById("score");
const nextBtn = document.getElementById("next-btn");

function loadQuestion() {
    const q = quiz[currentQuestion];
    questionEl.textContent = `Q${currentQuestion + 1}: ${q.question}`;
    optionsEl.innerHTML = "";

    q.options.forEach(option => {
        const btn = document.createElement("div");
        btn.textContent = option;
        btn.className = "option";
        btn.addEventListener("click", () => checkAnswer(option));
        optionsEl.appendChild(btn);
    });
}

function checkAnswer(selected) {
    const q = quiz[currentQuestion];
    if (selected === q.answer) {
        score += q.marks;
        alert(`Correct! You earned ${q.marks} marks.`);
    } else {
        alert(`Wrong! Correct answer: ${q.answer}\nMarks: ${q.marks}`);
    }
    nextBtn.style.display = "block";
}

nextBtn.addEventListener("click", () => {
    currentQuestion++;
    if (currentQuestion < quiz.length) {
        loadQuestion();
        nextBtn.style.display = "none";
    } else {
        questionEl.textContent = "Quiz Completed!";
        optionsEl.innerHTML = "";
        scoreEl.textContent = `Your total score: ${score} out of ${quiz.reduce((acc, q) => acc + q.marks, 0)}`;
        nextBtn.style.display = "none";
    }
});

// Initialize first question
loadQuestion();
nextBtn.style.display = "none";
</script>

</body>
</html>
