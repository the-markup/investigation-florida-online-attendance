# Online Attendance in Florida

This repository contains data related to our story, "[Remote Learning During the Pandemic Has Hit Vulnerable Students the Hardest.](https://themarkup.org/coronavirus/2020/08/13/remote-learning-attendance-inequity-florida-schools)"

In general, the data for our findings can be found in the `data` folder. Responsive data from our public records requests can be found in the `/data/input/foia` folder, all formatted as csv files. 

## Installation

For the python portion, run `pip install -r requirements.txt`.

For the R notebook, we recommend following the [R programming language in Jupyter Notebook](https://docs.anaconda.com/anaconda/navigator/tutorials/r-lang/) installation instructions in the Anaconda documentation. 

## Notebooks

### 0-scraping-florida-scorecard

This notebook can be used to automatically populate the `data/input/scorecard` folder. Run this before running other notebooks.

### 1-creating-florida-crosswalks

Some school districts included only the schools' names in their public records response. This notebook matches the names with their corresponding school number. 

### 2-cleaning-florida-csvs

This notebook generates a csv file that combines online attendance data, historical data, and school demographic data. Results are later used in `4-analysis-r`. 

### 3-analysis

This notebook calculates figures and statistics used in the story. 

### 4-analysis-r

This notebook calculates additional figures and statistics used in the story. 

## Data

This folder contains csv-formatted data we received from districts in Florida in response to public records requests, data obtained from the Florida Department of Education website, and data we created in reporting our story.

### Public Records Response Data

Public records response data can be found as csv files in the `data/input/foia` folder.

We sent public records requests to school districts in the [10 most populous](https://www.florida-demographics.com/counties_by_population) Florida counties asking for attendance rates broken down by individual schools, starting when distance learning began in March. We chose to focus on Florida because of its strong public records law, large school districts, and news reports indicating counties were keeping attendance records. 

We received responsive, usable data from three districts: Broward, Hillsborough, and Miami-Dade. The others either did not respond, declined to provide data, or provided only very general figures. 

Of those three, Broward was the only district that provided daily attendance and enrollment figures. Miami-Dade provided daily attendance percentages, while Hillsborough provided weekly figures instead of daily counts.

### Florida Department of Education Data

#### Historical Attendance Data
To get a sense of what attendance looked like before the pandemic and the switch to remote learning, we compared the Broward data with the average daily attendance rate for the 2018–19 school year, which the [Florida Department of Education maintains](http://www.fldoe.org/accountability/data-sys/edu-info-accountability-services/pk-12-public-school-data-pubs-reports/students.stml) for each school.

#### School Demographic and Performance Data

We also wanted to look at not just overall attendance, but also how the move online is impacting kids of different races and socioeconomic levels, and whether schools already struggling with academic achievement were faring differently. 

We pulled information about each school from the [Florida Department of Education’s 2018-2019 School Report Cards](https://edudata.fldoe.org/ReportCards/Schools.html?school=0051&district=43). We used each school’s letter grade, found at the top of the report, to assess its academic achievement. Florida assigns each public school a letter grade–A, B, C, D, or F–to “provide an easily understandable way to measure the performance of a school.” Schools are graded on to 11 components, including standardized test performance and graduation rates. We also pulled information on the age groups each school serves, its Title I status, and whether or not it was an alternative school. For Miami-Dade, we gathered the student count included at the top of each report card to get an estimate of what their daily attendance counts were.

Additionally, we used the economic and race/ethnicity classifications found in the "Educator Qualifications and Equity" section of each report card.

For what Florida refers to as a “poverty classification,” the state uses:

> Free and Reduced Price Lunch (FRPL) data submitted by districts for students enrolled in public schools during survey 2 (October). The USDA National School Lunch Program multiplier is applied, if applicable, to the school's FRPL rate and then all public schools in the state are ranked highest to lowest with the top 25% of schools classified as high poverty, the bottom 25% of schools classified as low poverty, and the middle 50% as neither high nor low poverty.

For what Florida refers to as a “minority classification,” the state uses:

> demographic data submitted by districts for students enrolled in public schools during survey 2 (October). The school's minority rate includes enrolled students with a race/ethnicity of Hispanic, American Indian/Alaska Native, Asian, Black/African American, or Native Hawaiian/Other Pacific Islander. All public schools in the state are ranked using their minority rate from highest to lowest with the top 25% of schools classified as high minority, the bottom 25% of schools classified as low minority, and the middle 50% as neither high nor low minority. 

A “data note” explains that both classifications are meant to help “parents and others to compare schools with similar populations.”

### Cleaned Data

For the Broward public record response data, we had to match school names with school IDs in order to merge with other datasets. These keys can be generated with the `notebooks/1-creating-florida-crosswalks.ipynb` notebook and subsequently found in the `data/intermediary/keys` folder.

A merged version of the Broward data used to create the graphics in our story, `data/output/broward.csv`, can be generated with the `notebooks/2-cleaning-florida-csv.ipynb` notebook. This notebook also does a similar analysis to estimated Miami-Dade data.

## Licensing

Copyright 2020, The Markup News Inc.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
