# Energy_Market_Resilence_Metric | Trend , Insight, Recommendation
Numpy | Pandas | Matplotlib.pyplot | Seaborn | Jupyter Notebook

## Project Overview
Energix Enterprise is a prominent player in the Energy and Utilities sector, specializing in electricity generation and distribution across various regions. With a diversified energy portfolio encompassing both fossil fuels and renewable sources, the company has been a vital contributor to the energy landscape for over two decades. 
Its energy generation and distribution operations span a wide spectrum, from traditional coal and natural gas power plants to cutting-edge wind and solar facilities. The company's commitment to sustainability and environmental responsibility has driven significant investments in renewable energy technologies.
However, recent disruptions in the energy market have raised concerns about the company's ability to maintain its operations and profitability in the face of unforeseen challenges.

##  Tech Stack
* Python
* Excel

### Dataset Overview
This case study contains 4 datasets, and they are as follows.

#### Historical Energy Data: 

✓ Date/Time: Timestamp of the recorded data.

✓ Location/Region: The geographical region where energy is generated or distributed.

✓ Energy Source: Type of energy source (e.g., fossil fuels, renewables).

✓ Energy Production (kWh): Amount of energy generated in kilowatt-hours.

✓ Energy Consumption (kWh): Amount of energy consumed in kilowatt-hours.

✓ Energy Price (USD/kWh): The cost of energy during the period in US dollars per kilowatt-hour.

✓ Operational Costs (USD): Costs associated with production, maintenance, and distribution in US dollars.

✓ Energy Demand (kWh): Total energy demand during the period in kilowatt-hours.


#### Market Data:

✓ Date/Time: Timestamp of the recorded market data.

✓ Market Price (USD/kWh): Price of energy in the market in US dollars per kilowatt-hour.

✓ Competitor Data: Information about competitors' market strategies (e.g., High, Medium, Low).

✓ Market Trends: Trends and fluctuations in the energy market (e.g., Upward, Stable, Downward).

✓ Market Demand (kWh): Information about market demand for energy in kilowatt-hours.


 

#### Infrastructure and Maintenance Records:

✓ Date/Time: Timestamp of infrastructure and maintenance records.

✓ Infrastructure Status: Information on the condition of infrastructure (e.g., Good, Fair, Poor).

✓ Maintenance Activities: Details of maintenance activities (e.g., Routine Maintenance, Repairs, Upgrades).

✓ Technology Limitations: Information about limitations and challenges posed by existing technology (e.g., None, Low, Moderate, High).


 
#### Regulatory and Compliance Data:

✓ Date/Time: Timestamp of regulatory changes or compliance activities.

✓ Regulatory Changes: Details of changes in energy regulations and policies.

✓ Compliance Status: Information on the company's compliance with regulations (e.g., Compliant, Non-compliant).

✓ Compliance Costs (USD): Costs associated with ensuring compliance in US dollars.


### Data Sample Preview
| Date/Time| Location/Region |	Energy_Source	| Energy_Demand |	Energy_Consumption_(kWh) | Energy_Price |	Operational_Costs	| Energy_Production_(kWh) |
|----------|-----------------|----------------|---------------|--------------------------|--------------|-------------------|-------------------------|
| 1/1/2012 |	Region A	     | Fossil Fuels	  |     24016	    |        21848	           |0.13163	      |1564.239198	      |          31604          |
|2/1/2012	 |  Region C	     |  Fossil Fuels	| 56200	        |        34796	           |0.160969456	  | 3837.295411	      |          11734          |


### Business Problem

Energix Enterprise currently faces several significant challenges:
1. Fluctuations in Energy Demand and Supply: The energy market experiences fluctuations due to market volatility and evolving consumer behavior. These variations impact the company's operations and profitability.
2. Rising Competition from Renewable Energy Providers: The emergence of renewable energy providers has intensified competition, affecting Energix Enterprise  Energy's market share and pricing strategies.
3. Regulatory Changes and Environmental Regulations: Evolving regulations and environmental mandates have a substantial impact on the company's operations, necessitating compliance measures that add to operational costs.
4. Aging Infrastructure and Technology Limitations: Aging infrastructure and outdated technology hinder operational efficiency, risk management, and the company's ability to adapt to market dynamics.

