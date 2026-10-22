# Student Grade Report

A small Python script that reads student scores from CSV data, calculates each student's average, assigns a letter grade, prints a summary table, and exports the results as JSON.

Missing or invalid scores (for example an empty cell or the text `bad data`) don't crash the script. They are skipped, the average is calculated from the valid scores only, and the student's row is flagged in the NOTES column.

## Requirements

- Python 3.6 or newer
- No third-party packages (uses only the standard library: `csv`, `io`, `json`)

## Setup

1. Save `grade_report.py` to a folder of your choice.
2. Confirm Python is installed:

   ```
   python3 --version
   ```

No further installation is needed.

## Usage

Run the script from the folder that contains it:

```
python3 grade_report.py
```

It prints a summary table, the class average, the student count, and a JSON export of the results.

### Using your own data

The student data is stored in the `CSV_DATA` variable near the top of `grade_report.py`. To use your own data, replace its contents, keeping the header row:

```
name,score1,score2,score3
Jane Doe,88,92,79
```

Each row needs a name and three scores. Scores must be whole numbers; anything else is treated as invalid and skipped.

## Sample output

```
==================================================
NAME                   AVG  GRADE  NOTES
==================================================
James Omondi          84.3      B  All scores valid
Sandra Weru           80.0      B  1 invalid score(s)
Patrick Njiru         90.7      A  All scores valid
Grace Achieng         65.0      D  1 invalid score(s)
Brian Kamau           55.0      F  All scores valid
==================================================

Class average: 75.0
Students: 5
```

The script then prints the JSON export. Each record contains `name`, `scores` (the original values as entered), `average`, and `grade`.

## Grading scale

| Average | Grade |
|---------|-------|
| 90 and above | A |
| 80 to 89.9 | B |
| 70 to 79.9 | C |
| 60 to 69.9 | D |
| Below 60 | F |
| No valid scores | N/A |

## Notes on how results are calculated

- Each student's average is rounded to one decimal place.
- The class average is the mean of the students' individual averages (students with no valid scores are excluded), rounded to one decimal place.
- The grade is based on the rounded average.

## Project structure

```
grade_report/
├── grade_report.py   # the script
└── README.md         # this file
```
