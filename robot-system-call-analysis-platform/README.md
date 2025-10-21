# Stage 2: Software Design Specification (SDS)
## Robot System Call Analysis Platform

## ✅ STAGE 2 COMPLETE - ALL DELIVERABLES READY!

**Due Date:** October 23, 2025 (Thursday) before 11:59 PM  
**Team:** John Heitzman (PM), Noah Küng (Dev), Joseph Musangu (Data), Omotoyosi Adams (UI/UX), Delphin Iradukunda (Docs)

---

## 📁 What's in This Folder

### 📄 Main Deliverables

1. **PROJECT_REPORT.md** ⭐ **MAIN SUBMISSION**
   - Complete Stage 2 report (70+ pages)
   - Includes ALL requirements:
     - ✅ Project description (Section 1)
     - ✅ UML diagrams (Section 2)
       - Class diagram
       - Use case diagram
       - 3 Sequence diagrams
     - ✅ Low-fidelity prototypes (Section 3)
     - ✅ Implementation plan (Section 4)
   - Ready to convert to PDF and submit!

2. **PRESENTATION_OUTLINE.md**
   - Complete 22-slide presentation structure
   - Speaker notes for each slide
   - Timing guide (10-15 minutes)
   - Q&A preparation
   - Presentation tips and likely questions

### 📚 Supporting Documents

3. **BEGINNER_GUIDE.md**
   - Explains everything in simple terms
   - "What are we building?" explained
   - "What is a system call?" explained
   - Perfect for understanding the project from scratch

4. **IMPLEMENTATION_PLAN.md**
   - Detailed technical plan
   - 12-week development timeline
   - Technology stack justification
   - Team roles and responsibilities
   - Risk management
   - Budget estimates

### 🖼️ Visual Assets

