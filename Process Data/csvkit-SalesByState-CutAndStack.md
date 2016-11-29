// csvkit
// Sales by State

// Cut out States and single year's sales
csvcut -c 1,2,3 salesbystate.csv > sales1999.csv
csvcut -c 1,2,4 salesbystate.csv > sales2000.csv
csvcut -c 1,2,5 salesbystate.csv > sales2001.csv
csvcut -c 1,2,6 salesbystate.csv > sales2002.csv
csvcut -c 1,2,7 salesbystate.csv > sales2003.csv
csvcut -c 1,2,8 salesbystate.csv > sales2004.csv
csvcut -c 1,2,9 salesbystate.csv > sales2005.csv
csvcut -c 1,2,10 salesbystate.csv > sales2006.csv
csvcut -c 1,2,11 salesbystate.csv > sales2007.csv
csvcut -c 1,2,12 salesbystate.csv > sales2008.csv
csvcut -c 1,2,13 salesbystate.csv > sales2009.csv
csvcut -c 1,2,14 salesbystate.csv > sales2010.csv
csvcut -c 1,2,15 salesbystate.csv > sales2011.csv
csvcut -c 1,2,16 salesbystate.csv > sales2012.csv
csvcut -c 1,2,17 salesbystate.csv > sales2013.csv
csvcut -c 1,2,18 salesbystate.csv > sales2014.csv

// stack each years csv of sales and add the year as a column
csvstack -n year -g 1999,2000,2001,2002,2003,2004,2005,2006,2007,2008,2009,2010,2011,2012,2013,2014 sales1999.csv sales2000.csv sales2001.csv sales2002.csv sales2003.csv sales2004.csv sales2005.csv sales2006.csv sales2007.csv sales2008.csv sales2009.csv sales2010.csv sales2011.csv sales2012.csv sales2013.csv sales2014.csv > salesbystate-final.csv
