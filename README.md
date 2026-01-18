# Offshore Wind Farm Site Analysis & Visualization

---

## Project Overview
This project implements a data-driven decision tool for evaluating offshore wind farm locations using environmental data. The system analyzes wind and wave conditions, applies engineering constraints, and generates visual summaries to support infrastructure siting decisions.

The focus is on:
- Automating evaluation of environmental feasibility constraints
- Processing large geospatial and time-series datasets
- Producing clear engineering graphics for decision-making

---

## Key Capabilities

- Evaluates multiple environmental constraints for offshore wind farm viability
- Integrates global geospatial models with local buoy sensor data
- Automates pass/fail decisions using quantitative thresholds
- Produces a multi-panel visual summary for rapid assessment
- Designed to scale to evaluate many potential sites

---

## Technologies & Skills Demonstrated

- **Language:** MATLAB
- **Data Handling:** CSV ingestion, matrix indexing, time-series analysis
- **Numerical Analysis:** Statistical metrics, threshold-based decision logic
- **Visualization:** Contour maps, histograms, time-series plots
- **Engineering Reasoning:** Design constraints, risk evaluation, data validation

---

## Project Structure

    ├── analyzeWindFarm.m       # Evaluates environmental constraints for a site
    ├── makePlots.m             # Generates a multi-panel environmental summary
    ├── lat.csv                 # Latitude grid
    ├── lon.csv                 # Longitude grid
    ├── windSpeedData.csv       # Global wind speed model
    ├── waveHeightData.csv      # Global wave height model
    ├── buoyData.csv            # Local buoy time-series measurements
    ├── UnitTest_analyzeWindFarm.m
    ├── UnitTest_makePlots.m

---

## Analysis Logic

### Constraint Evaluation
Each candidate site is evaluated against five independent constraints:

1. Wind speed must fall within an acceptable operating range  
2. Average wave height must be below a maximum threshold  
3. Extreme wave conditions must be rare beyond a defined risk tolerance  
4. Structural deck height must exceed all estimated rogue waves  
5. Wave height variability must remain within acceptable limits  

Each constraint is computed independently and returned as a boolean result.

---

## Example Usage

    % Evaluate environmental feasibility
    [c1, c2, c3, c4, c5] = analyzeWindFarm( ...
        'windSpeedData.csv', ...
        'waveHeightData.csv', ...
        'buoyData.csv', ...
        3.5, 14.7, ...
        6.2, 95, ...
        25);
    % Generate environmental summary visualization
    makePlots( ...
        'windSpeedData.csv', ...
        'waveHeightData.csv', ...
        'buoyData.csv', ...
        3.5, 14.7, ...
        6.2); 
    
## Example Output

    Environmental feasibility results:
    Constraint 1: TRUE
    Constraint 2: TRUE
    Constraint 3: TRUE
    Constraint 4: TRUE
    Constraint 5: FALSE

## Generated File:

environmentalSummary.png

### The output figure includes:
- Global wind speed map
- Global wave height map
- Feasible site map with candidate location highlighted
- Histogram of local wave heights
- Time-series comparison of local vs. modeled wave conditions

## Design Highlights
- Separates analysis logic from visualization logic for modularity
- Uses vectorized operations for efficient data processing
- Produces publication-quality engineering graphics
- Designed to support rapid comparison of potential offshore sites
- Easily extensible to batch-evaluate many locations
  
## Why This Project Matters
- Translates real-world engineering constraints into code
- Works with heterogeneous environmental datasets
- Builds tools that support infrastructure and energy decisions
- Communicates complex data clearly through visualization
