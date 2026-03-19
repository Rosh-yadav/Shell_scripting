

👉 **How to check what’s happening inside your system (CPU, memory, processes)**

---

# ⚡ 1. Run the command

```bash
top
```

👉 Opens a **live dashboard** of your system
👉 Press `q` to quit

---

# 📊 2. First line (System overview)

Example:

```bash
top - 19:38:28 up 2 days, load average: 0.52, 0.58, 0.59
```

👉 Meaning:

* Time
* Uptime (how long system is running)
* Load average

### 🎯 Important:

👉 **Load average = system workload**

* 1 core → load 1 = full usage
* More cores → higher load is OK

---

# 🔄 3. Second line (Processes)

```bash
Tasks: 6 total, 1 running, 5 sleeping
```

👉 Meaning:

* total → all processes
* running → using CPU
* sleeping → waiting
* zombie → broken process (ignore for now)

---

# ⚙️ 4. Third line (CPU usage)

```bash
%Cpu(s): us, sy, id, wa ...
```

👉 Focus only on this for now:

* `us` → user processes
* `sy` → system processes
* `id` → idle (free CPU)
* `wa` → waiting (slow disk/network)

💡 Simple rule:

* High `id` → system is free ✅
* Low `id` → system busy ⚠️

---

# 🧠 5. Memory (RAM)

```bash
MiB Mem: total, free, used
```

👉 Shows RAM usage

* free → unused
* used → used
* available → usable

---

# 📋 6. Process list (MOST USEFUL)

Columns:

* `PID` → process ID
* `USER` → who started it
* `%CPU` → CPU usage
* `%MEM` → memory usage
* `COMMAND` → program name

👉 This is where you:

* find heavy processes
* debug system issues

---

# 🔥 What you should REALLY understand

👉 `top` helps you answer:

* Is CPU busy?
* Is memory full?
* Which process is causing problem?

---

# 🧠 What this lesson is trying to teach

👉 **You don’t always need to press keys inside `top` — you can start it with settings already applied**

---

# ⚙️ Instead of doing this inside `top`:

* Press `M` → sort by memory
* Press `c` → show full path
* Press `u` → filter user

👉 You can do it directly while starting `top`

---

# 🚀 Examples

### 1. Sort by memory

```bash
top -o %MEM
```

👉 Same as pressing `M` inside `top`
👉 Shows highest memory usage first

---

### 2. Show full command path

```bash
top -c
```

👉 Shows:

```
/usr/bin/python script.py
```

instead of just:

```
python
```

---

### 3. Show processes of a user

```bash
top -u root
```

👉 Shows only processes owned by `root`

# 🧠 Simple memory trick

👉

* `-o` → order
* `-c` → command path
* `-u` → user

---

