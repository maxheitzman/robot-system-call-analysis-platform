# Stage 2 Presentation Outline
## Robot System Call Analysis Platform
**10-15 Minute Presentation | October 23, 2025**

---

## 📊 Presentation Structure

### Recommended Timing
- **Introduction:** 1-2 minutes
- **Problem Statement:** 2 minutes
- **System Design:** 4-5 minutes
- **User Interface:** 2-3 minutes
- **Implementation Plan:** 2-3 minutes
- **Q&A:** 2-3 minutes

---

## 🎯 Slide Outline

### Slide 1: Title Slide (30 seconds)
```
[Logo/Image of UMD Husky Robot]

Robot System Call Analysis Platform
UMD Husky Cyber Threat Detection System

CS 4366 - Senior Capstone Project
Fall 2025 - Stage 2: Software Design Specification

Team Members:
- John Heitzman (Project Manager)
- Noah Küng (Lead Developer)
- Joseph Musangu (Data Analyst)
- Omotoyosi Adams (UI/UX Designer)
- Delphin Iradukunda (Documentation Specialist)

October 23, 2025
```

**Speaker Notes:**
- Introduce yourself and team
- Brief mention of project name
- Move quickly to next slide

---

### Slide 2: Problem Statement (1 minute)
```
The Challenge

🤖 Military robots generate MILLIONS of system calls
📊 1.2M+ system calls in our dataset
⚠️ Need to detect anomalies and cyber threats
🔍 Current methods are manual and reactive

[Visual: Image of robot with data flowing]
```

**Speaker Notes:**
- "Autonomous robots like the UMD Husky generate massive amounts of system call data"
- "We're talking about 11,200 system calls per second"
- "Currently, analyzing this data for security threats or performance issues is manual and time-consuming"
- "Our platform automates this process using machine learning"

---

### Slide 3: Our Solution (1 minute)
```
What We're Building

An intelligent platform that:
✓ Monitors robot system calls in real-time
✓ Detects anomalies using AI (LSTM neural networks)
✓ Analyzes performance patterns across different modes
✓ Provides actionable insights to engineers

[Visual: High-level system diagram]
```

**Speaker Notes:**
- "We're building a comprehensive analysis platform"
- "It uses LSTM neural networks - the same technology behind ChatGPT's language understanding"
- "But we're applying it to detect unusual patterns in robot behavior"
- "Think of it like antivirus software, but for robots"

---

### Slide 4: Dataset Overview (30 seconds)
```
Working with Real Military Data

📁 DoD SAFE Dataset
   • 6 CSV files totaling 1.4GB
   • 1.2M+ system call records
   • Multiple operational modes:
     - Autonomous driving
     - Manual control
     - Test scenarios

[Visual: Table showing dataset stats]
```

**Speaker Notes:**
- "We're working with real data from DoD research"
- "This gives us a realistic foundation for our analysis"
- Quick mention of data volume

---

### Slide 5: System Architecture - Overview (1 minute)
```
System Architecture

[Large visual diagram showing:]

Data Collection → Processing → Analysis → Visualization
     ↓              ↓            ↓             ↓
CSV Import      Parser      LSTM Model    Dashboard
Real-time    Validator    Anomaly Detector  Reports

Storage Layer: PostgreSQL + Redis Cache
```

**Speaker Notes:**
- Walk through the flow left to right
- "Data comes in from CSV files or real-time streams"
- "Processing layer validates and structures it"
- "Analysis layer uses our LSTM model to detect patterns"
- "Users interact through a web dashboard"
- "All backed by a robust database"

---

### Slide 6: UML Class Diagram (1 minute)
```
Class Diagram - System Structure

[Include actual class diagram image here]

Key Components:
• Data Collection Layer (3 classes)
• Processing Layer (3 classes)
• Analysis & AI Layer (4 classes)
• Storage Layer (3 classes)
• API & Services Layer (3 classes)
• User Interface Layer (3 classes)

Total: 25+ classes organized in 7 packages
```

