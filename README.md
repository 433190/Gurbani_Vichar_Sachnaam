# Sikh History Quiz

# Define the questions, answers, and marks
quiz = [
    {"question": "Who was the founder of Sikhism?", "answer": "Guru Nanak Dev Ji", "marks": 1},
    {"question": "In which year was Guru Nanak Dev Ji born?", "answer": "1469", "marks": 1},
    {"question": "Which Guru compiled the Adi Granth, the holy scripture of Sikhs?", "answer": "Guru Arjan Dev Ji", "marks": 2},
    {"question": "What is the significance of Vaisakhi in Sikhism?", "answer": "Formation of Khalsa in 1699", "marks": 2},
    {"question": "Who was the 10th Sikh Guru?", "answer": "Guru Gobind Singh Ji", "marks": 1},
    {"question": "What are the five Ks of Sikhism?", "answer": "Kesh, Kangha, Kara, Kachera, Kirpan", "marks": 2},
    {"question": "Which battle is Guru Gobind Singh Ji famous for?", "answer": "Battle of Chamkaur", "marks": 2},
    {"question": "Who was the first Sikh martyr?", "answer": "Guru Arjan Dev Ji", "marks": 1},
    {"question": "Where is the Golden Temple located?", "answer": "Amritsar, Punjab, India", "marks": 1},
    {"question": "Which Guru introduced the concept of Langar?", "answer": "Guru Nanak Dev Ji", "marks": 1}
]

score = 0

print("Welcome to the Sikh History Quiz!\n")

# Loop through the quiz
for i, q in enumerate(quiz, 1):
    print(f"Q{i}: {q['question']}")
    user_answer = input("Your answer: ").strip()
    if user_answer.lower() == q["answer"].lower():
        print("Correct!")
        score += q["marks"]
    else:
        print(f"Wrong! The correct answer is: {q['answer']}")
    print(f"Marks for this question: {q['marks']}\n")

print(f"Quiz completed! Your total score is: {score} out of {sum(q['marks'] for q in quiz)}")
