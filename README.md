# MYSQL-group-by
Calculate total revenue in each category for every week in 2021. (‘order_date’ field is a timestamp value)
use practice;
SELECT 
    sum(order_detail.Revenue),item_detail.cateogory,customer_id,week(customers_orders.order_date)
FROM
    order_detail
        JOIN
    item_detail
        on order_detail.Item_id=item_detail.Item_id
        join customers_orders
        on customers_orders.order_id=order_detail.order_id where year(customers_orders.order_date)>'2020'
        group by item_detail.cateogory,yearweek(customers_orders.order_date);
