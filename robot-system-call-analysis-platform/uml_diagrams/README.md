# UML Diagrams

This folder contains all UML diagrams for the Robot System Call Analysis Platform.

## Files

1. **class_diagram.puml** - Class diagram showing system architecture
2. **use_case_diagram.puml** - Use case diagram showing user interactions
3. **sequence_diagram_1_realtime_monitoring.puml** - Real-time monitoring sequence
4. **sequence_diagram_2_data_analysis.puml** - Historical data analysis sequence
5. **sequence_diagram_3_data_import.puml** - CSV import process sequence

## How to View/Render These Diagrams

### Option 1: Online PlantUML Editor (Easiest!)
1. Go to http://www.plantuml.com/plantuml/uml/
2. Copy the contents of any `.puml` file
3. Paste into the editor
4. The diagram will render automatically
5. Click "PNG" or "SVG" to download

### Option 2: VS Code Extension
1. Install "PlantUML" extension in VS Code
2. Install Graphviz: `brew install graphviz` (Mac) or download from https://graphviz.org/download/
3. Open any `.puml` file
4. Press `Alt+D` (or `Option+D` on Mac) to preview
5. Right-click → "Export Current Diagram" to save as PNG/SVG

### Option 3: Command Line
```bash
# Install PlantUML
brew install plantuml graphviz

# Generate PNG images
plantuml class_diagram.puml
plantuml use_case_diagram.puml
plantuml sequence_diagram_*.puml

# Generate SVG (better quality)
plantuml -tsvg class_diagram.puml
```

### Option 4: Online Tools
- **draw.io**: Import PlantUML code (File → Import → PlantUML)
- **Lucidchart**: Supports PlantUML import (paid feature)

## For Your Report

1. Render each diagram as PNG (high resolution: 300 DPI)
2. Insert into your Word/Google Docs report
3. Add captions explaining each diagram

## Diagram Descriptions

### Class Diagram
Shows the object-oriented structure with:
- 25+ classes organized in 7 packages
- Data Collection Layer (RobotDataCollector, CSVFileImporter)
- Data Processing Layer (SystemCallParser, DataProcessor)
- Analysis Layer (PatternRecognizer, LSTMModel, AnomalyDetector)
- Storage Layer (DatabaseManager, SystemCallRepository)
- API Layer (RESTAPIController, Services)
- UI Layer (Dashboard, VisualizationEngine)
- Security Layer (AuthenticationManager)

### Use Case Diagram
Shows 29 use cases across 7 categories:
- Real-time Monitoring (4 use cases)
- Data Analysis (5 use cases)
- Anomaly Detection (4 use cases)
- Performance Optimization (4 use cases)
- Reporting & Export (4 use cases)
- System Configuration (4 use cases)
- Data Collection (4 use cases)

5 actor types: System Administrator, Data Analyst, Research Scientist, System Engineer, Security Analyst

### Sequence Diagrams

**Diagram 1: Real-Time Monitoring**
- Shows real-time system call collection and monitoring
- Includes anomaly detection and alert flow
- Demonstrates dashboard update cycle
- 11,200 system calls/second throughput

**Diagram 2: Historical Data Analysis**
- Shows pattern recognition using LSTM model
- Includes statistical analysis and reporting
- Demonstrates comparative analysis between operational modes
- Processes 1.2M+ system call records

**Diagram 3: CSV Data Import**
- Shows bulk data import process
- Includes validation, parsing, and storage
- Demonstrates batch processing (10,000 records/batch)
- Handles 95.6 MB files with 632,986 records

## Quick Tip

For your presentation, consider:
- Using the online PlantUML editor for quick renders
- Exporting as SVG for crisp presentation slides
- Highlighting key components with colored boxes
- Walking through one sequence diagram in detail

