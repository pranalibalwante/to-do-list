# to-do-list
class Task:
    def __init__(self, title, description=""):
        self.title = title
        self.description = description
        self.completed = False

    def mark_complete(self):
        self.completed = True

    def __str__(self):
        status = "Completed" if self.completed else "Not Completed"
        return f"Task: {self.title}\nDescription: {self.description}\nStatus: {status}"

class ToDoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)

    def view_tasks(self):
        for i, task in enumerate(self.tasks):
            print(f"{i + 1}. {task}")

    def update_task(self, index, title=None, description=None):
        if 0 <= index < len(self.tasks):
            if title:
                self.tasks[index].title = title
            if description:
                self.tasks[index].description = description

    def delete_task(self, index):
        if 0 <= index < len(self.tasks):
            del self.tasks[index]

    def mark_task_complete(self, index):
        if 0 <= index < len(self.tasks):
            self.tasks[index].mark_complete()

def main():
    todo_list = ToDoList()

    while True:
        print("\nTo-Do List Application")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Update Task")
        print("4. Delete Task")
        print("5. Mark Task as Complete")
        print("6. Exit")

        choice = input("Choose an option: ")

        if choice == "1":
            title = input("Enter task title: ")
            description = input("Enter task description: ")
            task = Task(title, description)
            todo_list.add_task(task)
        elif choice == "2":
            todo_list.view_tasks()
        elif choice == "3":
            index = int(input("Enter task number to update: ")) - 1
            title = input("Enter new title (or press Enter to skip): ")
            description = input("Enter new description (or press Enter to skip): ")
            todo_list.update_task(index, title if title else None, description if description else None)
        elif choice == "4":
            index = int(input("Enter task number to delete: ")) - 1
            todo_list.delete_task(index)
        elif choice == "5":
            index = int(input("Enter task number to mark complete: ")) - 1
            todo_list.mark_task_complete(index)
        elif choice == "6":
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
