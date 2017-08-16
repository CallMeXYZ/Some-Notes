- 总天数 select  `to_days('2015-1-18')`
- 当前时间与特定时间所差周数的实现	
```
  declare i int;
  set i =  timestampdiff(week,date(date_add(p_time,interval 8-dayofweek(p_time) day)),date(date_add(now(),interval 8-dayofweek(now()) day)));
  return  if(i<0,abs(i),i+1) ;
```
- `limit`后只能跟常量
- `count()` 返回`hibernate`是`BigInteger`
- `hibernate` 返回值不`add scale`,直接返回`Object[]` 时，sql里不能设置别名 如`select text.text as name`
- `update table set 。。 where id=(select * from (select max(id) from table) as A)`必须再次select下
- `SET GLOBAL event_scheduler = ON; 或者在mysql.ini下添加event_scheduler=1`
- update可以用`order by limit 1`
- `alter table users AUTO_INCREMENT=123456`
- cursor 一定要在not found 时设置标记 然后leave loop。否则死循环！！！！2货
