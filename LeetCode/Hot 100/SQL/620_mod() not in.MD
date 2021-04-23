select * 
from cinema as t2 
where t2.id not in
(select t1.id
from cinema as t1
where t1.description = 'boring' or mod(t1.id,2)=0)
order by rating desc;
