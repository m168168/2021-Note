

1:  poi_procuct 

poi :     筛选 子节点   根据 市场    ，出入口，楼栋号 ，停车场  

从数据库中采用分层抽样。10000 个中 有2094 个满足查询条件 



2：输出第一个文件，分支预测

统计无父点的子点比例 

3：周边召回

输出父子关系

4: 产品库验证父点是否存在

统计父点不存在的比例



父子关系建设：

1: 标记数据，指标的产出。

| 父子节点个数 | 总分支数 | 预测分支 | 分支预测准确率 |
| ------------ | -------- | -------- | -------------: |
| 68           | 1655     | 1590     |         96.07% |

| 召回距离 | 建立总对数 | 父子节点个数 | 子节点个数 | 子节点覆盖率 | 父节点覆盖率 | 准确率      |
| -------- | ---------- | ------------ | ---------- | ------------ | ------------ | ----------- |
| 500      | 3771       | 65           | 1261       | 0.793081761  | 0.913043478  | 0.999734818 |

2: 新人培训

3: 未挂接poi的case拆解 ，完成80% 预计今天完成 https://huolala.feishu.cn/wiki/wikcnF779eVZQmobovq0GNDl3Oh#yk3Z34

4: 验证生产库已构建的父子关系，是否在产品库存在，如果不存，在验证准确率 预计周五完成







```
select *
from poi
where  kind like '%出入口%'
or kind like '%门%'
or kind like '%普通停车位%'
or kind like '%内部楼栋%'
or kind like '%住宅区%'
or kind like '%停车场%'
or kind like '%门址点%'
or kind like '%市场%'
limit  10000
/*
出入口
门
普通停车位
内部楼栋
住宅区
停车场
门址点
市场
*/

select *
from poi
where  (kind like '%出入口%'
or kind like '%门%'
or kind like '%普通停车位%'
or kind like '%内部楼栋%'
or kind like '%住宅区%'
or kind like '%停车场%'
or kind like '%门址点%')
and kind like '%市场%'
limit  10000

select *
from poi

where  (kind like '%出入口%'
or kind like '%门%'
or kind like '%普通停车位%'
or kind like '%内部楼栋%'
or kind like '%住宅区%'
or kind like '%停车场%'
or kind like '%商圈%'
or kind like '商铺'
or kind like '休闲广场'
or kind like '购物'
or kind like '门址点'
or kind like '门址'
or kind like '写字楼'
or kind like '交通设施'
or kind like '停车场出入口')
and kind like '%市场%'


limit  100000


select *
from poi
where  ((kind like '%出入口%'
or kind like '%门%'
or kind like '%普通停车位%'
or kind like '%内部楼栋%'
or kind like '%住宅区%'
or kind like '%停车场%'
or kind like '%商圈%'
or kind like '商铺'
or kind like '购物'
or kind like '交通设施'
or kind like '停车场出入口')
and kind like '%市场%')
or kind like '停车场'
or kind like '出入口'

所有的数据  我都放到hive map_export中aoi_release表中的'2021-06-18'分区下了。
select  count(*) from map_export.aoi_release where dt ='2021-06-18'

delete  from tmp_poi_id_boyang0730
where  fa_id in (
select  fa_id
from tmp_poi_id_boyang0730);


select  poi_id
from poi_0715 ,tmp_poi_id_boyang0730
where poi_0715.poi_id = tmp_poi_id_boyang0730.fa_id
```