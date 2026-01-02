# Robot System Call Analysis Platform - Capstone Project

**Course:** CS 4366 - Senior Capstone Project Fall 2025  
**Team:** Team 5  
**Project Website:** [https://jomusangu.github.io/capstone_website/](https://jomusangu.github.io/capstone_website/)

## 👥 Team Members

- **John Heitzman** (Project Manager) - Full-Stack Development, System Architecture, DevOps & AI Integration
- **Noah Küng** (Lead Developer) - AI/ML Engineer
- **Joseph Musangu** (Data Analyst) - Data Analysis/UI & UX
- **Omotoyosi Adams** (UI/UX Designer) - Data Engineer
- **Delphin Iradukunda** (Documentation Specialist) - Data Analysis Research

### Technical Contributions by Role

**John Heitzman (Max) - Primary Technical Contributions:**
- **System Architecture:** ROS integration, backend API design, system architecture
- **Full-Stack Development:** Backend Flask API, frontend dashboard enhancements, real-time processing
- **AI/ML Implementation:** GPS prediction algorithms, boundary detection systems, LSTM training pipeline
- **DevOps & Infrastructure:** Docker containerization, deployment automation, system integration
- **Data Analysis Tools:** Graph generation, performance benchmarking, analysis scripts
- **Testing & Validation:** System testing, validation frameworks, performance optimization

*See [Husky Dashboard Repository](https://github.com/maxheitzman/husky-dashboard) and [Implementation Comparison](https://github.com/maxheitzman/husky-dashboard/blob/main/IMPLEMENTATION_COMPARISON.md) for detailed technical contributions.*

## 📋 Project Overview

This capstone project focuses on developing a system based on the **DoD SAFE dataset** for system call pattern recognition and anomaly detection. The project monitors, analyzes, and detects anomalies in system call patterns from autonomous robotic systems, specifically the UMD Husky autonomous ground robot.

**Key Features:**
- Real-time monitoring of 11,200+ system calls per second
- LSTM-based anomaly detection (94% accuracy)
- Sensor data validation and security
- Emergency stop system for threat detection
- Multi-user dashboard with role-based access

## 📁 Project Structure

### `/stage1/`
**Status:** ✅ Completed

Contains all Stage 1 deliverables:
- Project description and requirements
- Team formation and initial planning
- Presentation materials
- Website prototype

### `/stage2/`
**Status:** ✅ Completed

Software Design Specification (SDS):
- UML diagrams (Class, Use Case, Sequence)
- Low-fidelity prototype (5 HTML mockups)
- Implementation plan
- Complete project report (70+ pages)

### `/stage3/`
**Status:** ✅ Completed

Implementation Phase:
- Functional working prototype
- ROS 2 sensor data integration
- Anomaly detection implementation
- Real-time dashboard deployment
- End-to-end monitoring demonstration

**Key Components:**
- `maxs_demo_version/` - Enhanced demo version with improvements
- `josephs_version/` - Joseph's implementation version
- Analysis tools and benchmarking
- GPS prediction and boundary detection
- LSTM training pipeline

### `/robot-system-call-analysis-platform/`
Complete project documentation:
- Project reports
- UML diagrams
- UI prototypes
- Implementation plans
- Team meeting guides

### `/husky-dashboard/`
**Separate Repository:** [maxheitzman/husky-dashboard](https://github.com/maxheitzman/husky-dashboard)

GPS Anomaly Detection Component:
- ROS sensor data poisoning detection dashboard
- GPS prediction models (LSTM)
- Poison injection system
- Enhanced backend implementation
- Implementation comparison document

**See:** [Husky Dashboard Repository](https://github.com/maxheitzman/husky-dashboard) for details

### `/DoD SAFE-IRdf4AjAzcCACu3m/`
Project data and resources:
- LSTM model for system call pattern recognition
- CSV datasets from autonomous vehicle testing
- Documentation and analysis scripts
- Training data and model checkpoints

## 🔗 Repository Links

### Main Group Repository
**GitHub:** [maxheitzman/robot-system-call-analysis-platform](https://github.com/maxheitzman/robot-system-call-analysis-platform)

**Contains:**
- Complete project structure
- All stage deliverables (Stage 1, 2, 3)
- Documentation and reports
- UML diagrams and prototypes

### Husky Dashboard Repository
**GitHub:** [maxheitzman/husky-dashboard](https://github.com/maxheitzman/husky-dashboard)

**Contains:**
- GPS anomaly detection dashboard
- Enhanced implementation with improvements
- Implementation comparison document

### Project Website
**URL:** [https://jomusangu.github.io/capstone_website/](https://jomusangu.github.io/capstone_website/)

**Contains:**
- Project overview
- Team information
- Progress updates
- Meeting notes
- Interview schedules

### Original Shared Repository
**Reference:** [joMusangu/husky-dashboard](https://github.com/joMusangu/husky-dashboard/tree/feature/gps-anomaly-detection)

Base repository that served as starting point for GPS anomaly detection component.

## 📊 Dataset Information

- **Source:** DoD SAFE (Department of Defense System Analysis for Enhanced Security)
- **Robot:** UMD Husky autonomous ground robot
- **Volume:** 1.4GB, 1.2M+ system calls
- **Time Period:** June-August 2024
- **Components:** global_planner (56.6%), front_ouster (25.7%), os_cloud_node (11.2%)

## 🏗️ System Architecture

- **Backend:** Python 3.11+ with Flask, TensorFlow, PostgreSQL
- **Frontend:** React 18 with TypeScript, Material-UI, Chart.js (planned)
- **Current Frontend:** HTML/CSS/JavaScript with Chart.js
- **Infrastructure:** Docker, AWS (optional)
- **Security:** Data integrity validation, threat detection, emergency stop

## 📚 Key Documentation

- [Stage 2 Project Report](./stage2/PROJECT_REPORT.md)
- [Stage 3 Project Report](./stage3/PROJECT_REPORT.md)
- [Implementation Plan](./robot-system-call-analysis-platform/IMPLEMENTATION_PLAN.md)
- [Husky Dashboard README](./husky-dashboard/README.md)
- [Repository Status](./REPOSITORY_STATUS.md)

## 🎯 Project Status

### ✅ Completed Stages

1. **Stage 1:** Project Kickoff (August - October 2025)
   - Requirements gathering
   - Team formation
   - Initial planning

2. **Stage 2:** Software Design Specification (October 2025)
   - UML diagrams
   - Prototypes
   - Implementation plan

3. **Stage 3:** Implementation (November 2025 - Present)
   - Functional prototype
   - ROS 2 integration
   - Anomaly detection
   - Real-time dashboard

## 📞 Contact

**Project Manager:** John Heitzman  
**Email:** maxheitzman@gmail.com

---

*CS 4366 - Senior Capstone Project Fall 2025 - Team 5*