### Aim of the Project
1.  Resilience Planning: Create a comprehensive resilience plan outlining response procedures for various disruptions, ensuring business continuity.
2.  Upgrade Technology Infrastructure: Identify technology gaps and implement infrastructure upgrades for improved operational efficiency.
3.  Optimize Energy Production and Pricing: Implement data-driven strategies for optimizing energy production and pricing to maintain profitability.
4.  Data Analysis: Utilize historical data and market trends to identify vulnerabilities and potential disruption points in the energy market.

### Project Scope
Data Collection and Preparation: Gather and clean data from various sources, ensuring data quality using Python.
Exploratory Data Analysis (EDA): 
1. Explore historical trends, market dynamics, and key variables using Python. Identify patterns, outliers, and anomalies in the data using Python.
2. Optimization Strategies: Develop pricing and production optimization strategies based on data analysis using Python. Implement strategies to adapt to changing market conditions using Python.
3. Infrastructure Upgrade: Identify technology gaps and implement infrastructure upgrades for improved efficiency using Python. Integrate real-time monitoring and reporting systems using Python.
4. Resilience Planning: Create a comprehensive resilience plan in Python, outlining response procedures for various disruptions.Conduct simulations and stress tests using Python to evaluate the effectiveness of the plan.
5. Documentation and Reporting: Document the entire project, including data sources, methodologies, and findings using Python.
6. Provide actionable insights and recommendations for ABC Energy Corporation using Python.

### Environment Setup in Jupyter Notebook
```Python
import pandas as pd 
import matplotlib.pyplot as plt 
import seaborn as sns 
import numpy as np 
import matplotlib.ticker as ticker
```
### Loading all the dataset
```Python
hist_data = pd.read_csv("historical_energy_data.csv")
inf_data = pd.read_csv("infrastructure_data.csv")
mark_data = pd.read_csv("market_data.csv")
reg_data = pd.read_csv("regulatory_data.csv")
hist_data.head()

```

### UNDERSTANDING THE STRUCTURE OF THE DATA
```Python
hist_data.info()
hist_data.describe()
inf_data.info()
inf_data.describe()
reg_data.info()
reg_data.describe()
```

### DATA CLEANING
```Python
date_format = "%d/%m/%Y"
hist_data['Date/Time'] = pd.to_datetime(hist_data['Date/Time'],format= date_format)

new_date_format = "%d-%m-%Y"
hist_data['Date/Time'] = pd.to_datetime(hist_data['Date/Time'],format= new_date_format)

reg_data['Date/Time'] = pd.to_datetime(reg_data['Date/Time'])
mark_data['Date/Time'] = pd.to_datetime(mark_data['Date/Time'])
date_format = "%d/%m/%Y"
inf_data['Date/Time'] = pd.to_datetime(inf_data['Date/Time'],format= date_format)

new_date_format = "%d-%m-%Y"
inf_data['Date/Time'] = pd.to_datetime(inf_data['Date/Time'],format= new_date_format)
```
### EXPLORATORY DATA ANALYSIS
### 1. ENGERGY DEMAND, PRODUCTION AND CONSUMPTION OVER TIME
```Python
import matplotlib.ticker as ticker
#INSERT THIS LINE TO CONVERT TO DATETIME ---
hist_data['Date/Time'] = pd.to_datetime(hist_data['Date/Time'], dayfirst=True)


# Extract the year and month from the "Date/Time" c=Column 

hist_data["Year"] = hist_data['Date/Time'].dt.year
hist_data["Month"] = hist_data['Date/Time'].dt.month

# Create a new column "Year-month" for easy plotting 
hist_data["Year_month"] = hist_data['Date/Time'].dt.to_period("M")

# Aggregating data on a monthly basics 
month_data = hist_data.groupby("Year_month").mean(numeric_only=True)

#setting figures 
plt.figure(figsize=(15,8))
ax = plt.gca()

#plotting
sns.lineplot(data=month_data, x=month_data.index.astype(str), y='Energy Production (kWh)', label='Energy Production', color='blue', linestyle='-',linewidth=1.5, errorbar=None)
sns.lineplot(data=month_data, x=month_data.index.astype(str), y='Energy Consumption (kWh)', label='Energy Comsumption', color='red', linestyle='-',linewidth=1.5, errorbar=None)
sns.lineplot(data=month_data, x=month_data.index.astype(str), y='Energy Demand', label='Energy Demand', color='green', linestyle='-',linewidth=1.5, errorbar=None)

#Setting the title and labels

ax.xaxis.set_major_locator(ticker.MaxNLocator(12))

plt.title("Monthly Aggregate of Energy Production Consumption, and Demand Over Time")
plt.xlabel("Date")
plt.ylabel('Kwh')
plt.legend(loc='upper left', bbox_to_anchor=(1,1))
plt.grid(True, which='both', linestyle='--', linewidth=0.5)


#Setting our label
labels = month_data.index.astype(str).tolist()
n = 6

plt.tight_layout()
plt.subplots_adjust(hspace=0.5)
plt.show()

```
<img width="1231" height="650" alt="Screenshot 2025-10-13 181144" src="https://github.com/user-attachments/assets/2437e22f-2ded-4cb3-881c-6d904791ef0e" />

