# Dash Components

<center>
    <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/logo.png" width="300" alt="cognitiveclass.ai logo" />
</center>

### Objectives

After completing the lab you will be able to:

*   Work with Dash Callbacks

**Estimated time needed:** 30 minutes

### Dataset Used

[Airline Reporting Carrier On-Time Performance](https://developer.ibm.com/exchanges/data/all/airline?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01&cm_mmc=Email_Newsletter-\_-Developer_Ed%2BTech-\_-WW_WW-\_-SkillsNetwork-Courses-IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork-20297740&cm_mmca1=000026UJ&cm_mmca2=10006555&cm_mmca3=M12345678&cvosrc=email.Newsletter.M12345678&cvo_campaign=000026UJ) dataset from [Data Asset eXchange](https://developer.ibm.com/exchanges/data?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01&cm_mmc=Email_Newsletter-\_-Developer_Ed%2BTech-\_-WW_WW-\_-SkillsNetwork-Courses-IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork-20297740&cm_mmca1=000026UJ&cm_mmca2=10006555&cm_mmca3=M12345678&cvosrc=email.Newsletter.M12345678&cvo_campaign=000026UJ)

# About Skills Network Cloud IDE

This Skills Network Labs Cloud IDE (Integrated Development Environment) provides a hands-on environment in your web browser for completing course and project related labs. It utilizes Theia, an open-source IDE platform, that can be run on desktop or on the cloud.
So far in the course you have been using Jupyter notebooks to run your python code. This IDE provides an alternative for editing and running your Python code. In this lab you will be using this alternative Python runtime to create and launch your Dash applications.

### Important Notice about this lab environment

Please be aware that sessions for this lab environment are not persisted. When you launch the Cloud IDE, you are presented with a 'dedicated computer on the cloud' exclusively for you. This is available to you as long as you are actively working on the labs.

Once you close your session or it is timed out due to inactivity,  you are logged off, and this 'dedicated computer on the cloud' is deleted along with any files you may have created, dowloaded or installed.  The next time you launch this lab, a new environment is created for you.

*If you finish only part of the lab and return later, you may have to start from the beginning. So, it is a good idea to plan to your time accordingly and finish your labs in a single session.*

# Let's start creating dash application

### Theme

Extract average monthly arrival delay time and see how it changes over the year. Year range is from 2010 to 2020.

### Expected Output

Below is the expected result from the lab. Our dashboard application consists of three components:

*   Title of the application
*   Component to enter input year
*   Chart conveying the average monthly arrival delay

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/lab2\_output.png)

### To do:

1.  Import required libraries and read the dataset
2.  Create an application layout
3.  Add title to the dashboard application using HTML H1 component
4.  Add an input text box using core input component
5.  Add the line chart using core graph component
6.  Run the app

# Get the tool ready

*   Create a new python script, by clicking on the menu bar and selecting **File**->**New File**, as in the image below.

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/file1.png)

*   Provide the file name as `dash_interactivity.py`

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/lab2\_file.png)

*   Open a new terminal, by clicking on the menu bar and selecting **Terminal**->**New Terminal**, as in the image below.

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/lab2\_new_terminal.png)

*   Now, you have script and terminal ready to start the lab.

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/lab2\_terminal.png)

*   Install python packages required to run the application. Copy and paste the below command to the terminal.

```
pip install pandas dash
```

{: codeblock}

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/install.png)

# TASK 1 - Read the data

Let's start with

*   Importing necessary libraries
*   Reading the data

Copy the below code to the `dash_interactivity.py` script and review the code.

```
# Import required libraries
import pandas as pd
import plotly.graph_objects as go
import dash
import dash_html_components as html
import dash_core_components as dcc
from dash.dependencies import Input, Output

# Read the airline data into pandas dataframe
airline_data =  pd.read_csv('https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/Data%20Files/airline_data.csv', 
                            encoding = "ISO-8859-1",
                            dtype={'Div1Airport': str, 'Div1TailNum': str, 
                                   'Div2Airport': str, 'Div2TailNum': str})
```

{: codeblock}

# TASK 2 - Create dash application and get the layout skeleton

Next, we create a skeleton for our dash application. Our dashboard application layout has three components as seen before:

*   Title of the application
*   Component to enter input year inside a layout division
*   Chart conveying the average monthly arrival delay inside a layout division

Mapping to the respective Dash HTML tags:

*   Title added using `html.H1()` tag
*   Layout division added using `html.Div()` and input component added using `dcc.Input()` tag inside the layout division.
*   Layout division added using `html.Div()` and chart added using `dcc.Graph()` tag inside the layout division.

Copy the below code to the `dash_interactivity.py` script and review the structure.

*NOTE*: Copy below the current code

