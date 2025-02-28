# A-look-into-Edmonton-Bike-Riders-
What the project does
This project explores Bike Riding Habits of biker riders in Edmonton

Why the project is useful
Can help map out ways to give support to people in order to encourage bike riding using demographic information

How users can get started with the project:
Edmonton Open Data Portal is where the dataset is located
Original Data Set: “Bike Ridership - Edmonton Insight Community”
Number of Respondents: 816
Community Insight Members: 646
Anonymous Respondents: 170

Where users can get help with your project:
- Adding in more variables to consider
- Utilizing and adding in larger data sets from Edmonton and or other cities in Alberta and Canada
  
Who maintains and contributes to the project:
Currently, I maintain the project 

Here is the code I used:

import pandas as pd
bike = pd.read_csv('bike.csv')
bike.index +=1
bike.head()

bike = bike.rename(columns={'Why_Ride_Bike_To go shopping, dine out, run errands, visit people, go to a movie or similar activities (transportation trips)': 'Entertainment/Errands',
                            'Why_Ride_Bike_Recreation or leisure enjoyment': 'Recreational', 'Why_Ride_Bike_Commuting to work or school': 'Commute',
                            'Why_Ride_Bike_Other reasons': 'Other Reasons', 'Age_Rollup_Detailed (Study: Profiling Questionnaire 2014)': 'Age Range',
                            'Q15_Household_Income (Study: Profiling Questionnaire 2014)': 'Household Income'})
Biking_in_Edmonton = bike[['Age Range', 'Commute', 'Other Reasons', 'Entertainment/Errands', 'Recreational', 'Household Income']] ##Added new variable
Biking_in_Edmonton = Biking_in_Edmonton[Biking_in_Edmonton['Age Range'] != 'Did not answer' ]
Biking_in_Edmonton = Biking_in_Edmonton.dropna()
Biking_in_Edmonton

Age_range2 = Biking_in_Edmonton[['Age Range']]
Household_Income = Biking_in_Edmonton[['Household Income']]

bb = Biking_in_Edmonton[['Commute']]
Commute_yes = bb[bb['Commute'] == 1]
Commute_yes = Commute_yes.rename(columns={'Commute': 'Yes Commute'})

dd = Biking_in_Edmonton[['Commute']]
Commute_no = dd[dd['Commute'] == 0]
Commute_no = Commute_no.rename(columns={'Commute': 'No Commute'})
Commute_no['No Commute'] = Commute_no['No Commute'].replace({0: 1})

cc = Biking_in_Edmonton[['Other Reasons']]
Other_yes = cc[cc['Other Reasons'] == 1]
Other_yes = Other_yes.rename(columns={'Other Reasons': 'Yes Other'})

ee = Biking_in_Edmonton[['Other Reasons']]
Other_no = ee[ee['Other Reasons'] == 0]
Other_no = Other_no.rename(columns={'Other Reasons': 'No Other'})
Other_no['No Other'] = Other_no['No Other'].replace({0: 1})

rr = Biking_in_Edmonton[['Recreational']]
Recreational_yes = rr[rr['Recreational'] == 1]
Recreational_yes = Recreational_yes.rename(columns={'Recreational': 'Yes Recreational'})

tt = Biking_in_Edmonton[['Recreational']]
Recreational_no = tt[tt['Recreational'] == 0]
Recreational_no = Recreational_no.rename(columns={'Recreational': 'No Recreational'})
Recreational_no['No Recreational'] = Recreational_no['No Recreational'].replace({0: 1})

jj = Biking_in_Edmonton[['Entertainment/Errands']]
Entertainment_yes = jj[jj['Entertainment/Errands'] == 1]
Entertainment_yes = Entertainment_yes.rename(columns={'Entertainment/Errands': 'Yes Entertainment'})

kk = Biking_in_Edmonton[['Entertainment/Errands']]
Entertainment_no = kk[kk['Entertainment/Errands'] == 0]
Entertainment_no = Entertainment_no.rename(columns={'Entertainment/Errands': 'No Entertainment'})
Entertainment_no['No Entertainment'] = Entertainment_no['No Entertainment'].replace({0: 1})

Dataset3 = pd.concat([Age_range2, Household_Income, Commute_yes, Commute_no, Other_yes, Other_no, Recreational_yes, Recreational_no, Entertainment_yes, Entertainment_no], axis=1)

Dataset3 = Dataset3.fillna(0)
Dataset3


qw = Household_Income[['Household Income']]
qw1 = qw[qw['Household Income'] == 'Prefer not to answer']
qw1 =  qw1.rename(columns={'Household Income': 'Prefer not to answer'})
qw1 = (qw1['Prefer not to answer'] != 1).astype(int)

