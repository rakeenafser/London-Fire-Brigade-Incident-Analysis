# London Fire Brigade Incident Demand & Resource Utilisation Analysis

**Exploratory Data Analysis | Python | Pandas | GeoPandas | Matplotlib**

An exploratory analysis of 771,311 London Fire Brigade incident records covering January 2018 to September 2024, examining how emergency incident demand varies across time, London boroughs and incident categories.

The project investigates not only **how frequently incidents occur**, but also how different incident types contribute to **recorded fire-appliance resource demand**.

## Project Overview

Emergency services respond to a wide range of incidents, including fires, false alarms and special services. Understanding these incidents requires looking beyond overall incident counts.

This project explores four key questions:

- How did recorded incident demand change between 2018 and 2023?
- How does incident demand vary by season, time of day and London borough?
- How do geographical patterns differ between all incidents and fire-only incidents?
- How does each incident category's share of recorded pump-hours compare with its share of incidents?

The analysis is descriptive. It does not evaluate response times, operational efficiency or the appropriateness of fire-appliance deployments.

## Key Findings

### 1. Overall incident demand increased, while recorded fires declined

Between 2018 and 2023, total recorded incidents increased by **19.3%**, while recorded fire incidents decreased by **18.1%**.

Special service incidents increased by **41.6%** over the same period, demonstrating that changes in overall incident demand were not driven by fires alone.

![Annual incident trends](figures/annual_incident_trends.png)

### 2. Geographic patterns differ between all incidents and fires

The geographical distribution of overall incident demand differs from the distribution of recorded fires.

Westminster had the highest average annual overall incident rate per 1,000 residents during 2018–2023. Kensington and Chelsea and Camden also recorded relatively high overall rates.

When examining fire-only incident rates, boroughs such as Greenwich and Waltham Forest became more prominent.

![London borough geographic comparison](figures/london_side_by_side_map_comparison.png)

*Both maps use average annual incident rates per 1,000 residents for 2018–2023. The colour scales differ, so the maps should be interpreted as comparisons of geographical patterns rather than direct colour-intensity comparisons.*

### 3. Incident frequency does not fully describe recorded resource demand

The analysis compared each incident category's proportion of recorded incidents against its proportion of recorded pump-hours.

| Incident category | Share of incidents | Share of recorded pump-hours |
|---|---:|---:|
| False alarms | 49.4% | 40.4% |
| Special services | 35.3% | 31.9% |
| Fires | 15.3% | 27.7% |

Although fires represented a relatively small proportion of incidents, they accounted for a considerably larger share of recorded pump-hours.

False alarms, meanwhile, accounted for almost half of incidents and approximately 40% of recorded pump-hours.

These findings illustrate why incident counts and recorded appliance-time demand should be considered together.

![Incident volume versus pump-hour share](figures/incident_vs_pump_hours.png)

### 4. Incident composition varies across London boroughs

Borough-level analysis highlighted differences in the composition of recorded emergency incidents.

Westminster recorded the highest absolute number of false alarms during the study period, while the City of London had a particularly high proportion of false alarms relative to its total recorded incidents.

![Borough incident composition](figures/borough_incident_composition.png)

Additional analyses explore seasonal demand, hourly patterns, property categories and borough-level false-alarm comparisons.

## Tools and Technical Approach

**Python:** Data processing, exploratory analysis and visualisation.

**Pandas and NumPy:** Data cleaning, date processing, aggregation, grouping and analytical calculations.

**GeoPandas and Shapely:** Borough-level spatial analysis, geographic joins and choropleth maps.

**Matplotlib:** Statistical charts, geographical visualisation and comparative figures.

Key analytical steps included:

1. Examining incident categories, missing values and reporting periods.
2. Preparing complete-year data for comparable annual, seasonal and hourly analysis.
3. Aggregating incident counts by category, date, hour and borough.
4. Joining borough-level incident data with population estimates and geographical boundaries.
5. Calculating average annual incident rates per 1,000 residents.
6. Converting recorded rounded pump-minutes into pump-hours and comparing category-level resource-demand shares.
7. Creating reproducible Python visualisations.

## Data Sources

- **London Fire Brigade incident records:** January 2018–September 2024.
- **London borough population dataset:** Fixed borough-level population estimates supplied with the analysis data.
- **Office for National Statistics:** December 2023 local authority district geographical boundaries.

The precise original source and reference year of the population-estimate file have not been independently verified. Population-based rates should therefore be interpreted as estimates conditional on the supplied population figures.

The raw datasets are not included in this repository. Reproducing the analysis requires obtaining the relevant source data and placing them in the expected local directory structure.

## Repository Structure

```text
London-Fire-Brigade-Incident-Analysis/
├── README.md
├── requirements.txt
├── LFB_Analysis_Code_Only.ipynb
└── figures/
    ├── annual_incident_trends.png
    ├── borough_incident_composition.png
    ├── false_alarm_borough_comparison.png
    ├── hourly_incident_demand.png
    ├── incident_vs_pump_hours.png
    ├── london_fire_only_map.png
    ├── london_incident_demand_map.png
    ├── london_side_by_side_map_comparison.png
    ├── property_resource_utilisation.png
    └── seasonal_incident_demand.png
```

## Running the Analysis

Clone or download the repository and install the required Python packages:

```bash
pip install -r requirements.txt
```

Create a `data/` directory in the project root and provide the following files:

```text
data/
├── LFB2018-2024.csv
├── LondonBoroughPopulationData.csv
└── london_boundaries.geojson
```

Open `LFB_Analysis_Code_Only.ipynb` in JupyterLab or Jupyter Notebook and run the cells in sequence.

The notebook expects the datasets to follow the filenames and schemas used in the original analysis. The population-estimate file is not currently linked to a verified external download, so full independent reproduction requires access to that input.

## Analytical Limitations

- **Partial 2024 coverage:** The source incident data end in September 2024. Annual comparisons use the complete years 2018–2023.
- **Population estimates:** Geographic rates use a fixed population denominator rather than annual population estimates.
- **City of London:** Excluded from population-normalised borough rate maps because it is absent from the supplied population file.
- **Recorded pump-hours:** Calculated from rounded pump-minute values. These are not exact on-scene durations, firefighter labour hours or financial costs.
- **Scope:** The analysis describes recorded operational demand. It does not assess response performance, deployment efficiency or whether particular incidents were preventable.

## Conclusion

The analysis highlights the importance of examining emergency-service demand through multiple measures.

Overall incident counts show how frequently different emergencies are recorded, while geographical rates reveal variation across boroughs. Comparing incident categories with recorded pump-hour shares provides an additional perspective on the fire-appliance time associated with different types of incidents.

Together, these measures offer a more informative descriptive picture of London Fire Brigade incident demand than incident totals alone.
