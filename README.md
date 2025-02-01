# **Building Energy Benchmarks Data Cleaning with Regex**




**Overview**


This project focuses on cleaning a CSV file containing building energy benchmarks, specifically for properties in Calgary, Alberta. The dataset contains key information such as property identifiers, energy use statistics, emissions, and other building-related data.

Regular Expressions (Regex) were used to extract and clean specific data points to ensure that values are ready for analysis. This process included:

**Extracting numeric values from text-based columns like Property GFA (m²), Energy Use (GJ), and Emissions.**



**Standardizing postal codes to ensure they follow the correct Canadian format (A1A 1A1).**


**Cleaning and extracting meaningful text from the Property Name and Address fields.**


**Converting data types to ensure that numeric fields are properly formatted for analysis.**

Regex Tasks
1. Extract Numeric Values from Text-Based Columns
Some fields, such as Property GFA (m²), Energy Use (GJ), and Emissions, sometimes contain non-numeric characters or extra spaces. Regex was used to clean these fields by extracting only the numeric values and converting them into appropriate numerical types.

Regex Pattern:

## Extract only the numeric values (integers or floats)
numeric_pattern = r"(\d+(\.\d+)?)"
Example usage:


import re

def extract_numeric(value):
    match = re.search(numeric_pattern, str(value))
    if match:
        return float(match.group(1))
    return None

## Applying this to columns like Energy Use and Property GFA
df['Property GFA'] = df['Property GFA'].apply(extract_numeric)
df['Energy Use'] = df['Energy Use'].apply(extract_numeric)
This ensures that values such as 1838 m² are converted to 1838.0 for analysis.
