
## Full Dates
```
Date = ADDCOLUMNS(
  CALENDAR(DATE(2009,1,1), DATE(2016,12,31)),
  "DateAsInteger", FORMAT ([DATE],"YYYYMMDD"),
  "DateAsIntegerDash", FORMAT ([DATE],"YYYY-MM-DD"),
  "Year", YEAR ( [DATE]),
  "Monthnumber", FORMAT ( [Date], "MM" ),
  "YearMonthnumber", FORMAT ( [Date], "YYYY/MM" ),
  "YearMonthShort", FORMAT ( [Date], "YYYY/mmm" ),
  "MonthNameShort", FORMAT ( [Date], "mmm" ),
  "MonthNameLong", FORMAT ( [Date], "mmmm" ),
  "DayOfWeekNumber", WEEKDAY ( [Date] ),
  "DayOfWeek", FORMAT ( [Date], "dddd" ),
  "DayOfWeekShort", FORMAT ( [Date], "ddd" ),
  "Quarter", "Q" & FORMAT ( [Date], "Q" ),
  "YearQuarter", FORMAT ( [Date], "YYYY" ) & "/Q" & FORMAT ( [Date], "Q" )
  )
```
---
*Source: http://kohera.be/blog/business-intelligence/how-to-create-a-date-table-in-power-bi-in-2-simple-steps/*
---


## Fiscal Year Starting in April
Set Quarters from calendar quarters to fiscal quarters
```
Fiscal Quarter = IF([Quarter] = "Q1", "Q4", IF([Quarter] ="Q2", "Q1", IF([Quarter] = "Q3", "Q2", "Q3")))
```

Set Month number from calendar to fiscal number.
```
Fiscal Month = IF([Monthnumber] > 3, [Monthnumber] -3, [Monthnumber] + 9 )
```

Set fiscal year for Q4 to previous calendar year to account for Q4 going into the next calendar year.

|Month|Calendar Year|Fiscal Year|
|---|---|---|
|January|2017|2016|
```
Fiscal Year = if(MONTH([DATE]) < 4, YEAR([DATE])-1, YEAR([DATE]))
```


## Single Years, Months, Day Of Week
1999,2000,2001,2002,2003,2004,2005,2006,2007,2008,2009,2010,2011,2012,2013,2014,2015,2016,2017
January,February,March,April,May,June,July,August,September,October,November,December
Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec
Monday,Tuesday,Wednesday,Thursday,Friday,Saturday,Sunday
Mon,Tues,Wed,Thur,Fri,Sat,Sun
