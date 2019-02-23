>SELECT <列名> FROM <表名> WHERE <条件>

>SELECT * FROM order_header WHERE order_status = '完工'

>SELECT order_no FROM order_header WHERE order_status = '完工' AND order_type = 1

>SELECT order_no FROM order_header WHERE order_type = 1 OR order_status = '下达'

>SELECT
order_no,
order_type,
order_status
FROM
order_header
WHERE
>order_status IN ( '开工', '完工', '下达' )

>SELECT order_no FROM order_header WHERE order_status LIKE '%工%'

>SELECT order_status FROM order_header GROUP BY order_status

>SELECT order_status, COUNT(1) FROM order_header GROUP BY order_status

>SELECT order_status, COUNT(1) FROM order_header GROUP BY order_status HAVING COUNT(1) > 2

>SELECT DISTINCT order_type FROM order_header

>SELECT
order_no,
order_type,
order_status,
CASE
WHEN order_type = 1 THEN '生产订单'
WHEN order_type = 2 THEN '更改订单'
WHEN order_type = 3 THEN '废弃订单'
ELSE '未知类型'
END AS type_desc
FROM
>order_header

>SELECT
order_no,
type_desc
FROM
(
SELECT
order_no,
order_type,
order_status,
CASE
WHEN order_type = 1 THEN '生产订单'
WHEN order_type = 2 THEN '更改订单'
WHEN order_type = 3 THEN '废弃订单'
ELSE '未知类型'
END AS type_desc
FROM
order_header
>) t

>INSERT INTO order_header ( order_no, order_type, order_status, order_date, createdon )
VALUES
>( '2018102109', 2, '下达', sysdate( ), sysdate( ) )

>UPDATE order_header SET order_no = '112109' WHERE order_no = '2018102109'

>DELETE FROM order_header WHERE order_no = '112109'
