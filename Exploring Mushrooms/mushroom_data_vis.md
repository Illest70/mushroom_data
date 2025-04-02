```python
# Import necessary libraries
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load the dataset (replace 'path_to_file' with the actual file path)
df = pd.read_csv('mushroom_data.csv')

# Check the types of variables and their unique values
print("Variable Types and Counts:")
for column in df.columns:
    print(f"{column}: {df[column].nunique()} unique values")

# Initialize variables for analysis
bar_graph_columns = []
diverse_columns = []

# Categorize variables for visualization
for column in df.columns:
    unique_count = df[column].nunique()
    if unique_count < 10:  # Suitable for bar graph visualization
        bar_graph_columns.append(column)
    else:  # More diverse data
        diverse_columns.append(column)

print("\nColumns suitable for bar graph visualization:", bar_graph_columns)
print("Columns with high diversity:", diverse_columns)

# Bar Graph Visualization
print("\nGenerating bar graphs for columns with <10 unique values...")
for column in bar_graph_columns:
    sns.countplot(data=df, x=column, order=df[column].value_counts().index)
    
    # Rotate x-axis labels and adjust font sizes for readability
    plt.xticks(rotation=30, fontsize=10)
    plt.xlabel(column, fontsize=12)
    
    # Add informative title
    plt.title(f"{column} Value Counts", fontsize=14)
    
    # Display plot and clear previous formatting
    plt.show()
    plt.clf()

# Pie Chart Visualization for columns with <6 unique values
print("\nGenerating pie charts for columns with <6 unique values...")
for column in bar_graph_columns:
    if df[column].nunique() < 6:
        df[column].value_counts().plot.pie(autopct='%1.1f%%', startangle=90, figsize=(6, 6))
        
        # Add informative title
        plt.title(f"{column} Value Distribution")
        
        # Display plot and clear previous formatting
        plt.show()
        plt.clf()

# Insights from graphs
print("\nAnalysis Insights:")
for column in bar_graph_columns:
    print(f"For {column}:")
    mode_value = df[column].mode()[0]
    print(f"  - Most common value (mode): {mode_value}")
    print(f"  - Diversity score: {df[column].nunique()} unique values")
```

    Variable Types and Counts:
    Class: 2 unique values
    Cap Shape: 6 unique values
    Cap Surface: 4 unique values
    Cap Color: 10 unique values
    Bruises: 2 unique values
    Odor: 8 unique values
    Gill Attachment: 2 unique values
    Gill Spacing: 2 unique values
    Gill Size: 2 unique values
    Gill Color: 12 unique values
    Stalk Shape: 2 unique values
    Stalk Root: 5 unique values
    Stalk Surface Above Ring: 4 unique values
    Stalk Surface Below Ring: 4 unique values
    Stalk Color Above Ring: 9 unique values
    Stalk Color Below Ring: 9 unique values
    Veil Type: 1 unique values
    Veil Color: 4 unique values
    Ring Number: 2 unique values
    Ring Type: 4 unique values
    Spore Print Color: 9 unique values
    Population: 6 unique values
    Habitat: 7 unique values
    
    Columns suitable for bar graph visualization: ['Class', 'Cap Shape', 'Cap Surface', 'Bruises', 'Odor', 'Gill Attachment', 'Gill Spacing', 'Gill Size', 'Stalk Shape', 'Stalk Root', 'Stalk Surface Above Ring', 'Stalk Surface Below Ring', 'Stalk Color Above Ring', 'Stalk Color Below Ring', 'Veil Type', 'Veil Color', 'Ring Number', 'Ring Type', 'Spore Print Color', 'Population', 'Habitat']
    Columns with high diversity: ['Cap Color', 'Gill Color']
    
    Generating bar graphs for columns with <10 unique values...
    


    
![png](output_0_1.png)
    



    
![png](output_0_2.png)
    



    
![png](output_0_3.png)
    



    
![png](output_0_4.png)
    



    
![png](output_0_5.png)
    



    
![png](output_0_6.png)
    



    
![png](output_0_7.png)
    



    
![png](output_0_8.png)
    



    
![png](output_0_9.png)
    



    
![png](output_0_10.png)
    



    
![png](output_0_11.png)
    



    
![png](output_0_12.png)
    



    
![png](output_0_13.png)
    



    
![png](output_0_14.png)
    



    
![png](output_0_15.png)
    



    
![png](output_0_16.png)
    



    
![png](output_0_17.png)
    



    
![png](output_0_18.png)
    



    
![png](output_0_19.png)
    



    
![png](output_0_20.png)
    



    
![png](output_0_21.png)
    


    
    Generating pie charts for columns with <6 unique values...
    


    
![png](output_0_23.png)
    



    
![png](output_0_24.png)
    



    
![png](output_0_25.png)
    



    
![png](output_0_26.png)
    



    
![png](output_0_27.png)
    



    
![png](output_0_28.png)
    



    
![png](output_0_29.png)
    



    
![png](output_0_30.png)
    



    
![png](output_0_31.png)
    



    
![png](output_0_32.png)
    



    
![png](output_0_33.png)
    



    
![png](output_0_34.png)
    



    
![png](output_0_35.png)
    



    
![png](output_0_36.png)
    


    
    Analysis Insights:
    For Class:
      - Most common value (mode): Edible
      - Diversity score: 2 unique values
    For Cap Shape:
      - Most common value (mode): Convex
      - Diversity score: 6 unique values
    For Cap Surface:
      - Most common value (mode): Scaly
      - Diversity score: 4 unique values
    For Bruises:
      - Most common value (mode): False
      - Diversity score: 2 unique values
    For Odor:
      - Most common value (mode): Foul
      - Diversity score: 8 unique values
    For Gill Attachment:
      - Most common value (mode): Free
      - Diversity score: 2 unique values
    For Gill Spacing:
      - Most common value (mode): Close
      - Diversity score: 2 unique values
    For Gill Size:
      - Most common value (mode): Broad
      - Diversity score: 2 unique values
    For Stalk Shape:
      - Most common value (mode): Tapering
      - Diversity score: 2 unique values
    For Stalk Root:
      - Most common value (mode): Bulbous
      - Diversity score: 5 unique values
    For Stalk Surface Above Ring:
      - Most common value (mode): Smooth
      - Diversity score: 4 unique values
    For Stalk Surface Below Ring:
      - Most common value (mode): Smooth
      - Diversity score: 4 unique values
    For Stalk Color Above Ring:
      - Most common value (mode): White
      - Diversity score: 9 unique values
    For Stalk Color Below Ring:
      - Most common value (mode): White
      - Diversity score: 9 unique values
    For Veil Type:
      - Most common value (mode): Partial
      - Diversity score: 1 unique values
    For Veil Color:
      - Most common value (mode): White
      - Diversity score: 4 unique values
    For Ring Number:
      - Most common value (mode): One
      - Diversity score: 2 unique values
    For Ring Type:
      - Most common value (mode): Pendant
      - Diversity score: 4 unique values
    For Spore Print Color:
      - Most common value (mode): White
      - Diversity score: 9 unique values
    For Population:
      - Most common value (mode): Several
      - Diversity score: 6 unique values
    For Habitat:
      - Most common value (mode): Woods
      - Diversity score: 7 unique values
    


    <Figure size 640x480 with 0 Axes>



```python

```
