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

| Function | Description |
| --- | --- |
| `avg()` | Arithmetic mean of numeric values. |
| `c()` | Alias for `count()`. |
| `count()` | Counts events, or field occurrences when specified. |
| `dc()` | Counts unique field values. |
| `distinct_count()` | Alias for `dc()`. |
| `earliest()` | First value chronologically, using event timestamps. |
| `estdc()` | Estimates the number of unique values. |
| `estdc_error()` | Theoretical relative error of the estimated distinct count. |
| `exactperc<int>()` | Exact value at the specified percentile. |
| `first()` | First value encountered in input order. |
| `last()` | Last value encountered in input order. |
| `latest()` | Last value chronologically, using event timestamps. |
| `list()` | Lists values in input order, including duplicates. |
| `max()` | Maximum value. |
| `median()` | Middle value of sorted numeric values. |
| `min()` | Minimum value. |
| `mode()` | Most frequently occurring value. |
| `p<int>()` | Alias for `perc<int>()`. |
| `perc<int>()` | Specified percentile; may be approximate. |
| `range()` | Difference between maximum and minimum numeric values. |
| `stdev()` | Sample standard deviation. |
| `stdevp()` | Population standard deviation. |
| `sum()` | Sum of numeric values. |
| `sumsq()` | Sum of squared numeric values. |
| `upperperc<int>()` | Upper bound of the estimated percentile. |
| `values()` | Lists unique values in lexicographical order. |
| `var()` | Sample variance. |
| `varp()` | Population variance. |


### Lookup / InputLookup

BASIC LOOKUP

Syntax  
```| lookup <lookup-table-name> <lookup-field1> OUTPUT <lookup-field2>```

Example  
```| lookup ColorCodes.csv ColorCode OUTPUT ColorName```


**ColorCodes.csv**

| ColorCode | ColorName |
| --- | --- |
| 1 | Red |
| 2 | Green |
| 3 | Blue |

EXCLUDE INPUTLOOKUP CRITERIA

```
index=proxy
earliest=-20m
NOT [alexa_top_500.csv]
| top 10 uri
```

```lookup local=f```  
means NOT LOCAL

View a LOOKUP .CSV

```| inputlookup table.csv```

Example:  
```| inputlookup event_id.csv```


### If

```if(<IF>, <THEN>, <ELSE>)```
