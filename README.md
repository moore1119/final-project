# final-project
import os

def display_menu():
    print("Note Taking Application")
    print("1. View Notes")
    print("2. Add Note")
    print("3. Edit Note")
    print("4. Delete Note")
    print("5. Exit")

def view_notes():
    note_files = [f for f in os.listdir(".") if f.endswith(".txt")]
    if not note_files:
        print("No notes found.")
        return
    print("Available notes:")
    for i, file in enumerate(note_files, 1):
        print(f"{i}. {file}")
    choice = input("Enter the number of the note you want to view: ")
    if choice.isdigit() and 1 <= int(choice) <= len(note_files):
        with open(note_files[int(choice) - 1], "r") as file:
            print("Your note:")
            print(file.read())
    else:
        print("Invalid choice.")

def add_note():
    note_name = input("Enter the name of your note (without extension): ")
    note_name += ".txt"
    note_content = input("Enter your note: ")
    with open(note_name, "w") as file:
        file.write(note_content)
    print("Note added successfully.")

def edit_note():
    note_files = [f for f in os.listdir(".") if f.endswith(".txt")]
    if not note_files:
        print("No notes found.")
        return
    print("Available notes:")
    for i, file in enumerate(note_files, 1):
        print(f"{i}. {file}")
    choice = input("Enter the number of the note you want to edit: ")
    if choice.isdigit() and 1 <= int(choice) <= len(note_files):
        note_name = note_files[int(choice) - 1]
        with open(note_name, "r") as file:
            print("Current content of the note:")
            print(file.read())
        new_content = input("Enter the new content for the note: ")
        with open(note_name, "w") as file:
            file.write(new_content)
        print("Note edited successfully.")
    else:
        print("Invalid choice.")

def delete_note():
    note_files = [f for f in os.listdir(".") if f.endswith(".txt")]
    if not note_files:
        print("No notes found.")
        return
    print("Available notes:")
    for i, file in enumerate(note_files, 1):
        print(f"{i}. {file}")
    choice = input("Enter the number of the note you want to delete: ")
    if choice.isdigit() and 1 <= int(choice) <= len(note_files):
        note_name = note_files[int(choice) - 1]
        os.remove(note_name)
        print("Note deleted successfully.")
    else:
        print("Invalid choice.")

def main():
    while True:
        display_menu()
        choice = input("Enter your choice: ")
        if choice == "1":
            view_notes()
        elif choice == "2":
            add_note()
        elif choice == "3":
            edit_note()
        elif choice == "4":
            delete_note()
        elif choice == "5":
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please enter a valid option.")

if __name__ == "__main__":
    main()

