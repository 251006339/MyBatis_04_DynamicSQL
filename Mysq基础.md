# MyBatis_04_DynamicSQL
1.语法:
  select 要查询的东西  
    from 表 
    where 条件
    order by 排序的字段|表达式|函数|别名 [asc|desc]
2.常见函数
  1.字符函数
     concat拼接
     sustr截取子串
     upper大写
     lower小写
     trim取前后指定的空格和字符
     ltrim去左边空格
     rtrim去右边空格
     replase替换
     lpad左填充
     rpad右填充
     instr返回子串第一次出现的索引
     length 获取字节个数
  2.数学函数
    round 四舍五入
    rand 随机数
    floor向下取整
    ceil向上取整
    mod取余
    truncate截断
  3.日期函数
    now 当前系统日期+时间
    curdate当前系统日期
    curtime当前系统时间
    str_to_date将字符转换成日期
    date_format 将日期转换成字符
  4.流程控制函数
    if ()  <--java-->三元运算符
    case (语句)        <--java-->  switch(值)
      when  值1 then                   case 值1 break;  
       else                         case 值2 break;   
      end                              default  xxx;     
              
   case                         <--java-->         if(条件){}  else if(条件2){}
     when 条件1 then 要显示值1或语句1
     when 条件2 then 要显示的值2或语句2
    end;          
  5.其他函数
     select version();当前版本
     select databse ;  当前库
     select user;   当前连接用户
     
    
二、分组函数  
     sum 求和
     max 最大值
     min 最小值
     avg 平均值
     count 计数
     
     特点:
     1.以上五个分组函数都忽略null值,除了count(*)
     2.sum和avg一般用于处理数值型
       max,min,count可以处理任务数据类型
     3.都可以搭配distinct使用,用于统计去重后的结果
     select sum(distinct salary),sum(salary)from employees;
    select count(distinct salary),count(salary)from employees;
     4.count的参数可以支持:
           字段,*,常量值,一般放1
     效率:
     MyISAM存储引擎下,count(*)的效率高 计数器 统计行数
     INNODB存储引擎下,count(*)和count(1)的效率差不多,比count字段要高一些
     建议使用count(*)
     
   和分组函数一同查询的字段有限制
    select avg(salary),employee_id from emp
    和分组函数一同查询的字段最好是分组后的字段
   询公司的最大值,最小值,平均值,总和
   select max(salary) mx_sal,min(salary) mi_sal,round(avg(salary),2) g_sal,sum(salary) sm_sal from emp
   查询员工表中的最大入职时间和最小入职时间的相关天数(diffrence)
   select datediff(now(),'1995-1-1')//两个时间相差的天数
   select datediff(max(hiredate),min(hiredate)) DIFFRENCE from emp;
   select datediff(max(hiredate),min(hiredate))                                  
  
    
    
    
    
   
