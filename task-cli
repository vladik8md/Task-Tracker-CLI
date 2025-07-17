import argparse
import json
import os

file_path = "tasks.json"

def load():
    if not os.path.exists(file_path):
        return []
    with open(file_path, "r") as file:
        return json.load(file)

def save(tasks):
    with open(file_path, "w") as file:
        json.dump(tasks, file, indent=4)

def get_next_id(tasks):
    return max([task["id"] for task in tasks], default=0) + 1

def add(description: str):
    tasks = load()
    id = get_next_id(tasks)
    task = {"id" : id, "description" : description, "status" : "todo"}
    tasks.append(task)
    save(tasks)
    print(f"Task added successfully (ID: {id})")

def update(id: int, description: str):
    tasks = load()
    for task in tasks:
        if task["id"] == id:
            task["description"] = description
            task["status"] = "todo"
    save(tasks)
    print(f"Task updated successfully (ID: {id})")

def delete(id: int):
    tasks = load()
    for task in tasks:
        if task["id"] == id:
            tasks.remove(task)
    save(tasks)
    print(f"Task deleted successfully (ID: {id})")

def mark_in_progress(id: int):
    tasks = load()
    for task in tasks:
        if task["id"] == id:
            task["status"] = "in-progress"
    save(tasks)
    print(f"Task updated successfully (ID: {id})")

def mark_done(id: int):
    tasks = load()
    for task in tasks:
        if task["id"] == id:
            task["status"] = "done"
    save(tasks)
    print(f"Task updated successfully (ID: {id})")

def list(status):
    tasks = load()
    filtered = tasks if status is None else [task for task in tasks if task["status"] == status]
    if not filtered:
        print("No tasks.")
    for task in filtered:
        print(f"{task["id"]}. ({task["status"].upper()}) {task["description"].capitalize()}")

def main():
    parser = argparse.ArgumentParser(prog="task-cli")
    subparsers = parser.add_subparsers(dest="command")

    parser_add = subparsers.add_parser("add")
    parser_add.add_argument("description", type=str)

    parser_update = subparsers.add_parser(name="update")
    parser_update.add_argument("id", type=int)
    parser_update.add_argument("description", type=str)

    parser_delete = subparsers.add_parser(name="delete")
    parser_delete.add_argument("id", type=int)

    parser_mark_in_progress = subparsers.add_parser(name="mark-in-progress")
    parser_mark_in_progress.add_argument("id", type=int)

    parser_mark_done = subparsers.add_parser(name="mark-done")
    parser_mark_done.add_argument("id", type=int)

    parser_list = subparsers.add_parser(name="list")
    parser_list.add_argument("status", nargs="?", default=None, choices=["done", "todo", "in-progress"])

    args = parser.parse_args()

    if args.command == "add":
        add(args.description)
    elif args.command == "update":
        update(args.id, args.description)
    elif args.command == "delete":
        delete(args.id)
    elif args.command == "mark-in-progress":
        mark_in_progress(args.id)
    elif args.command == "mark-done":
        mark_done(args.id)
    elif args.command == "list":
        list(args.status)
    else:
        parser.print_help()

if __name__ == "__main__":
    main()