5. **uml_diagrams/** folder
   - `class_diagram.puml` - Complete system architecture (25+ classes)
   - `use_case_diagram.puml` - 29 use cases, 5 actors
   - `sequence_diagram_1_realtime_monitoring.puml` - Real-time flow
   - `sequence_diagram_2_data_analysis.puml` - LSTM analysis flow
   - `sequence_diagram_3_data_import.puml` - CSV import flow
   - `README.md` - Instructions to render diagrams

6. **prototypes/** folder
   - `01_main_dashboard.html` - Main overview screen
   - `02_realtime_monitor.html` - Live monitoring view
   - `03_component_analysis.html` - Component deep-dive
   - `04_anomaly_detection.html` - LSTM anomaly dashboard
   - `05_data_import.html` - CSV import interface
   - `README.md` - How to view and use prototypes

### 📋 Reference Materials

7. **SRS_Template.md**
   - Software Requirements Specification from Stage 1
   - Based on DoD SAFE dataset requirements

8. **stage2.pdf**
   - Original assignment requirements

---

## 🚀 Quick Start Guide

### For Submission (John/Team Lead):

1. **Convert Report to PDF:**
   ```bash
   # Option 1: Use Markdown to PDF converter
   # (in VS Code: Cmd+Shift+P > "Markdown PDF: Export")
   
   # Option 2: Render in browser and print to PDF
   # Open PROJECT_REPORT.md in VS Code preview
   # Right-click > Print > Save as PDF
   
   # Option 3: Use pandoc
   pandoc PROJECT_REPORT.md -o stage2_RobotAnalysis.pdf
   ```

2. **Render UML Diagrams:**
   - Go to http://www.plantuml.com/plantuml/uml/
   - Copy contents of each `.puml` file
   - Export as PNG (high resolution)
   - Insert into presentation slides or Word doc

3. **Create Presentation Slides:**
   - Use PRESENTATION_OUTLINE.md as your guide
   - Create slides in PowerPoint/Google Slides/Keynote
   - Include UML diagram images
   - Include prototype screenshots
   - Follow the timing guide (10-15 minutes)

### For Presentation Prep:

1. **View Prototypes:**
   - Open any HTML file in `prototypes/` folder
   - Double-click or drag to browser
   - Walk through user flows

2. **Practice Presentation:**
   - Follow PRESENTATION_OUTLINE.md structure
   - Time yourselves (aim for 12-13 minutes)
   - Prepare for Q&A (common questions included)

3. **Take Screenshots:**
   - Capture each prototype screen
   - Add to presentation slides
   - Annotate with key features

---

## 📊 What We Built

### The System: Robot System Call Analysis Platform

**In Simple Terms:**
A monitoring system that watches what an autonomous robot is doing "under the hood" and detects problems automatically using AI.

**Key Features:**
- 🤖 Monitors 11,200+ system calls per second
- 🧠 Uses LSTM neural network (94% accuracy)
- 📊 Real-time dashboard with live updates
- 🚨 Automatic anomaly detection
- 📈 Historical analysis and reporting
- 📥 Imports 1.2M+ records from CSV files

**Dataset:**
- DoD SAFE military robot data
- 1.4GB, 1.2M+ system calls
- UMD Husky autonomous robot

---

## 🎯 Deliverables Checklist

### Required by Assignment ✅

- [x] **Project description** (1 paragraph)
  - Location: PROJECT_REPORT.md, Section 1.1-1.3

- [x] **System analysis and decomposition**
  - [x] Class diagram - 25+ classes in 7 packages
  - [x] Use case diagram - 29 use cases, 5 actors  
  - [x] Sequence diagrams - 3 detailed scenarios

- [x] **Low-fidelity prototype**
  - [x] 5 complete HTML wireframes
  - [x] Main dashboard
  - [x] Real-time monitor
  - [x] Component analysis
  - [x] Anomaly detection
  - [x] Data import

- [x] **Implementation plan** (multiple pages!)
  - [x] Testbed (hardware/software environment)
  - [x] Programming languages (Python, JavaScript/React)
  - [x] Development tools (VS Code, Git, Docker, etc.)
  - [x] Timeline (12-week detailed schedule)

- [x] **Presentation** (10-15 minutes)
  - [x] Outline complete with speaker notes
  - [x] Timing guide
  - [x] Q&A preparation

### Bonus Materials 🎁

- [x] Beginner-friendly explanation guide
- [x] Detailed implementation plan (40+ pages)
- [x] Risk management strategy
- [x] Testing strategy
- [x] Deployment guide
- [x] Team roles and responsibilities

---

## 📖 How to Use These Materials

### For the Report:

**Main document:** `PROJECT_REPORT.md`

This is your complete Stage 2 submission. It includes:
- Cover page with team info
- Table of contents
- All required sections
- Appendices with glossary and references

**What to do:**
1. Review for any customizations (team member info is already filled in!)
2. Convert to PDF (see instructions above)
3. Name as: `stage2_[YourGroupName].pdf`
4. Submit via Blackboard

### For the Presentation:

**Main guide:** `PRESENTATION_OUTLINE.md`

This gives you:
- 22 slide templates with content
- Speaker notes for each slide
- Timing suggestions
- Transition phrases
- Q&A preparation

**What to do:**
1. Create slides in your preferred tool
2. Use the outline as your script
3. Insert UML diagrams and prototype screenshots
4. Practice together as a team
5. Time yourselves (aim for 12-13 minutes)

### For Understanding the Project:

**Start here:** `BEGINNER_GUIDE.md`

Perfect if you need to:
- Explain the project to someone
- Understand what system calls are
- Refresh your memory on concepts
- Answer "why are we building this?"

---

## 🎓 Project Data

This project uses the **DoD SAFE dataset** located at:
`../DoD SAFE-IRdf4AjAzcCACu3m/`

### Key Resources
- **LSTM Model Documentation**: `../DoD SAFE-IRdf4AjAzcCACu3m/DoD SAFE-TRdYakPxRdrWZUHz/NSSSIP 2024 - System Call Pattern Recognition Model Documentation, Schweers.pdf`
- **CSV Data**: `../DoD SAFE-IRdf4AjAzcCACu3m/DoD SAFE-TRdYakPxRdrWZUHz/csvs_dev_test_bags/`
- **LSTM Model Code**: `../DoD SAFE-IRdf4AjAzcCACu3m/DoD SAFE-TRdYakPxRdrWZUHz/lstm_model/`
- **Requirements**: `../DoD SAFE-IRdf4AjAzcCACu3m/DoD SAFE-TRdYakPxRdrWZUHz/srs_requirements.txt`

---

## 🎯 Grading Criteria

From the assignment:
- ✅ **Clarity of UML diagrams** - We have detailed, well-documented diagrams
- ✅ **Clarity of low-fidelity prototype** - 5 interactive HTML mockups with design notes
- ✅ **Quality of project report** - Comprehensive 70+ page report
- ✅ **Quality of presentation** - Complete outline with speaker notes

**Total Score:** 30% of final grade

---

## ✨ What Makes This Submission Strong

1. **Comprehensive Coverage**
   - Goes beyond minimum requirements
   - Multiple sequence diagrams (3) when 1+ required
   - Multiple prototypes (5) showing complete system
   - Detailed implementation plan (40+ pages)

2. **Real-World Application**
   - Uses actual DoD military research data
   - Addresses real security and performance problems
   - Production-ready architecture

3. **Clear Documentation**
   - Beginner-friendly guide for accessibility
   - Professional report structure
   - Step-by-step presentation outline
   - Code-level detail in diagrams

4. **Technical Depth**
   - 25+ classes in class diagram
   - 29 use cases across 5 user types
   - LSTM neural network integration
   - 12-week implementation timeline with milestones

5. **Team Collaboration**
   - Clear role assignments
   - Realistic timeline
   - Risk management included
   - Testing strategy defined

---

## 🔍 Need Help?

### Understanding the Project?
→ Read `BEGINNER_GUIDE.md`

### Rendering UML Diagrams?
→ See `uml_diagrams/README.md`

### Viewing Prototypes?
→ See `prototypes/README.md`

### Creating Presentation?
→ Follow `PRESENTATION_OUTLINE.md`

### Technical Details?
→ Read `IMPLEMENTATION_PLAN.md`

### Everything in One Place?
→ Read `PROJECT_REPORT.md`

---

## 🚀 Next Steps (After Stage 2)

1. **Immediate** (Before Oct 23):
   - ✅ Review PROJECT_REPORT.md
   - ⏳ Convert to PDF
   - ⏳ Create presentation slides
   - ⏳ Practice presentation
   - ⏳ Submit on Blackboard

2. **After Submission**:
   - Present in class (date TBD)
   - Receive feedback
   - Begin Stage 3 (Implementation!)

3. **Stage 3 Preview** (Weeks 1-12):
   - Set up development environment
   - Build backend (Python/Flask)
   - Build frontend (React)
   - Integrate LSTM model
   - Deploy to production
   - See IMPLEMENTATION_PLAN.md for complete timeline

---

## 📞 Contact

**Project Manager:** John Heitzman  
**Email:** maxheitzman@gmail.com  

**Team Members:**
- Noah Küng (Lead Developer) - noah.kueng.1@gmail.com
- Joseph Musangu (Data Analyst) - tmusangu@ttu.edu
- Omotoyosi Adams (UI/UX Designer) - omoadams@ttu.edu
- Delphin Iradukunda (Documentation Specialist) - diraduku@ttu.edu

---

## 🎉 You're Ready to Submit!

Everything is complete. Just need to:
1. Convert PROJECT_REPORT.md to PDF
2. Create presentation slides from PRESENTATION_OUTLINE.md
3. Practice as a team
4. Submit and present!

**Great work on Stage 2! 🚀**

