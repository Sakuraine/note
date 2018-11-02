# V1.0.4协议一览表


## BossWeb平台端协议.md

协议地址所在位置： seeing\wiki\协议文档\BossWeb平台端协议.md

### 新增协议
| 协议地址                                     | 协议名称          | 人员   | 备注   |
| ---------------------------------------- | ------------- | ---- | ---- |
| [GET]/sys_service/eye_examination/list   | 检查项列表查询       | 陈慧杰  |      |
| [GET]/sys_service/eye_examination/indicator/list | 检查项信息-指标项列表查询 | 陈慧杰  |      |
| [GET]/sys_service/eye_examination/indicator/info | 指标项信息查询       | 陈慧杰  |      |
| [GET]/sys_service/platform_personer/list | 平台人员列表        | 陈慧杰  |      |
| [GET]/sys_service/statistic/tenant/pagelist | 租户统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/patient/pagelist | 患者统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/book/pagelist | 挂号统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/recipe/pagelist | 处方统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/optometr/pagelist | 视光统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/drug/pagelist | 药品统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/drug/list    | 药品列表          | 陈慧杰  |      |
| [GET]/sys_service/statistic/goods/pagelist | 商品统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/goods/list   | 商品列表          | 陈慧杰  |      |

 ### 需要修改的协议

| 协议地址                                     | 协议名称       | 人员   | 备注          |
| ---------------------------------------- | ---------- | ---- | ----------- |
| [POST]/tenant_service/tenant_regapply     | 新增租户申请   | 陈慧杰  | 添加销售人员和客服经理 |
| [GET]/tenant_service/tenant_regapply     | 新增租户申请查询   | 陈慧杰  | 添加销售人员和客服经理 |
| [POST]/tenant_service/tenant_regapply/update | 新增租户信息查询   | 陈慧杰  | 添加销售人员和客服经理 |
| [POST]/tenant_service/tenant_regapply/examine | 审核租户申请   | 陈慧杰  | 添加销售人员和客服经理,前端无需修改 |
| [GET]/tenant_service/tenant              | 租户基本信息协议   | 陈慧杰  | 添加销售人员和客服经理 |
| [GET]/tenant_service/tenant/update_base  | 租户基本信息更新协议 | 陈慧杰  | 添加销售人员和客服经理 |


## schedule定时任务端协议.md
原数据：
spring.redis.database=15

新增数据：
配置项： 平台端数据统计的0点任务：每天0点
schedule.platform.statistic=0 0 0 * * ?

hash