**Speaker Notes:**
- "Our system is organized into clear layers"
- Point to diagram: "Data flows from top to bottom"
- "Each layer has specific responsibilities"
- "This modular design makes it easy to test and maintain"
- Don't read every class name - highlight key ones

---

### Slide 7: UML Use Case Diagram (1 minute)
```
Who Uses the System and How?

[Include use case diagram image]

5 User Types:
👤 System Administrator - Monitoring & Configuration
👤 Data Analyst - Historical Analysis & Reporting
👤 Research Scientist - Pattern Analysis & Comparison
👤 System Engineer - Performance Optimization
👤 Security Analyst - Anomaly Detection & Threat Response

29 Use Cases across 7 categories
```

**Speaker Notes:**
- "We identified 5 different types of users"
- "Each has different needs and workflows"
- "For example, Security Analysts focus on anomaly detection"
- "While Data Analysts do deep historical analysis"
- "The system supports all these use cases"

---

### Slide 8: Sequence Diagram - Real-time Monitoring (1 minute)
```
How Real-time Monitoring Works

[Include sequence diagram image]

Process Flow:
1. Administrator opens dashboard
2. System connects to robot
3. Robot streams system calls (11,200/sec)
4. Parser validates and structures data
5. Anomaly detector checks for threats
6. Dashboard updates in real-time
7. Alerts trigger if anomalies detected
```

**Speaker Notes:**
- Walk through the sequence step by step
- "This happens continuously, 100 times per second"
- "The LSTM model checks each batch for anomalies"
- "If something unusual is detected, alerts are sent immediately"
- Emphasize the real-time nature

---

### Slide 9: The LSTM Model (1 minute)
```
AI-Powered Anomaly Detection

🧠 LSTM Encoder-Decoder Neural Network
   • Based on DoD SAFE research
   • 2 layers, 128 neurons each
   • Dropout: 0.2 for regularization
   • Trained on 1.2M+ system calls

How it works:
1. Learns normal robot behavior patterns
2. Identifies deviations from normal
3. Assigns confidence scores
4. Alerts on significant anomalies

Accuracy: 94%+ confidence

[Visual: Simple neural network diagram]
```

**Speaker Notes:**
- "LSTM stands for Long Short-Term Memory"
- "It's great at understanding sequences - like system calls over time"
- "We train it on normal robot behavior"
- "Then it can spot when things are unusual"
- "Think of it like teaching a guard dog what normal looks like"

---

### Slide 10: User Interface - Main Dashboard (1 minute)
```
Main Dashboard

[Screenshot of main dashboard prototype]

Features:
📊 Real-time statistics
📈 System call distribution charts
🔧 Component activity visualization
🔍 Recent activity feed
```

**Speaker Notes:**
- "This is what users see when they log in"
- "At a glance, they can see system health"
- "These charts show which system calls are most common"
- "The activity feed shows what's happening right now"
- "Everything updates in real-time"

---

### Slide 11: User Interface - Real-time Monitor (45 seconds)
```
Real-time Monitoring View

[Screenshot of real-time monitor prototype]

Features:
📈 Live call frequency graph
📋 Streaming system call table
⏸️ Pause/resume controls
🔍 Filter by component
```

**Speaker Notes:**
- "Engineers can drill down to see individual system calls"
- "This view shows every call as it happens"
- "They can filter to focus on specific components"
- "Useful for debugging and performance analysis"

---

### Slide 12: User Interface - Anomaly Detection (45 seconds)
```
Anomaly Detection Dashboard

[Screenshot of anomaly detection prototype]

Features:
🚨 Severity-coded alerts (Critical/Warning/Info)
🧠 LSTM model status display
📊 Confidence scores
🔍 Detailed investigation tools
✓ False positive handling
```

**Speaker Notes:**
- "This is where security analysts spend their time"
- "Anomalies are color-coded by severity"
- "Each alert shows confidence level and details"
- "Analysts can investigate, dismiss, or create alert rules"
- "The system learns from false positives"

