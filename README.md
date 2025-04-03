# analyze
# House Price Analysis

This repository contains a Python script for analyzing house price data across different countries over time. The script generates various visualizations and performs statistical tests to understand the trends, relationships, and distributions of key economic indicators related to house prices.

## Visualizations

The script generates the following visualizations:

1.  **Time Series Plot (`time_series.png`)**:
    * **Description**: A line plot showing the trend of the "House Price Index" over "Year" for the first 5 unique countries in the dataset. Each country's trend is represented by a separate line with a distinct color, and a legend identifies each country.
    * **Purpose**: To visualize how the house price index has changed over time for a subset of countries, allowing for a comparison of their temporal trends.
    * **Interpretation**: Look for patterns such as increasing or decreasing trends, volatility, and potential turning points in the house price index for each of the displayed countries.

2.  **Correlation Heatmap (`correlation_heatmap.png`)**:
    * **Description**: A heatmap displaying the pairwise correlations between numerical features in the dataset. The color intensity and the numerical annotations within each cell indicate the strength and direction (positive or negative) of the correlation. The `coolwarm` colormap is used, centered at 0.
    * **Purpose**: To identify which variables are strongly correlated with each other. This can help in understanding the relationships between factors like the House Price Index, Affordability Ratio, GDP Growth, and Inflation Rate.
    * **Interpretation**: Strong positive correlations (dark red) suggest that as one variable increases, the other tends to increase as well. Strong negative correlations (dark blue) suggest that as one variable increases, the other tends to decrease. Correlations close to zero (light colors) indicate a weak or no linear relationship.

3.  **Box Plot (`boxplot.png`)**:
    * **Description**: A box plot showing the distribution of the "House Price Index" for each "Country". Each box represents the interquartile range (IQR) of the house price index for a specific country, with a line inside indicating the median. Whiskers extend to show the variability outside the upper and lower quartiles, and individual points outside the whiskers represent potential outliers. The x-axis labels (country names) are rotated for better readability.
    * **Purpose**: To compare the central tendency, spread, and skewness of the house price index across different countries. It also helps in identifying potential outliers in each country's data.
    * **Interpretation**: Compare the median lines to see which countries have higher or lower median house price indices. The length of the boxes indicates the variability (IQR) within each country. Outliers may suggest unusual economic conditions or data points.

4.  **Distribution Plots (`distributions.png`)**:
    * **Description**: A series of histograms with kernel density estimates (KDE) overlaid, showing the distribution of four key numerical variables: "House Price Index", "Affordability Ratio", "GDP Growth (%)", and "Inflation Rate (%)". Each variable has its own subplot.
    * **Purpose**: To visualize the shape of the distribution of each variable, including its central tendency, spread, and skewness. The KDE provides a smooth estimate of the probability density function.
    * **Interpretation**: Examine the shape of each distribution. A bell-shaped curve suggests a normal distribution. Skewness (leaning to one side) indicates an asymmetry in the data. The spread of the distribution shows the variability of the variable.

5.  **3D Scatter Plot (`3d_scatter.html`)**:
    * **Description**: An interactive 3D scatter plot visualizing the relationship between "House Price Index" (x-axis), "Affordability Ratio" (y-axis), and "GDP Growth (%)" (z-axis). Each point represents a data entry, colored according to the "Country". The plot is saved as an interactive HTML file that can be opened in a web browser, allowing for rotation and zooming.
    * **Purpose**: To explore the multivariate relationship between these three key variables and how these relationships might differ across different countries.
    * **Interpretation**: Look for clusters of points belonging to the same country, which might indicate similar patterns in these three variables. Observe the overall trend and direction of the data points in the 3D space to understand how the variables jointly influence each other.

6.  **Pair Plot (`pairplot.png`)**:
    * **Description**: A grid of scatter plots showing the pairwise relationships between four selected numerical variables: "House Price Index", "Affordability Ratio", "GDP Growth (%)", and "Inflation Rate (%)". The diagonal of the grid contains histograms showing the distribution of each individual variable.
    * **Purpose**: To quickly visualize potential linear and non-linear relationships between all pairs of the selected variables, as well as the univariate distribution of each variable.
    * **Interpretation**: Examine the scatter plots for patterns or trends that suggest a relationship between two variables. The histograms on the diagonal provide information about the distribution of each variable.

