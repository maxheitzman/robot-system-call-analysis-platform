# 🎓 Beginner's Guide to Stage 2: Complete Walkthrough

## 📖 What Are We Actually Doing?

You're building a **System Call Analysis Platform** for a robot. Think of it like creating a diagnostic tool that monitors what a robot is doing "under the hood."

### 🤖 The Simple Version

**What you have:** 
- Data from a real military robot (UMD Husky) that shows everything the robot's computer did
- Over 1.2 MILLION recordings of the robot's computer operations
- Data collected during different activities (driving autonomously, being manually controlled, running tests)

**What you're building:** 
- A software system that analyzes this robot data
- A dashboard that shows what's happening in the robot
- Tools to detect if something is going wrong

**Why it matters:**
- Helps keep robots running smoothly
- Detects cyber attacks or malfunctions
- Improves robot performance

---

## 🎯 Stage 2: What You Need to Deliver

### Think of it like building a house:
1. **Blueprints (UML Diagrams)** - Show how your software is structured
2. **Sketch (Low-Fidelity Prototype)** - Rough drawings of what users will see
3. **Construction Plan (Implementation Plan)** - How you'll actually build it

### Due Date: **Thursday, October 23, 2025 at 11:59 PM**

---

## 📊 Understanding Your Data

### What is a System Call?

Imagine your robot is like a restaurant:
- **The Kitchen (Operating System)** does the real work
- **The Waiter (System Calls)** takes orders from customers to the kitchen
- Every time the robot wants to do something, it makes a "system call"

**Examples:**
- `clock_gettime` = "What time is it?" (46% of all calls!)
- `read` = "Give me data from a sensor"
- `write` = "Save this data to a file"
- `futex` = "Wait, I need to coordinate with another process" (22% of calls!)

### Your Robot's Brain

The robot has different "workers" (software components):
1. **global_planner** (56% of activity) - Figures out where to go
2. **front_ouster** (26% of activity) - Processes LiDAR (laser) sensor data
3. **os_cloud_node** (11% of activity) - Turns sensor data into 3D maps
4. **local_planning** (1.4% of activity) - Avoids obstacles

---

## 🎨 Part 1: UML Diagrams (The Blueprints)

### What is UML?
**UML = Unified Modeling Language** - It's like architectural blueprints, but for software!

### You Need 3 Types of Diagrams:

#### 1️⃣ **Class Diagram** - "What are the main parts?"

Think of it like an organizational chart showing:
- **Classes** = The main components (boxes)
- **Relationships** = How they connect (arrows)
- **Attributes** = What data they store
- **Methods** = What actions they can do

**Example for your project:**
```
┌─────────────────────┐
│  DataCollector      │
├─────────────────────┤
│ - robotIP: String   │
│ - sensorList: []    │
├─────────────────────┤
│ + collectData()     │
│ + processData()     │
└─────────────────────┘
         ↓
┌─────────────────────┐
│  SystemCallParser   │
├─────────────────────┤
│ - csvFile: File     │
│ - dataFrame: []     │
├─────────────────────┤
│ + parseCSV()        │
│ + filterCalls()     │
└─────────────────────┘
```

#### 2️⃣ **Use Case Diagram** - "Who uses it and what can they do?"

Shows:
- **Actors** = People or systems using your software (stick figures)
- **Use Cases** = Things they can do (ovals)
- **Relationships** = How they connect (lines)

**Example:**
```
     👤
Administrator
      |
      |---- (Monitor Robot)
      |---- (View System Calls)
      |---- (Generate Report)
      |---- (Detect Anomalies)
```

#### 3️⃣ **Sequence Diagram** - "What happens step-by-step?"

Shows the order of operations, like a timeline:

**Example: User views robot data**
```
User → Dashboard: Click "View Data"
Dashboard → Database: Request system calls
Database → Dashboard: Return data
Dashboard → Chart: Create visualization
Chart → User: Display graph
```

---

## 🖼️ Part 2: Low-Fidelity Prototype (The Sketch)

### What is Low-Fidelity?

**Low-fidelity** = Rough sketch, not pretty!

Think: **Napkin drawings**, not Photoshop designs!

You can:
- Draw on paper and take a photo
- Use Google Drawings
- Use Figma (free)
- Use PowerPoint shapes

### What to Include:

**Main Dashboard Screen:**
```
┌─────────────────────────────────────────────┐
│  🤖 Robot System Call Monitor        [User] │
├─────────────────────────────────────────────┤
│                                              │
│  ┌──────────────┐  ┌──────────────┐        │
│  │ Total Calls  │  │ Active Nodes │        │
│  │  1,234,567   │  │     10       │        │
│  └──────────────┘  └──────────────┘        │
│                                              │
│  📊 System Call Distribution                │
│  ┌────────────────────────────────────┐    │
│  │                                    │    │
│  │  ████ clock_gettime (46%)          │    │
│  │  ██ futex (22%)                    │    │
│  │  █ write (8%)                      │    │
│  │                                    │    │
│  └────────────────────────────────────┘    │
│                                              │
│  🔍 Recent Activity                         │
│  ┌────────────────────────────────────┐    │
│  │ 10:23:45 - global_planner           │    │
│  │ 10:23:46 - front_ouster              │    │
│  │ 10:23:47 - os_cloud_node             │    │
│  └────────────────────────────────────┘    │
│                                              │
│  [View Details] [Export Data] [Settings]   │
└─────────────────────────────────────────────┘
```

