# KNIME Example Workflows

This repository contains a structured collection of **KNIME Analytics Platform** example workflows, designed to demonstrate data manipulation, data aggregation, visualization, and basic machine learning classification techniques.

---

## 📁 Repository Structure

```text
Example Workflows/
├── workflowset.meta
└── Basic Examples/
    ├── workflowset.meta
    ├── Building a Simple Classifier/
    │   ├── CSV Reader (#14)/
    │   ├── Partitioning (#5)/
    │   ├── Decision Tree Learner (#10)/
    │   ├── Decision Tree Predictor (#4)/
    │   ├── Scorer (#12)/
    │   ├── Scatter Plot (#15)/
    │   ├── Statistics (#9)/
    │   ├── workflow.knime
    │   ├── workflow.svg
    │   └── workflow-metadata.xml
    │
    ├── Combine Clean and Summarize Spreadsheet Data/
    │   ├── data/
    │   │   ├── example_aggregation.xlsx
    │   │   ├── example_merger.xlsx
    │   │   ├── example_spreadsheet.xlsx
    │   │   ├── example_value_lookup.xlsx
    │   │   └── Rooms.xlsx
    │   ├── Excel Reader (#6, #7, #18)/
    │   ├── Column Filter (#27)/
    │   ├── Column Merger (#21)/
    │   ├── Concatenate (#8)/
    │   ├── Row Aggregator (#12)/
    │   ├── String To Number (#23)/
    │   ├── Value Lookup (#22)/
    │   ├── Bar Chart (#26)/
    │   ├── workflow.knime
    │   ├── workflow.svg
    │   └── workflow-metadata.xml
    │
    └── CountIf and SumIf/
        ├── data/
        │   └── olympics data/
        │       └── Olympic_Athlete_joined.xlsx
        ├── Column Appender (#31)/
        ├── Column Renamer (#28, #32)/
        ├── workflow.knime
        └── workflow-metadata.xml
