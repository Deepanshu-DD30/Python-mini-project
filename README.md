# Python-mini-project

"""To-Do list."""


def show_tasks(tasks):
    if not tasks:
        print("\nNo tasks yet.")
        return

    print("\nYour tasks:")
    for number, task in enumerate(tasks, start=1):
        mark = "x" if task["done"] else " "
        print(f"{number}. [{mark}] {task['text']}")


def main():
    tasks = []

    while True:
        print("\n--- TO-DO LIST ---")
        print("1. Show tasks")
        print("2. Add task")
        print("3. Complete task")
        print("4. Delete task")
        print("5. Exit")

        choice = input("Choose an option: ").strip()

        if choice == "1":
            show_tasks(tasks)

        elif choice == "2":
            text = input("Enter a task: ").strip()
            if text:
                tasks.append({"text": text, "done": False})
                print("Task added.")
            else:
                print("Task cannot be empty.")

        elif choice == "3":
            show_tasks(tasks)
            try:
                number = int(input("Enter task number to complete: "))
                tasks[number - 1]["done"] = True
                print("Task completed.")
            except (ValueError, IndexError):
                print("Invalid task number.")

        elif choice == "4":
            show_tasks(tasks)
            try:
                number = int(input("Enter task number to delete: "))
                removed = tasks.pop(number - 1)
                print(f"Deleted: {removed['text']}")
            except (ValueError, IndexError):
                print("Invalid task number.")

        elif choice == "5":
            print("Goodbye!")
            break

        else:
            print("Please choose a number from 1 to 5.")


if __name__ == "__main__":
    main()
