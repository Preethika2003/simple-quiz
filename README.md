# simple-quiz
class quiz():
  def __init__(self):
    self.questions=[
        {
            "question":"Which is the capital city of India?",
            "options":{"A":"Delhi","B":"Mumbai","C":"Kolkata","D":"Chennai"},
            "answer":"A"
        },
        {
            "question":"What is the largest planet in our solar system?",
            "options":{"A":"Earth","B":"Mars","C":"Jupiter","D":"Venus"},
            "answer":"C"
        },
        {
            "question":"What is the largest ocean in the world?",
            "options":{"A":"Atlantic Ocean","B":"Indian Ocean","C":"Arctic Ocean","D":"Pacific Ocean"},
            "answer":"D"
        },
        {
            "question":"What is the smallest country in the world?",
            "options":{"A":"Vatican City","B":"Monaco","C":"San Marino","D":"Liechtenstein"},
            "answer":"A"
        },
        {
            "question":"What is the largest country in the world by land area?",
            "options":{"A":"Russia","B":"China","C":"India","D":"United States"},
            "answer":"B"
        }
    ]
    self.score=0
    self.correct_answers = []
  def start_quiz(self):
    print("Welcome to the Quiz !")
    question_number=1
    for q in self.questions:
      print(f"Q{question_number}: {q['question']}")
      for option,answer in q["options"].items():
        print(f"{option}:{q['options'][option]}")
      user_answer=input("Enter your answer(A,B,C,D):")
      while user_answer not in ["A", "B", "C", "D"]:
        print("Invalid input! Please enter A, B, C, or D.")
        user_answer = input("Enter your answer (A, B, C, or D): ").upper()
      if user_answer == q["answer"]:
        self.score += 1
        print("Correct!\n")
      else:
        print("Wrong!\n")
        self.correct_answers.append((q["question"], q["answer"], q["options"][q["answer"]]))
      question_number += 1
    self.show_results()
  def show_results(self):
    print(f"\nQuiz Over! Your total score: {self.score}/{len(self.questions)}")
    print("\nCorrect Answers:")
    for question, correct_option, correct_answer in self.correct_answers:
      print(f"{question}")
      print(f"  Correct Answer: {correct_option}. {correct_answer}\n")
while True:
  print("\n1. Start Quiz")
  print("2. Exit")
  choice = input("Enter your choice (1-2): ")
  if choice == "1":
    quiz_instance = quiz()
    quiz_instance.start_quiz()
  elif choice == "2":
    print("Exiting...")
    break
  else:
    print("Invalid choice! Please enter 1 or 2.")