qw2 = qw[qw['Household Income'] == 'Under $20,000']
qw2 = qw2.rename(columns={'Household Income': 'Under $20,000'})
qw2 = (qw2['Under $20,000'] != 1 ).astype(int)

qw3 = qw[qw['Household Income'] == '$20,000 to $29,999']
qw3 = qw3.rename(columns={'Household Income': '$20,000 to $29,999'})
qw3 = (qw3['$20,000 to $29,999'] != 1).astype(int)

qw4 = qw[qw['Household Income'] == '$30,000 to $39,999']
qw4 = qw4.rename(columns={'Household Income': '$30,000 to $39,999'})
qw4 = (qw4['$30,000 to $39,999'] != 1).astype(int)

qw5 = qw[qw['Household Income'] == '$40,000 to $49,999']
qw5 = qw5.rename(columns={'Household Income': '$40,000 to $49,999'})
qw5 = (qw5['$40,000 to $49,999'] != 1).astype(int)

qw6 = qw[qw['Household Income'] == '$50,000 to $59,999']
qw6 = qw6.rename(columns={'Household Income': '$50,000 to $59,999'})
qw6 = (qw6["$50,000 to $59,999"] != 1).astype(int) #Changing the boolean value of True into an integer

qw7 = qw[qw['Household Income'] == '$60,000 to $79,999']
qw7 = qw7.rename(columns={'Household Income': '$60,000 to $79,999'})
qw7 = (qw7["$60,000 to $79,999"] != 1).astype(int)

qw8 = qw[qw['Household Income'] == '$80,000 to $99,999']
qw8 = qw8.rename(columns={'Household Income': '$80,000 to $99,999'})
qw8 = (qw8["$80,000 to $99,999"] != 1).astype(int)

qw9 = qw[qw['Household Income'] == '$100,000 to $149,000']
qw9 = qw9.rename(columns={'Household Income': '$100,000 to $149,000'})
qw9 = (qw9["$100,000 to $149,000"] != 1).astype(int)

qw10 = qw[qw['Household Income'] == '$150,000 and over']
qw10 = qw10.rename(columns={'Household Income': '$150,000 and over'})
qw10 = (qw10['$150,000 and over'] != 1).astype(int)


Dataset5 = pd.concat([Age_range2, qw1, qw2, qw3, qw4, qw5, qw6, qw7, qw8, qw9, qw10], axis=1)
Dataset5 = Dataset5.fillna(0)
Dataset5

bikeride = (Dataset3['Age Range'].apply(str)).tolist()

commute1 = (Dataset3['Yes Commute'].tolist())
commute2 = (Dataset3['No Commute'].tolist())

Other_yes = (Dataset3['Yes Other'].tolist())
Other_no = (Dataset3['No Other'].tolist())

Recreational_yes = (Dataset3['Yes Recreational'].tolist())
Recreational_no = (Dataset3['No Recreational'].tolist())

Entertainment_yes = (Dataset3['Yes Entertainment'].tolist())
Entertainment_no = (Dataset3['No Entertainment'].tolist())



print('Age Column')
print(bikeride)
print('')
print('Commute 1 Column')
print(commute1)
print('')
print('Commute 2 Column')
print(commute2)
print('')
print('Other 1 Column')
print(Other_yes)
print('')
print('Other 2 Column')
print(Other_no)
print('')
print('Recreational 1 Column')
print(Recreational_yes)
print('')
print('Recreational 2 Column')
print(Recreational_no)
print('')
print('Entertainment 1 Column')
print(Entertainment_yes)
print('')
print('Entertainment 2 Column')
print(Entertainment_no)


Prefer_not_to_answer = (Dataset5['Prefer not to answer'].tolist())
Under_twenty = (Dataset5['Under $20,000'].tolist())
twenty_twentynine = (Dataset5['$20,000 to $29,999'].tolist())
thirty_thirtynine = (Dataset5['$30,000 to $39,999'].tolist())
forty_fortynine = (Dataset5['$40,000 to $49,999'].tolist())
fifty_fiftynine = (Dataset5['$50,000 to $59,999'].tolist())
sixty_seventynine = (Dataset5['$60,000 to $79,999'].tolist())
eighty_ninetynine = (Dataset5['$80,000 to $99,999'].tolist())
onehundred_onefourtynine = (Dataset5['$100,000 to $149,000'].tolist())
onefifty = (Dataset5['$150,000 and over'].tolist())


print(Prefer_not_to_answer)
print(Under_twenty)
print(twenty_twentynine)
print(thirty_thirtynine)
print(forty_fortynine)
print(fifty_fiftynine)
print(sixty_seventynine)
print(eighty_ninetynine)
print(onehundred_onefourtynine)