---

## 📝 Part 3: Implementation Plan (The Construction Plan)

### This is your "How We'll Build It" document

**What to include:**

### 1. **Testbed** (What hardware/setup you need)
- Laptop/desktop with Linux or macOS
- Access to DoD SAFE dataset (you already have it!)
- Internet connection for cloud deployment

### 2. **Programming Languages**
- **Python** - For data analysis and backend
  - Why? Great for data analysis, machine learning
  - Libraries: pandas (data), Flask (web server), matplotlib (charts)
- **JavaScript** - For the web dashboard
  - Why? Makes interactive websites
  - Libraries: React (user interface), Chart.js (graphs)

### 3. **Development Tools**
- **VS Code** - Code editor (you're using it!)
- **Git** - Version control
- **Docker** - Containerization (packages everything together)
- **PostgreSQL** - Database to store data
- **Jupyter Notebook** - For data exploration

### 4. **Timeline** (Example - adjust based on your team)
```
Week 1-2:  Set up development environment
Week 3-4:  Build data processing backend
Week 5-6:  Create database and API
Week 7-8:  Build web dashboard frontend
Week 9-10: Testing and refinement
Week 11:   Deployment and documentation
Week 12:   Final presentation prep
```

---

## 🎤 Part 4: Presentation (10-15 Minutes)

### Structure:

**Slide 1: Title**
- Project name
- Team members
- Date

**Slide 2-3: Problem Statement**
- What problem are you solving?
- Why does it matter?

**Slide 4-6: System Design**
- Show your UML diagrams
- Explain the main components

**Slide 7-8: User Interface**
- Show your prototype mockups
- Walk through a user scenario

**Slide 9-10: Implementation Plan**
- Technologies you'll use
- Timeline and milestones

**Slide 11: Team Roles**
- Who's doing what?

**Slide 12: Questions**
- Q&A slide

---

## 💡 Key Concepts Explained

### System Call Pattern Recognition

**The Simple Version:**
Your robot makes millions of "calls" to its operating system. By analyzing these patterns, you can:
1. **Detect problems** - Unusual patterns might mean something's wrong
2. **Optimize performance** - See what's slow and fix it
3. **Detect attacks** - Hackers create unusual patterns
4. **Monitor health** - Is the robot working normally?

### Real-World Analogy

Think of it like your phone:
- Apps make system calls constantly
- Battery monitor tracks these calls
- If an app makes too many calls → drains battery
- If an app makes weird calls → might be malware

Your project does the same thing, but for a military robot!

---

## 🛠️ Tools We'll Use to Create Your Deliverables

### For UML Diagrams:
- **Draw.io** (free, online) - Easiest!
- **Lucidchart** (free for students)
- **PlantUML** (code-based, we can generate)

### For Prototype:
- Paper and pencil (seriously!)
- PowerPoint shapes
- Figma (free)
- Google Drawings

### For Report:
- Microsoft Word
- Google Docs
- LaTeX (if you're fancy)

---

## 📋 Checklist for Stage 2

### Before October 23rd, you need:

- [ ] **Class Diagram** showing main components
- [ ] **Use Case Diagram** showing user interactions
- [ ] **Sequence Diagrams** (2-3) showing key processes
- [ ] **Low-Fidelity Prototype** screens (3-5 main screens)
- [ ] **Implementation Plan** (1-2 pages)
- [ ] **Project Report** combining all above
- [ ] **Presentation Slides** (10-15 slides)

---

## 🤝 Your Team Members

Based on your Stage 1 info:
- **John Heitzman (You!)** - Project Manager
- **Noah Küng** - Lead Developer
- **Joseph Musangu** - Data Analyst
- **Omotoyosi Adams** - UI/UX Designer
- **Delphin Iradukunda** - Documentation Specialist

### Suggested Task Division for Stage 2:
- **John (PM)** - Coordinate everything, implementation plan
- **Noah (Dev)** - Class diagram, technical architecture
- **Joseph (Data)** - Data flow sequence diagrams
- **Omotoyosi (UI/UX)** - Low-fidelity prototype, user flows
- **Delphin (Docs)** - Use case diagram, report writing

---

## 🎯 What I'll Help You Build Now

I'm going to create ALL of these for you:

1. ✅ Detailed UML Class Diagram (with code)
2. ✅ Complete Use Case Diagram (with descriptions)
3. ✅ Multiple Sequence Diagrams
4. ✅ Low-Fidelity Prototype designs
5. ✅ Full Implementation Plan
6. ✅ Presentation outline
7. ✅ Complete project report

Let's get started! 🚀

---

## ❓ Common Questions

**Q: Do I need to build the actual software now?**
A: NO! Stage 2 is just the DESIGN phase. You're planning, not coding yet.

**Q: How technical should the UML diagrams be?**
A: Detailed enough to show you've thought it through, but not every tiny detail.

**Q: Can I use the LSTM model that's already in the data?**
A: YES! You're building a platform that uses and improves on that existing work.

**Q: What if I don't understand something?**
A: That's okay! Focus on the big picture. You're monitoring robot system calls to detect problems.

---

Ready? Let's build your Stage 2 deliverables! 🎉

