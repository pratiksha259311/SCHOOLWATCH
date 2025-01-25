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
import streamlit as st
import pandas as pd
import matplotlib.pyplot as plt

# Title and description
st.title("SchoolWatch: Mapping the Missing Education")
st.write("""
Welcome to SchoolWatch, a data-driven initiative aimed at identifying and addressing the global education gap.
""")

# Why I Chose This Idea
st.header("Why I Chose This Idea")
st.write("""
I chose this idea because it deeply resonates with my personal interests and experiences. Growing up, I was always fascinated by the challenges many children face in accessing basic education. My curiosity led me to explore how factors like age, gender, family background, and location influence this issue. I realized there was a significant gap in current understanding and awareness. This project aims to address that gap by shedding light on important aspects and providing solutions. By delving into this subject, I aim to make a meaningful impact on ensuring education for all children.
""")

# Out-of-School Children Rate section
st.header("Out-of-School Children Rate")
st.write("""
The UNICEF Global Database on Out-of-School Children Rate is a collection of information about children around the world who are not going to school. This data helps us understand how many kids are missing out on education and where they live. By looking at this information, we can find out which groups of children need the most help and why they are not attending school. This way, we can work on solutions to ensure every child has the opportunity to get an education and build a better future.
""")

# Example Data (replace with your actual data file)
data_out_of_school = pd.read_csv('out_of_school_children.csv')
st.dataframe(data_out_of_school)

# ICT Skills Proficiency
st.header("ICT Skills Proficiency")
st.write("""
The ICT Skills Proficiency dataset highlights how well children are performing with essential digital skills. It identifies which age groups and regions need more support and training, ensuring all children are prepared for the future and can benefit from digital opportunities.
""")
data_ict_skills = pd.read_csv('ict_skills.csv')
st.dataframe(data_ict_skills)

# Completion Rate
st.header("Completion Rate")
st.write("""
The Completion Rate dataset shows the percentage of children who finish their education at different levels, such as primary or secondary school. It helps identify regions or groups that need more support to ensure all children can complete their schooling.
""")
data_completion = pd.read_csv('completion_rate.csv')
st.dataframe(data_completion)

# Net Attendance
st.header("Net Attendance")
st.write("""
The Net Attendance dataset shows the percentage of children who are regularly attending school at different levels, such as primary and secondary school. It helps identify regions or groups where school attendance needs improvement to ensure all children have consistent access to education.
""")
data_attendance = pd.read_csv('net_attendance.csv')
st.dataframe(data_attendance)

# Literacy Rate
st.header("Literacy Rate")
st.write("""
The Literacy Rate dataset shows the percentage of children who can read and write at different levels. This data helps identify areas that need more support to improve literacy skills and ensure every child can achieve basic education standards.
""")
data_literacy = pd.read_csv('literacy_rate.csv')
st.dataframe(data_literacy)

# School Age Digital Connectivity
st.header("School Age Digital Connectivity")
st.write("""
The School-Age Digital Connectivity dataset shows the percentage of children with access to the internet and digital devices. This data helps identify regions where improved digital infrastructure is needed to ensure all children can participate in digital learning.
""")
data_digital_connectivity = pd.read_csv('digital_connectivity.csv')
st.dataframe(data_digital_connectivity)

# Impact of My Idea
st.header("Impact of My Idea")
st.write("""
1. **Increased Awareness**: By highlighting the data on out-of-school children, the project raises awareness about the issue, bringing it to the attention of policymakers, educators, and the public.
2. **Data-Driven Insights**: The analysis provides valuable insights into the factors contributing to educational disparities, such as age, gender, family background, and location, enabling targeted interventions.
3. **Policy Recommendations**: The project offers actionable recommendations to policymakers, helping them create effective strategies to improve school attendance and completion rates.
4. **Resource Allocation**: Identifying regions with high out-of-school rates allows for better allocation of resources and support to the areas that need it most.
5. **Educational Programs**: The data can be used to design and implement educational programs that address specific challenges faced by different demographic groups.
6. **Digital Inclusion**: By analyzing ICT skills and digital connectivity, the project highlights the importance of digital literacy and access, promoting initiatives to bridge the digital divide.
7. **Community Engagement**: Engaging local communities in the discussion and solutions fosters a sense of ownership and responsibility towards ensuring every child has access to education.
8. **Long-Term Impact**: Ensuring that more children complete their education can have long-term positive effects on society, including reduced poverty rates and increased economic opportunities.
9. **Global Collaboration**: Sharing findings and best practices globally can inspire other countries and organizations to adopt similar approaches, creating a collective effort towards achieving universal education.
""")

