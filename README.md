# To-Do-List
A simple To-Do List application built using Python.

tasks = []

while True:
    print("\n========== TO-DO LIST ==========")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Mark Task as Completed")
    print("4. Delete Task")
    print("5. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        task = input("Enter Task: ")
        date = input("Enter Due Date (DD-MM-YYYY): ")

        task_data = {
            "task": task,
            "date": date,
            "status": "Pending"
        }

        tasks.append(task_data)
        print("Task Added Successfully!")

    elif choice == "2":
        if len(tasks) == 0:
            print("\nNo Tasks Available!")
        else:
            print("\n========== TASK LIST ==========")
            for i in range(len(tasks)):
                print(f"\nTask No. : {i+1}")
                print("Task     :", tasks[i]["task"])
                print("Due Date :", tasks[i]["date"])
                print("Status   :", tasks[i]["status"])

    elif choice == "3":
        if len(tasks) == 0:
            print("\nNo Tasks Available!")
        else:
            for i in range(len(tasks)):
                print(f"{i+1}. {tasks[i]['task']} ({tasks[i]['status']})")

            num = int(input("Enter Task Number to Complete: "))

            if 1 <= num <= len(tasks):
                tasks[num-1]["status"] = "Completed"
                print("Task Marked as Completed!")
            else:
                print("Invalid Task Number!")

    elif choice == "4":
        if len(tasks) == 0:
            print("\nNo Tasks Available!")
        else:
            for i in range(len(tasks)):
                print(f"{i+1}. {tasks[i]['task']}")

            num = int(input("Enter Task Number to Delete: "))

            if 1 <= num <= len(tasks):
                deleted = tasks.pop(num-1)
                print(f"'{deleted['task']}' Deleted Successfully!")
            else:
                print("Invalid Task Number!")

    elif choice == "5":
        print("\nThank You for Using To-Do List!")
        break

    else:
        print("Invalid Choice! Please Try Again.")
