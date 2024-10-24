<div style="display: flex; flex-direction: column; border: 1px solid #ddd; font-size: 16px; font-family: sans-serif; line-height: 1.2em; box-shadow: rgba(0, 0, 0, 0) 0px 0px 0px 0px, rgba(0, 0, 0, 0) 0px 0px 0px 0px, rgba(0, 0, 0, 0.1) 0px 1px 3px 0px, rgba(0, 0, 0, 0.06) 0px 1px 2px 0px;">
  <div style="border-bottom: 1px solid #ddd; width: 100%; padding: 10px 20px; color: #666;">From: Jordan Michaels (jordan.michaels@omni.co)</div>
  <div style="border-bottom: 1px solid #ddd; width: 100%; padding: 10px 20px; color: #666;">Subject: Urgent Analysis Needed on Social Media Engagement!</div>
  <div style="padding:20px 40px;">
    Hey Team,

    Hope everyone's feeling as energized as a freshly charged quantum battery! 🚀 We've got an exciting task that just landed on our plates, straight from the top brass at OmniVerse. Our visionary leader, Leo Ike, is eager to see some insightful data on user engagement with our latest social initiatives: **RealityPlus** and **EmotiSense**.

    We've been collecting a treasure trove of user posts, and it's time to dive deep and see how our beloved users are interacting with some key topics of interest. Now, keep this under wraps, but we're particularly curious about how certain *emotional* keywords are resonating with our audience. Words like *amazing*, *triggered*, *OmniCo*, and even *depressed*.

    Your mission, should you choose to accept it (and you really don't have a choice, do you? Haha!), is to analyze this data and help us understand which keywords are driving the most significant user lifetime value (LTV). Remember, the higher the LTV, the more our users are, let's say, "invested" in our platforms.

    All the data you need is in the `posts.csv` file, and the keywords are listed in `keywords.txt`. Please write your code in `main.py` and document any thoughts in `report.md`. Let's make Leo proud!

    Cheers to data and beyond,

    Jordan Michaels
    Senior Data Enthusiast Manager
    OmniCo

    <div style="font-size: 11px; color: #666">
      CONFIDENTIALITY NOTICE: This message contains proprietary information of OmniCo and is protected by the OmniCo Cybernetic Legal AI (CLAIR) system. Unauthorized use or disclosure is strictly prohibited and may result in immediate action, including significant penalties. By proceeding, you acknowledge and agree to these terms across all timelines. Remember, at OmniCo, we’re not just shaping the future—we own it.
    </div>

  </div>
</div>

---

# Project: Analyzing Social Media Engagement for OmniCo

Welcome to your first major project at OmniCo! You'll be stepping into the shoes of a data analyst to uncover insights from social media posts related to our groundbreaking initiatives, **RealityPlus** and **EmotiSense**. Your analysis will help us understand user interactions and guide future developments.

## Project Overview

You will:

1. Read and process social media posts from `posts.csv`.
2. Read and store keywords from `keywords.txt`.
3. Analyze the posts to count keyword occurrences.
4. Calculate the total user lifetime value (LTV) for each keyword.
5. Identify the top 10 keywords based on total LTV.
6. Write the results to `top_keywords.csv`.

**Bonus:** (Optional) Analyze engagement metrics to find keywords with the highest total likes, shares, and comments.

**Reflection:** Consider the ethical implications of this analysis and document your thoughts in `report.md`.

---

## Step-by-Step Guide

### 1. Setting Up Your Workspace

- **Open your project repository** in VSCode.
- Ensure you have the following files:
  - `main.py` (your Python script).
  - `posts.csv` (the data file with social media posts).
  - `keywords.txt` (a list of keywords to analyze).
  - `report.md` (for your reflection).

### 2. Reading the Keywords

**Goal:** Read the keywords from `keywords.txt` into a list.

**Instructions:**

- **Open `keywords.txt`** for reading.
  - Use the `open()` function with the appropriate mode.
  - _Refer to the OmniCodex section 'Reading Files'._
- **Read all lines** from the file.
  - Each line contains one keyword.
  - _See 'Reading Text Files into Lists' in the OmniCodex._
- **Strip whitespace** from each line.
  - This removes any leading/trailing spaces or newline characters.
  - Hint: Use the `strip()` method.
  - _Refer to 'Stripping Whitespace' in the OmniCodex._
- **Store the keywords** in a list called `keywords_list`.
  - This list will be used to check for keyword occurrences in the posts.

**Example Snippet:**

```python
# Open the file and read lines
with open('keywords.txt', 'r') as file:
    keywords_list = []
    for line in file:
        # TODO: Strip whitespace and add to keywords_list
```

### 3. Reading the Posts Data

**Goal:** Read the posts from `posts.csv` into a list of dictionaries.

**Instructions:**

- **Open `posts.csv`** for reading.
  - Use `with open()` as before.
  - _Refer to 'Reading Files' in the OmniCodex._
- **Read the header line** and store the column names.
  - Use `file.readline()` to read the first line.
  - _Look at 'Skipping Header Rows' in the OmniCodex._
- **Initialize an empty list** called `posts_list`.
- **Iterate over each remaining line** in the file.
  - _Refer to 'Reading and Processing CSV Files' in the OmniCodex._
  - For each line:
    - **Strip whitespace** using `strip()`.
      - _Refer to 'Stripping Whitespace' in the OmniCodex._
    - **Split the line** by commas to get the field values.
      - _Refer to 'Splitting Strings' in the OmniCodex._
    - **Create a dictionary** for each post.
      - Make sure your post dictionary has keys for at least for all of the post fields (see above).
    - **Convert numeric fields** to the appropriate data types.
      - For example, convert `user_ltv` to a float.
      - _Refer to 'Converting Strings to Numbers' in the OmniCodex._
    - **Add the dictionary** to `posts_list`.

### 4. Initializing Keyword Dictionaries

**Goal:** Prepare dictionaries to keep track of keyword counts and total LTVs.

**Instructions:**

- **Create an empty dictionary** called `keyword_counts`.
  - This will map each keyword to the number of times it appears.
- **Create another empty dictionary** called `keyword_ltv`.
  - This will map each keyword to the total LTV accumulated from posts containing that keyword.
- **Initialize both dictionaries** with the keywords from `keywords_list`.
  - Set initial counts and LTVs to zero.
  - _Refer to 'Using Dictionaries to Count and Sum Values' in the OmniCodex._

### 5. Analyzing the Posts

**Goal:** Count keyword occurrences and sum LTVs.

**Instructions:**

- **Iterate over each post** in `posts_list`.
  - Access the `content` and `user_ltv` fields from each post dictionary.
  - _Refer to 'Loops and Iteration' in the OmniCodex._
- **For each keyword** in `keywords_list`:
  - **Check if the keyword is in the content**.
    - You may want to **convert both the content and keyword to lowercase** to ensure case-insensitive matching.
      - Use `lower()` method.
      - _Refer to 'Converting Strings to Lowercase or Uppercase' in the OmniCodex._
  - **If the keyword is found**:
    - **Increment** the count in `keyword_counts` for that keyword by 1.
    - **Add** the post's `user_ltv` to the total in `keyword_ltv` for that keyword.
      - _Refer to 'Using Dictionaries to Count and Sum Values' in the OmniCodex._

### 6. Preparing the Results

**Goal:** Identify the top 10 keywords based on total LTV.

**Instructions:**

- **Create a list of tuples** where each tuple contains:
  - The keyword.
  - The total LTV (`keyword_ltv`).
- **Sort the list** in descending order based on the total LTV.
  - Use the `sorted()` function with a custom key.
  - _Refer to 'Sorting Data' in the OmniCodex._
- **Select the top 10 keywords** from the sorted list.

**Example Snippet:**

```python
# Create a list of tuples
keyword_ltv_list = []

for keyword in keywords_list:
    total_ltv = keyword_ltv[keyword]
    keyword_ltv_list.append((keyword, total_ltv))

# Sort the list by total LTV in descending order
sorted_keywords = sorted(keyword_ltv_list, key=lambda x: x[1], reverse=True)

# Get the top 10 keywords
top_keywords = sorted_keywords[:10]
```

### 7. Writing the Results to a File

**Goal:** Write the top keywords and their total LTVs to `top_keywords.csv`.

**Instructions:**

- **Open `top_keywords.csv`** for writing.
  - Use `with open()` and specify the write mode.
  - _Refer to 'Writing Files' and 'Writing CSV Files' in the OmniCodex._
- **Write a header row** with the column names: `keyword,total_ltv`.
- **Iterate over the `top_keywords` list**.
  - For each tuple:
    - **Write a line** to the file in CSV format.
    - Ensure that numeric values are converted to strings.
    - You may format the `total_ltv` to two decimal places using string formatting.
      - _Refer to 'String Formatting' in the OmniCodex._

**Example Snippet:**

```python
with open('top_keywords.csv', 'w') as file:
    # Write header
    file.write('keyword,total_ltv\n')

    # Write each keyword and total LTV
    for keyword, total_ltv in top_keywords:
        # TODO: create a string for the line that includes the keyword and total_ltv separated by a comma
        # line = ?
        file.write(line)
```

### 8. Displaying the Results

**Goal:** Print the top 10 keywords and their total LTVs to the console.

**Instructions:**

- **Iterate over the `top_keywords` list**.
  - Use a loop to print each keyword and its total LTV.
- **Format the output** for readability.
  - For example, align the text and numbers.
  - _Refer to 'Formatting and Printing Output' in the OmniCodex._

**Example Snippet:**

```python
print("Top 10 Keywords by Total LTV:")
print("-----------------------------")
for keyword, total_ltv in top_keywords:
    print(f"{keyword:<20} ${total_ltv:.2f}")
```

---

## Bonus Section (Optional)

**Goal:** Identify keywords with the highest total engagement (likes + shares + comments).

**Instructions:**

- **Initialize a dictionary** called `keyword_engagement` with keywords as keys and zero as initial values.
  - _Refer to 'Using Dictionaries to Count and Sum Values' in the OmniCodex._
- **In your analysis loop**, when a keyword is found in a post:
  - **Sum the engagement metrics** (`likes`, `shares`, `comments`).
  - **Add the engagement** to the total in `keyword_engagement` for that keyword.
- **Create a list of tuples** containing keywords and their total engagement.
- **Sort and select the top keywords** based on total engagement.
  - _Refer to 'Sorting Data' in the OmniCodex._
- **Write the results** to a file named `top_engagement.csv` with columns `keyword,total_engagement`.
  - _Refer to 'Writing CSV Files' in the OmniCodex._

---

## Reflection

In `report.md`, write a brief reflection (approximately 300 words) on the following:

- **Ethical Implications:**
  - Consider how analyzing and leveraging emotionally charged keywords might affect users.
  - Reflect on the responsibility of companies when using data to influence user behavior.
- **Real-World Applications:**
  - Discuss how such analysis is used in the industry.
  - Think about the balance between business goals and user well-being.

---

## Finalizing Your Project

- **Test your code** thoroughly to ensure it runs without errors and produces the expected results.
- **Ensure all files** (`main.py`, `top_keywords.csv`, any bonus files, `report.md`) are saved and up to date.
- **Commit your changes** in VSCode:
  - Stage all changed files.
  - Write a meaningful commit message, e.g., "Completed social media engagement analysis."
- **Push your commits** to your GitHub repository:
  - Use the Git integration in VSCode or the command line.
- **Verify** that your files are correctly uploaded by checking your repository on GitHub.

---

# Congratulations!

You've completed a comprehensive data analysis project, applying key programming concepts and critical thinking about the impact of technology on society. Great job!

---

_Remember, at OmniCo, every line of code you write is a step toward reshaping reality. Keep questioning, keep coding, and keep pushing the boundaries!_
