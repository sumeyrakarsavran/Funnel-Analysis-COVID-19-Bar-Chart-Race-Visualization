# Funnel Analysis & COVID-19 Bar Chart Race Visualization

This project demonstrates advanced data visualization techniques using Plotly and `bar_chart_race`. It includes two complementary visualizations: a funnel chart representing a conversion process and an animated bar chart race showing the spread of COVID-19 cases across countries over time.

<img width="1340" height="525" alt="newplot" src="https://github.com/user-attachments/assets/c96bd302-bc3e-4c93-b8df-1a0195fb6dde" />


https://github.com/user-attachments/assets/d09dc95f-d60f-4cee-94da-fd2b5ebbd6ec


## Project Overview

The project focuses on storytelling with data by transforming raw numbers into clear visual insights. It demonstrates how to:

- Visualize step-by-step conversion funnels using Plotly
- Animate time-series data into shareable MP4 videos with `bar_chart_race` and `ffmpeg`
- Compare multiple countries over time and show dynamic ranking changes

## Technologies Used

- Python
- pandas
- plotly
- bar_chart_race
- ffmpeg (for video rendering)

## Installation

Install required libraries:

```
pip install plotly
pip install bar_chart_race
pip install ffmpeg
```

Note: `ffmpeg` is required to export the animation as an MP4 video.

## Part 1: Funnel Chart Visualization

A funnel chart visualizes a multi-step conversion process where participants drop off at each stage.

Example stages:

- Website visit
- Downloads
- Potential customers
- Requested price
- Invoice sent

Purpose:

- Analyze conversion efficiency
- Identify bottlenecks in a process
- Present marketing or sales pipelines clearly

The funnel is created using Plotly Express for interactivity and clear presentation.

## Part 2: COVID-19 Bar Chart Race Animation

Dataset

Source: `corona_dat.csv`

Countries analyzed (example): China, Italy, Brazil, Spain, United States, Turkey

Data processing steps:

- Use the date column as the time index
- Filter and select country-level data
- Calculate cumulative case counts where needed
- Prepare time-series data in wide format for animation

Bar chart race visualization:

- Shows how COVID-19 cases evolved over time
- Provides relative comparisons between countries
- Highlights dynamic ranking changes across dates

Output:

- MP4 video file: `covid19.mp4` (example output name)
- Animated visualization generated programmatically and exportable for presentations

## Example Usage

Create and export a bar chart race (high-level example):

```python
import pandas as pd
import bar_chart_race as bcr

# load and prepare data
df = pd.read_csv('corona_dat.csv', parse_dates=['date'])
# pivot so index is date and columns are countries
df_pivot = df.pivot(index='date', columns='country', values='cases').fillna(0)

# create animation
bcr.bar_chart_race(df=df_pivot, filename='covid19.mp4', orientation='h', sort='desc')
```

For the funnel chart, use Plotly Express to create an interactive funnel and display or save it as HTML for sharing.
