# OmniCodex: Essential Python Guide for Data Analysis

Welcome to the **OmniCodex**, your comprehensive guide to mastering the fundamental Python concepts needed for data analysis at OmniCo. This guide is designed to help you navigate through your projects with confidence, providing clear explanations and code patterns that you can apply to your work.

---

## Table of Contents

1. [Reading and Writing Files](#1-reading-and-writing-files)
   - [Reading Files](#reading-files)
   - [Skipping Header Rows](#skipping-header-rows)
   - [Reading and Processing CSV Files](#reading-and-processing-csv-files)
   - [Reading Text Files into Lists](#reading-text-files-into-lists)
   - [Writing Files](#writing-files)
   - [Writing CSV Files](#writing-csv-files)
2. [String Manipulation](#2-string-manipulation)
   - [Stripping Whitespace](#stripping-whitespace)
   - [Splitting Strings](#splitting-strings)
   - [Converting Strings to Lowercase or Uppercase](#converting-strings-to-lowercase-or-uppercase)
   - [Checking for Substrings](#checking-for-substrings)
   - [Counting Substring Occurrences](#counting-substring-occurrences)
   - [Converting Strings to Numbers](#converting-strings-to-numbers)
3. [Working with Data Structures](#3-working-with-data-structures)
   - [Lists](#lists)
   - [Dictionaries](#dictionaries)
   - [Nested Dictionaries](#nested-dictionaries)
   - [Updating Nested Dictionaries](#updating-nested-dictionaries)
   - [Extracting Keys and Values as Lists](#extracting-keys-and-values-as-lists)
   - [Using Dictionaries to Count and Sum Values](#using-dictionaries-to-count-and-sum-values)
4. [Control Flow Statements](#4-control-flow-statements)
5. [Loops and Iteration](#5-loops-and-iteration)
6. [Performing Calculations](#6-performing-calculations)
   - [Basic Arithmetic Operations](#basic-arithmetic-operations)
   - [Using min() and max() Functions](#using-min-and-max-functions)
   - [Calculating Percentage Increases](#calculating-percentage-increases)
   - [Avoiding Division by Zero](#avoiding-division-by-zero)
   - [Casting Values During Calculations](#casting-values-during-calculations)
   - [Sorting Data](#sorting-data)
7. [Formatting and Printing Output](#7-formatting-and-printing-output)
8. [Error Handling](#8-error-handling)
9. [Best Practices](#9-best-practices)
10. [Additional Tips](#10-additional-tips)
11. [Conclusion](#11-conclusion)

---

## 1. Reading and Writing Files

### Reading Files

To process data stored in files, you'll need to read the file content into your program.

**Example: Reading a file line by line**

```python
# Open the file in read mode
with open('data.txt', 'r') as file:
    # Iterate over each line in the file
    for line in file:
        # Process the line
        print(line)
```

- **Note:** Using `with open()` ensures the file is properly closed after its contents have been processed.

### Skipping Header Rows

When reading CSV files, you might need to skip the header row.

**Example: Skipping the header**

```python
with open('data.csv', 'r') as file:
    # Read the header line
    header = file.readline()
    # Process the remaining lines
    for line in file:
        # Process the line
        print(line)
```

### Reading and Processing CSV Files

Often, data is stored in CSV (Comma-Separated Values) files. You can read and process CSV files by splitting each line into fields.

**Example: Reading a CSV file and processing data**

```python
# Open the CSV file
with open('employees.csv', 'r') as file:
    # Read and discard the header line
    header = file.readline()
    # Process each line in the file
    for line in file:
        # Remove leading/trailing whitespace characters (including newline)
        line = line.strip()
        # Split the line into a list of values based on commas
        fields = line.split(',')
        # Access individual fields
        employee_id = fields[0]
        name = fields[1]
        department = fields[2]
        salary = fields[3]
        # Output the processed data
        print(f"ID: {employee_id}, Name: {name}, Department: {department}, Salary: {salary}")
```

**Sample `employees.csv` content:**

```
EmployeeID,Name,Department,Salary
E001,Alice Smith,Sales,75000
E002,Bob Johnson,Engineering,82000
E003,Charlie Lee,Marketing,68000
```

**Output of the code:**

```
ID: E001, Name: Alice Smith, Department: Sales, Salary: 75000
ID: E002, Name: Bob Johnson, Department: Engineering, Salary: 82000
ID: E003, Name: Charlie Lee, Department: Marketing, Salary: 68000
```

- **Explanation:**
  - `line.strip()` removes any leading/trailing whitespace, including newline characters.
  - `fields = line.split(',')` splits the line into a list of values.
  - `fields[0]` accesses the first element in the list (EmployeeID).
  - `fields[1:]` accesses elements from index 1 to the end (Name, Department, Salary).

### Reading Text Files into Lists

To read a text file and store each line as an element in a list, you can use list comprehension or loop through the file.

**Example: Reading a text file into a list**

```python
# Method 1: Using a loop
keywords = []
with open('keywords.txt', 'r') as file:
    for line in file:
        keyword = line.strip()
        keywords.append(keyword)

# Method 2: Using list comprehension
with open('keywords.txt', 'r') as file:
    keywords = [line.strip() for line in file]

print(keywords)
```

- **Explanation:**
  - `keywords.txt` contains a list of keywords, one on each line.
  - `line.strip()` removes any leading or trailing whitespace, including newline characters.
  - The result is a list called `keywords` containing all the keywords from the file.

### Writing Files

To output data or results to a file, you can write to a file using the following pattern:

**Example: Writing data to a file**

```python
# Open the file in write mode
with open('output.txt', 'w') as file:
    # Write data to the file
    file.write('Hello, OmniCo!\n')
    file.write('Data analysis complete.')
```

### Writing CSV Files

When you need to write data to a CSV file, you can write strings formatted with commas separating the values.

**Example: Writing data to a CSV file**

```python
# Data to write
data = [
    {'keyword': 'happy', 'total_ltv': 250},
    {'keyword': 'sad', 'total_ltv': 150},
    {'keyword': 'excited', 'total_ltv': 300}
]

# Open the CSV file in write mode
with open('top_keywords.csv', 'w') as file:
    # Write the header row
    file.write('keyword,total_ltv\n')
    # Write data rows
    for item in data:
        line = f"{item['keyword']},{item['total_ltv']}\n"
        file.write(line)
```

- **Explanation:**
  - We create a list of dictionaries, each representing a row of data.
  - We open 'top_keywords.csv' for writing.
  - We write the header row with column names.
  - For each item in `data`, we format a line as 'keyword,total_ltv' and write it to the file.

---

## 2. String Manipulation

### Stripping Whitespace

When reading lines from a file, you may need to remove extra whitespace characters like newline (`\n`).

**Example: Removing trailing whitespace**

```python
line = line.strip()
```

### Splitting Strings

To break a string into a list of substrings based on a delimiter (e.g., commas in a CSV file), use the `split()` method.

**Example: Splitting a comma-separated string**

```python
data = 'apple,banana,cherry'
fruits = data.split(',')  # ['apple', 'banana', 'cherry']
```

### Converting Strings to Lowercase or Uppercase

To perform case-insensitive comparisons, you can convert strings to lowercase or uppercase using the `lower()` or `upper()` methods.

**Example: Converting to lowercase**

```python
text = 'Hello World'
lower_text = text.lower()  # 'hello world'
```

### Checking for Substrings

To check if a substring exists within a string, use the `in` operator.

**Example: Checking for a substring**

```python
keyword = 'hello'
text = 'Hello World'

# Case-sensitive check
if keyword in text:
    print('Found keyword (case-sensitive)')

# Case-insensitive check
if keyword.lower() in text.lower():
    print('Found keyword (case-insensitive)')
```

- **Explanation:**
  - `in` operator checks for the presence of a substring.
  - Converting both strings to lowercase ensures the comparison is case-insensitive.

### Counting Substring Occurrences

To count how many times a substring appears in a string, use the `count()` method.

**Example: Counting occurrences of a substring**

```python
text = 'Happy happy joy joy happy days'
keyword = 'happy'

# Case-insensitive count
occurrences = text.lower().count(keyword.lower())
print(f'The keyword "{keyword}" occurs {occurrences} times.')
```

- **Explanation:**
  - `text.lower()` converts the entire string to lowercase.
  - `keyword.lower()` ensures the keyword is also in lowercase.
  - `count()` returns the number of non-overlapping occurrences of the substring.

### Converting Strings to Numbers

Data read from files is often in string format. To perform calculations, convert strings to integers or floats.

**Example: Converting strings to numeric types**

```python
number_str = '42'
number_int = int(number_str)      # 42 as an integer
number_float = float(number_str)  # 42.0 as a float
```

---

## 3. Working with Data Structures

### Lists

A list is an ordered collection of items.

**Example: Creating and accessing a list**

```python
# Create a list of departments
departments = ['Sales', 'Engineering', 'Marketing', 'HR']

# Access the first department
first_department = departments[0]  # 'Sales'

# Access departments from index 1 to the end
remaining_departments = departments[1:]  # ['Engineering', 'Marketing', 'HR']
```

### Dictionaries

A dictionary stores data in key-value pairs.

**Example: Creating and using a dictionary**

```python
# Create a dictionary of employee IDs and names
employees = {
    'E001': 'Alice Smith',
    'E002': 'Bob Johnson',
    'E003': 'Charlie Lee'
}

# Access a value by key
employee_name = employees['E001']  # 'Alice Smith'
```

### Nested Dictionaries

Dictionaries can contain other dictionaries as values.

**Example: Nested dictionary**

```python
# Create a dictionary of employees with their details
employees = {
    'E001': {'name': 'Alice Smith', 'department': 'Sales', 'salary': 75000},
    'E002': {'name': 'Bob Johnson', 'department': 'Engineering', 'salary': 82000},
    'E003': {'name': 'Charlie Lee', 'department': 'Marketing', 'salary': 68000}
}

# Access nested values
alice_department = employees['E001']['department']  # 'Sales'
```

### Updating Nested Dictionaries

You can update values within a nested dictionary by specifying the keys in sequence.

**Example: Updating a nested dictionary**

```python
# Update Bob's salary
employees['E002']['salary'] = 85000

# Add a new key-value pair to Charlie's details
employees['E003']['email'] = 'charlie.lee@omnico.com'
```

- **Note:** If the key does not exist, it will be added to the dictionary.

### Extracting Keys and Values as Lists

You can extract all the keys or values from a dictionary and convert them into a list.

**Example: Getting a list of employee IDs**

```python
# Get a list of employee IDs
employee_ids = list(employees.keys())  # ['E001', 'E002', 'E003']
```

### Using Dictionaries to Count and Sum Values

You can use dictionaries to keep track of counts or sums associated with keys.

**Example: Counting occurrences of keywords in text**

```python
# List of keywords
keywords = ['happy', 'sad', 'excited']

# Initialize a dictionary to store counts
keyword_counts = {keyword: 0 for keyword in keywords}

# Sample texts
texts = [
    'I feel so happy today!',
    'This is a sad story.',
    'She is very excited about the trip.',
    'Happy times are here.',
    'Feeling happy and excited!'
]

# Count occurrences
for text in texts:
    for keyword in keywords:
        # Perform a case-insensitive search
        count = text.lower().count(keyword)
        keyword_counts[keyword] += count

print(keyword_counts)
```

- **Explanation:**
  - We initialize `keyword_counts` with keys as keywords and values as 0.
  - For each text, we count how many times each keyword appears.
  - We update the count in the dictionary accordingly.

**Example: Summing values associated with keywords**

Suppose each text also has an associated value, and we want to sum the values for each keyword found.

```python
# Data items with text and value
data_items = [
    {'text': 'I feel so happy today!', 'value': 10},
    {'text': 'This is a sad story.', 'value': 5},
    {'text': 'She is very excited about the trip.', 'value': 8},
    {'text': 'Happy times are here.', 'value': 7},
    {'text': 'Feeling happy and excited!', 'value': 15}
]

# Initialize sums dictionary
keyword_sums = {keyword: 0 for keyword in keywords}

# Sum values for keywords
for item in data_items:
    text = item['text']
    value = item['value']
    for keyword in keywords:
        if keyword in text.lower():
            keyword_sums[keyword] += value

print(keyword_sums)
```

- **Explanation:**
  - For each data item, we check if a keyword is in the text.
  - If found, we add the item's value to the corresponding keyword's sum.

---

## 4. Control Flow Statements

### If Statements

Use `if`, `elif`, and `else` to execute code based on conditions.

**Example: Checking employee performance**

```python
sales = 120000

if sales >= 100000:
    print('Excellent performance')
elif sales >= 70000:
    print('Good performance')
else:
    print('Needs improvement')
```

---

## 5. Loops and Iteration

### For Loops

Use `for` loops to iterate over sequences like lists or dictionaries.

**Example: Iterating over a list**

```python
departments = ['Sales', 'Engineering', 'Marketing']

for dept in departments:
    print(dept)
```

### Iterating Over Dictionaries

When iterating over dictionaries, you can access keys and values.

**Example: Iterating over dictionary items**

```python
employees = {
    'E001': 'Alice Smith',
    'E002': 'Bob Johnson',
    'E003': 'Charlie Lee'
}

for emp_id, name in employees.items():
    print(f'ID: {emp_id}, Name: {name}')
```

### Looping Through Nested Dictionaries and Computing Values

You can loop through a nested dictionary to perform calculations and update the dictionary.

**Example: Calculating bonuses and adding them to the dictionary**

```python
# Existing nested dictionary of employees and their salaries
employees = {
    'E001': {'name': 'Alice Smith', 'department': 'Sales', 'salary': 75000},
    'E002': {'name': 'Bob Johnson', 'department': 'Engineering', 'salary': 85000},
    'E003': {'name': 'Charlie Lee', 'department': 'Marketing', 'salary': 68000}
}

# Loop through each employee to calculate bonuses
for emp_id, details in employees.items():
    salary = details['salary']
    # Calculate bonus: 10% of salary
    bonus = salary * 0.10
    # Add the bonus to the employee's details
    employees[emp_id]['bonus'] = bonus

# The employees dictionary now includes the bonus amount
print(employees)
```

**Output:**

```python
{
    'E001': {'name': 'Alice Smith', 'department': 'Sales', 'salary': 75000, 'bonus': 7500.0},
    'E002': {'name': 'Bob Johnson', 'department': 'Engineering', 'salary': 85000, 'bonus': 8500.0},
    'E003': {'name': 'Charlie Lee', 'department': 'Marketing', 'salary': 68000, 'bonus': 6800.0}
}
```

- **Explanation:**
  - For each employee, we calculated a bonus equal to 10% of their salary.
  - We added a new key `'bonus'` to each employee's dictionary.

### While Loops

Use `while` loops to execute a block of code as long as a condition is true.

**Example: Using a while loop**

```python
count = 0
while count < 5:
    print(f'Count is {count}')
    count += 1
```

### Using Break Statements

The `break` statement exits the nearest enclosing loop.

**Example: Exiting a loop early**

```python
for number in range(10):
    if number == 5:
        break  # Exit the loop when number is 5
    print(number)
```

---

## 6. Performing Calculations

### Basic Arithmetic Operations

You can perform arithmetic operations using `+`, `-`, `*`, `/`, and `%`.

**Example: Calculating the average salary**

```python
total_salary = 228000
number_of_employees = 3
average_salary = total_salary / number_of_employees  # 76000.0
```

### Using min() and max() Functions

The `min()` and `max()` functions return the smallest and largest of the input values, respectively.

**Example: Limiting salary increases**

```python
increase = 5000
max_increase = 4000
adjusted_increase = min(increase, max_increase)  # adjusted_increase is 4000
```

**Example: Ensuring a minimum bonus**

```python
bonus = 2000
min_bonus = 2500
adjusted_bonus = max(bonus, min_bonus)  # adjusted_bonus is 2500
```

### Calculating Percentage Increases

**Example: Calculating the percentage increase in sales**

```python
previous_sales = 100000
current_sales = 125000
increase = current_sales - previous_sales
percentage_increase = (increase / previous_sales) * 100  # 25.0%
```

### Avoiding Division by Zero

Always ensure the denominator is not zero before dividing.

**Example: Safe division**

```python
if number_of_employees != 0:
    average_salary = total_salary / number_of_employees
else:
    average_salary = 0  # Handle the zero division case appropriately
```

### Casting Values During Calculations

When performing calculations that result in float values, you may need to cast them to integers.

**Example: Converting a float to an integer**

```python
value = 76.75
integer_value = int(value)  # 76
```

- **Note:** Casting to `int` truncates the decimal part.

### Sorting Data

To sort data such as a list of tuples or dictionaries based on a specific value, use the `sorted()` function with a `key` parameter.

**Example: Sorting a list of tuples**

```python
# List of tuples (keyword, total_ltv)
keyword_data = [('happy', 32), ('sad', 15), ('excited', 27)]

# Sort the list in descending order based on total_ltv
sorted_keyword_data = sorted(keyword_data, key=lambda x: x[1], reverse=True)
print(sorted_keyword_data)
```

- **Explanation:**
  - `key=lambda x: x[1]` tells the `sorted()` function to sort based on the second element in each tuple.
  - `reverse=True` sorts the list in descending order.

**Example: Sorting a list of dictionaries**

```python
# List of dictionaries
keyword_data = [
    {'keyword': 'happy', 'total_ltv': 32},
    {'keyword': 'sad', 'total_ltv': 15},
    {'keyword': 'excited', 'total_ltv': 27}
]

# Sort the list in descending order based on 'total_ltv'
sorted_keyword_data = sorted(keyword_data, key=lambda x: x['total_ltv'], reverse=True)
print(sorted_keyword_data)
```

- **Explanation:**
  - The `key` function extracts the 'total_ltv' value from each dictionary for sorting.

---

## 7. Formatting and Printing Output

### Using the Print Function

Display information using the `print()` function.

**Example: Printing a message**

```python
print('Welcome to OmniCo!')
```

### String Formatting

Format strings to include variables and control numeric precision.

**Example: Using f-strings**

```python
name = 'Alice'
salary = 75000

print(f'{name} has a salary of ${salary:.2f}')  # 'Alice has a salary of $75000.00'
```

- `:.2f` formats the number to two decimal places.

### Formatting Strings for Files

When writing formatted data to a file, you can use f-strings and special characters like `\n` (newline) and `\t` (tab).

**Example: Writing formatted text to a file**

```python
with open('employee_report.txt', 'w') as file:
    file.write('Employee Report\n')
    file.write('---------------\n')
    file.write('ID\tName\t\t\tDepartment\tSalary\n')
    for emp_id, data in employees.items():
        line = f"{emp_id}\t{data['name']}\t{data['department']}\t${data['salary']}\n"
        file.write(line)
```

### Aligning Text Output

You can use formatting options to align text and numbers.

**Example: Formatting with alignment**

```python
# Left-align text and format numbers with precision
line = f"{emp_id:<5}{data['name']:<20}{data['department']:<15}${data['salary']:>10.2f}\n"
```

- `<` : Left-align within the available space.
- `>` : Right-align within the available space.
- `.2f` : Format the number with two decimal places.

---

## 8. Error Handling

### Handling Exceptions

Use `try` and `except` blocks to handle potential errors.

**Example: Handling ValueError**

```python
value = 'abc'

try:
    number = int(value)
except ValueError:
    print('Cannot convert to integer.')
```

---

## 9. Best Practices

### Writing Readable Code

- Use meaningful variable names.
- Keep code organized and properly indented.
- Break down complex problems into smaller, manageable pieces.

### Commenting Your Code

- Add comments to explain non-obvious parts of your code.
- Keep comments concise and relevant.

**Example:**

```python
# Calculate the average salary
average_salary = total_salary / number_of_employees
```

#### Commenting Complex Logic

When implementing complex algorithms or logic, add comments to explain the steps.

**Example: Explaining a bonus calculation algorithm**

```python
# Loop through each employee to calculate bonus
for emp_id, details in employees.items():
    salary = details['salary']
    # Calculate bonus as 10% of salary
    bonus = salary * 0.10
    # Add the bonus to the employee's details
    details['bonus'] = bonus
```

### Following Style Guidelines

- Use consistent naming conventions (`snake_case` for variables and functions).
- Avoid overly long lines; keep them under 80 characters when possible.
- Separate code into logical sections with blank lines.

---

## 10. Additional Tips

### Testing Your Code

- Regularly test your code with different inputs to ensure it works correctly.

### Debugging

- Use print statements or a debugger to trace and fix issues.

### Asking for Help

- If you're stuck, don't hesitate to reach out to a peer or mentor.

### Handling Data Carefully

- Be cautious when manipulating data to avoid unintended consequences.
- Ensure that you understand the data structure before performing operations.

---

## 11. Conclusion

This guide covers the essential Python concepts you'll need for your data analysis projects. Refer back to these sections as you work through your code. Remember, practice and persistence are key to becoming proficient in programming.

Good luck with your projects, and happy coding!

---

_This guide is intended for internal use by OmniCo team members. Please handle the material responsibly and maintain confidentiality._
