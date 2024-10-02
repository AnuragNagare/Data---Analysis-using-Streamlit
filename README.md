# Data-Analysis-using-Streamlit

This code creates an **interactive dashboard** using **Streamlit** that allows users to analyze movies based on various criteria like score, genre, and year. It integrates several libraries like **Pandas** for data manipulation, **Plotly** and **Matplotlib** for visualizations, and **Streamlit** widgets for user interactivity. Here's a step-by-step breakdown of how the code works:

### 1. **Webpage Setup**
- **Streamlit Configuration**:
  - `st.set_page_config(page_title="Movies analysis", layout='wide')` sets the title of the webpage to **"Movies analysis"** and the layout to **wide**, so the content takes up the full width of the screen.
  - `st.header("Interactive Dashboard")` and `st.subheader("Interact with this dashboard using the widgets on the sidebar")` add a title and a subtitle to the webpage.

### 2. **Reading and Preparing Data**
- **Load CSV Data**: The code reads a movies dataset using `pd.read_csv()` from a URL and stores it in `movies_data`. The dataset contains information about movies like name, year, genre, score, and budget.
  - `movies_data.info()`, `movies_data.duplicated()`, and `movies_data.count()` print information about the dataset (data types, duplicated entries, number of rows, etc.), and `movies_data.dropna()` drops any rows with missing values to clean the data.

### 3. **Creating Sidebar Widgets**
- The sidebar contains widgets that allow the user to filter and interact with the dataset:
  - **Slider for Movie Scores**: 
    - A slider allows the user to filter movies by their score (`st.slider()`). The score can range from 1.0 to 10.0, and by default, it selects movies with scores between 3.0 and 4.0.
  - **Multiselect for Genres**: 
    - The `st.multiselect()` widget allows the user to choose multiple genres. By default, it selects genres like **Animation, Horror, Fantasy, and Romance**.
  - **Selectbox for Year**: 
    - The `st.selectbox()` widget lets the user choose a specific year to filter the movies released in that year.

### 4. **Handling Interactivity**
- **Score Filtering**: 
  - The `score_info` variable holds a boolean mask that checks whether the movie's score falls within the selected range from the slider.
- **Genre and Year Filtering**: 
  - The `new_genre_year` variable creates a boolean mask that filters movies based on both the selected genres (from `multiselect`) and the selected year (from `selectbox`).

### 5. **Displaying Filtered Data**
- The app uses Streamlit's **column layout** to show two visualizations side-by-side:
  - **Column 1** (`col1`):
    - Displays a list of movies filtered by genre and year using `st.dataframe()`. The filtered data (`dataframe_genre_year`) shows the name, genre, and year of each movie.
  - **Column 2** (`col2`):
    - Displays a **line plot** using **Plotly** to show the count of movies (grouped by genre) within the selected score range. The data is grouped by genre, and the plot is created using `px.line()`.

### 6. **Additional Visualization (Bar Graph for Budget)**
- The code also creates a bar chart using **Matplotlib** to show the average budget of movies grouped by genre:
  - **Data Preparation**: 
    - `avg_budget = movies_data.groupby('genre')['budget'].mean().round()` calculates the average budget for each genre.
  - **Plotting**: 
    - A **bar chart** is created using `plt.bar()` with genre on the x-axis and average budget on the y-axis. The chart is displayed on the app using `st.pyplot()`.

### Summary:
- **Input Filters**: Users can select the score range, genres, and year using interactive widgets in the sidebar.
- **Data Display**: The filtered list of movies is displayed in a table.
- **Visualizations**:
  - A **line plot** shows the count of movies per genre within the selected score range.
  - A **bar chart** displays the average movie budget for each genre.

This setup allows for a dynamic, interactive exploration of movie data, enabling users to quickly visualize patterns based on their selections.





https://github.com/user-attachments/assets/74c67e21-3f74-49d2-a9a1-adb127a4b92e

