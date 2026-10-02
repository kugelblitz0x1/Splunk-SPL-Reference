# Splunk Basics

SORT BY TIME: ASCENDING  
```| sort _time```

SORT BY TIME: DESCENDING  
```| sort - _time```

SEARCHES ARE DESCENDING BY DEFAULT > NEWEST IS ON TOP

### TIPS

Prevent limiting the search  
```limit=0```

Limit the search  
```limit=<value>```

Convert EPOCH time to HUMAN READABLE  
```| convert ctime(time)```

Fill all null fields  
```fillnull value=<VALUE> <FIELD>```

Example:  
```| fillnull value="-" url```

Don't Include RAW logs  
```| fields - _raw```

### STATS

Common Syntax
```| stats values(<FIELD>) as <COLUMN>
values(<FIELD>) as <COLUMN> count by <FIELD>
```

### Stats Functions

**Description:** Functions used with the stats command. Each time you invoke the stats command, you can use more than one function. However, you can use only one BY clause.

avg()  
c()  
count()  
dc()  
distinct_count()  
earliest()  
estdc()  
estdc_error()  
exactperc<int>()  
first()  
last()  
latest()  
list()  
max()  
median()  
min()  
mode()  
p<int>()  
perc<int>()  
range()  
stdev()  
stdevp()  
sum()  
sumsq()  
upperperc<int>()  
values()  
var()  
varp()
