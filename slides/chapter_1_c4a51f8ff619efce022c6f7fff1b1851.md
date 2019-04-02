---
title: Insert title here
key: c4a51f8ff619efce022c6f7fff1b1851

---
## Title Slide

```yaml
type: "TitleSlide"
key: "0e6f6681aa"
```

`@lower_third`

name: Jason Medina
title: Data Analyst


`@script`
Welcome to the final section of the second chapter of SQL for spread sheet users.  In this section, we will continue to aggregate rows from data tables and learn how to combine CASE WHEN statements with aggregate functions. Let's start!


---
## Viewing data from ORDERS and CUSTOMER tables

```yaml
type: "TwoRows"
key: "e65e36ab08"
code_zoom: 87
```

`@part1`
```SELECT * FROM ORDERS LIMIT 5``` {{1}}

```order_id, customer_id, order_type, order_date,  order_amount```{{2}}


`@part2`
```SELECT * FROM CUSTOMERS LIMIT 5``` {{3}}

```customer_id, customer_name, zip_code, email_address```{{4}}


`@script`
Recall the customers and orders table from chapter 1. As previously demonstrated, executing a basic select star from with a limit will return a data sample with column names and row values.  Thinking back to the first lesson from this chapter, can you identify a way to aggregate on each table?


---
## Aggregation examples

```yaml
type: "TwoRows"
key: "4281c4c42b"
```

`@part1`
&nbsp;

```SELECT order_type, SUM(order_value) AS amount 
GROUP BY order_type``` {{1}}


`@part2`
&nbsp;


```SELECT customer_name, COUNT(email_address) AS email_count GROUP BY customer_name``` {{2}}


`@script`
Earlier in this chapter we saw with SQL how to SELECT a column or columns to apply an aggregate function,such as SUM or COUNT, along with GROUP BY to aggregate values over a field from the data table.  

This code goes down rows from the orders table to SUM or COUNT row values and returns the results grouped by order_type or customer_name respectively.  

In the first example, we answer the question What is the sum of order_value by order_type?.  While the second example answers What is the count of email address for each customer name?


---
## Filtering data for aggregation

```yaml
type: "TwoRows"
key: "9d7a375fe4"
```

`@part1`
&nbsp;

```SELECT order_type, SUM(order_value) AS amount
WHERE order_date = '2019-03-17' GROUP BY order_type``` {{1}}


`@part2`
&nbsp;

```SELECT zip_code, COUNT(email_address) WHERE email_address IS NULL GROUP BY zip_code``` {{2}}


`@script`
Imagine we are asked to find the order values by order type for a specific calendar date, such as March 17th, 2019.  Given our SQL knowledge for how to aggregate and filter data with SQL, we recognize this is done by applying a WHERE constraint to filter our data table for the given date.

Likewise, suppose we discover the email_address field contains NULL values for some rows.  In order to find out how many email addresses are null we can COUNT the number of rows where email_address is null.  

In other words, we want to sum the order value when the order date is March 17th 2019 and in the other example we count the case when email address is null.


---
## Combine CASE WHEN with SUM

```yaml
type: "FullSlide"
key: "e0605ab8f6"
```

`@part1`
&nbsp;

```SELECT order_type,SUM(CASE WHEN order_date = '2019-03-17' THEN order_value ELSE 0 END) AS amount
GROUP BY order_type```


`@script`
Combining an aggregate function such as SUM or COUNT with a CASE WHEN statement provides additional flexibility when writing SQL, and is similar to a SUMIFS or COUNTIFS spreadsheet functions.  

We apply the aggregate SUM function to the order_value only for rows when the case criteria is satisfied.  

If the criteria, or order date for this example, is anything other than 2019-03-17, the ELSE portion of the CASE WHEN will SUM zero instead of the order value.


---
## Combine CASE WHEN with COUNT

```yaml
type: "FullSlide"
key: "130524e24d"
```

`@part1`
&nbsp;

```SELECT COUNT(CASE WHEN email_address IS NULL THEN email_address END) AS count_email_address```{{1}}

&nbsp;{{2}}


```SELECT sum(CASE WHEN email_address IS NULL THEN 1 else 0 END) AS count_email_address```{{3}}


`@script`
In the second example, we want to return a count of email addresses for the case when email address is null.  We can accomplish this with a similar approach to the prior example by combining the count function with case when logic.

Here, we count the email address for the case when email address is null.  If the email address is not null then we count nothing.

In similar fashion, combining SUM and CASE WHEN would also work here.  This highlights the flexibility and control SQL provides when combining SUM with CASE WHEN statement logic.


---
## Let's practice!

```yaml
type: "FinalSlide"
key: "a54374b7e0"
```

`@script`
Up to now we have seen how to review detail from data tables, and how to use aggregate functions such as SUM and COUNT to describe summarized data.

In the following exercises you will have the chance to apply these learnings.

Let's practice!

