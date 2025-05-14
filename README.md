# Exno.7-Prompt-Engineering
# Date:
# Register no.
# Aim: To Develop a prompt-based application tailored to their personal needs, fostering creativity and practical problem-solving skills while leveraging the capabilities of large language models.

The aim of this project is to create a prompt-based application that helps users organize and track their daily tasks. The application is designed to mimic an interaction with an AI system, similar to ChatGPT, where the user can input simple commands (prompts) to:
1.	Organize tasks by scheduling them throughout the day.
2.	Update task statuses based on the user's progress.
3.	Show the user's task completion status and progress.
This report walks through the code, explaining its core functionality, step-by-step usage, and output.


# Algorithm: Develop a prompt-based application using ChatGPT - To demonstrate how to create a prompt-based application to organize daily tasks, showing the progression from simple to more advanced prompt designs and their corresponding outputs.
The application works through the following steps:
1.	Initialize Task List: Predefine a set of daily tasks such as Yoga, Breakfast, Exercise, etc., with their respective durations and default statuses.
2.	Generate Schedule: Automatically generate a schedule that assigns specific time slots to each task, based on a given start time.
3.	Update Task Status: Allow the user to interact with the app by updating the status of any task (from "Not Started" to "In Progress" or "Completed").
4.	Track Progress: The user can view their overall progress, such as how many tasks are completed out of the total tasks for the day.
5.	Provide Feedback: The system generates real-time feedback based on the user’s actions, showing the current task schedule and the progress made.
Code Walkthrough
The code is implemented in Python and uses the datetime library to manage and format times. The core of the app is the DailyTaskManager class, which manages the task list, schedule, and user interactions.
1. Task Initialization
The DailyTaskManager class begins by initializing a list of tasks, each containing a task name, estimated duration (in minutes), and a default status of “Not Started”.
python
CopyEdit
```class DailyTaskManager:
    def __init__(self):
        self.tasks = [
            {"task": "Yoga", "duration": 30, "status": "Not Started"},
            {"task": "Breakfast", "duration": 20, "status": "Not Started"},
            {"task": "Daily Commute", "duration": 45, "status": "Not Started"},
            {"task": "Exercise", "duration": 40, "status": "Not Started"},
            {"task": "Focus on Learning", "duration": 120, "status": "Not Started"}
        ] ```
•	Explanation: This initialization creates a list of tasks with duration (how long each task will take) and status (default status).
________________________________________
2. Displaying the Schedule
The show_schedule() method generates a daily schedule starting from a specified time (default is 07:00 AM). It computes the start and end times for each task based on its duration.
python
CopyEdit
```def show_schedule(self, start_time="07:00"):
    print("\nYour Daily Task Schedule:")
    current_time = datetime.datetime.strptime(start_time, "%H:%M")
    for task in self.tasks:
        end_time = current_time + datetime.timedelta(minutes=task['duration'])
        task['start'] = current_time.strftime("%H:%M")
        task['end'] = end_time.strftime("%H:%M")
        print(f"{task['start']} - {task['end']}: {task['task']} [{task['status']}]")
        current_time = end_time ```
•	Explanation: The method uses datetime to calculate start and end times for each task. It then prints out the schedule, showing the start time, end time, task name, and its current status.
________________________________________
3. Updating Task Status
The update_task_status() method allows the user to update the status of any task. The user is prompted to enter the task name and the new status (Not Started, In Progress, Completed).
python
CopyEdit
```def update_task_status(self, task_name, status):
    for task in self.tasks:
        if task["task"].lower() == task_name.lower():
            task["status"] = status
            print(f"Updated '{task['task']}' to status: {status}")
            return
    print("Task not found.") ```
•	Explanation: The method loops through the task list and finds the task that matches the name entered by the user. It updates the status and prints a message confirming the change.
________________________________________
4. Showing Task Progress
The show_progress() method displays how many tasks have been completed out of the total number of tasks. It also provides a detailed status for each task.
python
CopyEdit
```def show_progress(self):
    completed = sum(1 for t in self.tasks if t['status'] == 'Completed')
    total = len(self.tasks)
    print(f"\nProgress: {completed}/{total} tasks completed.")
    for task in self.tasks:
        print(f"- {task['task']}: {task['status']}") ```
•	Explanation: This method counts the tasks marked as “Completed” and calculates the total number of tasks. It then prints the progress summary and the status of each task.
________________________________________
5. Main Program Logic
The __main__ block starts the application. It initializes a DailyTaskManager instance, displays the schedule, and provides a menu for user interactions.
python
CopyEdit
```if __name__ == "__main__":
    manager = DailyTaskManager()
    manager.show_schedule()

    while True:
        print("\nOptions: \n1. Update Task Status\n2. Show Progress\n3. Show Schedule\n4. Exit")
        choice = input("Enter your choice (1-4): ")
        if choice == '1':
            task_name = input("Enter task name: ")
            status = input("Enter new status (Not Started/In Progress/Completed): ")
            manager.update_task_status(task_name, status)
        elif choice == '2':
            manager.show_progress()
        elif choice == '3':
            manager.show_schedule()
        elif choice == '4':
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Try again.") ```
•	Explanation: The main loop continuously prompts the user to:
o	Update task status.
o	Show the progress of tasks.
o	Display the daily schedule.
o	Exit the program.
________________________________________
Example Output
1. Initial Schedule
The user sees the following schedule when they run the app:
yaml
CopyEdit
Your Daily Task Schedule:
07:00 - 07:30: Yoga [Not Started]
07:30 - 07:50: Breakfast [Not Started]
07:50 - 08:35: Daily Commute [Not Started]
08:35 - 09:15: Exercise [Not Started]
09:15 - 11:15: Focus on Learning [Not Started]
2. Updating a Task Status
When the user updates a task status, such as marking Yoga as Completed:
pgsql
CopyEdit
Enter task name: Yoga
Enter new status: Completed
Updated 'Yoga' to status: Completed
3. Showing Task Progress
When the user asks to see their progress, the app shows:
yaml
CopyEdit
Progress: 1/5 tasks completed.
- Yoga: Completed
- Breakfast: Not Started
- Daily Commute: Not Started
- Exercise: Not Started
- Focus on Learning: Not Started




# Result: The Prompt is executed successfully


