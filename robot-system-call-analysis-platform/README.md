# Robot System Call Analysis Platform

**Course:** CS 4366 - Senior Capstone Project Fall 2025  
**Stage:** 2 - Software Design Specification (SDS)  
**Team:** John Heitzman, Noah Küng, Joseph Musangu, Omotoyosi Adams, Delphin Iradukunda

## 🎯 Project Overview

The Robot System Call Analysis Platform is an intelligent software system designed to monitor, analyze, and detect anomalies in system call patterns from autonomous robotic systems. Built upon the Department of Defense SAFE dataset, this platform provides real-time monitoring, historical analysis, and machine learning-powered threat detection for the UMD Husky autonomous ground robot.

## 🔑 Key Features

- **Real-time Monitoring:** 11,200+ system calls per second
- **LSTM Anomaly Detection:** 94% accuracy using neural networks
- **Sensor Data Validation:** Security validation between sensors and control
- **Emergency Stop System:** Automatic robot shutdown on threat detection
- **Multi-user Dashboard:** Role-based access for different user types
- **Historical Analysis:** Comparative analysis across operational modes

## 📊 Dataset

- **Source:** DoD SAFE (Department of Defense System Analysis for Enhanced Security)
- **Robot:** UMD Husky autonomous ground robot
- **Volume:** 1.4GB, 1.2M+ system calls
- **Time Period:** June-August 2024
- **Components:** global_planner (56.6%), front_ouster (25.7%), os_cloud_node (11.2%)

## 🏗️ System Architecture

- **Backend:** Python 3.11+ with Flask, TensorFlow, PostgreSQL
- **Frontend:** React 18 with TypeScript, Material-UI, Chart.js
- **Infrastructure:** Docker, AWS (optional)
- **Security:** Data integrity validation, threat detection, emergency stop

## 📁 Repository Structure

```
├── PROJECT_REPORT.md              # Complete 70+ page report
├── PRESENTATION_OUTLINE.md         # 22-slide presentation guide
├── IMPLEMENTATION_PLAN.md          # Detailed technical roadmap
├── STAGE2_COMPLETE_OVERVIEW.md     # Everything consolidated
├── BEGINNER_GUIDE.md               # Simple explanations
├── TEAM_MEETING_GUIDE.md           # Team coordination
├── URGENT_ACTION_PLAN.md           # Submission checklist
├── UML_DIAGRAMS_EXPLAINED.md      # UML guide
├── UI_PROTOTYPES_EXPLAINED.md      # Prototype guide
├── SECURITY_ENHANCEMENTS_SUMMARY.md # Security features
├── uml_diagrams/                   # UML diagrams (6 files)
│   ├── class_diagram.puml
│   ├── use_case_diagram.puml
│   ├── sequence_diagram_1_realtime_monitoring.puml
│   ├── sequence_diagram_2_data_analysis.puml
│   ├── sequence_diagram_3_data_import.puml
│   └── sequence_diagram_4_security_validation.puml
├── prototypes/                     # UI prototypes (5 files)
│   ├── 01_main_dashboard.html
│   ├── 02_realtime_monitor.html
│   ├── 03_component_analysis.html
│   ├── 04_anomaly_detection.html
│   └── 05_data_import.html
└── docs/                           # Additional documentation
```

## 🚀 Quick Start

### **For Stage 2 Submission:**
1. Read `STAGE2_COMPLETE_OVERVIEW.md` for everything you need
2. Follow `URGENT_ACTION_PLAN.md` for submission steps
3. Use `TEAM_MEETING_GUIDE.md` for team coordination

### **For UML Diagrams:**
1. Go to `uml_diagrams/` folder
2. Use PlantUML to render diagrams: http://www.plantuml.com/plantuml/uml/
3. Follow `UML_DIAGRAMS_EXPLAINED.md` for detailed instructions

### **For UI Prototypes:**
1. Go to `prototypes/` folder
2. Open HTML files in browser
3. Follow `UI_PROTOTYPES_EXPLAINED.md` for screenshot instructions

## 📋 Stage 2 Deliverables

- ✅ **Project Report** (70+ pages) - Complete system documentation
- ✅ **UML Diagrams** (6 diagrams) - Class, Use Case, 4 Sequence diagrams
- ✅ **UI Prototypes** (5 screens) - Complete dashboard mockups
- ✅ **Implementation Plan** (40+ pages) - Detailed technical roadmap
- ✅ **Presentation Outline** (22 slides) - Complete presentation guide

## 🔒 Security Features

- **Sensor Data Validation:** Checks data integrity before reaching control board
- **Threat Detection:** LSTM-based anomaly detection with 94% accuracy
- **Emergency Stop:** Automatic robot shutdown on security threats
- **User Alerts:** Real-time notifications for security events
- **Audit Logging:** Complete security event tracking

## 👥 Team Members

- **John Heitzman** (Project Manager) - maxheitzman@gmail.com
- **Noah Küng** (Lead Developer) - noah.kueng.1@gmail.com
- **Joseph Musangu** (Data Analyst) - tmusangu@ttu.edu
- **Omotoyosi Adams** (UI/UX Designer) - omoadams@ttu.edu
- **Delphin Iradukunda** (Documentation Specialist) - diraduku@ttu.edu

## 📅 Timeline

- **Stage 1:** Software Requirements Specification (Completed)
- **Stage 2:** Software Design Specification (Due: October 23, 2025)
- **Stage 3:** Implementation (Weeks 1-12)
- **Final Presentation:** TBD

## 📞 Contact

**Project Manager:** John Heitzman  
**Email:** maxheitzman@gmail.com

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Ready for Stage 2 submission! 🚀**