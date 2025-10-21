# Low-Fidelity Prototypes

These are wireframe mockups showing the key user interface screens for the Robot System Call Analysis Platform.

## Files

1. **01_main_dashboard.html** - Main dashboard with system overview
2. **02_realtime_monitor.html** - Real-time monitoring view
3. **03_component_analysis.html** - Individual component analysis
4. **04_anomaly_detection.html** - LSTM-based anomaly detection dashboard
5. **05_data_import.html** - CSV data import interface

## How to View

Simply open any `.html` file in your web browser:
- Double-click the file
- Or right-click → Open With → Browser

## What is Low-Fidelity?

Low-fidelity prototypes are:
- **Simplified wireframes** - Focus on layout and functionality, not visual polish
- **Black and white** - Minimal colors, basic shapes
- **Quick to create** - Can be made in hours, not days
- **Easy to modify** - Simple to update based on feedback

Think of them as "blueprints" before building the actual house!

## Key Features Demonstrated

### 01_main_dashboard.html
- System overview statistics
- Bar charts showing system call distribution
- Component activity visualization
- Recent activity feed
- Navigation sidebar

### 02_realtime_monitor.html
- Live system call stream (scrolling table)
- Real-time metrics (calls/second, execution time)
- Connection status indicator
- Filter and search functionality
- Auto-scroll controls

### 03_component_analysis.html
- Component selector (switch between robot parts)
- Detailed performance metrics
- Pie chart showing system call distribution
- Timeline showing activity patterns
- Data table with actionable insights
- Performance recommendations

### 04_anomaly_detection.html
- LSTM model status display
- Anomaly severity levels (Critical/Warning/Info)
- Detailed anomaly cards with context
- Confidence scores
- Investigation and action buttons
- Model configuration settings

### 05_data_import.html
- Drag-and-drop file upload area
- CSV format requirements
- Real-time import progress bar
- Import history table
- Detailed import summary statistics
- Data quality metrics

## For Your Report

When including these in your Stage 2 report:

1. **Take Screenshots** - Capture each screen
2. **Add Captions** - Explain what each screen does
3. **Annotate** - Use arrows to highlight key features
4. **User Flow** - Show how a user would navigate between screens

Example caption:
> *Figure 1: Main Dashboard - Provides system administrators with an at-a-glance view of robot health, system call distribution, and recent activity. Users can navigate to detailed views using the left sidebar.*

## Design Principles Used

- **Clear hierarchy** - Important info at the top
- **Consistent layout** - Similar elements look similar
- **Actionable** - Buttons for key tasks
- **Data-driven** - Metrics and visualizations throughout
- **Progressive disclosure** - Details available on demand

## User Flows Demonstrated

### Flow 1: Monitor Robot Health
1. User opens Main Dashboard (01)
2. Views system statistics and activity
3. Clicks "Real-time Monitor" in sidebar
4. Sees live system call stream (02)

### Flow 2: Investigate Component
1. User on Main Dashboard (01)
2. Clicks "View Details" for a component
3. Arrives at Component Analysis view (03)
4. Reviews metrics and recommendations
5. Exports data for further analysis

### Flow 3: Detect and Investigate Anomaly
1. System detects anomaly automatically
2. User receives notification
3. Opens Anomaly Detection view (04)
4. Reviews anomaly details and confidence
5. Decides on action (investigate, dismiss, or create alert rule)

### Flow 4: Import Historical Data
1. User navigates to Data Import (05)
2. Drags CSV file to upload area
3. Monitors real-time progress
4. Reviews import summary
5. Data available for analysis

## Next Steps (For Actual Implementation)

After approval of these prototypes:
- Add color scheme and branding
- Implement responsive design for mobile
- Add animations and transitions
- Create interactive components
- Implement actual data visualization libraries
- Add accessibility features

## Feedback Welcome!

These prototypes are meant to be discussed and modified. If you or your team have suggestions:
- Sketch changes directly on printouts
- Note missing features
- Identify confusing elements
- Suggest improvements

The whole point of low-fidelity prototypes is to get feedback **before** spending time on development!

