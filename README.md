# SCHOOLWATCH
SchoolWatch: Identifying and addressing global education gaps by analyzing data on out-of-school children. 

import pandas as pd
import matplotlib.pyplot as plt

# Load the datasets
out_of_school_data = pd.read_excel('path_to_your_downloaded_file/Out_of_school_rate_2022_formatted.xlsx')
attendance_data = pd.read_excel('path_to_your_downloaded_file/Adjusted_net_attendance_rate_2022_formatted.xlsx')
completion_data = pd.read_excel('path_to_your_downloaded_file/Completion_rate_2022_formatted.xlsx')
ict_skills_data = pd.read_excel('path_to_your_downloaded_file/ICT-Skills_2022.xlsx')
literacy_data = pd.read_excel('path_to_your_downloaded_file/Literacy-rate_2021-1.xlsx')
digital_connectivity_data = pd.read_excel('path_to_your_downloaded_file/School-Age-Digital-Connectivity.xlsx')

# Clean the datasets (if necessary)
out_of_school_data = out_of_school_data.dropna()
attendance_data = attendance_data.dropna()
completion_data = completion_data.dropna()
ict_skills_data = ict_skills_data.dropna()
literacy_data = literacy_data.dropna()
digital_connectivity_data = digital_connectivity_data.dropna()

# Example Analyses:

# Out-of-School Rate by Age
out_of_school_age_group = out_of_school_data.groupby('Age')['Out_of_School_Rate'].sum()

# Attendance Rate by Age
attendance_age_group = attendance_data.groupby('Age')['Adjusted_Net_Attendance_Rate'].mean()

# Completion Rate by Age
completion_age_group = completion_data.groupby('Age')['Completion_Rate'].mean()

# ICT Skills Proficiency by Age
ict_skills_age_group = ict_skills_data.groupby('Age')['ICT_Skills_Proficiency'].mean()

# Literacy Rate by Age
literacy_age_group = literacy_data.groupby('Age')['Literacy_Rate'].mean()

# Digital Connectivity Rate by Age
digital_connectivity_age_group = digital_connectivity_data.groupby('Age')['Digital_Connectivity_Rate'].mean()

# Plotting the data
plt.figure(figsize=(12, 8))

plt.subplot(2, 3, 1)
plt.bar(out_of_school_age_group.index, out_of_school_age_group.values)
plt.xlabel('Age')
plt.ylabel('Out-of-School Rate')
plt.title('Out-of-School Rate by Age')

plt.subplot(2, 3, 2)
plt.plot(attendance_age_group.index, attendance_age_group.values, marker='o')
plt.xlabel('Age')
plt.ylabel('Adjusted Net Attendance Rate')
plt.title('Adjusted Net Attendance Rate by Age')

plt.subplot(2, 3, 3)
plt.plot(completion_age_group.index, completion_age_group.values, marker='o')
plt.xlabel('Age')
plt.ylabel('Completion Rate')
plt.title('Completion Rate by Age')

plt.subplot(2, 3, 4)
plt.plot(ict_skills_age_group.index, ict_skills_age_group.values, marker='o')
plt.xlabel('Age')
plt.ylabel('ICT Skills Proficiency')
plt.title('ICT Skills Proficiency by Age')

plt.subplot(2, 3, 5)
plt.plot(literacy_age_group.index, literacy_age_group.values, marker='o')
plt.xlabel('Age')
plt.ylabel('Literacy Rate')
plt.title('Literacy Rate by Age')

plt.subplot(2, 3, 6)
plt.plot(digital_connectivity_age_group.index, digital_connectivity_age_group.values, marker='o')
plt.xlabel('Age')
plt.ylabel('Digital Connectivity Rate')
plt.title('Digital Connectivity Rate by Age')

plt.tight_layout()
plt.show()


