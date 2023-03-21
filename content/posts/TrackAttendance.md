---
title: "Using Python to Track Attendance"
date: 2023-03-21T14:41:41+05:30
draft: true
---

```python
import requests
from bs4 import BeautifulSoup
from bs4 import SoupStrainer
import pandas as pd
import re

#deets.json contains 4 key-value pairs as shown above
deets = pd.read_json('deets.json',typ = "Series")
#deets.index.tolist()
#['collegeLoginUrl', 'attendanceUrl', 'username', 'password']

with requests.Session() as sesh:
    response = sesh.get(deets.collegeLoginUrl)

    #making payload for post
    #payload contains required parameters to login
    soup = BeautifulSoup(response.content)
    payload = dict()
    for tag in soup.find_all("input",attrs = {"type":"hidden"}):
        payload[tag['name']] = tag['value']
    payload['username'] = deets.username
    payload['passwd'] = deets.password

    #sending payload with post method
    response = sesh.post(deets.collegeLoginUrl,data = payload)
    if response.status_code == requests.codes.ok:
        response = sesh.get(deets.attendanceUrl)
    
#to check whether we have logged in or not
#print(response.content.decode(),file = open("AttendancePage.html",'w'))

#to find the table that tracks the number of classes i have attended 
soup = BeautifulSoup(response.content.decode(),parse_only = SoupStrainer("table"))
thtag = soup.find("th",string = re.compile("attendance",flags = re.IGNORECASE))
table = thtag.find_parent("table")

#had to install lmxml and tabulate
#column-1 had subjects which i removed using iloc
df = pd.read_html(table.decode())[0].iloc[:,[0,2,3]]
print(df.to_markdown(index = False,tablefmt="grid"))

total = df.iloc[2,:]

attendance = (total['Classes Attended'])/total['Classes Held']*100
attendance = "{:.2f}".format(attendance)

print(f"Overall Attendance : {attendance}")
```