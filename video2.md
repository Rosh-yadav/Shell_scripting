

👉 **Problem → Thinking → Actual Script → Explanation**

---

# 🧠 HOW TO THINK (Most Important)

Before writing script, always think:

1. What is the problem?
2. Which Linux command solves it?
3. Add condition / loop
4. Automate

---

# 📘 SCENARIO 1: Deploy app to multiple servers

## ❓ Problem:

Copy file + restart service on many servers

---

## 🧠 Thinking:

* Copy file → `scp`
* Run command remotely → `ssh`
* Multiple servers → loop

---

## 💻 Script:

```bash
servers=("server1" "server2")

for s in "${servers[@]}"
do
  scp app.html $s:/var/www/html/
  ssh $s "systemctl restart apache2"
done
```

---

## 🧠 Explanation:

* Loop → goes to each server
* `scp` → copies file
* `ssh` → runs command remotely

---

# 📘 SCENARIO 2: Disk usage alert

## ❓ Problem:

Alert if disk > 80%

---

## 🧠 Thinking:

* Get disk → `df -h`
* Extract % → `awk`
* Compare → `if`

---

## 💻 Script:

```bash
threshold=80

usage=$(df / | awk 'NR==2 {print $5}' | sed 's/%//')

if [ $usage -gt $threshold ]; then
  echo "Disk is full: $usage%"
else
  echo "Disk is OK"
fi
```

---

## 🧠 Explanation:

* `df` → disk info
* `awk` → pick % column
* `sed` → remove `%`
* `if` → compare

---

# 📘 SCENARIO 3: Service check

## ❓ Problem:

Start service if stopped

---

## 🧠 Thinking:

* Check service → `systemctl is-active`
* If not active → start

---

## 💻 Script:

```bash
service="apache2"

status=$(systemctl is-active $service)

if [ "$status" != "active" ]; then
  echo "Service not running, starting..."
  systemctl start $service
else
  echo "Service already running"
fi
```

---

## 🧠 Explanation:

* Store status in variable
* Compare
* Take action

---

# 📘 SCENARIO 4: Delete old files

## ❓ Problem:

Delete files older than 10 days

---

## 🧠 Thinking:

* Find files → `find`
* Condition → `-mtime +10`
* Action → delete

---

## 💻 Script:

```bash
find /tmp -type f -mtime +10 -delete
```

---

## 🧠 Explanation:

* `/tmp` → folder
* `-mtime +10` → older than 10 days
* `-delete` → remove

---

# 📘 SCENARIO 5: CPU usage alert

## ❓ Problem:

Check CPU usage

---

## 🧠 Thinking:

* Get CPU → `top`
* Filter → `grep + awk`
* Compare

---

## 💻 Script:

```bash
threshold=80

cpu=$(top -bn1 | grep "Cpu(s)" | awk '{print 100 - $8}')

cpu_int=${cpu%.*}

if [ $cpu_int -gt $threshold ]; then
  echo "High CPU usage: $cpu%"
else
  echo "CPU is normal"
fi
```

---

## 🧠 Explanation:

* `top` → CPU data
* `$8` → idle → subtract from 100
* Compare

---

# 📘 SCENARIO 6: Website health check

## ❓ Problem:

Check if website is working

---

## 🧠 Thinking:

* Send request → `curl`
* Get status → 200 = OK

---

## 💻 Script:

```bash
status=$(curl -s -o /dev/null -w "%{http_code}" https://google.com)

if [ $status -eq 200 ]; then
  echo "Website is UP"
else
  echo "Website DOWN"
fi
```

---

## 🧠 Explanation:

* `curl` → send request
* `200` → success

---

# 🔥 BEST WAY TO LEARN (Follow This)

For each scenario:

👉 Step 1: Identify command
👉 Step 2: Test command manually
👉 Step 3: Put in script
👉 Step 4: Add condition/loop

---

# 🎯 If Interviewer Asks

👉 “How will you monitor CPU?”

✔ Answer:

> I will use the `top` command to fetch CPU usage, parse the output using `awk`, and compare it with a threshold using an if condition in a shell script.

---

