# Stage 2: Software Design Specification (SDS)
# Robot System Call Analysis Platform
## UMD Husky Cyber Threat Detection System

**Course:** CS 4366 - Senior Capstone Project Fall 2025  
**Date:** October 23, 2025  
**Version:** 1.0

---

**Team Members:**

| Name | Student ID | Role | Email |
|------|------------|------|-------|
| John Heitzman | R11626572 | Project Manager | maxheitzman@gmail.com |
| Noah Küng | R11846843 | Lead Developer | noah.kueng.1@gmail.com |
| Joseph Musangu | R11854643 | Data Analyst | tmusangu@ttu.edu |
| Omotoyosi Adams | R11873126 | UI/UX Designer | omoadams@ttu.edu |
| Delphin Iradukunda | R11828594 | Documentation Specialist | diraduku@ttu.edu |

---

## Table of Contents

1. [Project Description](#1-project-description)
2. [System Analysis and Decomposition](#2-system-analysis-and-decomposition)
   - 2.1 [Class Diagrams](#21-class-diagrams)
   - 2.2 [Use Case Diagrams](#22-use-case-diagrams)
   - 2.3 [Sequence Diagrams](#23-sequence-diagrams)
3. [Low-Fidelity Prototype](#3-low-fidelity-prototype)
4. [Implementation Plan](#4-implementation-plan)
   - 4.1 [Testbed](#41-testbed)
   - 4.2 [Programming Languages](#42-programming-languages)
   - 4.3 [Development Tools/Devices](#43-development-toolsdevices)
   - 4.4 [Timeline](#44-timeline)
5. [Appendices](#5-appendices)

---

## 1. Project Description

### 1.1 Overview

The Robot System Call Analysis Platform is an intelligent software system designed to monitor, analyze, and detect anomalies in system call patterns from autonomous robotic systems. Built upon the Department of Defense SAFE (System Analysis for Enhanced Security) dataset, this platform provides real-time monitoring, historical analysis, and machine learning-powered threat detection for the UMD Husky autonomous ground robot.

### 1.2 Problem Statement

Modern autonomous robots generate millions of system calls during operation - over 11,200 calls per second in the case of the UMD Husky robot. These system calls represent the robot's interactions with its operating system and provide critical insights into:

- **Performance bottlenecks** - Identifying slow or inefficient operations
- **Security threats** - Detecting unusual patterns that may indicate cyber attacks
- **Operational health** - Monitoring normal vs. abnormal behavior
- **Component interactions** - Understanding how different robot subsystems communicate

Currently, analyzing this massive volume of data requires manual review by engineers and security analysts - a time-consuming, error-prone process that cannot detect threats in real-time. There is a critical need for an automated, intelligent system that can process this data continuously, learn normal behavior patterns, and alert operators to anomalies as they occur.

### 1.3 Proposed Solution

Our platform addresses these challenges through:

1. **Automated Data Processing** - Import and process CSV files containing millions of system call records, or monitor real-time data streams from active robots

2. **Machine Learning-Based Anomaly Detection** - Deploy an LSTM (Long Short-Term Memory) encoder-decoder neural network trained on the DoD SAFE dataset to identify unusual behavior patterns with 94%+ confidence

3. **Real-Time Monitoring Dashboard** - Provide engineers and security analysts with live visualization of system calls, component activity, and performance metrics updated at 10Hz (10 times per second)

4. **Historical Analysis Tools** - Enable data scientists to perform comparative analysis across different operational modes (autonomous driving, manual control, test scenarios) and identify long-term trends

5. **Comprehensive Reporting** - Generate detailed reports in multiple formats (PDF, CSV, JSON) for documentation, auditing, and further analysis

### 1.4 Key Features

- **High-Throughput Processing**: Handle 11,200+ system calls per second
- **AI-Powered Detection**: LSTM neural network with 94% accuracy
- **Real-Time Visualization**: Live dashboards with sub-second updates
- **Multi-Mode Analysis**: Compare autonomous, manual, and test operations
- **Scalable Architecture**: Cloud-ready, containerized deployment
- **Role-Based Access**: Support multiple user types (admins, analysts, engineers, security)
- **Data Export**: Multiple format support for external analysis

### 1.5 Dataset

The project leverages the DoD SAFE dataset, which contains:

- **Total Volume**: 1.4GB of system call data
- **Total Records**: 1,200,000+ system calls
- **Time Period**: June-August 2024
- **Operational Modes**: Autonomous, manual control, and test scenarios
- **Sensors**: GPS, LiDAR (Ouster), cameras, IMU
- **Robot Platform**: UMD Husky autonomous ground robot

**Dataset Composition:**

| File | Size | Records | Mode | Duration |
|------|------|---------|------|----------|
| test-gps-no-cam.csv | 95.6 MB | 632,986 | Test | 52 seconds |
| gps-no-cam.csv | 52.2 MB | 346,466 | Autonomous | 28 seconds |
| man-gps-no-cam.csv | 32.5 MB | 216,199 | Manual | 17 seconds |
| full-cam.csv | 23.5 MB | 154,618 | Autonomous | 12 seconds |
| auto-gps-no-cam.csv | 5.9 MB | 40,031 | Autonomous | 3.6 seconds |
| auto-gps-no-cam-processed.csv | 4.7 MB | 40,031 | Autonomous | 3.6 seconds |

### 1.6 Target Users

The system serves five primary user groups:

1. **System Administrators** - Configure the platform, manage users, monitor overall system health
2. **Data Analysts** - Perform historical analysis, generate reports, identify trends
3. **Research Scientists** - Conduct comparative studies, test hypotheses, publish findings
4. **System Engineers** - Optimize robot performance, identify bottlenecks, improve efficiency
5. **Security Analysts** - Monitor for threats, investigate anomalies, respond to alerts

### 1.7 Expected Impact

This platform will:

- **Reduce threat detection time** from hours/days to seconds
- **Automate 80%+ of manual analysis** currently performed by engineers
- **Provide early warning** of performance degradation or security issues
- **Enable research** into robotic system behavior and optimization
- **Serve as a foundation** for similar analysis tools across other robotic platforms

---

## 2. System Analysis and Decomposition

This section presents the UML (Unified Modeling Language) diagrams that define the system's architecture, user interactions, and operational flows.

### 2.1 Class Diagrams

The class diagram illustrates the object-oriented structure of the Robot System Call Analysis Platform. The system is organized into seven logical packages, each containing related classes that work together to provide specific functionality.

#### 2.1.1 Architecture Overview

Our system follows a layered architecture pattern:

```
┌─────────────────────────────────────────────┐
│      User Interface Layer (React)           │
├─────────────────────────────────────────────┤
│      API & Service Layer (Flask REST)       │
├─────────────────────────────────────────────┤
│      Analysis & Intelligence Layer (ML)     │
├─────────────────────────────────────────────┤
│      Data Processing Layer (Python)         │
├─────────────────────────────────────────────┤
│      Storage Layer (PostgreSQL + Redis)     │
├─────────────────────────────────────────────┤
│      Data Collection Layer (Importers)      │
└─────────────────────────────────────────────┘
```

#### 2.1.2 Key Packages and Classes

**Data Collection Layer** (3 classes)
- `RobotDataCollector`: Manages real-time TCP connections to robots
- `CSVFileImporter`: Handles bulk CSV file imports
- `SystemCallData`: Data model representing a single system call record

**Data Processing Layer** (3 classes)
- `SystemCallParser`: Parses raw data into structured format
- `DataProcessor`: Cleans, normalizes, and categorizes data
- `RobotComponentAnalyzer`: Analyzes individual robot component behavior

**Analysis & Intelligence Layer** (4 classes)
- `PatternRecognizer`: Orchestrates LSTM model for pattern detection
- `LSTMModel`: TensorFlow-based neural network implementation
- `AnomalyDetector`: Identifies unusual patterns and generates alerts
- `PerformanceAnalyzer`: Evaluates system performance and identifies bottlenecks

**Storage Layer** (3 classes)
- `DatabaseManager`: Low-level database connection and query execution
- `SystemCallRepository`: Repository pattern for system call data access
- `CacheManager`: Redis-based caching for performance optimization

**API & Service Layer** (3 classes)
- `RESTAPIController`: HTTP endpoints for client communication
- `DataService`: Business logic for data operations
- `AnalysisService`: Business logic for analysis operations

**User Interface Layer** (3 classes)
- `Dashboard`: Main application view controller
- `VisualizationEngine`: Chart and graph generation
- `ReportGenerator`: PDF, CSV, and JSON report creation

**Security & Authentication** (2 classes)
- `AuthenticationManager`: User login, logout, token validation
- `User`: User entity with roles and permissions

#### 2.1.3 Key Design Patterns

1. **Repository Pattern** (Storage Layer)
   - Abstracts data access logic
   - Makes it easy to change database implementation
   - Simplifies unit testing with mock repositories

2. **Service Layer Pattern** (API & Service Layer)
   - Separates business logic from API controllers
   - Enables reuse across different interfaces (REST, GraphQL, CLI)
   - Facilitates testing of business rules

3. **Model-View-Controller (MVC)** (Overall Architecture)
   - Model: Data classes and repositories
   - View: React components
   - Controller: Service layer and API controllers

4. **Observer Pattern** (Real-time Updates)
   - WebSocket connections for live data streaming
   - Pub/Sub through Redis for event notifications

#### 2.1.4 Class Diagram Location

The complete class diagram is available in:
- `stage2/uml_diagrams/class_diagram.puml` (PlantUML source)
- Rendered versions can be generated using PlantUML

**To view the diagram:**
1. Visit http://www.plantuml.com/plantuml/uml/
2. Copy contents of `class_diagram.puml`
3. Paste and view the rendered diagram
4. Export as PNG or SVG for inclusion in presentations

---

### 2.2 Use Case Diagrams

The use case diagram illustrates the functional requirements of the system from the users' perspectives. It shows who uses the system (actors) and what they can do with it (use cases).

#### 2.2.1 Actors

The system supports five types of actors:

1. **System Administrator**
   - Primary responsibilities: System configuration, user management, monitoring
   - Technical expertise: High
   - Access level: Full administrative access

2. **Data Analyst**
   - Primary responsibilities: Historical analysis, report generation, trend identification
   - Technical expertise: Medium-High
   - Access level: Read access to all data, export capabilities

3. **Research Scientist**
   - Primary responsibilities: Comparative analysis, hypothesis testing, pattern exploration
   - Technical expertise: High (statistical/ML background)
   - Access level: Read access, advanced analysis tools

4. **System Engineer**
   - Primary responsibilities: Performance optimization, troubleshooting, system tuning
   - Technical expertise: High (robotics/systems background)
   - Access level: Read access, performance tools

5. **Security Analyst**
   - Primary responsibilities: Threat detection, anomaly investigation, incident response
   - Technical expertise: High (security background)
   - Access level: Read access, anomaly tools, alerting

**Non-Human Actor:**
6. **Robot System**
   - Provides system call data to the platform
   - Initiates real-time data streams
   - No direct user interface

#### 2.2.2 Use Case Categories

The system provides 29 use cases organized into 7 functional categories:

**Real-time Monitoring (4 use cases)**
- UC-001: Monitor Real-time System Calls
- UC-002: View Live Dashboard
- UC-003: Receive Alerts
- UC-004: Track Robot Components

**Data Analysis (5 use cases)**
- UC-005: Analyze Historical Data
- UC-006: Generate Statistics
- UC-007: Identify Patterns
- UC-008: Compare Operational Modes
- UC-009: Analyze Component Behavior

**Anomaly Detection (4 use cases)**
- UC-010: Detect Anomalies
- UC-011: Identify Cyber Threats
- UC-012: Validate Behavior Patterns
- UC-013: Configure Thresholds

**Performance Optimization (4 use cases)**
- UC-014: Analyze Performance Metrics
- UC-015: Identify Bottlenecks
- UC-016: Generate Recommendations
- UC-017: Compare Baselines

**Reporting & Export (4 use cases)**
- UC-018: Generate Reports
- UC-019: Export Data (CSV/JSON/PDF)
- UC-020: Schedule Reports
- UC-021: Create Custom Visualizations

**System Configuration (4 use cases)**
- UC-022: Configure System Settings
- UC-023: Manage User Accounts
- UC-024: Set Up Data Collection
- UC-025: Configure Storage

**Data Collection (4 use cases)**
- UC-026: Collect System Call Data
- UC-027: Import CSV Files
- UC-028: Process Robot Streams
- UC-029: Validate Data Quality

#### 2.2.3 Relationship Types

The diagram uses three types of relationships:

**1. Association** (solid line)
- Connects actors to use cases they can perform
- Example: System Administrator → Configure System Settings

**2. Include** (dashed arrow with <<include>>)
- Indicates a use case that is always part of another
- Example: "Monitor Real-time System Calls" includes "Collect System Call Data"

**3. Extend** (dashed arrow with <<extend>>)
- Indicates optional behavior that may occur
- Example: "Detect Anomalies" may extend to "Identify Cyber Threats"

#### 2.2.4 Use Case Diagram Location

The complete use case diagram is available in:
- `stage2/uml_diagrams/use_case_diagram.puml` (PlantUML source)

---

### 2.3 Sequence Diagrams

Sequence diagrams show how objects interact in a particular scenario over time. They illustrate the flow of messages between components in specific use cases. We have created three detailed sequence diagrams covering the most critical system operations.

#### 2.3.1 Sequence Diagram 1: Real-Time System Call Monitoring

**Scenario**: A system administrator opens the real-time monitoring dashboard to observe live robot activity.

**Actors**: System Administrator  
**Components Involved**: Dashboard, RESTAPIController, DataService, RobotDataCollector, SystemCallParser, DatabaseManager, AnomalyDetector, VisualizationEngine, Robot System

**Flow**:

1. **Initialization Phase**
   - Administrator opens monitoring dashboard
   - Dashboard requests connection to robot
   - DataService initiates RobotDataCollector
   - RobotDataCollector establishes TCP connection to robot
   - Connection status returned to dashboard

2. **Real-Time Data Collection Loop** (repeating every 100ms)
   - Robot streams system call data
   - RobotDataCollector receives and forwards to SystemCallParser
   - Parser validates and structures the data
   - Data passed to DataService
   - DataService stores data in database
   - DataService checks for anomalies via AnomalyDetector
   - If anomaly detected: Alert sent to dashboard
   - If normal: Continue processing

3. **Dashboard Update**
   - Administrator requests dashboard refresh
   - Dashboard queries recent system calls via API
   - DataService retrieves from database
   - Results returned as JSON
   - VisualizationEngine creates charts
   - Updated dashboard displayed to administrator

4. **User Interaction**
   - Administrator clicks "View Details" for a component
   - API requests component analysis
   - DataService queries component-specific data
   - Analysis performed (frequency, distribution, metrics)
   - Results visualized and displayed

**Key Characteristics**:
- Real-time throughput: 11,200 system calls/second
- Update frequency: 10Hz (every 100ms)
- Latency target: < 100ms from robot to dashboard
- Anomaly detection: Inline with data processing

**Diagram Location**: `stage2/uml_diagrams/sequence_diagram_1_realtime_monitoring.puml`

---

#### 2.3.2 Sequence Diagram 2: Historical Data Analysis and Pattern Recognition

**Scenario**: A data analyst performs historical analysis on system call data using the LSTM pattern recognition model.

**Actors**: Data Analyst  
**Components Involved**: Dashboard, RESTAPIController, AnalysisService, PatternRecognizer, LSTMModel, SystemCallRepository, DataProcessor, ReportGenerator, VisualizationEngine

**Flow**:

1. **Analysis Request**
   - Analyst selects "Historical Analysis" on dashboard
   - Analyst specifies parameters:
     - Date range (e.g., August 1-5, 2024)
     - Robot component (e.g., global_planner)
     - Analysis type (e.g., pattern recognition)
   - Request submitted to API

2. **Data Retrieval**
   - AnalysisService requests data from SystemCallRepository
   - Repository queries database for specified time range and component
   - Returns large dataset (e.g., 22,672 records for global_planner)

3. **Data Processing**
   - DataProcessor cleans the raw data:
     - Removes duplicates
     - Handles missing values
     - Normalizes timestamps
     - Categorizes system calls
   - Returns cleaned DataFrame

4. **Pattern Recognition (LSTM)**
   - PatternRecognizer prepares sequences for LSTM input
   - LSTMModel performs inference:
     - Forward pass through encoder-decoder network (2 layers, 128 neurons, dropout 0.2)
     - Generates predictions for each sequence
     - Identifies patterns and anomalies
   - Returns pattern analysis results

5. **Statistical Analysis**
   - DataProcessor computes statistics:
     - Mean execution time: 86 microseconds
     - Call frequency: 11,200 calls/second
     - Distribution by type (clock_gettime 46%, futex 22%, etc.)
     - Component interactions
   - Returns statistical report

6. **Visualization**
   - VisualizationEngine creates multiple charts:
     - Time series: call frequency over time
     - Pie chart: system call distribution
     - Bar chart: component comparison
     - Heatmap: temporal patterns
     - Box plot: execution time distribution
   - Dashboard displays all visualizations

7. **Report Generation**
   - Analyst clicks "Generate Report"
   - ReportGenerator creates PDF document with sections:
     - Executive summary
     - Data overview
     - Pattern analysis
     - Statistical findings
     - Anomaly detection results
     - Performance metrics
     - Recommendations
   - Exports charts as PNG images
   - Compiles complete PDF report
   - Download link provided to analyst

8. **Comparative Analysis** (Optional)
   - Analyst selects "Compare Modes"
   - Specifies modes to compare (e.g., autonomous vs. manual)
   - System retrieves data for both modes in parallel
   - DataProcessor compares datasets:
     - Autonomous: More planning activity, 11,200 calls/sec
     - Manual: Reduced planning, more I/O, 12,700 calls/sec
   - VisualizationEngine creates side-by-side comparison charts
   - Results displayed to analyst

**Key Characteristics**:
- Dataset size: Up to 1.2M+ system calls
- LSTM inference time: < 30 seconds for full dataset
- Pattern confidence: 94%+ accuracy
- Export formats: PDF, CSV, JSON

**Diagram Location**: `stage2/uml_diagrams/sequence_diagram_2_data_analysis.puml`

---

#### 2.3.3 Sequence Diagram 3: CSV Data Import and Processing

**Scenario**: A system administrator imports a large CSV file containing historical system call data.

**Actors**: System Administrator  
**Components Involved**: Dashboard, RESTAPIController, DataService, CSVFileImporter, SystemCallParser, DataProcessor, SystemCallRepository, DatabaseManager, CacheManager

**Flow**:

1. **File Upload**
   - Administrator navigates to "Import Data" section
   - Selects CSV file (e.g., test-gps-no-cam.csv, 95.6 MB)
   - Clicks "Upload"
   - File sent to API via multipart form data

2. **File Validation**
   - API validates file:
     - Checks file extension (.csv)
     - Verifies file size (< 500 MB limit)
     - Confirms file is not empty
   - If valid: Proceed to import
   - If invalid: Return error message

3. **File Processing Initialization**
   - DataService initiates CSVFileImporter
   - Importer opens file stream
   - Reads header row
   - Validates CSV structure (13 columns required)
   - Extracts file metadata:
     - Size: 95.6 MB
     - Estimated records: 632,986
   - Sends progress update to dashboard (10%)

4. **Data Parsing Loop** (batch processing, 10,000 records at a time)
   
   For each batch:
   
   a. **Reading & Parsing**
   - Importer reads next 10,000 rows
   - SystemCallParser processes each row:
     - Parses 13 columns:
       1. Epoch Time → double
       2-5. Time components → integers
       6. Node → string
       7. PID → integer
       8. System Call → string
       9-10. Unfinished/Resumed → strings
       11. Execution Time → double
       12. Return Code → integer
       13. Arguments → string
   - Creates SystemCallData objects
   - Validates data integrity

   b. **Data Cleaning**
   - DataProcessor cleans the batch:
     - Removes duplicates
     - Handles missing values (e.g., PID = -1 if missing)
     - Normalizes timestamps
     - Categorizes system calls into known types
   - Returns processed data

   c. **Data Storage**
   - SystemCallRepository saves batch to database
   - DatabaseManager begins transaction
   - Inserts all 10,000 records
   - Commits transaction
   - Returns confirmation

   d. **Cache Management**
   - CacheManager invalidates related cache entries
   - Ensures fresh data on next query

   e. **Progress Update**
   - Importer reports progress to DataService
   - DataService updates API
   - Dashboard updates progress bar
   - Administrator sees: "130,000 / 632,986 records (20%)"

   Loop continues until all data processed...

5. **Import Completion**
   - Importer closes file stream
   - Generates import summary:
     - Total records: 632,986
     - Successfully imported: 632,850
     - Errors: 136 (validation failures)
     - Duration: 45 seconds
     - Processing rate: 14,063 records/second
   - Summary returned to dashboard

6. **Success Display**
   - Dashboard shows success message:
     - "✓ Import complete! 632,850 records imported"
   - Displays detailed summary statistics:
     - System call distribution
     - Top components
     - Error details (if any)

7. **Post-Import Analysis** (Optional)
   - Administrator clicks "View Import Summary"
   - API retrieves import metadata from database
   - Displays comprehensive statistics:
     - File details
     - Record counts
     - Success rate: 99.98%
     - System call breakdown
     - Component activity
     - Duration and performance metrics

**Key Characteristics**:
- Maximum file size: 500 MB
- Batch size: 10,000 records
- Processing rate: 14,000+ records/second
- Validation: Schema and data integrity checks
- Error handling: Logs errors but continues processing
- Progress tracking: Real-time updates to UI

**Diagram Location**: `stage2/uml_diagrams/sequence_diagram_3_data_import.puml`

---

### 2.4 System Architecture Summary

The UML diagrams collectively define a robust, scalable system architecture:

**Key Architectural Principles:**

1. **Separation of Concerns**: Each layer has distinct responsibilities
2. **Modularity**: Components can be developed, tested, and deployed independently
3. **Scalability**: Horizontal scaling through containerization and load balancing
4. **Performance**: Caching, batching, and asynchronous processing
5. **Maintainability**: Clear interfaces, design patterns, and documentation
6. **Security**: Authentication, authorization, and data protection throughout

**Technology Alignment:**
- **Backend**: Python Flask implements Service and Storage layers
- **Frontend**: React implements UI Layer
- **Database**: PostgreSQL provides persistent storage
- **Cache**: Redis provides in-memory caching and pub/sub
- **ML**: TensorFlow implements LSTM models
- **API**: RESTful endpoints and WebSockets for communication

---

## 3. Low-Fidelity Prototype

Low-fidelity prototypes are simplified wireframes that focus on layout, functionality, and user flow rather than visual design. They allow stakeholders to understand the user interface before significant development effort is invested.

### 3.1 Prototype Philosophy

Our low-fidelity prototypes follow these principles:

- **Simple aesthetics**: Black, white, and gray only; no colors or images
- **Clear layout**: Focus on information hierarchy and component placement
- **Functional elements**: Show buttons, forms, tables, and charts
- **Realistic content**: Use actual data from the DoD SAFE dataset
- **Interactive elements**: Clearly labeled buttons and navigation

The goal is to answer: "What does the user see?" and "How do they navigate?" - not "What does it look like?"

### 3.2 Prototype Screens

We have created five HTML-based low-fidelity prototype screens covering the primary user interfaces:

#### 3.2.1 Screen 1: Main Dashboard

**Purpose**: Provide an at-a-glance view of system health and activity

**File**: `stage2/prototypes/01_main_dashboard.html`

**Key Elements**:
- **Header**: Application title and user menu
- **Sidebar Navigation**: Links to all major sections (Dashboard, Real-time Monitor, Historical Analysis, Component View, Anomaly Detection, Reports, Data Import, Settings)
- **Statistics Cards**: Four key metrics
  - Total System Calls: 1,234,567
  - Active Components: 10
  - Calls per Second: 11,200
  - Anomalies Detected: 0
- **System Call Distribution Chart**: Bar chart showing:
  - clock_gettime: 46%
  - futex: 22%
  - write: 8%
  - select: 6.6%
  - recvfrom: 5.7%
  - read: 5.1%
- **Robot Component Activity Chart**: Bar chart showing:
  - global_planner: 56.6%
  - front_ouster: 25.7%
  - os_cloud_node: 11.2%
  - Others: 6.5%
- **Recent Activity Feed**: Live stream of recent system calls with timestamps
- **Action Buttons**: Export Data, Generate Report, Configure Alerts, Settings

**User Flow**:
1. User logs in → Arrives at main dashboard
2. Quickly scans statistics cards for system health
3. Views charts for distribution insights
4. Checks recent activity for any issues
5. Clicks sidebar item to navigate to detailed view

---

#### 3.2.2 Screen 2: Real-Time Monitor

**Purpose**: Display live system call stream for detailed monitoring

**File**: `stage2/prototypes/02_realtime_monitor.html`

**Key Elements**:
- **Status Bar**: Connection status ("● CONNECTED - Robot: UMD-Husky-01 | Mode: Autonomous") with system health badge
- **Control Panel**:
  - Play/Pause monitoring buttons
  - Export Stream button
  - Auto-scroll checkbox
  - Refresh rate selector (100ms, 250ms, 500ms, 1000ms)
- **Metrics Grid**:
  - Current Call Rate: 11,247 calls/second
  - Avg Execution Time: 86μs
  - Active Processes: 10
- **Live Graph**: Line chart showing system call frequency over last 60 seconds
- **System Call Stream Table**: Scrolling table with columns:
  - Timestamp (HH:MM:SS.mmm)
  - Component (node name)
  - PID (process ID)
  - System Call (call type)
  - Details (arguments and return values)
- **Filter Box**: Search/filter by component name

**User Flow**:
1. User navigates to Real-time Monitor from sidebar
2. System automatically starts streaming data
3. User observes live call stream in table
4. User can pause to inspect specific calls
5. User filters by component to focus on specific subsystem
6. User exports stream for offline analysis

**Real-Time Behavior**:
- Table updates 10 times per second (every 100ms)
- Auto-scrolls to show latest calls
- Metrics update in real-time
- Graph animates left-to-right showing timeline

---

#### 3.2.3 Screen 3: Component Analysis

**Purpose**: Deep-dive into individual robot component behavior

**File**: `stage2/prototypes/03_component_analysis.html`

**Key Elements**:
- **Breadcrumb Navigation**: Dashboard > Component View > global_planner
- **Component Selector**: Chips for quick switching between components (global_planner, front_ouster, os_cloud_node, local_planning, etc.)
- **Statistics Grid**: Four key metrics for selected component
  - Total System Calls: 22,672 (56.6% of all calls)
  - Avg Execution Time: 78μs (9% faster than average)
  - Call Frequency: 6,341 calls/second
  - Active Processes: 3 (PIDs: 1234, 1235, 1236)
- **Pie Chart**: System call distribution for this component
  - clock_gettime: 46%
  - futex: 22%
  - write: 14%
  - others: 18%
- **Timeline Chart**: Call frequency over last 60 seconds
- **Data Table**: Top system calls by frequency with columns:
  - System Call name
  - Count
  - Percentage
  - Avg Execution Time
  - Total Time
  - Actions (View Details button)
- **Performance Insights Panel**: Color-coded messages:
  - ✓ Normal Behavior (green)
  - ⚠ Optimization Opportunity (yellow)
  - ℹ Information (blue)
- **Action Buttons**: Generate Report, Export Data (CSV), Set Alert Threshold, Compare with Baseline

**User Flow**:
1. User selects component from selector chips
2. Views statistics and charts specific to that component
3. Identifies performance bottlenecks in data table
4. Reads AI-generated insights and recommendations
5. Exports data or generates report for documentation
6. Compares current performance with historical baseline

**Insights Example**:
- "✓ Normal Behavior: System call patterns match expected behavior for global path planning component"
- "⚠ Optimization Opportunity: High frequency of clock_gettime calls (46%) suggests potential for timestamp caching"

---

#### 3.2.4 Screen 4: Anomaly Detection Dashboard

**Purpose**: Monitor and investigate detected anomalies using LSTM model

**File**: `stage2/prototypes/04_anomaly_detection.html`

**Key Elements**:
- **Status Banner**: "● LSTM MODEL ACTIVE | Last scan: 2 minutes ago | Next scan: in 58 seconds" with Scan Now and Configure Model buttons
- **Alert Summary Grid**: Four statistics cards
  - Critical Anomalies: 0 (last 24 hours)
  - Warnings: 3 (require attention)
  - Info Alerts: 7 (minor deviations)
  - Pattern Confidence: 94% (model accuracy)
- **LSTM Model Status Panel**: Six metrics
  - Model Version: v2.4 (DoD SAFE LSTM Encoder-Decoder)
  - Training Data: 1.2M system calls from 6 datasets
  - Dropout Rate: 0.2 (regularization)
  - Hidden Layers: 2 (128 neurons each)
  - Patterns Learned: 47 distinct behaviors
  - Avg Detection Time: 23ms per sequence
- **Visualization Grid**:
  - Anomaly Trend chart (last 7 days)
  - Anomaly Distribution pie chart (by type)
- **Anomaly List**: Cards for each detected anomaly with:
  - Title and severity badge (CRITICAL/WARNING/INFO)
  - Detection timestamp, component, confidence %
  - Description of anomaly
  - Pattern Details section (expandable)
  - Action buttons: View Full Details, Mark as False Positive, Create Alert Rule, Run Diagnostics

**Example Anomaly Cards**:

1. **WARNING**: "Unusual System Call Sequence Detected"
   - Detected: 2025-10-13 10:15:32
   - Component: global_planner
   - Confidence: 87%
   - Description: Pattern deviates from learned normal behavior
   - Pattern: Expected "clock_gettime → futex → write", Observed "futex (x15) → clock_gettime (x89) → write (x2)"
   - Potential Causes: Resource contention, deadlock prevention, or adaptive behavior

2. **WARNING**: "Elevated Execution Time"
   - Detected: 2025-10-13 09:42:18
   - Component: front_ouster
   - Confidence: 92%
   - Description: Execution times significantly higher than baseline
   - Metrics: Baseline 86μs → Current 245μs (+185%)
   - Impact: May affect LiDAR data processing throughput

- **Detection Settings Panel**: Configuration options
  - Sensitivity Level: Low/Medium/High (70%/80%/90% confidence)
  - Scan Interval: 30s/1min/5min/10min
  - Save Settings, Retrain Model, Model Performance Report buttons

**User Flow**:
1. User opens Anomaly Detection dashboard
2. Views summary of alerts at top
3. Reviews LSTM model status and performance
4. Scrolls through anomaly cards
5. Clicks "View Full Details" for an anomaly of interest
6. Reviews pattern details and confidence
7. Decides on action:
   - Investigate further → Run Diagnostics
   - False alarm → Mark as False Positive
   - Important pattern → Create Alert Rule
8. Adjusts detection settings if needed
9. Monitors trends over time in visualization charts

**Color Coding**:
- **Critical** (red): Immediate action required
- **Warning** (yellow): Should be investigated
- **Info** (blue): Minor deviation, FYI

---

#### 3.2.5 Screen 5: Data Import Interface

**Purpose**: Upload and process CSV system call data files

**File**: `stage2/prototypes/05_data_import.html`

**Key Elements**:
- **Upload Section**: Large drag-and-drop area with:
  - File icon
  - "Drop CSV files here or click to browse"
  - Format requirements: "System call CSV with 13 columns, Max 500 MB"
  - Browse Files button
- **Format Requirements Panel**: Detailed specification
  - Lists all 13 required columns with data types
  - Tip: "Use syscall_bagreader_script.py for automatic format compliance"
- **Currently Processing Section**: Active import with:
  - File name: test-gps-no-cam.csv
  - Metadata: Size (95.6 MB), Records (~632,986), Start time
  - Progress bar: 68% Complete (430,000 / 632,986 records)
  - Processing metrics: Estimated time remaining, Processing rate (14,063 records/sec)
  - Control buttons: Pause, Cancel
- **Import Statistics Grid**: Three metrics
  - Total Records Imported: 430,031 (last 24 hours)
  - Files Processed: 5 (this session)
  - Success Rate: 99.97% (data quality)
- **Import History Table**: Columns
  - File Name
  - Size
  - Records
  - Date Imported
  - Duration
  - Status (✓ SUCCESS badge)
  - Actions: [View] [Export] [Delete]
- **Import Summary Panel**: Detailed breakdown of latest import
  - File details (name, size, record count)
  - Success rate and error count
  - System call distribution (clock_gettime 46%, futex 22%, etc.)
  - Top components (global_planner 56.6%, front_ouster 25.7%, etc.)
- **Action Buttons**: Import Another File, View All Data, Import Settings, View Import Log

**User Flow**:
1. User navigates to Data Import from sidebar
2. User drags CSV file to upload area (or clicks Browse)
3. System validates file format
4. Import begins automatically
5. User monitors real-time progress bar
6. User can pause/cancel if needed
7. Upon completion, user reviews import summary
8. User checks history table to verify past imports
9. User clicks "View All Data" to begin analysis

**Import Process**:
1. File validation (format, size, columns)
2. Batch processing (10,000 records at a time)
3. Data cleaning and normalization
4. Database insertion
5. Cache invalidation
6. Summary generation

**Error Handling**:
- Invalid file format → Clear error message
- Duplicate data → Skip or update existing records
- Validation failures → Log errors but continue processing
- Partial import → Show success count and error log

---

### 3.3 Design Rationale

**Why Low-Fidelity?**

At this stage of the project, we prioritize:
1. **Functionality over aesthetics** - Ensure all features are represented
2. **User flow validation** - Confirm navigation makes sense
3. **Stakeholder feedback** - Easy to modify based on input
4. **Quick iteration** - Can update prototypes in minutes
5. **Focus on substance** - No distractions from colors/fonts/images

**Transition to High-Fidelity**:

In Stage 3 (implementation), these prototypes will evolve to:
- Modern color scheme (blues, grays for cyber/tech theme)
- Professional typography (system fonts for performance)
- Icons and visual elements (Material Icons)
- Smooth animations and transitions (React Spring)
- Responsive design (mobile-friendly layouts)
- Accessibility features (WCAG 2.1 AA compliance)

### 3.4 User Experience Principles

Our UI design follows established UX best practices:

1. **Information Hierarchy** - Most important data at top
2. **Consistency** - Similar elements look and behave similarly
3. **Progressive Disclosure** - Details available on demand
4. **Feedback** - System always indicates current state
5. **Error Prevention** - Validation and confirmation before destructive actions
6. **Efficiency** - Keyboard shortcuts and quick actions for power users

### 3.5 Accessibility Considerations

Even in low-fidelity, we've designed for accessibility:
- Clear labels for all controls
- Logical tab order for keyboard navigation
- Color not used as sole indicator (text labels too)
- Adequate spacing between clickable elements
- Semantic HTML structure

### 3.6 Prototype Location

All prototype HTML files are in: `stage2/prototypes/`

To view:
1. Open any HTML file in a web browser
2. Files are self-contained (no external dependencies)
3. Best viewed on desktop/laptop (1400px+ width)

---

## 4. Implementation Plan

This section details the technical approach, timeline, and resources required to build the Robot System Call Analysis Platform.

### 4.1 Testbed

#### 4.1.1 Development Hardware

**Developer Workstations** (5 team members):
- **Minimum Specifications**:
  - CPU: Quad-core (Intel i5 / AMD Ryzen 5 or better)
  - RAM: 16GB (32GB recommended for ML work)
  - Storage: 256GB SSD minimum
  - GPU: Optional - NVIDIA with CUDA for faster LSTM training
- **Operating Systems**:
  - Primary: macOS or Linux (Ubuntu 22.04)
  - Windows: Via WSL2 (Windows Subsystem for Linux)

**Development Server**:
- **Specifications**:
  - 8 vCPUs
  - 32GB RAM
  - 500GB SSD
  - Ubuntu 22.04 LTS
- **Options**:
  - Option A: University server (if available)
  - Option B: AWS EC2 t3.2xlarge (~$150/month)
  - Option C: Local server (repurposed hardware)

#### 4.1.2 Production Infrastructure

**Cloud Deployment (AWS)**:
- **Application Server**: EC2 t3.xlarge (4 vCPUs, 16GB RAM)
- **Database**: RDS PostgreSQL db.t3.large (2 vCPUs, 8GB RAM)
- **Cache**: ElastiCache Redis (cache.t3.medium)
- **Storage**: S3 bucket for file uploads and backups
- **CDN**: CloudFront for static assets
- **Load Balancer**: Application Load Balancer (for future scaling)

**Alternative Deployment Options**:
- **Platform-as-a-Service**: Heroku, Railway, or DigitalOcean App Platform
- **Self-Hosted**: University data center or on-premises servers
- **Hybrid**: Database on-premises, application in cloud

#### 4.1.3 Development Environment Setup

**Each developer will have**:
- Local PostgreSQL 15 instance
- Local Redis 7 instance
- Python 3.11 virtual environment
- Node.js 20 runtime
- Docker Desktop (for containerization)
- Git (version control)

**Shared Resources**:
- GitHub repository (code hosting)
- Development server (integration testing)
- Staging environment (pre-production testing)
- Shared database (test data)

---

### 4.2 Programming Languages

#### 4.2.1 Backend: Python 3.11+

**Rationale**:
- **Data Science Ecosystem**: Best support for pandas, numpy, TensorFlow
- **Rapid Development**: Concise syntax, extensive libraries
- **Machine Learning**: First-class support for LSTM models
- **Community**: Largest data science community
- **Team Expertise**: Team has Python experience

**Core Frameworks & Libraries**:

**Web Framework**:
- **Flask 3.0+**: Lightweight, flexible, perfect for REST APIs

**Data Processing**:
- **pandas 2.0+**: DataFrame operations, CSV parsing
- **numpy 1.24+**: Numerical computations
- **scipy 1.11+**: Statistical analysis

**Machine Learning**:
- **TensorFlow 2.15+**: LSTM model implementation
- **Keras 3.0+**: High-level neural network API
- **scikit-learn 1.3+**: Preprocessing, metrics

**Database**:
- **SQLAlchemy 2.0+**: ORM for database operations
- **psycopg2**: PostgreSQL adapter
- **redis-py**: Redis client

**API & Communication**:
- **Flask-RESTful**: REST API framework
- **Flask-SocketIO**: WebSocket support
- **Flask-CORS**: Cross-origin resource sharing
- **Celery 5.3+**: Asynchronous task queue

**Testing**:
- **pytest**: Unit and integration testing
- **pytest-cov**: Code coverage reporting
- **faker**: Test data generation

**Utilities**:
- **python-dotenv**: Environment variables
- **click**: CLI tools
- **loguru**: Logging

#### 4.2.2 Frontend: JavaScript (React 18)

**Rationale**:
- **Component-Based**: Modular, reusable UI components
- **Large Ecosystem**: Extensive library support
- **Performance**: Virtual DOM for efficient updates
- **Team Knowledge**: Widely used, good learning resources
- **Industry Standard**: Most popular frontend framework

**Core Technologies**:

**JavaScript Framework**:
- **React 18**: UI component library
- **TypeScript 5+**: Type safety (optional but recommended)

**Build Tools**:
- **Vite 5.0+**: Fast dev server, optimized builds

**State Management**:
- **Redux Toolkit**: Global state management
- **React Query**: Server state caching

**UI Libraries**:
- **Material-UI (MUI) 5+**: Component library
- **Chart.js 4.0+**: Data visualization
- **React-Chartjs-2**: React wrapper for Chart.js
- **D3.js 7.0+**: Advanced custom visualizations

**HTTP & WebSockets**:
- **Axios**: HTTP client
- **Socket.io-client**: Real-time communication

**Utilities**:
- **React Router 6+**: Client-side routing
- **date-fns**: Date manipulation
- **lodash**: Utility functions

**Testing**:
- **Jest**: Unit testing
- **React Testing Library**: Component testing
- **Cypress**: End-to-end testing

#### 4.2.3 Database: SQL (PostgreSQL)

**Rationale**:
- **Relational Model**: Our data has clear relationships
- **ACID Compliance**: Data integrity critical for security analysis
- **Performance**: Excellent for time-series data
- **JSON Support**: Flexible schema for complex data
- **Mature**: Battle-tested, reliable

**Database**: PostgreSQL 15+

#### 4.2.4 Configuration & Deployment: YAML, Dockerfile

**Docker** for containerization
**YAML** for configuration files
**Bash** for deployment scripts

---

### 4.3 Development Tools/Devices

#### 4.3.1 Integrated Development Environments (IDEs)

**VS Code** (Primary IDE for all team members):
- **Extensions**:
  - Python (Pylance, Black formatter)
  - ESLint (JavaScript linting)
  - Prettier (code formatting)
  - Docker
  - GitLens (Git visualization)
  - REST Client (API testing)
- **Why**: Free, lightweight, excellent extensions, cross-platform

**PyCharm Professional** (Optional for Python work):
- **Benefits**: Superior Python refactoring, debugging, database tools
- **Availability**: Free with student license

#### 4.3.2 Version Control

**Git + GitHub**:
- **Repository**: https://github.com/[team-repo]/robot-analysis-platform
- **Branch Strategy**: GitFlow
  - `main`: Production-ready code
  - `develop`: Integration branch
  - `feature/*`: Feature development
  - `bugfix/*`: Bug fixes
  - `release/*`: Release preparation
- **Workflow**:
  - Feature branches from `develop`
  - Pull requests for code review
  - Squash merge to `develop`
  - Merge `develop` to `main` for releases

#### 4.3.3 API Development & Testing

**Postman**:
- API endpoint testing
- Collection of all endpoints
- Automated tests
- Team-shared collections

**Swagger/OpenAPI**:
- API documentation
- Interactive API explorer
- Auto-generated from code

#### 4.3.4 Database Management

**DBeaver** (Universal database tool):
- GUI for PostgreSQL
- Query builder
- ER diagrams
- Data import/export

**Redis Commander** (Redis GUI):
- Visualize cache contents
- Monitor key expiration
- Debugging

#### 4.3.5 Containerization & Orchestration

**Docker Desktop**:
- Container runtime
- Multi-container development environment
- Image building

**Docker Compose**:
- Orchestrate multiple containers (backend, frontend, database, cache)
- One-command development environment startup

#### 4.3.6 CI/CD Pipeline

**GitHub Actions**:
- Automated testing on pull requests
- Code quality checks (linting, formatting)
- Security scanning
- Automated deployment

**Example Workflow**:
```yaml
on: [pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - Checkout code
      - Setup Python
      - Install dependencies
      - Run pytest
      - Upload coverage report
```

#### 4.3.7 Monitoring & Logging

**Prometheus** (Metrics collection):
- Application performance metrics
- System resource usage
- Custom business metrics

**Grafana** (Metrics visualization):
- Real-time dashboards
- Alert management
- Historical analysis

**ELK Stack** (Optional - Centralized logging):
- **Elasticsearch**: Log storage and search
- **Logstash**: Log processing
- **Kibana**: Log visualization

#### 4.3.8 Communication & Project Management

**Slack** (Team communication):
- Daily standups
- Quick questions
- GitHub integration for notifications

**Jira** or **GitHub Projects** (Task tracking):
- Sprint planning
- Backlog management
- Burndown charts

**Google Drive** (Documentation):
- Meeting notes
- Design documents
- Shared resources

#### 4.3.9 Machine Learning Tools

**Jupyter Notebook**:
- Exploratory data analysis
- LSTM model experimentation
- Visualization prototyping

**TensorBoard**:
- Model training visualization
- Performance metrics
- Hyperparameter tuning

---

### 4.4 Timeline

#### 4.4.1 Development Schedule (12 Weeks)

**Week 1-2: Foundation & Setup**

*Objectives*: Establish development environment, database, and project structure

*Tasks*:
- Set up Git repository with branch strategy
- Configure local development environments (all team members)
- Install PostgreSQL, Redis, Python, Node.js
- Create Docker development environment (docker-compose.yml)
- Initialize Flask backend skeleton
- Initialize React frontend skeleton (Vite + React)
- Set up CI/CD pipeline (GitHub Actions basics)
- Design and implement database schema
- Create SQLAlchemy models
- Write database migration scripts (Alembic)
- Create seed data for testing
- Unit tests for models

*Deliverables*:
- [ ] Git repository ready
- [ ] All team members' environments working
- [ ] Database schema implemented
- [ ] Docker compose file for dev environment
- [ ] Basic CI/CD pipeline running
- [ ] Initial documentation (README, setup guide)

*Team Assignments*:
- **John**: DevOps setup, CI/CD, coordination
- **Noah**: Backend skeleton, Flask configuration
- **Joseph**: Database schema design, seed data creation
- **Omotoyosi**: Frontend skeleton, component library selection
- **Delphin**: Documentation, setup guides

---

**Week 3-4: Data Processing Backend**

*Objectives*: Implement CSV import, data parsing, and LSTM model integration

*Tasks*:
- Implement `CSVFileImporter` class
- Implement `SystemCallParser` class
- Data validation logic (schema checking)
- Error handling and logging framework
- Progress tracking for long-running imports
- API endpoints: POST /api/data/import, GET /api/data/imports
- Set up TensorFlow environment
- Load pre-trained LSTM model from DoD SAFE dataset
- Implement `LSTMModel` class (inference only initially)
- Implement `PatternRecognizer` class
- Implement `AnomalyDetector` class
- API endpoints: POST /api/analysis/detect-anomalies
- Model performance testing with sample data
- Unit tests for all data processing classes
- Integration tests for full import pipeline

*Deliverables*:
- [ ] CSV import working (tested with all 6 dataset files)
- [ ] LSTM model loaded and performing inference
- [ ] Anomaly detection functional
- [ ] API endpoints for import and analysis
- [ ] Test coverage > 70% for new code

*Team Assignments*:
- **Noah**: API endpoints, Flask routes, request handling
- **Joseph**: CSV import, data parsing, LSTM integration, anomaly detection
- **Omotoyosi**: File upload UI component
- **Delphin**: API documentation (Swagger)
- **John**: Testing, integration, performance benchmarks

---

**Week 5-6: Database Operations & API Layer**

*Objectives*: Complete REST API, implement repository pattern, add real-time features

*Tasks*:
- Implement `SystemCallRepository` class
- Implement `DatabaseManager` class
- Create REST API endpoints:
  - GET /api/system-calls (with pagination, filtering)
  - GET /api/system-calls/:id
  - GET /api/components (list all robot components)
  - GET /api/components/:id
  - GET /api/components/:id/analysis (detailed component stats)
  - GET /api/anomalies (with filters)
  - GET /api/anomalies/:id
- Implement WebSocket support (Flask-SocketIO)
- Real-time data streaming endpoint (ws://api/stream)
- Implement caching layer (Redis)
- Cache frequently accessed data (recent system calls, component summaries)
- Cache invalidation on new data
- API performance optimization:
  - Database indexing
  - Query optimization
  - Response compression
- Rate limiting (prevent API abuse)
- Authentication system:
  - User registration
  - Login (JWT tokens)
  - Role-based access control (admin, analyst, engineer, viewer)
- Unit tests for repositories and API endpoints
- Integration tests for WebSocket connections
- API documentation complete (Swagger/OpenAPI)

*Deliverables*:
- [ ] Complete REST API (all endpoints functional)
- [ ] WebSocket real-time streaming working
- [ ] Redis caching implemented
- [ ] Authentication and authorization working
- [ ] API documentation published
- [ ] Performance targets met (< 200ms response time)

*Team Assignments*:
- **Noah**: Core API endpoints, WebSocket implementation
- **Joseph**: Repository pattern, database query optimization
- **Omotoyosi**: Begin API integration in frontend
- **Delphin**: Comprehensive API documentation
- **John**: Authentication system, testing, monitoring setup

---

**Week 7-8: Frontend Dashboard Implementation**

*Objectives*: Build all five main UI views with data visualization

*Tasks*:
- Set up React project structure (feature-based organization)
- Implement routing (React Router)
- Create reusable components:
  - Header with navigation
  - Sidebar menu
  - Statistics card
  - Data table (with sorting, filtering, pagination)
  - Chart wrapper components
- Implement state management (Redux Toolkit + React Query)
- **Screen 1: Main Dashboard**
  - Statistics cards (4)
  - Bar charts (system call distribution, component activity)
  - Recent activity feed
  - Navigation sidebar
- **Screen 2: Real-Time Monitor**
  - WebSocket connection to backend
  - Live metrics (calls/second, execution time)
  - Real-time scrolling table
  - Live line chart
  - Pause/resume controls
- **Screen 3: Component Analysis**
  - Component selector
  - Component statistics
  - Pie chart (call distribution)
  - Timeline chart
  - Data table (top calls)
  - Performance insights
- **Screen 4: Anomaly Detection**
  - Anomaly summary cards
  - LSTM model status panel
  - Anomaly list with cards
  - Severity color coding
  - Action buttons
- **Screen 5: Data Import**
  - File upload (drag-and-drop)
  - Progress bar
  - Import history table
  - Import summary
- Integrate Chart.js and React-Chartjs-2
- Implement responsive design (desktop-first, then mobile)
- Loading states and error handling
- Form validation
- Unit tests for components (Jest + React Testing Library)

*Deliverables*:
- [ ] All 5 main views implemented and functional
- [ ] Data visualization working (charts display real data from API)
- [ ] Real-time updates working (WebSocket integration)
- [ ] Responsive design (works on tablets and desktops)
- [ ] Component test coverage > 60%

*Team Assignments*:
- **Omotoyosi**: UI components, styling, layout, UX refinement
- **Noah**: React state management, API integration, WebSocket client
- **Joseph**: Chart components, data transformation for visualization
- **Delphin**: User help system, tooltips, documentation
- **John**: User acceptance testing, feedback collection

---

**Week 9-10: Advanced Features & Refinement**

*Objectives*: Add reporting, export, and advanced analysis features

*Tasks*:
- **Reporting System**:
  - Implement `ReportGenerator` class (backend)
  - PDF generation (using ReportLab or WeasyPrint)
  - CSV export
  - JSON export
  - Report templates (standard reports)
  - Custom report builder (select components, time range, metrics)
  - API endpoints: POST /api/reports/generate
- **Comparative Analysis**:
  - Compare operational modes (autonomous vs. manual)
  - Compare time periods (this week vs. last week)
  - Compare components (global_planner vs. front_ouster)
  - Statistical tests (t-test, ANOVA)
  - Visualization of comparisons (side-by-side charts)
- **Anomaly Detection Refinement**:
  - Email notifications for critical anomalies
  - SMS notifications (Twilio integration) (optional)
  - Alert rules (user-configurable thresholds)
  - False positive handling (user feedback loop)
  - Model retraining interface (re-train with new data)
  - Anomaly investigation tools (drill-down views)
- **Advanced UI Features**:
  - Search functionality (global search across all data)
  - Advanced filtering (multi-field filters)
  - Data export from any view
  - Keyboard shortcuts for power users
  - Dark mode (optional)
- **Performance Optimization**:
  - Frontend bundle optimization (code splitting)
  - Image optimization
  - Lazy loading for large tables
  - Virtualization for long lists
  - Backend query optimization
  - Database indexing review
- Unit and integration tests for new features

*Deliverables*:
- [ ] Report generation working (PDF, CSV, JSON)
- [ ] Comparative analysis tools functional
- [ ] Anomaly alert system operational
- [ ] Advanced UI features implemented
- [ ] Performance improvements measurable

*Team Assignments*:
- **Joseph**: Comparative analysis algorithms, statistical tests, report generation
- **Noah**: Anomaly alert system, notification integrations
- **Omotoyosi**: Advanced UI features, UX polish
- **Delphin**: User guides for new features
- **John**: Performance optimization, integration testing

---

**Week 11: Testing & Quality Assurance**

*Objectives*: Comprehensive testing, bug fixes, performance validation

*Tasks*:
- **Unit Testing**:
  - Increase backend coverage to 80%+
  - Increase frontend coverage to 70%+
  - Fix failing tests
  - Add missing test cases
- **Integration Testing**:
  - End-to-end API tests (Postman collection)
  - Database integration tests
  - LSTM model integration tests
  - WebSocket connection tests
- **End-to-End Testing** (Cypress):
  - User flow 1: Import CSV → View Dashboard → Analyze Component
  - User flow 2: Real-time monitoring → Detect anomaly → Investigate
  - User flow 3: Historical analysis → Generate report → Export data
  - User flow 4: Login → Configure settings → Create alert rule
- **Performance Testing** (Apache JMeter or Locust):
  - Load test: 1000 concurrent API requests
  - Stress test: Find breaking point
  - Endurance test: 24-hour stability test
  - Spike test: Sudden traffic increase
  - Validate targets:
    - API response time < 200ms (p95)
    - Dashboard load time < 2 seconds
    - Real-time latency < 100ms
    - Handle 11,200 system calls/second
- **Security Testing**:
  - SQL injection testing
  - XSS vulnerability testing
  - CSRF protection validation
  - Authentication bypass attempts
  - Authorization testing (role enforcement)
  - Data encryption validation
- **User Acceptance Testing** (UAT):
  - Recruit 5-10 test users (classmates, professors)
  - Provide test scenarios
  - Collect feedback
  - Prioritize fixes
- **Bug Fixing**:
  - Triage all discovered bugs (critical, high, medium, low)
  - Fix critical and high priority bugs
  - Document known issues for medium/low priority
- **Code Review**:
  - Review all code for quality
  - Refactor where needed
  - Add comments and documentation
  - Ensure consistent style

*Deliverables*:
- [ ] Test coverage targets met (80% backend, 70% frontend)
- [ ] All critical and high priority bugs fixed
- [ ] Performance targets validated
- [ ] Security vulnerabilities addressed
- [ ] UAT feedback incorporated
- [ ] Code review complete

*Team Assignments*:
- **All team members**: Testing in their respective areas
- **John**: Test coordination, UAT planning, performance testing
- **Noah**: Backend tests, security testing
- **Joseph**: Integration tests, data validation
- **Omotoyosi**: Frontend tests, E2E tests
- **Delphin**: Test documentation, bug tracking

---

**Week 12: Deployment & Documentation**

*Objectives*: Production deployment, final documentation, handoff preparation

*Tasks*:
- **Production Environment Setup**:
  - Provision AWS resources (EC2, RDS, ElastiCache, S3)
  - Configure security groups and networking
  - Set up SSL certificates (HTTPS)
  - Configure domain and DNS
  - Set up monitoring (Prometheus, Grafana)
  - Configure backups (automated daily backups)
  - Set up logging (centralized logs)
- **Database Migration**:
  - Export development/staging data
  - Import to production database
  - Verify data integrity
  - Set up database replication (optional)
- **Application Deployment**:
  - Build production Docker images
  - Push images to container registry (Docker Hub or AWS ECR)
  - Deploy backend containers
  - Deploy frontend (build + upload to S3 + CloudFront)
  - Configure environment variables
  - Run database migrations
  - Verify all services running
- **Deployment Validation**:
  - Smoke tests (basic functionality)
  - Load testing on production
  - Security scan
  - Verify monitoring and alerts
- **Documentation**:
  - **System Architecture Documentation**:
    - Component diagrams
    - Data flow diagrams
    - Deployment architecture
  - **API Documentation**:
    - Complete Swagger/OpenAPI spec
    - Example requests and responses
    - Authentication guide
  - **User Manual**:
    - Getting started guide
    - Feature walkthroughs
    - Screenshots and videos
    - FAQ section
  - **Administrator Guide**:
    - Installation instructions
    - Configuration options
    - Backup and recovery procedures
    - Troubleshooting guide
    - Security best practices
  - **Developer Guide**:
    - Setup instructions
    - Architecture overview
    - Code organization
    - Testing guide
    - Contributing guidelines
  - **Deployment Guide**:
    - Step-by-step deployment process
    - Environment configuration
    - Rollback procedures
    - Monitoring and alerting
- **Final Presentation Preparation**:
  - Create presentation slides
  - Prepare live demo
  - Rehearse presentation
  - Record demo video (backup)
- **Handoff**:
  - Transfer repository access
  - Share credentials (securely)
  - Provide contact information
  - Schedule training session (if applicable)

*Deliverables*:
- [ ] Production deployment complete and stable
- [ ] All documentation finalized and accessible
- [ ] User training completed
- [ ] Handoff documentation delivered
- [ ] Final presentation ready

*Team Assignments*:
- **Noah**: Production deployment, DevOps, backend configuration
- **Joseph**: Data migration, database optimization, backup setup
- **Omotoyosi**: User manual, UI documentation, video tutorials
- **Delphin**: Complete documentation suite, organize all docs
- **John**: Deployment coordination, final review, handoff preparation, presentation

---

#### 4.4.2 Milestone Summary

| Week | Milestone | Completion Criteria |
|------|-----------|---------------------|
| 2 | Foundation Complete | Dev environments working, database schema implemented |
| 4 | Data Processing Ready | CSV import + LSTM integration working |
| 6 | API Layer Complete | All REST endpoints + WebSocket + authentication |
| 8 | Frontend MVP | All 5 views functional with real data |
| 10 | Feature Complete | All advanced features implemented |
| 11 | Testing Complete | All tests passing, performance validated |
| 12 | Production Deployed | Live system operational, documentation complete |

#### 4.4.3 Risk Buffer

We've built in buffer time for:
- **Learning curve**: New technologies may take longer to learn
- **Integration issues**: Components may not integrate smoothly
- **Bug fixes**: More bugs than anticipated
- **Scope changes**: Requirements may evolve

If we run ahead of schedule, we'll add:
- Additional data visualizations
- Mobile-responsive design
- Advanced ML features (ensemble models)
- Performance optimizations

#### 4.4.4 Team Collaboration

**Daily Standups** (15 minutes):
- What did you do yesterday?
- What will you do today?
- Any blockers?

**Weekly Meetings** (1 hour):
- Sprint review (demo completed work)
- Sprint retrospective (what went well, what to improve)
- Sprint planning (next week's tasks)

**Bi-Weekly Stakeholder Updates**:
- Progress demonstration
- Feedback collection
- Requirement clarification

**Code Reviews**:
- All pull requests reviewed by at least one team member
- Focus on functionality, code quality, and test coverage

**Pair Programming** (as needed):
- Complex features
- Learning new technologies
- Debugging difficult issues

---

## 5. Appendices

### Appendix A: File Structure

```
robot-analysis-platform/
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── models/              # Database models
│   │   ├── repositories/        # Data access layer
│   │   ├── services/            # Business logic
│   │   ├── api/                 # REST endpoints
│   │   ├── ml/                  # LSTM model code
│   │   ├── utils/               # Helper functions
│   │   └── config.py            # Configuration
│   ├── tests/                   # Backend tests
│   ├── migrations/              # Database migrations
│   ├── requirements.txt         # Python dependencies
│   ├── Dockerfile
│   └── README.md
├── frontend/
│   ├── src/
│   │   ├── components/          # React components
│   │   ├── pages/               # Page components
│   │   ├── services/            # API clients
│   │   ├── store/               # Redux store
│   │   ├── utils/               # Helper functions
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── public/                  # Static assets
│   ├── tests/                   # Frontend tests
│   ├── package.json
│   ├── Dockerfile
│   └── README.md
├── docs/
│   ├── architecture.md
│   ├── api.md
│   ├── user-manual.md
│   └── admin-guide.md
├── docker-compose.yml           # Development environment
├── .github/
│   └── workflows/               # CI/CD pipelines
│       ├── test.yml
│       └── deploy.yml
├── README.md                    # Project README
└── LICENSE
```

### Appendix B: Technology Version Summary

| Technology | Version | Purpose |
|------------|---------|---------|
| Python | 3.11+ | Backend language |
| Flask | 3.0+ | Web framework |
| PostgreSQL | 15+ | Database |
| Redis | 7.0+ | Cache |
| TensorFlow | 2.15+ | ML framework |
| React | 18+ | Frontend framework |
| Node.js | 20+ | Frontend runtime |
| Docker | 24+ | Containerization |
| Vite | 5.0+ | Build tool |
| Chart.js | 4.0+ | Visualization |

### Appendix C: Glossary

| Term | Definition |
|------|------------|
| **Anomaly** | Unusual pattern in system call data that deviates from learned normal behavior |
| **CSV** | Comma-Separated Values - text file format for tabular data |
| **DoD SAFE** | Department of Defense System Analysis for Enhanced Security - research program |
| **LiDAR** | Light Detection and Ranging - laser-based 3D sensing technology |
| **LSTM** | Long Short-Term Memory - type of neural network for sequence data |
| **REST API** | Representational State Transfer Application Programming Interface |
| **System Call** | Request from a program to the operating system kernel |
| **UML** | Unified Modeling Language - standard for software design diagrams |
| **WebSocket** | Protocol for real-time bidirectional communication |

### Appendix D: References

1. **DoD SAFE Dataset**: System call data from UMD Husky robot (June-August 2024)
2. **LSTM Paper**: "NSSSIP 2024 - System Call Pattern Recognition Model Documentation" by Schweers
3. **Flask Documentation**: https://flask.palletsprojects.com/
4. **React Documentation**: https://react.dev/
5. **TensorFlow Documentation**: https://www.tensorflow.org/
6. **PostgreSQL Documentation**: https://www.postgresql.org/docs/
7. **Material-UI Documentation**: https://mui.com/
8. **Chart.js Documentation**: https://www.chartjs.org/

### Appendix E: Contact Information

**Project Manager**: John Heitzman  
Email: maxheitzman@gmail.com

**GitHub Repository**: [To be created]

**Project Wiki**: [GitHub Wiki]

**Issue Tracker**: [GitHub Issues]

---

## Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-10-13 | John Heitzman | Initial creation for Stage 2 submission |

---

**END OF DOCUMENT**

---

## Submission Checklist

Before submitting, verify:

- [ ] Project description (1 paragraph) ✓
- [ ] Class diagram included ✓
- [ ] Use case diagram included ✓
- [ ] Sequence diagrams included (3) ✓
- [ ] Low-fidelity prototype included (5 screens) ✓
- [ ] Implementation plan - Testbed described ✓
- [ ] Implementation plan - Programming languages justified ✓
- [ ] Implementation plan - Development tools listed ✓
- [ ] Implementation plan - Timeline provided (12 weeks) ✓
- [ ] Report formatted (letter size, 11pt, single-space) ✓
- [ ] All team members' names included ✓
- [ ] Presentation slides prepared (10-15 minutes)
- [ ] File naming: stage2_[GroupName].pdf

**Ready for submission! 🚀**

