
## 1. **Build and Query a Database**

### **Tools You Can Use:**
- **Python's built-in `sqlite3` module** — for lightweight database creation  
- **Pandas** — to load CSVs and interact with tabular data  
- **Jupyter Notebook** — for exploratory and interactive work  
- **VSCode** — for script development and file management  

---

### **Example Workflow**

#### Step 1: **Create or Connect to a SQLite Database**
```python
import sqlite3

# Connect to (or create) a database
conn = sqlite3.connect("my_database.db")
cursor = conn.cursor()
```

#### Step 2: **Create a Table**
```python
cursor.execute("""
CREATE TABLE IF NOT EXISTS students (
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER,
    grade TEXT
)
""")
conn.commit()
```

#### Step 3: **Insert Records**
```python
cursor.execute("INSERT INTO students (name, age, grade) VALUES (?, ?, ?)",
               ("John Doe", 20, "A"))
conn.commit()
```

#### Step 4: **Query the Database**
```python
cursor.execute("SELECT * FROM students")
rows = cursor.fetchall()

for row in rows:
    print(row)
```

---

## 2. **Update and Delete Records Safely**

To prevent **SQL injection** and ensure safety, always use **parameterized queries**.

**Update Example**:
```python
cursor.execute("UPDATE students SET grade = ? WHERE id = ?", ("B", 1))
conn.commit()
```

**Delete Example**:
```python
cursor.execute("DELETE FROM students WHERE id = ?", (1,))
conn.commit()
```

---

## 3. **Load Database Data into Pandas**

### Load SQL query results into a DataFrame:
```python
import pandas as pd

df = pd.read_sql_query("SELECT * FROM students", conn)
print(df)
```

### Load CSV into a DataFrame and insert into a database:
```python
df = pd.read_csv("students.csv")
df.to_sql("students", conn, if_exists="append", index=False)
```

---

## Scenario: Loading Names & Surnames from CSV into a Database

For example, you have a CSV file containing **names and surnames**, and you want to load that data into a database table with columns for `first_name`, `last_name`, and optionally `age`.

**CSV (`people.csv`):**
```
first_name,last_name
John,Doe
Jane,Smith
Bob,Brown
```

---

## Python Script
```python
import sqlite3
import pandas as pd

# Step 1: Connect (or create) SQLite database
conn = sqlite3.connect("my_database.db")
cursor = conn.cursor()

# Step 2: Create the 'persons' table
cursor.execute("""
CREATE TABLE IF NOT EXISTS persons (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    age INTEGER
)
""")
conn.commit()

# Step 3: Load CSV data
df = pd.read_csv("people.csv")  # CSV has 'first_name' and 'last_name' columns

# Step 4: Add an 'age' column
df['age'] = 30  # Example: set all ages to 30

# Step 5: Insert data into the database
df.to_sql("persons", conn, if_exists="append", index=False)

# Step 6: Verify insertion
result = pd.read_sql_query("SELECT * FROM persons", conn)
print(result)

# Step 7: Close connection
conn.close()
```