---

### Slide 13: User Interface - Component Analysis (30 seconds)
```
Component Deep Dive

[Screenshot of component analysis prototype]

Analyze individual robot components:
• global_planner (56.6% of activity)
• front_ouster (LiDAR - 25.7%)
• os_cloud_node (11.2%)
• And more...

See performance metrics, bottlenecks, and recommendations
```

**Speaker Notes:**
- "Each robot component can be analyzed individually"
- "This helps identify performance bottlenecks"
- "Engineers can see exactly what each component is doing"

---

### Slide 14: Implementation Plan - Technology Stack (1 minute)
```
Technology Stack

Backend:
🐍 Python 3.11+ with Flask
🧠 TensorFlow/Keras for LSTM
🗄️ PostgreSQL database
⚡ Redis for caching

Frontend:
⚛️ React 18 with TypeScript
📊 Chart.js & D3.js for visualization
🎨 Material-UI components

DevOps:
🐳 Docker containers
☁️ AWS deployment
🔄 GitHub Actions CI/CD
```

**Speaker Notes:**
- "We chose modern, battle-tested technologies"
- "Python is perfect for data analysis and ML"
- "React gives us a responsive, fast dashboard"
- "Everything runs in Docker containers"
- "We can deploy to cloud or on-premises"

---

### Slide 15: Implementation Plan - Timeline (1 minute)
```
12-Week Development Plan

Phase 1 (Weeks 1-2): Foundation
   ✓ Development environment
   ✓ Database setup

Phase 2 (Weeks 3-4): Data Processing
   • CSV import
   • LSTM integration

Phase 3 (Weeks 5-6): API Layer
   • REST APIs
   • Real-time WebSockets

Phase 4 (Weeks 7-8): Frontend Dashboard
   • All 5 main views
   • Data visualization

Phase 5 (Weeks 9-10): Advanced Features
   • Reporting
   • Anomaly refinement

Phase 6 (Week 11): Testing & Refinement
   • Unit, integration, E2E tests
   • Performance optimization

Phase 7 (Week 12): Deployment
   • Production deployment
   • Documentation
```

**Speaker Notes:**
- "We have a clear 12-week plan"
- "Each phase builds on the previous one"
- "We're using Agile methodology with weekly sprints"
- "By week 8, we'll have a working prototype"
- "Weeks 9-12 are for polish and deployment"

---

### Slide 16: Implementation Plan - Team Roles (30 seconds)
```
Team Organization

👔 John Heitzman - Project Manager
   • Coordination, DevOps, integration testing

💻 Noah Küng - Lead Developer
   • Backend architecture, APIs, React components

📊 Joseph Musangu - Data Analyst
   • Database design, LSTM integration, analysis

🎨 Omotoyosi Adams - UI/UX Designer
   • Interface design, styling, user experience

📝 Delphin Iradukunda - Documentation Specialist
   • Technical docs, user manuals, API docs

Everyone: Testing, code review, collaboration
```

**Speaker Notes:**
- "We've organized our team based on strengths"
- "But everyone contributes to all areas"
- "Daily standups keep us synchronized"
- "Code reviews ensure quality"

---

### Slide 17: Key Features Recap (45 seconds)
```
What Makes Our System Unique?

✨ Real-time processing (11,200 calls/second)
🧠 AI-powered anomaly detection (94% accuracy)
📊 Comprehensive visualization dashboards
🔍 Multi-mode analysis (auto/manual/test)
📈 Historical trend analysis
📥 Easy CSV import (1.2M+ records)
🚀 Scalable cloud architecture
🔒 Security-first design

Built on real DoD research data
```

**Speaker Notes:**
- "Let me summarize what sets our platform apart"
- Go through bullets quickly
- "Most importantly, it's built on real military research"
- "This isn't a toy project - it's designed for production use"

---

