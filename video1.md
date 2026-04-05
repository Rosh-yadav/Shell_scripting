
# 📘 Shell Scripting Interview Notes (Q&A Format)

---

## 1. How do you declare a variable in a shell script?

### ✅ Answer:

A variable is declared using `name=value` (no spaces).

### 💻 Example:

```bash
name="roshni"
echo $name
```

### 🧪 Practice:

* Create variable `city=Delhi`
* Print it

---

## 2. How do you make a shell script executable?

### ✅ Answer:

Use `chmod +x` to add execute permission.

### 💻 Example:

```bash
chmod +x script.sh
./script.sh
```

### 🧪 Practice:

* Create `test.sh`
* Make it executable and run it

---

## 3. How do you pass arguments to a shell script?

### ✅ Answer:

Use `$1`, `$2`, `$3` for arguments.

### 💻 Example:

```bash
echo "First: $1"
echo "Second: $2"
```

Run:

```bash
./script.sh hello world
```

### 🧪 Practice:

* Pass your name and role as arguments
* Print both

---

## 4. How do you check if a file exists?

### ✅ Answer:

Use `if` with `-e`.

### 💻 Example:

```bash
if [ -e file.txt ]; then
  echo "File exists"
else
  echo "File not found"
fi
```

### 🧪 Practice:

* Check for a file `demo.txt`

---

## 5. How do you write a loop in shell script?

### ✅ Answer:

Use `for` loop.

### 💻 Example:

```bash
for i in 1 2 3
do
  echo $i
done
```

### 🧪 Practice:

* Print numbers from 1 to 10

---

## 6. How do you redirect output and error to a file?

### ✅ Answer:

Use `&>` to redirect both stdout and stderr.

### 💻 Example:

```bash
ls wrongfile &> output.txt
```

### 🧪 Practice:

* Run a wrong command and store output in `log.txt`

---

## 7. How do you schedule a script using cron?

### ✅ Answer:

Use `crontab -e` and define schedule.

### 💻 Example:

```bash
0 0 * * * /home/user/script.sh
```

👉 Runs daily at midnight

### 🧪 Practice:

* Schedule a script to run every minute

---

## 8. How do you find and replace text in a file?

### ✅ Answer:

Use `sed` command.

### 💻 Example:

```bash
sed -i 's/old/new/g' file.txt
```

### 🧪 Practice:

* Replace "hello" with "hi" in a file

---

## 9. How do you read user input?

### ✅ Answer:

Use `read` command.

### 💻 Example:

```bash
echo "Enter name:"
read name
echo "Hello $name"
```

### 🧪 Practice:

* Ask user for age and print it

---

## 10. How do you check exit status of a command?

### ✅ Answer:

Use `$?`

### 💻 Example:

```bash
ls file.txt
echo $?
```

### 🧪 Practice:

* Run valid & invalid command
* Print success/failure

---

## 11. How do you create a function?

### ✅ Answer:

Use function syntax.

### 💻 Example:

```bash
myfunc() {
  echo "Hello from function"
}

myfunc
```

### 🧪 Practice:

* Create function to print your name

---

## 12. How do you append text to a file?

### ✅ Answer:

Use `>>` operator.

### 💻 Example:

```bash
echo "New line" >> file.txt
```

### 🧪 Practice:

* Add multiple lines to a file

---

## 13. How do you get current date and time?

### ✅ Answer:

Use `date` command.

### 💻 Example:

```bash
date
```

Store:

```bash
now=$(date)
echo $now
```

### 🧪 Practice:

* Print only date (not time)

---

## 14. How do you handle errors in shell script?

### ✅ Answer:

Use `set -e` and `trap`.

### 💻 Example:

```bash
set -e
trap 'echo "Error at line $LINENO"' ERR
```

### 🧪 Practice:

* Add error handling to a script

--

---

# 🧠 1. Arguments (`$1`, `$2`) — Simple Understanding

### 👉 Think like this:

When you run a script:

```bash
./script.sh hello world
```

* `hello` → goes into `$1`
* `world` → goes into `$2`

### 💻 Script:

```bash
echo "First: $1"
echo "Second: $2"
```

### 🧠 Memory Trick:

👉 `$1 = first input`, `$2 = second input`

---

# 🧠 2. IF-ELSE Syntax (Your confusion about `[ ]`)

### ✅ Correct Syntax:

```bash
if [ condition ]; then
  echo "Yes"
else
  echo "No"
fi
```

### ❗ Important Rules:

* Space after `[` and before `]` → **VERY IMPORTANT**
* `-e` → checks if file exists

### 💻 Example:

```bash
if [ -e file.txt ]; then
  echo "File exists"
else
  echo "File not found"
fi
```

### 🧠 Memory Trick:

👉 `if [ condition ] → then → else → fi`

---

# 🧠 3. `echo` (Printing)

Yes, you are right ✅
👉 `echo` = print statement in shell

```bash
echo "Hello"
```

---

---

# 🧠 5. IMPORTANT DOUBT: `&>` (Where file gets created?)

This is where you were confused — let’s fix it clearly 👇

---

## 🔥 Case 1: No path given

```bash
ls wrongfile &> output.txt
```

👉 File `output.txt` will be created in **current directory**

### Example:

If you are in:

```bash
/home/roshni
```

Then file will be:

```bash
/home/roshni/output.txt
```

---

## 🔥 Case 2: With full path

```bash
ls wrongfile &> /home/roshni/logs/output.txt
```

👉 File will be created in:

```
/home/roshni/logs/
```

---

## ⚠️ Important Rule:

👉 Folder must exist
👉 Otherwise error will come

---

## 🧠 Memory Trick:

👉 No path → current folder
👉 With path → specified folder

---

# 🧠 6. `read` (User Input)

You said:

> read is for user input and give input to user

✔ Slight correction:

👉 `read` = **take input FROM user (not give)**

### 💻 Example:

```bash
echo "Enter name:"
read name
echo "Hello $name"
```

---

# 🧠 7. `$?` (Very Important Interview Question)

Your answer is already correct 👍
Let me make it crystal clear:

---

## 💻 Example:

```bash
ls file.txt
echo $?
```

### Output cases:

* `0` → command success ✅
* `1` or other → failed ❌

---

## 🧠 Real Example:

```bash
ls abc.txt   # file not present
echo $?
```

Output:

```
2
```

👉 means FAILED

---

## 💻 Use in IF:

```bash
ls file.txt

if [ $? -eq 0 ]; then
  echo "Success"
else
  echo "Failed"
fi
```

---

## 🧠 Memory Trick:

👉 `$? = result of last command`

---

# 🎯 FINAL SIMPLE SUMMARY (Interview Ready)

👉 Arguments → `$1 $2` (input from command line)
👉 if → `[ condition ]` (spaces important)
👉 echo → print
👉 for → loop over values
👉 `&>` → store output + error in file
👉 read → take input from user
👉 `$?` → check success or failure

---


