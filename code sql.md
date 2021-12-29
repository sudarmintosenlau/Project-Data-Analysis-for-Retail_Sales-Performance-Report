--- Overall Performance by Year ---

SELECT 
	left(order_date,4) as years,
	sum(sales) as sales,
	count(order_status) as number_of_order 
FROM 
	dqlab_sales_store
WHERE 
	order_status = 'Order Finished'
GROUP BY 
	left(order_date,4);


--- Overall Performance by Product Sub Category ---

SELECT 
	left(order_date,4) as years,
	product_sub_category,sum(sales) as sales
FROM 
	dqlab_sales_store
WHERE 
	left(order_date,4) in ('2011','2012') and order_status = 'Order Finished'
GROUP BY 
	left(order_date,4),product_sub_category
ORDER BY 
	left(order_date,4),sum(sales) 
DESC;


--- Promotion Effectiveness and Efficiency by Years ---

SELECT 
	left(order_date,4) as years,
	sum(sales) as sales,
	sum(discount_value) as promotion_value,
	round((sum(discount_value)/sum(sales))*100,2) as burn_rate_percentage
FROM 
	dqlab_sales_store
WHERE 
	order_status = 'Order Finished'
GROUP BY 
	left(order_date,4);


--- Promotion Effectiveness and Efficiency by Product Sub Category ---

SELECT 
	left(order_date,4) as years,
	product_sub_category,
	product_category,
	sum(sales) as sales,
	sum(discount_value) as promotion_value,
	round((sum(discount_value)/sum(sales))*100,2) as burn_rate_percentage
FROM 
	dqlab_sales_store
WHERE 
	left(order_date,4) ='2012' and order_status = 'Order Finished'
GROUP BY 
	left(order_date,4),product_sub_category,product_category
ORDER BY 
	sum(sales) 
DESC;


--- Customers Transactions per Year ---

SELECT 
	left(order_date,4) as years, 
	count(distinct customer) as number_of_customer
FROM 
	dqlab_sales_store
WHERE 
	left(order_date,4) in ('2009','2010','2011','2012') and order_status = 'Order Finished'
GROUP BY 
	left(order_date,4)
ORDER BY 
	left(order_date,4);
