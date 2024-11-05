# Active Product Sales Analysis with Python

**Project Overview**

The Active Product Sales Analysis project provides a data-driven approach to analyzing sales patterns throughout the day. By examining transaction frequencies across various hours, this analysis identifies peak sales times, offering valuable insights for business strategy and promotional planning.

Through Python’s powerful data analysis libraries, this project processes and visualizes transactional data to highlight sales trends and uncover actionable insights. It includes everything from data preprocessing and time-based analysis to visualizations that inform business decisions.

**Contents**

* Installation
* Dataset Overview
* Project Workflow
* Data Visualization
* Insights and Conclusion

**Installation**

To get started with the project, install the following required Python packages:

* **numpy**

* **pandas**

* **matplotlib**

Install these packages using pip:

      pip install numpy pandas matplotlib

**Dataset Overview**

The dataset (**Order_details-masked.csv**) contains transaction data with time-stamped records. This project focuses on analyzing the time of day that each transaction occurred, specifically examining hourly transaction frequencies to identify high-activity periods.

**Project Workflow**

**1. Data Preparation**

* **Import Libraries:** Load essential libraries (**numpy, pandas**, and **matplotlib**) for data handling and visualization.

* **Load Dataset:** Import the transaction dataset into a pandas DataFrame for easy access and analysis.

      import numpy as np
      import pandas as pd
      import matplotlib.pyplot as plt

      Order_Details = pd.read_csv(r"path_to_file/Order_details-masked.csv")
      Order_Details.head()

  ![image](https://github.com/user-attachments/assets/1cc78f25-d7ca-48c3-a132-9ac27bc9c24c)


**2. Creating a Time Column**

* **Convert Transaction Dates:** Transform the **Transaction Date** column to a DateTime format to enable time-based analysis.

* **Extract Hourly Data:** Create a new column to extract the hour of each transaction, setting up the data for hourly trend analysis.

      Order_Details['Time'] = pd.to_datetime(Order_Details['Transaction Date'])
      Order_Details['Hour'] = Order_Details['Time'].dt.hour

**3. Identifying Peak Sales Hours**

* **Calculate Hourly Frequencies:** Use **value_counts** to count transactions for each hour, highlighting the busiest periods.

* **Select Top 24 Hours:** For illustration, display the top 24 hours with the highest transaction frequencies.

      timemost1 = Order_Details['Hour'].value_counts().index.tolist()[:24]
      timemost2 = Order_Details['Hour'].value_counts().values.tolist()[:24]

**4. Structuring Hourly Data**

* **Organize Data:** Combine hours and their transaction counts for easier analysis and display.

      tmost = np.column_stack((timemost1, timemost2))
      print(" Hour Of Day" + "\t" + "Cumulative Number of Purchases \n")
      print('\n'.join('\t\t'.join(map(str, row)) for row in tmost))

**5. Visualizing Sales Patterns**

* **Plotting Hourly Transactions:** Use a line plot to visualize the number of transactions across hours, revealing peak sales periods.

      plt.figure(figsize=(20, 10))
      plt.title('Sales Frequency Per Hour (Weekly Distribution)',
                fontdict={'fontname': 'monospace', 'fontsize': 30}, y=1.05)
      plt.ylabel("Number Of Transactions", fontsize=18, labelpad=20)
      plt.xlabel("Hour of Day", fontsize=18, labelpad=20)
      plt.plot(timemost1, timemost2, color='m')
      plt.grid()
      plt.show()

![image](https://github.com/user-attachments/assets/37098179-9dc1-4870-a0e6-6ed854d85cc1)


**Insights and Conclusion**

The analysis indicates distinct patterns in sales activity, with late evening hours exhibiting the highest transaction volumes. Such insights can guide business decisions, such as timing promotional efforts during peak sales periods. By leveraging these findings, businesses can align marketing and operations with customer purchase behavior, optimizing both engagement and sales potential.

This project exemplifies how structured data analysis can transform transaction data into actionable business insights, paving the way for deeper exploration into customer preferences and buying habits.


















