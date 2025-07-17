# Task CLI

A simple command-line task management tool written in Python. It allows you to add, update, delete, and manage the status of your tasks stored in a JSON file.

## Features

- Add new tasks with a description.

- Update existing tasks by ID.

- Delete tasks by ID.

- Mark tasks as in-progress or done.

- List all tasks or filter tasks by status (todo, in-progress, done).

## Installation

1. Make sure you have **Python 3** installed on your system.

2. Download the **task-cli.py** script (or save your script file).

*No external dependencies are required.*

## Usage

Run the script from your terminal:

` python task-cli.py <command> [arguments] `

## Commands

### add
Add a new task.

` python task-cli.py add "Task description" `

### update
Update the description of an existing task by ID.

` python task-cli.py update <id> "New task description" `

### delete
Delete a task by ID.

` python task-cli.py delete <id> `

### mark-in-progress
Mark a task as in progress by ID.

` python task-cli.py mark-in-progress <id> `

### mark-done
Mark a task as done by ID.

` python task-cli.py mark-done <id> `

### list
List all tasks or filter by status (todo, in-progress, done).

```
python task-cli.py list
python task-cli.py list todo
python task-cli.py list done
python task-cli.py list in-progress
```

## Data Storage

Tasks are stored in a JSON file named tasks.json in the same directory as the script.

Each task has the following fields:
- id: Unique integer identifier.
- description: Task description.
- status: Task status (todo, in-progress, or done).

## Example

```
python task-cli.py add "Write README file"
python task-cli.py list
python task-cli.py mark-in-progress 1
python task-cli.py list in-progress
python task-cli.py mark-done 1
python task-cli.py list done
python task-cli.py delete 1
```

## License

*This project is open source and free to use.*

## Reference

[Roadmap Project](https://roadmap.sh/projects/task-tracker)