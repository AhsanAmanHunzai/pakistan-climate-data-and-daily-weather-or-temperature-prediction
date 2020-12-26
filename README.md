# pakistan-climate-data-and-daily-weather-or-temperature-prediction
This was my Semester project for Machine Learning course by Dr. Saeed Rehman. In this repository I have also open-sources the collected dataset and with time I will try my best to improve its documentation and its overall working. The dataset contains data of almost 7 parameters which can be used in many other predicting model.
## [Weather/Temperature Prediction] Project Report
## Contents

- Project Name:
- Details about Dataset:
   - Target/Location Dataset:
   - Was dataset available online (in one collectable form)?
- Tools used to Process Data
   - Macro Recorder
   - Source of data
   - Google Form..............................................................................................................................................
- Implementation in MATLAB
   - Initial setup
   - Filter data
   - Displaying Plots
- Regression
   - Code:
   - Testing or Demonstration:
      - First try:
      - Second try
   - Data Matrix/Comparison


## Project Name:

Weather Prediction

## Details about Dataset:

### Target/Location Dataset:

Islamabad, Pakistan

### Was dataset available online (in one collectable form)?

No, I wasn’t able to find a collection or dataset relating to Pakistan weather I had to design and code a
special program to that would scrap the data relating to Pakistani weather and collect and much data as
possible.

[http://www.pmdnmcc.net/RealTime/Data/CT.txt](http://www.pmdnmcc.net/RealTime/Data/CT.txt)

The above image shows the data the PMD has published and this data itself has no additional
parameters and the file itself is Plaint Text and not CSV (Comma Separated Values). This led to the
conclusion that the data published was not useful.


## Tools used to Process Data

### Macro Recorder

At first, I used **Macro recorder** to automate the process of collecting dataset from the online discreate
sources available and coding as well as the screen capture was done all in a custom and unique way.

I did make a short video clip of the process which would demonstrate how the macro was working.

YouTube: https://youtu.be/-duyzc3GyAM

### Source of data

I used the website [http://www.worldweatheronline.com](http://www.worldweatheronline.com) to capture data with the method mentioned above.

Since I was able to collect valuable data in a short period of time I decided to open-source the data so
that other students or researchers on the internet can contribute and find it helpful as well.

Link to my profile:

https://data.world/ahsanaman/ (Check the resources)

https://data.world/ahsanaman/ahsanamanpakistan-climate-data-and-daily-weather-reports

(this is direct link)

### Google Form..............................................................................................................................................

When the data was captured the macro, script was recorded in a way that, it was able to copy each
year’s data in a variable and post it in Google Form that I designed specifically for this project.

Using Google Form gave me the advantage that it automatically aligns the data and keeps a clean record
for the data entered, also it would export it in different file types like **CSV** , **PDF** ... etc.


## Implementation in MATLAB

### Initial setup

At first, we need to import the data into the MATLAB work environment.

We need to keep in mind that for training purposes we do need to keep the number of indexes or
categories same for each and every variable. Therefore, we need to set a condition for excluding rows
with un-importable cells.

### Filter data

After we import, we first need to run

### %% Filter Data
```
 daymonth=datetime(daymonth,'InputFormat','MM/dd/yyyy');
```
### This will convert the string datetime to actual datetime

### format


### Displaying Plots

Once we convert the class of the variable we can then use:
```
%% This is for Plotting the data for Humidity & Rain

hold on

 plot(daymonth,humidity,'LineWidth',3)

plot(daymonth,rain,"r",'LineWidth',3)

set(gca,'FontSize',6,'FontWeight','bold')

hold off
```
to display this plot that show relation between **Humidity** and **Rain.**

Keep in note that we have intentionally **excluded** the month June, October, November, December for
testing purposes.


Now run this code:
```
 %% This is for Plotting the data for Max and Min

### temperature

hold on

plot(daymonth,max_temp,'LineWidth',3)

plot(daymonth,min_temp,"r",'LineWidth',3)

plot(daymonth,avg_temp,"-g",'LineWidth',3)

set(gca,'FontSize',6,'FontWeight','bold')

 hold off
```
to display the plot that shows the relation between **MAX** , **MIN** & **AVERAGE** Temperature:

```
### %% This Plotting represents the combine effect of climate change

plot(daymonth,rain,'DisplayName','rain','LineWidth',2);

hold on;

 plot(daymonth,humidity,'DisplayName','humidity','LineWidth'2);

plot(daymonth,avg_temp,'DisplayName','avg_temp','LineWidth',2);

hold off;
```

## Regression

Since the workspace is all setup and running now, we need to open the Curve Fitting App that is all built-
in in MATLAB and add the following variables

```
### Code:

function [fitresult, gof] = createFit(humidity, pressure,avg_temp)

%CREATEFIT(HUMIDITY,PRESSURE,AVG_TEMP)

### % Create a fit.

### %

### % Data for 'untitled fit 1' fit:

### % X Input : humidity

### % Y Input : pressure

### % Z Output: avg_temp

### % Output:

### % fitresult : a fit object representing the fit.

### % gof : structure with goodness-of fit info.

### %

### % See also FIT, CFIT, SFIT.

### % Auto-generated by MATLAB on 25-Dec-2020 02:00:

### %% Fit: 'untitled fit 1'.

 [xData, yData, zData] = prepareSurfaceData( humidity,pressure, avg_temp );

### % Set up fittype and options.

ft = fittype( 'poly11' );

% Fit model to data.

[fitresult, gof] = fit( [xData, yData], zData, ft );

 % Plot fit with data.

figure( 'Name', 'untitled fit 1' );

 h = plot( fitresult, [xData, yData], zData );

legend( h, 'untitled fit 1', 'avg_temp vs. humidity, pressure', 'Location', 'NorthEast', 'Interpreter', 'none');

### % Label axes

xlabel( 'humidity', 'Interpreter', 'none' );

ylabel( 'pressure', 'Interpreter', 'none' );

zlabel( 'avg_temp', 'Interpreter', 'none' );

 grid on

 view( -169.7, 23.2 );
```

### Testing or Demonstration:

### As we mentioned earlier in the document, we excluded some of the Months

### intentionally for testing purpose now we are going to test our model for the test data.

#### To load our model we need to select the target path on the MATLAB and run the following code

#### on Live script

```
model= createFit_Code(humidity,pressure,avg_temp)
```
our model is now created

#### First try:


#### Second try


### Data Matrix/Comparison

# Actual Average temperature Predicted Average Temperature

# 16(actual) 17(predicted)

# 31(actual) 31(predicted)