### Slide 18: Expected Impact (30 seconds)
```
Why This Matters

🛡️ Enhanced Security
   • Detect cyber attacks early
   • Identify unusual behavior patterns

⚡ Improved Performance
   • Find bottlenecks automatically
   • Optimize robot operations

💰 Cost Savings
   • Reduce manual analysis time
   • Prevent system failures

🔬 Research Value
   • Platform for future research
   • Extensible to other robotic systems
```

**Speaker Notes:**
- "This platform has real-world impact"
- "It can detect security threats before they cause damage"
- "It helps engineers optimize performance"
- "And it provides a foundation for future robotics research"

---

### Slide 19: Challenges & Solutions (Optional - 30 seconds)
```
Anticipated Challenges

Challenge: Large dataset processing
✅ Solution: Pagination, indexing, caching

Challenge: Real-time performance
✅ Solution: WebSockets, Redis, optimized queries

Challenge: LSTM accuracy
✅ Solution: Extensive training, hyperparameter tuning

Challenge: User experience complexity
✅ Solution: Progressive disclosure, intuitive UI

We've planned for these from day one
```

**Speaker Notes:**
- "We've anticipated potential challenges"
- "And we have concrete solutions for each"
- "This shows we've thought deeply about implementation"

---

### Slide 20: Next Steps (30 seconds)
```
After Stage 2

✓ Stage 2 Complete: Design specification done

🎯 Next: Begin Implementation (Stage 3)
   • Week 1: Start development
   • Week 4: Working prototype
   • Week 8: Feature-complete MVP
   • Week 12: Production deployment

📅 Regular Updates
   • Weekly team meetings
   • Bi-weekly stakeholder demos
   • Continuous integration & testing
```

**Speaker Notes:**
- "We're ready to start building"
- "Development begins next week"
- "We'll have regular demos to show progress"
- "By December, we'll have a production-ready system"

---

### Slide 21: Demo (Optional - If time permits)
```
Quick Demo

[If you have time, show:]
1. Low-fidelity prototypes (open in browser)
2. Walk through user flow
3. Show UML diagrams (PlantUML rendered)

[Or just say:]
"All prototypes and diagrams are available
in our GitHub repository for review"
```

**Speaker Notes:**
- Only if you have extra time
- Quick walkthrough of prototypes
- Show how a user would navigate the system

---

### Slide 22: Questions (Remainder of time)
```
Questions?

[Team photo or project logo]

Contact:
John Heitzman - maxheitzman@gmail.com

GitHub Repository:
[Your repository URL]

Thank you!
```

**Speaker Notes:**
- Open the floor to questions
- Have team members answer questions in their area of expertise
- Be prepared to discuss:
  - Technical details
  - Timeline feasibility
  - Dataset specifics
  - Security considerations
  - Alternative approaches

---

## 🎤 Presentation Tips

### For the Team

**Before Presentation:**
- [ ] Practice together 2-3 times
- [ ] Time yourselves (aim for 12-13 minutes to leave time for Q&A)
- [ ] Decide who presents which slides
- [ ] Prepare for likely questions
- [ ] Test technology (projector, slides, demos)
- [ ] Bring backup (USB drive with slides)

**During Presentation:**
- **Speak clearly** - Project your voice
- **Make eye contact** - Look at audience, not just slides
- **Use transitions** - "Now let me hand it to Noah to discuss..."
- **Engage audience** - Ask rhetorical questions
- **Point to visuals** - "As you can see here..."
- **Watch time** - Have someone track time
- **Stay calm** - It's okay to say "I don't know, but I'll find out"

**Presentation Flow Suggestion:**
- **John:** Intro, problem, solution (Slides 1-3)
- **Noah:** Architecture & class diagram (Slides 5-6)
- **Joseph:** Use cases & LSTM model (Slides 7-9)
- **Omotoyosi:** UI prototypes (Slides 10-13)
- **Delphin:** Implementation plan (Slides 14-16)
- **John:** Wrap-up & Q&A (Slides 17-22)

### Likely Questions & Answers

