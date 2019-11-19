
# Issue,  cacophony-api, 19W47-1

---

> **api recordings query yields resultset with inconsistent fields**

## Returns

> resultset with "comment" field

## Expected

> no comment field

## Desired

> comment field to be in result set consistently not periodic dependent on user previous queries.
Also concerned what is happening in the API if the return result set can be altered ?

---

## NB

- *Setup code is hidden, look at the full  [.pmd](./Issue19W47d2-apiRecordingResultwithComment.pmd) file for python code sections*

---





```python
"""Confirm the client"""
cp_client.version, cp_client.get_devices_as_json()
```

```
('4.10.0.alpha.1',
 [{'devicename': 'ruru19w44a', 'id': 810, 'active': True, 'Users':
[]}])
```



Query the API using `api/v1/recordings?where……`

the  `cacophonyapi.UserAPI.query` code is here:
<https://github.com/TheCacophonyProject/python-api/blob/97055fc8db7467d78703204e975d28081271dc5a/src/cacophonyapi/user.py#0dTEPzkLWceF7z0koJaX1A>


```python
resultset=cp_client.query(endDate=strToSqlDateTime("2019-11-06 06:30:00"),startDate=strToSqlDateTime("2019-11-01 19:00:00"),
        limit=300,
        offset=0,
        tagmode="any")
```



Looking at the result set reurned from the query




## RESULT SET analysis

---

Number of records in result set:**292**

The Row of interest is:**258**

Is `comment` in fields of result set: **True**

The comment field value is: **'Gain Issue - Contrast gone very wrong 13s in'**

The Pandas Dataframe colums are:

```text
Index(['id', 'type', 'recordingDateTime', 'rawMimeType', 'fileMimeType',
       'processingState', 'duration', 'location', 'batteryLevel', 'DeviceId',
       'GroupId', 'comment', 'Group', 'Tags', 'Tracks', 'Device'],
      dtype='object')
```

and the values of row **258** are:


```python
df.iloc[rowOfInterest]
```

```
id                                                              414407
type                                                        thermalRaw
recordingDateTime                             2019-11-01T10:05:53.040Z
rawMimeType                                         application/x-cptv
fileMimeType                                                 video/mp4
processingState                                               FINISHED
duration                                                            16
location             {'type': 'Point', 'coordinates': [-36.03915, 1...
batteryLevel                                                      None
DeviceId                                                           810
GroupId                                                            137
comment                   Gain Issue - Contrast gone very wrong 13s in
Group                                   {'groupname': 'BSF1034CoveRd'}
Tags                 [{'what': None, 'detail': 'multiple animals', ...
Tracks               [{'id': 198734, 'TrackTags': []}, {'id': 19872...
Device                         {'id': 810, 'devicename': 'ruru19w44a'}
Name: 258, dtype: object
```


This document is created with pweave from [Issue19W47d2-apiRecordingResultwithComment.pmd](./Issue19W47d2-apiRecordingResultwithComment.pmd)
