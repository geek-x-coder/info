# [mariaDB] 날짜 계산

```sql
prod_dt < date_format(curdate() - interval ${save_days} DAY, '%Y%m%d')
and (car_type, body_no) in (select car_type, body_no from vmc.v_prod_ma where stn_cd in ('T340', 'T360')) 
```