### 2. Infrastructure Status and Tech Limitation
```Python
# Setting of figure and axis 
fig, axes = plt.subplots(1,2, figsize=(15, 8))

# Plotting the frequency of Infrastructure status  

sns.countplot(
    data=inf_data, 
    x="Infrastructure Status", 
    ax=axes[0], 
    order=['Good', 'Fair', 'Poor'],
    hue="Infrastructure Status", 
    legend=False, 
    palette='viridis' 
)
axes[0].set_title('Frequency of Infrastructure Status')
axes[0].set_xlabel('Infrastructure Status')
axes[0].set_ylabel('count')

# Plotting the frequency of Technology limitation 

sns.countplot(
    data=inf_data, 
    x="Technology Limitations", 
    ax=axes[1], 
    hue="Technology Limitations", 
    legend=False, 
    palette='viridis'
)
axes[1].set_title('Frequency of Technology Limitation')
axes[1].set_xlabel('Technology Limitation')           
axes[1].set_ylabel('count') 

plt.tight_layout()
plt.show()
```


<img width="1224" height="647" alt="Screenshot 2025-10-13 182034" src="https://github.com/user-attachments/assets/4d59dfd9-0e45-49e8-a066-72ba3806ccfb" />

### 3. Regulatory Changes and Compliance Cost

```Python
fig,(ax1, ax2)= plt.subplots(1,2, figsize=(15,6))

sns.countplot(
    data=reg_data, 
    x='Regulatory Changes', 
    ax=ax1, 
    hue='Regulatory Changes', 
    legend=False,             
    palette='viridis'
)


sns.histplot(data=reg_data, x="Compliance Costs", ax=ax2, bins= 30,kde=True ,color='skyBlue',)
ax2.set_title('Distribution Of Compliance Cost')
ax2.set_xlabel('Compliance Cost')
ax2.set_ylabel('Freq')

plt.tight_layout()
plt.show()
```

<img width="1234" height="485" alt="Screenshot 2025-10-13 214911" src="https://github.com/user-attachments/assets/02d5fba7-7961-4dcc-9465-135585b09ceb" />

