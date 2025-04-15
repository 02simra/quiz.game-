# quiz.game 
import java.util.Scanner;

class Question {
    String question;
    String[] options;
    char correctOption;

    Question(String question, String[] options, char correctOption) {
        this.question = question;
        this.options = options;
        this.correctOption = correctOption;
    }

    public void display() {
        System.out.println("\n" + question);
        char optionLabel = 'A';
        for (String option : options) {
            System.out.println(optionLabel + ") " + option);
            optionLabel++;
        }
    }

    public boolean isCorrect(char answer) {
        return Character.toUpperCase(answer) == correctOption;
    }
}

public class QuizGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Question[] questions = {
            new Question("What is the capital of France?",
                    new String[]{"Berlin", "Madrid", "Paris", "Rome"}, 'C'),

            new Question("Which language is used for Android development?",
                    new String[]{"Swift", "Kotlin", "Ruby", "C#"}, 'B'),

            new Question("What does CPU stand for?",
                    new String[]{"Central Processing Unit", "Computer Power Unit", "Central Print Unit", "Control Program Unit"}, 'A'),

            new Question("Which planet is known as the Red Planet?",
                    new String[]{"Earth", "Venus", "Mars", "Jupiter"}, 'C'),

            new Question("Who wrote 'Romeo and Juliet'?",
                    new String[]{"Charles Dickens", "William Shakespeare", "Mark Twain", "Jane Austen"}, 'B')
        };

        int score = 0;

        System.out.println("🎮 Welcome to the Quiz Game!");
        System.out.println("Choose the correct option (A/B/C/D):");

        for (int i = 0; i < questions.length; i++) {
            questions[i].display();
            System.out.print("Your answer: ");
            char answer = scanner.next().charAt(0);
            if (questions[i].isCorrect(answer)) {
                System.out.println("✅ Correct!");
                score++;
            } else {
                System.out.println("❌ Wrong! Correct answer: " + questions[i].correctOption);
            }
        }

        System.out.println("\n📊 You scored " + score + " out of " + questions.length);
        if (score == questions.length) {
            System.out.println("🎉 Perfect Score! You're a quiz master!");
        } else if (score >= 3) {
            System.out.println("👍 Good job! Try again to get full marks.");
        } else {
            System.out.println("😅 Better luck next time!");
        }
    }
}
