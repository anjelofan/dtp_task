# DTP Assignment 10: File Organizer Bash Script

## Objective
Create a bash script that automatically organizes files into categorized folders based on their extensions.


## Specifications

### Requirements

1. Create a bash script named `files_sorter.bash` at the root of the repository
2. The script must accept exactly **one argument**: the path to a folder containing files to be sorted (eg. `./files_sorter.bash unsorted_files`)
3. The script should create a `sorted_files` directory (if it doesn't exist) and organize files into subdirectories based on their extensions
    - If no files can be sorted into a specific category, a blank category folder should still be generated
4. Files with unrecognized extensions should be **ignored**
5. The script must handle filenames with spaces and special characters

### Allowed File Extensions & Categories

Your script only needs to recognize and sort files with these extensions:

| Extension | Category Folder |
|-----------|-----------------|
| `gif`, `png`, `jpg`, `jpeg` | `images` |
| `pdf`, `xls`, `txt`, `md` | `documents` |
| `cfg`, `sh` | `scripts` |
| `mp3` | `songs` |

## Making the Script Executable

Before running your script, you must make it executable:

```bash
chmod +x files_sorter.bash
```

### Normal Test Case

#### How to Run
```bash
./files_sorter.bash unsorted_files
```

#### Expected Behavior
Given a directory structure like:
```
unsorted_files/
├── vacation.jpg
├── report.pdf
├── song.mp3
├── notes.txt
├── logo.png
├── budget.xls
├── script.sh
├── meme.jpg
└── invoice.pdf
```

Your script should create:
```
sorted_files/
├── images/
│   ├── vacation.jpg
│   ├── logo.png
│   └── meme.jpg
├── documents/
│   ├── report.pdf
│   ├── notes.txt
│   ├── budget.xls
│   └── invoice.pdf
├── scripts/
│   └── script.sh
└── songs/
    └── song.mp3
```

 

## Bonus Section

### Bonus Requirement
Handle files with **bracket prefixes** (e.g., `[Test]filename.ext`). These files should be sorted into a **subdirectory** named after the bracket content.

### Bonus Test Case
The tester will create random files with `[Test]` prefixes. Your script should produce:

Given input:
```
unsorted_files/
├── [Test]vacation.jpg
├── report.pdf
├── [Test]song.mp3
└── notes.txt
```

Expected output:
```
sorted_files/
├── Test/
├── ├── documents/
│   ├── images/
│   │   └── vacation.jpg
|   ├── scripts/
│   └── songs/
│       └── song.mp3
├── documents/
│   ├── report.pdf
│   └── notes.txt
├── images/
├── scripts/
├── songs/
```

#### Automated Testing
Whenever a push or pull request to the github repository is made, a github action should automatically run. There will be two testcases, one for the regular points and another for bonus. The github actions job must succeed for the componet to be credited points.