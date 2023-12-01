# To-Do-List
#CodSoft #cppprograming #internship Task4
#include <iostream>
#include <vector>

using namespace std;

class Task {
public:
    string description;
    bool completed;

    Task(string desc) : description(desc), completed(false) {}
};

class ToDoList {
private:
    vector<Task> tasks;

public:
    void addTask(const string& taskDesc) {
        tasks.emplace_back(taskDesc);
    }

    void viewTasks() const {
   for (size_t i = 0; i < tasks.size(); ++i) {
            cout << i + 1 << ". " << tasks[i].description << " - " << (tasks[i].completed ? "Completed" : "Pending") << endl;
        }
    }

    void markCompleted(size_t taskIndex) {
        if (taskIndex >= 1 && taskIndex <= tasks.size()) {
            tasks[taskIndex - 1].completed = true;
            cout << "Task marked as completed." << endl;
        } else {
            cout << "Invalid task index." << endl;
        }
    }

    void removeTask(size_t taskIndex) {
        if (taskIndex >= 1 && taskIndex <= tasks.size()) {
            tasks.erase(tasks.begin() + taskIndex - 1);
            cout << "Task removed." << endl;
        } else {
            cout << "Invalid task index." << endl;
        }
    }
};

int main() {
    ToDoList todoList;

    while (true) {
        cout << "\n1. Add Task\n2. View Tasks\n3. Mark Task as Completed\n4. Remove Task\n5. Exit" << endl;
        cout << "Enter your choice (1-5): ";

        int choice;
        cin >> choice;

        switch (choice) {
            case 1: {
                string task;
                cout << "Enter the task: ";
                cin.ignore(); // Ignore newline character left in the buffer
                getline(cin, task);
                todoList.addTask(task);
                break;
            }
            case 2:
                todoList.viewTasks();
                break;
            case 3: {
                size_t taskIndex;
                cout << "Enter the task index to mark as completed: ";
                cin >> taskIndex;
                todoList.markCompleted(taskIndex);
                break;
            }
            case 4: {
                size_t taskIndex;
                cout << "Enter the task index to remove: ";
                cin >> taskIndex;
                todoList.removeTask(taskIndex);
                break;
            }
            case 5:
                return 0;
            default:
                cout << "Invalid choice. Please enter a number from 1 to 5." << endl;
        }
    }

    return 0;
}