colors2 = ('#718abf','#e84d60', '#714abf', '#c10e60', '#750bbf','#d10d60', '#600bbf', '#b20e60', '#128abf','#e10d60', '#714abf', '#340abc')
colors = ('#718abf','#e84d60', '#714abf', '#c10e60', '#750bbf','#d10d60', '#600bbf', '#b20e60')

grouped_income = Dataset3.groupby('Household Income')
Incomes = {}
for houseincome in grouped_income.groups:
  Incomes[houseincome] = grouped_income.get_group(houseincome)
Incomes

grouped_bike = Dataset3.groupby('Age Range')
Ages = {}
for age in grouped_bike.groups:
  Ages[age] = grouped_bike.get_group(age)
Ages

grouped_groups = Dataset5.groupby('Age Range')
Groups = {}
for group in grouped_groups.groups:
  Groups[group] = grouped_groups.get_group(group)
Groups

Range_Age = ['18-24', '25-29', '30-34', '35-39', '40-44', '45-49', '50-54', '55-59', '60-64', '65-69', '70-74', '75-79']
Commute = []
Commute2 = []
Other_yes = []
Other_no = []
Recreational_no = []
Recreational_yes = []
Entertainment_no = []
Entertainment_yes = []

for age in Range_Age:
  Commute.append(Ages[age]['Yes Commute'].sum())
  Commute2.append(Ages[age]['No Commute'].sum())
  Other_yes.append(Ages[age]['Yes Other'].sum())
  Other_no.append(Ages[age]['No Other'].sum())
  Recreational_yes.append(Ages[age]['Yes Recreational'].sum())
  Recreational_no.append(Ages[age]['No Recreational'].sum())
  Entertainment_yes.append(Ages[age]['Yes Entertainment'].sum())
  Entertainment_no.append(Ages[age]['No Entertainment'].sum())


print(Commute)
print(Commute2)
print(Other_yes)
print(Other_no)
print(Recreational_yes)
print(Recreational_no)
print(Entertainment_yes)
print(Entertainment_no)


Range_Income = ['Prefer not to answer', 'Under $20,000', '$20,000 to $29,999','$30,000 to $39,999', '$40,000 to $49,999', '$50,000 to $59,999', '$60,000 to $79,999','$80,000 to $99,999', '$100,000 to $149,000', '$150,000 and over']
list1 = []
list2 = []
list3 = []
list4 = []
list5 = []
list6 = []
list7 = []
list8 = []
list9 = []

for income in Range_Income:
  list1.append(Incomes[income]['Yes Commute'].sum())
  list2.append(Incomes[income]['No Commute'].sum())
  list3.append(Incomes[income]['Yes Other'].sum())
  list4.append(Incomes[income]['No Other'].sum())
  list5.append(Incomes[income]['Yes Recreational'].sum())
  list6.append(Incomes[income]['No Recreational'].sum())
  list7.append(Incomes[income]['Yes Entertainment'].sum())
  list8.append(Incomes[income]['No Entertainment'].sum())
  list9.append(Incomes[income]['Household Income'].sum())

Range_Income
print(list1)
print(list2)
print(list3)
print(list4)
print(list5)
print(list6)
print(list7)
print(list8)
print(list9)


Prefernottoanswer = []
Under20000 = []
TwentyTwentynine = []
thirtythirtynine = []
fourtyfortynine = []
fiftyfiftynine = []
sixtyseventynine = []
eighty99nine = []
onehundredonefourtynine = []
onefifty = []

for income in Range_Age:
  Prefernottoanswer.append(Groups[income]['Prefer not to answer'].sum())
  Under20000.append(Groups[income]['Under $20,000'].sum())
  TwentyTwentynine.append(Groups[income]['$20,000 to $29,999'].sum())
  thirtythirtynine.append(Groups[income]['$30,000 to $39,999'].sum())
  fourtyfortynine.append(Groups[income]['$40,000 to $49,999'].sum())
  fiftyfiftynine.append(Groups[income]['$50,000 to $59,999'].sum())
  sixtyseventynine.append(Groups[income]['$60,000 to $79,999'].sum())
  eighty99nine.append(Groups[income]['$80,000 to $99,999'].sum())
  onehundredonefourtynine.append(Groups[income]['$100,000 to $149,000'].sum())
  onefifty.append(Groups[income]['$150,000 and over'].sum())

print(Prefernottoanswer)
print(Under20000)
print(TwentyTwentynine)
print(thirtythirtynine)
print(fourtyfortynine)
print(fiftyfiftynine)
print(sixtyseventynine)
print(eighty99nine)

