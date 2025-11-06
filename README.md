# Tugas-Sturct-and-Union

#include <iostream>
#include <iomanip>
#include <string>
using namespace std;

const int NUM_STUDENTS = 20;

struct studentType {
    string studentFName;
    string studentLName;
    int testScore;
    char grade;
};

void getData(studentType students[], int size);
void calculateGrade(studentType students[], int size);
int highestScore(studentType students[], int size);
void printHighest(studentType students[], int size, int highest);

int main() {
    studentType students[NUM_STUDENTS];
    getData(students, NUM_STUDENTS);
    calculateGrade(students, NUM_STUDENTS);
    int high = highestScore(students, NUM_STUDENTS);
    printHighest(students, NUM_STUDENTS, high);
    return 0;
}

void getData(studentType students[], int size) {
    for (int i = 0; i < size; i++) {
        cout << "Enter first name, last name, and test score for student " << i + 1 << ": ";
        cin >> students[i].studentFName >> students[i].studentLName >> students[i].testScore;
    }
}

void calculateGrade(studentType students[], int size) {
    for (int i = 0; i < size; i++) {
        int score = students[i].testScore;
        if (score >= 90)
            students[i].grade = 'A';
        else if (score >= 80)
            students[i].grade = 'B';
        else if (score >= 70)
            students[i].grade = 'C';
        else if (score >= 60)
            students[i].grade = 'D';
        else
            students[i].grade = 'F';
    }
}

int highestScore(studentType students[], int size) {
    int highest = students[0].testScore;
    for (int i = 1; i < size; i++)
        if (students[i].testScore > highest)
            highest = students[i].testScore;
    return highest;
}

void printHighest(studentType students[], int size, int highest) {
    cout << "\nStudents with the highest test score (" << highest << "):\n";
    for (int i = 0; i < size; i++)
        if (students[i].testScore == highest)
            cout << left << setw(15) << students[i].studentLName
                 << students[i].studentFName << " - Grade: " << students[i].grade << endl;
}
