## LeetCode 最通俗的题解1

---

### 178 分数排名

MYSQL代码：

```mysql
select a.Score,
    sum(case 
        when b.Score>=a.Score then 1 
        end) as Rank
from Scores a, 
(select distinct Score from Scores ) b 
group by a.id 
order by a.Score desc; 
```

解题思路：

分两个表，a是最终输出表，b是对Score去重后的表。

```mysql
sum(case 
        when b.Score>=a.Score then 1 
        end) as Rank
```

这一段是将b表的每一个值，与a表的每一个值进行对比，凡是出现一个满足条件的，返回1，最终求和，以此值作为排名。

例如a表排名第一的值，在b只有一个值与其相等，满足条件的只有一个，返回1，求和也是1。