# Importance of This Issue
st.header("Importance of This Issue")
st.write("""
The issue of out-of-school children is critically important for several reasons:
1. **Right to Education**: Every child has the right to education. Ensuring that all children can attend school is a fundamental human rights issue.
2. **Breaking the Cycle of Poverty**: Education is a powerful tool for lifting individuals and communities out of poverty. Children who do not receive education are more likely to remain trapped in poverty.
3. **Economic Growth**: Educated populations are essential for economic growth and development. Countries with higher education levels tend to have stronger economies and more stable societies.
4. **Empowerment and Equality**: Education promotes gender equality and empowers children, especially girls, to participate fully in their communities and economies.
5. **Health and Well-being**: Educated individuals are more likely to lead healthier lives, have better access to healthcare, and make informed decisions about their well-being.
6. **Social Stability**: Education fosters social cohesion and reduces the likelihood of conflicts. It encourages understanding, tolerance, and peaceful coexistence.
7. **Global Progress**: Addressing the education gap is essential for achieving global development goals, such as the United Nations Sustainable Development Goals (SDGs).
8. **Innovation and Adaptation**: Education equips children with the skills they need to adapt to changing environments and contribute to innovation and technological advancements.
""")

# Sources of Data Sets Used
st.header("Sources of Data Sets Used")
st.write("""
1. **Out-of-School Rates Dataset**:
   - Source: UNICEF
   - Title: Out-of-School Rate 2022
   - Year: 2022
   - URL: [UNICEF Out-of-School Rate](https://data.unicef.org/topic/education/out-of-school-children/)

2. **Adjusted Net Attendance Rates Dataset**:
   - Source: UNICEF
   - Title: Adjusted Net Attendance Rate 2022
   - Year: 2022
   - URL: [UNICEF Net Attendance Rate](https://data.unicef.org/topic/education/attendance/)

3. **Completion Rates Dataset**:
   - Source: UNICEF
   - Title: Completion Rate 2022
   - Year: 2022
   - URL: [UNICEF Completion Rate](https://data.unicef.org/topic/education/completion/)

4. **ICT Skills Proficiency Dataset**:
   - Source: UNICEF
   - Title: ICT Skills 2022
   - Year: 2022
   - URL: [UNICEF ICT Skills](https://data.unicef.org/topic/education/ict-skills/)

5. **Literacy Rates Dataset**:
   - Source: UNICEF
   - Title: Literacy Rate 2021
   - Year: 2021
   - URL: [UNICEF Literacy Rate](https://data.unicef.org/topic/education/literacy/)

6. **Digital Connectivity Dataset**:
   - Source: UNICEF
   - Title: School-Age Digital Connectivity 2022
   - Year: 2022
   - URL: [UNICEF Digital Connectivity](https://data.unicef.org/topic/education/digital-connectivity/)
""")

# Thank You Section
st.header("Thank You")
st.write("""
We extend our deepest gratitude to everyone who has contributed to the success of the SchoolWatch project.
**Special Thanks To**:
- **UNICEF** for providing invaluable datasets and resources.
- **Mentors and Advisors** for their guidance and support throughout the project.
- **Team Members** for their dedication and hard work in making this initiative a reality.
- **Hackathon Organizers** for providing a platform to showcase our work and drive change.
Lastly, thank you to all the attendees and participants for your interest and engagement. Together, we can make a significant impact on bridging the education gap and ensuring every child has access to quality education.
""")

# Presented By Section
st.header("Presented By")
st.write("""
**[KUMARI PRATIKSHA]**  
Project Lead and Data Analyst  
SchoolWatch Initiative
""")



