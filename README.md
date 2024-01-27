# data-analysis-crm-001
#Analysis of historical revenue and booking data for creating a reservation priority chart and customer retention distribution #graph

#analysis is done in phases, each divided into six month periods, analytical insights are drawn looking at visual representations #in matplotlib as well to compare trends through phases to gain additional insights.


#data cleaning 

import pandas as pd

# Load the Excel file
file_path = ''  # Replace with your file path if youre running on a local ide, if online you upload your file at this point 
alphasports_data = pd.read_excel(file_path)

# Setting the correct header and dropping unnecessary columns and rows
alphasports_data.columns = alphasports_data.iloc[1]  # Set the second row as the header
alphasports_data = alphasports_data.drop([0, 1])  # Drop the first two rows

# Drop empty or irrelevant columns
alphasports_data = alphasports_data.dropna(axis=1, how='all')

# Cleaning 'Slot Date' column
alphasports_data['Slot Date'] = alphasports_data['Slot Date'].apply(lambda x: x.strip() if isinstance(x, str) else x)
alphasports_data['Slot Date'] = pd.to_datetime(alphasports_data['Slot Date'], errors='coerce')

# Converting 'Slot Cost' to numeric
alphasports_data['Slot Cost'] = pd.to_numeric(alphasports_data['Slot Cost'], errors='coerce')



#analysis of time popularity, logic implementation 



# Analyzing the frequency of bookings for each time slot
slot_time_counts = alphasports_data['Slot time'].value_counts()

# Sorting the results to see the most and least busy slots
sorted_slot_time_counts = slot_time_counts.sort_values(ascending=False)




