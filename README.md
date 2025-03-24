# British-Airways-Customer-Satisfaction-Dashboard

## Introduction
This Power BI project is an end-to-end portfolio dashboard designed to visualize customer reviews of British Airways. The interactive dashboard allows users to analyze customer feedback based on various metrics, filter data dynamically, and explore insights effectively.

## Features
- 📊 **Interactive Metrics Selection**: Users can toggle between different metrics such as Overall Rating, Cabin Staff Service, Entertainment, Food, Ground Service, Seat Comfort, and Value for Money.
- 🌍 **Geographic Analysis**: A map visualization displaying reviews by country, allowing users to filter data based on location.
- 📅 **Time-based Trends**: A timeline visualization showcasing average ratings by month.
- ✈️ **Aircraft-wise Ratings**: A bar chart illustrating the average customer rating by aircraft model.
- 🔎 **Comprehensive Filtering Options**: Users can filter data based on traveler type, seat type, aircraft model, continent, and date.
- 📈 **Summary Metrics**: Key performance indicators (KPIs) displayed at the top for quick insights.

## Data Sources
- **CSV Files**:
  - `ba_reviews.csv`: Contains customer reviews with columns such as author, date, review location, and multiple rating categories.
  - `countries.csv`: Maps review locations to corresponding countries and continents.

## Implementation in Power BI
### 1. **Data Loading & Transformation**
- Import both CSV files into Power BI.
- Use Power Query to clean and transform data:
  - Ensure proper data types for numerical and categorical columns.
  - Create a relationship between `ba_reviews` and `countries` tables based on the `Place` and `Country` columns.

### 2. **Creating Key Metrics**
- Define **DAX Measures** for average ratings across different categories:
  ```DAX
  AverageRating = AVERAGE(ba_reviews[Rating])
  AverageCabinStaff = AVERAGE(ba_reviews[Cabin_Staff])
  AverageEntertainment = AVERAGE(ba_reviews[Entertainment])
  ```
- Create a **DAX Parameter Table** to allow users to toggle between different metrics dynamically.

### 3. **Building the Visualizations**
- **Map Visualization**:
  - Convert `Place` to a geographical data type and use a Filled Map to display reviews by country.
  - Use color gradients to represent average ratings.
- **Time Series Chart**:
  - Use a Line Chart to show monthly trends in average ratings.
  - Enable slicers for filtering by different traveler types.
- **Aircraft Ratings Bar Chart**:
  - Use a clustered bar chart to display average ratings per aircraft model.
  - Group aircraft models with fewer than 50 reviews into an "Other" category for better visualization.
- **Summary KPI Cards**:
  - Display overall average ratings using **KPI cards**.
  - Format numbers to one decimal place for readability.

### 4. **Filters & Interactivity**
- **Slicers**:
  - Implement slicers for Traveler Type, Seat Type, Aircraft Model, and Continent.
  - Ensure cross-filtering across all visuals.
- **Dynamic Titles**:
  - Use **DAX expressions** to update titles dynamically based on the selected metric.
  ```DAX
  SelectedMetricTitle = "Average " & SELECTEDVALUE(MetricTable[Metric]) & " by Country"
  ```

### 5. **Design Enhancements**
- Use a **consistent color scheme** (e.g., green for positive ratings, red for low ratings).
- Format tooltips to display both rating scores and review counts.
- Adjust axis scales and gridlines for a cleaner layout.


## Conclusion
This Power BI portfolio project demonstrates how to create a professional and interactive dashboard for analyzing customer feedback. By following best practices in data visualization and interactive filtering, this dashboard provides actionable insights for business decision-making.

