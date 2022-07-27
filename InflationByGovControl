##Imports necessary packages and reads in data as pandas dfs

import pandas as pd
import altair as alt
from __future__ import print_function
from ipywidgets import interact, interactive, fixed, interact_manual
import ipywidgets as widgets
from IPython.display import display

lag0 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag0.csv')
lag1 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag1.csv')
lag2 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag2.csv')
lag3 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag3.csv')
lag4 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag4.csv')
lag5 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag5.csv')
lag6 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag6.csv')
lag7 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag7.csv')
lag8 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag8.csv')
lag9 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag9.csv')
lag10 = pd.read_csv('https://raw.githubusercontent.com/Angela-Merkel-Tree/DataRepo/main/lag10.csv')



##Creates series of visualiztions and toggles between them using ipywidgets

branches = ['Presidency', 'Congress (Both Chambers)', 'House of Representatives', 'Senate']

lag_selection = widgets.IntSlider(
    min=0, 
    max=10,
    description='Years Prior'
)
branch_selection = widgets.Dropdown(
    options=branches,
    value='Presidency',
    description='Branch of Government',
    disabled=False,
)

lag = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10']

party = alt.Scale(domain=('Democrat', 'Republican', 'Split'),
                      range=["blue", "red", "purple"])

var_prefixes = ['pres', 'both', 'house', 'senate']

for i in range(11):
    for j in range(len(branches)):
        if i == 0:
            globals()[branches[j]+'_lag'+lag[i]] = alt.Chart(globals()['lag'+lag[i]]).mark_bar().encode(
                x='Year:O',
                y='Average:Q',
                color=alt.Color(branches[j]+':N', scale=party),
                tooltip=['President:N', 'Average:Q'],
            ).properties(
                width=1000,
                height=800,
                title = 'Who Controlled the Presidency '+lag[i]+' Years Previously?'
            ).transform_filter(
                alt.FieldGTEPredicate(field='Year', gte=1963)
            )
        else:
            globals()[branches[j]+'_lag'+lag[i]] = alt.Chart(globals()['lag'+lag[i]]).mark_bar().encode(
                x='Year:O',
                y='Average:Q',
                color=alt.Color(branches[j]+':N', scale=party),
                tooltip=['Average:Q'],
            ).properties(
                width=1000,
                height=800,
                title = 'Who Controlled the '+branches[j]+' '+lag[i]+' Years Previously?'
            ).transform_filter(
                alt.FieldGTEPredicate(field='Year', gte=1963)
            )
        
def f(x,y):
    display(globals()[y+'_lag'+lag[x]])
    
interact(f, x=widgets.IntSlider(min=0, max=10,description='Years Prior',value=0),y=widgets.Dropdown(options=branches, description='Branch of Government'));