**Q: Why Python instead of Java/C++?**
A: Python has the best ecosystem for data science and machine learning. It's faster to develop in, and TensorFlow/PyTorch are Python-first. For our use case, Python's performance is sufficient - we're processing data, not controlling real-time robot movements.

**Q: How will you handle real-time data at 11,200 calls/second?**
A: We're using WebSockets for real-time communication, Redis for caching hot data, and database indexing for fast queries. In the UI, we'll display sampled data (every 10th call) rather than every single call. The full data is still analyzed, just not all displayed.

**Q: What if the LSTM model has low accuracy?**
A: We have contingency plans: 1) Fall back to statistical anomaly detection (z-scores), 2) Use rule-based pattern matching, 3) Ensemble methods combining multiple approaches. The existing DoD model has shown good results, so we're building on proven research.

**Q: How secure is the system?**
A: Security is built in from day one: encrypted data storage, HTTPS/WSS communication, role-based access control, SQL injection prevention, XSS protection, and regular security audits. We're following OWASP best practices.

**Q: Can this work with other robots, not just UMD Husky?**
A: Yes! The system is designed to be robot-agnostic. As long as system call data is available in CSV format or via network stream, it can be analyzed. We'd need to retrain the LSTM model on that robot's data.

**Q: How much will cloud hosting cost?**
A: For production: ~$333/month on AWS (EC2, RDS, Redis, S3). For development/MVP: ~$100/month. We can also deploy on university infrastructure to eliminate costs.

**Q: What happens if a team member drops out?**
A: We have knowledge sharing built in: documentation, code reviews, and pair programming. Each area has a primary and secondary owner. John (PM) can fill gaps if needed. The modular architecture means we can reduce scope without breaking the system.

---

## 📁 Presentation Materials Checklist

**Files to Prepare:**
- [ ] PowerPoint/Keynote/Google Slides file
- [ ] PDF version of slides (backup)
- [ ] UML diagram images (PNG, high-res)
- [ ] Prototype screenshots
- [ ] Low-fidelity prototypes (HTML files, if demo)
- [ ] Handout (optional): 1-page project summary
- [ ] USB drive backup

**Visual Assets Needed:**
- [ ] UMD Husky robot photo
- [ ] Class diagram (rendered from PlantUML)
- [ ] Use case diagram (rendered from PlantUML)
- [ ] Sequence diagram (rendered from PlantUML)
- [ ] Dashboard screenshot
- [ ] Real-time monitor screenshot
- [ ] Anomaly detection screenshot
- [ ] Component analysis screenshot
- [ ] Data import screenshot
- [ ] Team photo (optional)

---

## 🎯 Success Criteria for Presentation

**Content (40%):**
- [ ] Clear problem statement
- [ ] Comprehensive system design explained
- [ ] UML diagrams are clear and correct
- [ ] UI prototypes demonstrate functionality
- [ ] Implementation plan is realistic and detailed

**Delivery (30%):**
- [ ] Within time limit (10-15 minutes)
- [ ] All team members participate
- [ ] Clear, confident speaking
- [ ] Good transitions between speakers
- [ ] Engaging presentation style

**Visual Quality (15%):**
- [ ] Professional-looking slides
- [ ] Clear diagrams and images
- [ ] Consistent formatting
- [ ] Readable text size
- [ ] Not too much text per slide

**Q&A (15%):**
- [ ] Thoughtful, detailed answers
- [ ] Team demonstrates understanding
- [ ] Honest about challenges
- [ ] Shows preparation and research

---

## 🚀 Final Checklist

**Day Before:**
- [ ] Final practice run-through
- [ ] All slides finalized
- [ ] Backups prepared (USB, cloud)
- [ ] Outfits planned (business casual)
- [ ] Equipment tested
- [ ] Questions prepared for anticipated topics

**Day Of:**
- [ ] Arrive 15 minutes early
- [ ] Test projector connection
- [ ] Water bottles ready
- [ ] Deep breaths, stay calm!
- [ ] Remember: You know this material better than anyone

**You've got this! Good luck! 🍀**