bikegroupedincome = dict(Range_Age = Range_Age, Prefernottoanswer = Prefernottoanswer, Under20000 = Under20000,
                         TwentyTwentynine = TwentyTwentynine, thirtythirtynine = thirtythirtynine,
                         fourtyfortynine = fourtyfortynine, fiftyfiftynine = fiftyfiftynine, sixtyseventynine = sixtyseventynine,
                         eighty99nine = eighty99nine, onehundredonefourtynine = onehundredonefourtynine, onefifty = onefifty)
print(bikegroupedincome)
source = ColumnDataSource(data=bikegroupedincome)

bikeincome = dict(Range_Income = Range_Income, list1 = list1, list2 = list2,
                  list3 = list3, list4 = list4, list5 = list5, list6 = list6,
                  list7 = list7, list8 = list8, list9 = list9)
print(bikeincome)
source = ColumnDataSource(data=bikeincome)

bikedate = dict(Range_Age = Range_Age,
            Commute = Commute,
            Commute2 = Commute2,
            Other_yes = Other_yes,
            Other_no = Other_no,
            Recreational_yes = Recreational_yes,
            Recreational_no = Recreational_no,
            Entertainment_yes = Entertainment_yes,
            Entertainment_no = Entertainment_no)
print(bikedate)
source = ColumnDataSource(data=bikedate)

Answers = ['Yes Commute', 'No Commute', 'Yes Other Reasons', 'No Other Reasons', 'Yes Recreation', 'No Recreation', 'Yes Entertainment', 'No Entertainment']
x = [(biker, response) for biker in Range_Age for response in Answers]
y = sum(zip(bikedate['Commute'], bikedate['Commute2'], bikedate['Other_yes'], bikedate['Other_no'], bikedate['Recreational_yes'], bikedate['Recreational_no'], bikedate['Entertainment_yes'], bikedate['Entertainment_no']), ())
print('X Data: ')
print(x)
print('')
print('Y Data: ')
print(y)

Answers2 = ['Yes Commute', 'No Commute', 'Yes Other Reasons', 'No Other Reasons', 'Yes Recreation', 'No Recreation', 'Yes Entertainment', 'No Entertainment']
x_income = [(income, response) for income in Range_Income for response in Answers2]
y_income = sum(zip(bikeincome['list1'], bikeincome['list2'], bikeincome['list3'], bikeincome['list4'], bikeincome['list5'], bikeincome['list6'], bikeincome['list7'], bikeincome['list8']), ())
print('X Data: ')
print(x_income)
print('')
print('Y Data: ')
print(y_income)

Answers3 = ['18-24', '25-29', '30-34', '35-39', '40-44', '45-49', '50-54', '55-59', '60-64', '65-69', '70-74', '75-79']
x_incomeage = [(income2, response) for income2 in Range_Income for response in Answers3]
y_incomeage = sum(zip(bikegroupedincome['Prefernottoanswer'], bikegroupedincome['Under20000'], bikegroupedincome['TwentyTwentynine'], bikegroupedincome['thirtythirtynine'], bikegroupedincome['fourtyfortynine'], bikegroupedincome['fiftyfiftynine'], bikegroupedincome['sixtyseventynine'], bikegroupedincome['eighty99nine'], bikegroupedincome['onehundredonefourtynine'], bikegroupedincome['onefifty']), ())
print('X Data: ')
print(x_incomeage)
print('')
print('Y Data: ')
print(y_incomeage)

from bokeh.plotting import figure, show
from bokeh.io import output_notebook
from bokeh.models import ColumnDataSource
from bokeh.models import FactorRange
import math
from bokeh.layouts import row
output_notebook()

from bokeh.models import FactorRange
from bokeh.transform import factor_cmap

data = dict(x=x, y=y)
print(data)
source = ColumnDataSource(data=data)

data2 = dict(x_income=x_income, y_income=y_income)
print(data2)
source2 = ColumnDataSource(data=data2)

bikerider_visual = figure(title = "Edmonton Bikeridership Habits by Age", x_range=FactorRange(*x, group_padding=0.5), y_range=(0,80),
                          x_axis_label = "Biking Habits", y_axis_label = "Survey Respondents", height = 500, width = 2300)
bikerider_visual.xgrid.grid_line_color = None
bikerider_visual.xaxis.major_label_orientation = math.pi/2.2

bikerider_visual.line(x=x, y=y)
show(bikerider_visual)

bikerider_visual.vbar(x='x', top='y', width=0.4, legend_field = 'x', source=source,
       line_color='white', fill_color=factor_cmap('x', palette=colors, factors=Answers, start=1, end=2))
bikerider_visual.legend.orientation = "horizontal"
show(bikerider_visual)