### 4. Impact of Regulatory Changes and Operational Costs on Revenue
```Python
# Create Revenue column
hist_data["Revenue"] = hist_data["Energy Price"] * hist_data["Energy Consumption (kWh)"]

# Merge dataframes
merged_regulatory_data = pd.merge(hist_data, reg_data, on="Date/Time", how="inner")

# Create Year and Month columns
merged_regulatory_data["Year"] = merged_regulatory_data["Date/Time"].dt.year
merged_regulatory_data["Month"] = merged_regulatory_data["Date/Time"].dt.month

# --- FIX FOR TYPEERROR: Select only numeric columns for aggregation ---

# List all the columns that contain numbers you want to average
numeric_cols_to_average = [
    "Energy Demand",
    "Energy Consumption (kWh)",
    "Energy Price",
    "Operational Costs",
    "Energy Production (kWh)",
    "Revenue",
    "Compliance Costs"
]

# Select only the grouping keys ('Year', 'Month') and the numeric columns
data_for_aggregation = merged_regulatory_data[
    ["Year", "Month"] + numeric_cols_to_average
]

# Aggregate data (using the clean data_for_aggregation DataFrame)
monthly_aggregated_data = data_for_aggregation.groupby(["Year", "Month"]).mean().reset_index()

# Create 'Year-Month' column for plotting
monthly_aggregated_data["Year-Month"] = (
    monthly_aggregated_data["Year"].astype(str) + 
    '-' + 
    monthly_aggregated_data["Month"].astype(str).str.zfill(2)
) 

# --- Plotting Code ---

plt.figure(figsize=(15, 6))

# FILL BETWEEN 1: Operational Costs (Base Layer)
plt.fill_between(
    monthly_aggregated_data["Year-Month"], 
    monthly_aggregated_data["Operational Costs"], 
    color='blue', 
    label='Operational Costs', 
    alpha=0.5 
)

# FILL BETWEEN 2: Compliance Costs (Stacked on top of Operational Costs)
plt.fill_between(
    monthly_aggregated_data["Year-Month"], 
    monthly_aggregated_data["Operational Costs"],  
    monthly_aggregated_data['Operational Costs'] + monthly_aggregated_data['Compliance Costs'], 
    color='green',
    label='Compliance Costs',
    alpha=0.7
) 

# Line plot for Revenue
sns.lineplot(
    data=monthly_aggregated_data, 
    x="Year-Month",             
    y="Revenue", 
    label="Revenue", 
    color="red", 
    linewidth=2,
    errorbar=None 
)

plt.xlabel('Date')
plt.ylabel("Amount ($)")
plt.legend(loc="upper left")
plt.grid(True, which="both", linestyle="--", linewidth=0.5)

# Setting X-ticks
labels = monthly_aggregated_data["Year-Month"].tolist()
n = 6 
plt.xticks(labels[::n], labels[::n], rotation=45) 

plt.tight_layout()
plt.show()
```
<img width="1226" height="486" alt="Screenshot 2025-10-13 215146" src="https://github.com/user-attachments/assets/679823d1-5417-4180-a1fd-e0ddc20678ca" />

### 5. Analyzing Competition from Renewable Energy Providers
```Python
# Ensure necessary data columns are prepared
hist_data["Year"] = hist_data['Date/Time'].dt.year
hist_data["Month"] = hist_data['Date/Time'].dt.month

# Aggregate data: Select the column to sum BEFORE the .sum() call to avoid TypeError
monthly_aggregated_data = (
    hist_data.groupby(['Year', 'Month', 'Energy Source'])['Energy Production (kWh)']
    .sum()
    .reset_index()
)

# Create 'Year-Month' column (zero-padding the month for correct sorting/plotting)
monthly_aggregated_data["Year-Month"] = (
    monthly_aggregated_data["Year"].astype(str) + 
    '--' + 
    monthly_aggregated_data["Month"].astype(str).str.zfill(2)
)

plt.figure(figsize=(12, 4))

# --- CRITICAL ADDITION: PLOTTING THE LINE CHART ---
sns.lineplot(
    data=monthly_aggregated_data,
    x="Year-Month",
    y="Energy Production (kWh)",
    hue="Energy Source",  # This creates separate lines for each energy source
    errorbar=None         # Ensures clean lines without error bars
)
# --------------------------------------------------

plt.title('Monthly Aggregated Energy Production Trends by Energy Source Over Time')
plt.xlabel("Date")
plt.ylabel("Energy Production (Kwh)")

# NOTE: Seaborn's lineplot automatically generates the legend, but we can set its title
plt.legend(title="Energy Source") 

plt.grid(True, which='both', linestyle='--', linewidth=0.5)

# Setting X-ticks for cleaner display
labels = monthly_aggregated_data["Year-Month"].unique().tolist()
n = 6 

# Get tick positions (0, 1, 2, 3, ...) and filter them
tick_positions = np.arange(0, len(labels), n)
tick_labels = labels[::n]

# Use the filtered positions and labels with a visible rotation
plt.xticks(tick_positions, tick_labels, rotation=45, ha='right')

plt.tight_layout()
plt.show()
```

