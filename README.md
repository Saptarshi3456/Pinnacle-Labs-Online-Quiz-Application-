# Pinnacle-Labs-Online-Quiz-Application-
Build a C program that offers quizzes with questions, answers, scoring and time limits.
#include <stdio.h>
#include <stdlib.h>
#include <time.h>


typedef struct {
    char question[100];
    char answer[100];
    int points;
} Question;


int askQuestion(Question question) {
    printf("%s\n", question.question);
    char userAnswer[100];
    scanf("%s", userAnswer);
    if (strcmp(userAnswer, question.answer) == 0) {
        return question.points;
    } else {
        return 0;
    }
}

int main() {
    
    Question questions[] = {
        {"What is the capital of France?", "Paris", 10},
        {"What is 2+2?", "4", 10},
        {"What is the largest planet in our solar system?", "Jupiter", 10}
    };

    int numQuestions = sizeof(questions) / sizeof(Question);

    
    int timeLimit = 60; 

    
    time_t startTime = time(NULL);

    int score = 0;

    
    for (int i = 0; i < numQuestions; i++) {
        score += askQuestion(questions[i]);
    }

    
    time_t endTime = time(NULL);
    if (endTime - startTime > timeLimit) {
        printf("Time limit exceeded!\n");
    } else {
        printf("Your score is %d out of %d\n", score, numQuestions * 10);
    }

    return 0;
}