7.  **Bar Chart (`bar_chart.png`)**:
    * **Description**: A bar chart showing the average "House Price Index" for each "Country". The countries are sorted in descending order based on their average house price index. The x-axis represents the countries (with labels rotated for readability), and the y-axis represents the average house price index.
    * **Purpose**: To compare the average house price index across different countries.
    * **Interpretation**: The height of each bar indicates the average house price index for that country. This allows for a direct comparison of which countries have, on average, higher or lower house price indices.

8.  **Pie Chart (`pie_chart.png`)**:
    * **Description**: A pie chart showing the distribution of the average "Urbanization Rate (%)" across different "Country". Each slice of the pie represents a country, and the size of the slice is proportional to the average urbanization rate of that country. The percentage contribution of each country is displayed on the pie chart.
    * **Purpose**: To visualize the relative proportion of average urbanization rates among different countries in the dataset.
    * **Interpretation**: The size of each slice indicates the proportion of the total average urbanization rate contributed by that country. This can help in understanding the relative levels of urbanization across the countries in the dataset.

## Statistical Tests

The script performs the following statistical tests:

1.  **Normality Tests (using `scipy.stats.normaltest`)**:
    * **Description**: For each of the numerical columns ('House Price Index', 'Affordability Ratio', 'GDP Growth (%)', 'Inflation Rate (%)'), the script performs the D'Agostino-Pearson normality test. This test assesses whether a sample of data has been drawn from a normal distribution.
    * **Hypotheses**:
        * **Null Hypothesis ($H_0$)**: The data is normally distributed.
        * **Alternative Hypothesis ($H_a$)**: The data is not normally distributed.
    * **Output**: For each column, the script prints the calculated test statistic and the p-value.
    * **Interpretation**: If the p-value is less than a chosen significance level (e.g., 0.05), we reject the null hypothesis and conclude that the data for that column is likely not normally distributed.

2.  **ANOVA Test (Analysis of Variance) (using `scipy.stats.f_oneway`)**:
    * **Description**: An ANOVA test is performed to compare the means of the "House Price Index" across different "Country" groups. This test determines if there are any statistically significant differences in the average house price index between the countries.
    * **Hypotheses**:
        * **Null Hypothesis ($H_0$)**: The means of the house price index are the same across all countries.
        * **Alternative Hypothesis ($H_a$)**: At least one country has a different mean house price index compared to the others.
    * **Procedure**: The `f_oneway` function takes the house price index values for each country as separate input arrays.
    * **Output**: The script prints the calculated F-statistic and the p-value.
    * **Interpretation**: If the p-value is less than a chosen significance level (e.g., 0.05), we reject the null hypothesis and conclude that there is a statistically significant difference in the average house price index between at least two of the countries. Note that ANOVA does not identify which specific countries have significantly different means; further post-hoc tests would be needed for that.

## Libraries Used

* `matplotlib.pyplot` for creating basic plots.
* `seaborn` for enhanced statistical visualizations.
* `pandas` for data manipulation.
* `plotly.express` for creating interactive plots (like the 3D scatter plot).
* `scipy.stats` for performing statistical tests.

## How to Use

1.  Ensure you have the necessary Python libraries installed (`pandas`, `matplotlib`, `seaborn`, `plotly`, `scipy`). You can install them using pip:
    ```bash
    pip install pandas matplotlib seaborn plotly scipy
    ```
2.  Make sure you have your data loaded into a pandas DataFrame named `df`. The DataFrame should contain columns such as 'Year', 'Country', 'House Price Index', 'Affordability Ratio', 'GDP Growth (%)', 'Inflation Rate (%)', and 'Urbanization Rate (%)'.
3.  Run the Python script. It will generate the visualization files (`.png` and `.html`) in the same directory and print the results of the statistical tests to the console.

Check the generated image files and the console output for the analysis results.