<img width="1229" height="398" alt="Screenshot 2025-10-13 215541" src="https://github.com/user-attachments/assets/c0659e05-fdd1-4edf-86ee-a146ebe3a7de" />

### General Insights:
1. Dynamic Energy Landscape: Energix Enterprise experiences marked variances in energy production, consumption, and demand patterns. There are distinct periods where the demand overshadows production, highlighting potential areas of concern in market stability and supply consistency.
2. Pricing Volatility: Energix's energy pricing exhibits variability in alignment with broader market price trends. Notably, the energy price remains uncorrelated with energy demand, presenting potential challenges in sales predictability, and revenue forecasting.
3. Infrastructure & Technology Concerns: A significant portion of the company's infrastructure is categorized as "Poor." Coupled with pronounced technology limitations, there's a compelling case for comprehensive infrastructure rejuvenation. Preliminary analysis suggests that periods of 'Poor' infrastructure status and 'High' technology constraints may correlate with diminished energy production.
4. Regulatory & Financial Implications: Energix is continually navigating a changing regulatory landscape, with new mandates and modifications to existing ones. The financial ramifications, especially in terms of compliance costs and operational expenditures, are substantial. A juxtaposition of these costs with the firm's current revenue trajectory indicates a pressing profitability challenge.
5. Emergence of Renewables: The energy market is witnessing a paradigm shift with renewables gaining prominence. Data trends suggest instances where renewable energy production has eclipsed that of fossil fuels. For Energix, this underscores the dual challenges of evolving competition and potential erosion of market share.


### Resilience Planning and Recommendations
1. Balanced Energy Portfolio: Energix Enterprise should consider diversifying its energy production portfolio to mitigate the risks associated with fluctuations in demand and production. A balanced mix of renewable and non-renewable sources can help stabilize the energy supply and meet demand more consistently.
2. Dynamic Pricing Model: Given that energy price doesn't correlate with energy demand, Energix should consider implementing a dynamic pricing model. This model can adjust prices based on demand, production costs, and other market factors. Such a model can help in improving sales during high-demand periods and maintaining profitability during low-demand times.
3. Infrastructure Revamp: With most of the company's infrastructure in "Poor" status and high technology limitations, Energix should prioritize investments in infrastructure upgrades. Modernizing infrastructure can lead to increased production efficiency, reduced downtimes, and potentially higher energy output.
4. Regulatory Compliance Fund and Operational Cost: Given the periodic introduction of new regulations and the associated compliance costs and also operational cost, Energix should establish a dedicated fund or reserve to address these unforeseen expenses. This approach can help in budgeting and ensuring that costs don't significantly impact the company's bottom line.
5. Embrace Renewables: The trend towards renewable energy is evident. Energix should consider increasing its investments in renewable energy technologies and infrastructure. This not only aligns with global sustainability goals but also positions the company to better compete in an evolving energy market.
6. Cost Management & Revenue Generation: Considering the operational and compliance costs are impacting profitability, Energix should undertake a thorough review of its operations to identify cost-saving opportunities. Additionally, exploring alternative revenue streams, such as energy storage solutions or consultancy services, can further bolster the company's financial position.
7. Stakeholder Engagement: Engage with regulatory bodies proactively to stay ahead of potential regulatory changes. This proactive approach can help in better preparation and can also influence regulations in a manner favorable to Energix.
8. Market Research & Consumer Insights: Conduct regular market research to understand consumer preferences, especially concerning renewable energy. This can guide Energix's strategy in terms of energy source diversification and pricing.

## Conclusion
while Energix faces challenges in terms of fluctuating demand, aging infrastructure, and increasing competition from renewables, there are clear strategic paths available. By modernizing infrastructure, diversifying energy sources, and adopting a dynamic pricing model, Energix can position itself for sustained growth and profitability in the future energy market.