```
# Create a dash application
app = dash.Dash(__name__)

# Get the layout of the application and adjust it.
# Create an outer division using html.Div and add title to the dashboard using html.H1 component
# Add a html.Div and core input text component
# Finally, add graph component.
app.layout = html.Div(children=[html.H1(),
                                html.Div(["Input Year", dcc.Input(),], 
                                style={}),
                                html.Br(),
                                html.Br(),
                                html.Div(),
                                ])
```

{: codeblock}

# TASK 3 - Update layout components

### Application title

*   Heading reference: [Plotly H1 HTML Component](https://dash.plotly.com/dash-html-components/h1?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01)
*   Title as `Airline Performance Dashboard`
*   Use `style` parameter and make the title `center` aligned, with color code `#503D36`, and font-size as `40`. Check `More about HTML` section [here](https://dash.plotly.com/layout?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01).

### Input component

*   Update [dcc.Input](https://dash.plotly.com/dash-core-components/input?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01) component `id` as `input-year`, default `value` as `2010`, and `type` as `number`. Use `style` parameter and assign height of the input box to be `50px` and font-size to be `35`.
*   Use `style` parameter and assign font-size as `40` for the whole division.

### Output component

*   Add `dcc.Graph()` component to the second division.
*   Update [dcc.Graph](https://dash.plotly.com/dash-core-components/graph?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01) component `id` as `line-plot`.

# TASK 4 - Add the application callback function

The core idea of this application is to get year as user input and update the dashboard in real-time. We will be using `callback` function for the same.

Steps:

*   Define the callback decorator
*   Define the callback function that uses the input provided to perform the computation
*   Create graph and return it as an output
*   Run the application

Copy the below code to the `dash_interactivity.py` script and review the structure.

*NOTE*: Copy below the current code

```
# add callback decorator
@app.callback(Output(),
               Input())

# Add computation to callback function and return graph
def get_graph(entered_year):
    # Select data based on the entered year
    df =  airline_data[airline_data['Year']==int(entered_year)]
    
    # Group the data by Month and compute average over arrival delay time.
    line_data = df.groupby('Month')['ArrDelay'].mean().reset_index()
    
    # 
    fig = go.Figure(data=)
    fig.update_layout()
    return fig

# Run the app
if __name__ == '__main__':
    app.run_server()
```

{: codeblock}

# TASK 5 - Update the callback function

### Callback decorator

*   Refer examples provided [here](https://dash.plotly.com/basic-callbacks?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01)
*   Update output component id parameter with the id provided in the `dcc.Graph()` component and component property as `figure`.
*   Update input component id parameter with the id provided in the `dcc.Input()` component and component property as `value`.

### Callback function

*   Update `data` parameter of the `go.Figure()` with the scatter plot. Refer [here](https://plotly.com/python/line-and-scatter/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01#scatter-and-line-plot-with-goscatter). Sample syntax below:

```
go.Scatter(x='----', y='----', mode='-----', marker='----)
```

{: codeblock}

*   Update `x` as `line_data['Month']`, `y` as `line_data['ArrDelay']`, `mode` as `lines`, and `marker` as `dict(color='green')`.

*   Update `fig.update_layout` with title,  xaxis_title, and yaxis_title parameters.
    *   Title as `Month vs Average Flight Delay Time`
    *   `xaxis_title` as `Month`
    *   `yaxis_title` as `ArrDelay`
    Refer the update layout function [here](https://plotly.com/python/line-and-scatter/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01#style-scatter-plots).

Refer [here](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/4.7\_Dash_Interactivity.py) to know how your python code should look like.

# TASK 6 - Run the application

*   Firstly, install pandas and dash using the following command in the terminal

```
pip3 install pandas dash
```

{: codeblock}

*   Copy and paste the below command in the terminal to run the application.

```
python3 dash_interactivity.py
```

{: codeblock}

*   Observe the port number shown in the terminal.

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/port.png)

*   Click on the `Launch Application` option from the menu bar.

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/launch.png)

*   Provide the port number and click `OK`

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/l_port.png)

The app will open in a new browser tab like below:

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/labs/Module%204/images/lab2\_result.png)

### Congratulations, you have successfully created your dash application!

## Author

[Saishruthi Swaminathan](https://www.linkedin.com/in/saishruthi-swaminathan?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDV0101ENSkillsNetwork20297740-2021-01-01&cm_mmc=Email_Newsletter-\_-Developer_Ed%2BTech-\_-WW_WW-\_-SkillsNetwork-Courses-IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork-20297740&cm_mmca1=000026UJ&cm_mmca2=10006555&cm_mmca3=M12345678&cvosrc=email.Newsletter.M12345678&cvo_campaign=000026UJ)

## Changelog

| Date       | Version | Changed by | Change Description      |
| ---------- | ------- | ---------- | ----------------------- |
| 05-07-2021 | 1.0     | Saishruthi | Initial version created |

## <h3 align="center"> Â© IBM Corporation 2020. All rights reserved. <h3/>