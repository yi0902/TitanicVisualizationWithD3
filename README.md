# TitanicVisualizationWithD3
This project shows how to build a story-telling visualization with D3 through iterations.

## Summary
The chart is showing the difference of survival rates with regards of gender/pclass/age of Titanic passengers. A clear message is presented :  for each category (age/pclass combination), women had a much higher survival rate than men. If we only look into women, almost more than 90% of women of pclass 1 and 2 were survived, while women of pclass 3 with age between 40 and 60 had the lowest survival rate (less than 30% survived). Regarding men, for pclass 1 and 3, it seems that the survival rates decrease when the age increase.

## Design

###Initial design

![alt tag](viz/plot_1.png?raw=true)

**Chart type:** scatterplot 

**Visual encoding:**
	
	x-axis: Age
	y-axis: Fare
	color: Survived
	size: SibSp+Parch

**Interaction:**

+ *mouse-over data point:* show Name, Sex, SibSp, Parch, Pclass, Ticket, Cabin, Embarked, Survived, Age, Fare
+ *click on legends:* show/hide survived or non-survived data points

To be honest, I didn't think deeply for the initial design. I was more in the spirit to show as much as possible of information to users, which proved to be not efficient at all lately.

I chose scatter-plot though it couldn't give clear messages because I wanted to show users the dispersion of survived and non-survived people among age and ticket price dimensions, and leave users to get their own understanding of the dispersion. Age and Fare were chosen as axes because I thought they were two interesting features to look into. The color of data points was defined by the survival state, which can help distinguish easily survived & non-survived people's dispersion. I encoded the SibSp and Parch numbers into the size of points as I wanted to make users see if SibSp+Parch numbers of a person could impact his/her survival chance. I added many features in the mouse-over tool-tips in the aim of leaving users maximum of information to explore.

### 2nd design

![alt tag](viz/plot_2.png?raw=true)

After collecting feedback from Renaud and Charles, I think the main problem of the initial design is that it's not obvious to get messages from the chart as there isn't a clear relationship between age and fare. Renaud recommended to change the chart type, while I still want to use scatter-plot to show the data dispersion on these two dimensions. So I decided to enrich the information in the chart to overcome this shortcoming. 

+ Add four selective buttons to filter data in order to make patterns more clear
+ Add two information boxes to show the number of survived and non-survived people under different combinations/categories
+ Add another information box to show more clearly the ratio of survived people vs non-survived people

Other points mentioned in Renaud and Charles' feedback have also been improved:

+ Removed the "Parch", "SibSp", "Ticket" and "Embarked" information as they don't seem to be helpful in showing clear messages (no obvious patterns)
+ Changed the y axis label from "Fare" to "Ticket Price"

### 3rd design

![alt tag](viz/plot_3.png?raw=true)

The feedback of Pierre and Sébastien from 2nd iteration seem to be positive and they discovered main messages that I want to convey. 

Pierre identified an over-plotting issue when all data points are presented. So I reduced the size of data points to make the chart less charged. I also added the description of Pclass parameter at the bottom of the chart to make it more readable and clear for users (which should be done in 2nd design according to the feedback of Renaud).

+ For the question of outlier: I don't think they were outliers as they proved to be very rich people after searching in google
+ For the question of if all people are presented: the answer is no, as I excluded data points that have null values in age or fare field. This information can be found at the bottom of the chart.
  
### 4th design

![alt tag](viz/plot_4.png?raw=true)

The feedback from Udacity coach pointed to the same problem that Renaud mentioned: the scatter-plot was not efficient to convey messages of differences in terms of survival rate for combinations of gender/pclass/age. He suggested to use bar chart or pie chart.

I didn't agree much in the beginning as the 2nd design was more exploratory, changing to bar chart or pie chart would lose the dispersion information of survived & non-survived people. Then I realized that it was indeed not necessary to keep such information as my object was to show survival numbers/rates. So I changed to chart type to bar chart to make it easier to observe the survived number vs non-survived number. I used red bar to represent non-survived people number and green bar survived people. The chart was stayed exploratory.

### final design

![alt tag](viz/plot_final.png?raw=true)

From Ludovic's feedback, I realized that the chart was still not direct and efficient in terms of comparing survival rates of different combinations of gender/pclass/age. In additional, as there was a very obvious difference of survival rates between men and women, it worth to point it out directly for users instead of leaving them exploring.

So I decided to change the chart to be explanatory by displaying directly the survival rates of different categories in the same chart. 

+ The category axis was ordered first by pclass, then by age inside each pclass. 
+ I chose line chart to show the trends of survival rates along increasing of age and pclass. Two survival rates lines were plotted (one for men, the other for women) to make direct comparisons between gender on each category. 
+ The size of the bubbles on the lines represents the number of men/women fallen into this category, which could give an idea of reliability of the survival rate in this category.
+ I added two dash lines to better separate the pclasses on the category axis
+ Also, three background texts were added to indicate the pclass zones

## How to use?

In order to have an iteractive visualization, you need to launch a local http web server in the root folder. 

For example, you can start un command line console in the root folder and enter "c:\Python27\python.exe -m SimpleHTTPServer".

When the server is launched, go to your brower and type "http://localhost:8000/".

## Resources
[Dimple.js documentation](https://github.com/PMSI-AlignAlytics/dimple/wiki/dimple.chart)

[Dimple.js interactive lengend](http://dimplejs.org/advanced_examples_viewer.html?id=advanced_interactive_legends)

[Dimple.js storyboard control](http://dimplejs.org/advanced_examples_viewer.html?id=advanced_storyboard_control)

[Stackoverflow add vertical line](http://stackoverflow.com/questions/29352970/dimple-js-add-vertical-line)

[Bootstrap w3schools section](http://www.w3schools.com/bootstrap/)

[JQuery w3schools section](http://www.w3schools.com/jquery/)
