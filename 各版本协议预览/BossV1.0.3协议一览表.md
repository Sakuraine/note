# V1.0.3协议一览表


## BossWeb平台端协议.md

协议地址所在位置： seeing\wiki\协议文档\BossWeb平台端协议.md

| 协议地址                                     | 协议名称            | 人员   | 备注   |
| ---------------------------------------- | --------------- | ---- | ---- |
| [GET]/sys_service/ajax/record/list       | 分页查询ajax监控      | 陈慧杰  |      |
| [GET]/sys_service/version_mng/list       | 版本管理信息列表查询      | 陈慧杰  |      |
| [POST]/sys_service/version_mng/insert    | 版本管理信息新增        | 陈慧杰  |      |
| [GET]/sys_service/device/monitoring/exception | appweb监控异常查询    | 陈慧杰  |      |
| [GET]/sys_service/device/monitoring/all  | appweb监控全部查询    | 陈慧杰  |      |
| [GET]/sys_service/jasreport/list         | 打印模板维护列表查询      | 陈慧杰  |      |
| [GET]/sys_service/jasreport/tenet_getting | 租户个性设置默认打印模板查询  | 陈慧杰  |      |
| [POST]/sys_service/jasreport/tenet_setting | 租户个性设置默认打印模板    | 陈慧杰  |      |
| [GET]/sys_service/base_settings/printer/list | 打印模板打印类型列表查询    | 陈慧杰  |      |
| [POST]/sys_service/jasreport/upload/picture_template | 模板文件/预览图片的预上传   | 陈慧杰  |      |
| [POST]/sys_service/jasreport/insert      | 打印模板新增          | 陈慧杰  |      |
| [POST]/sys_service/jasreport/delete      | 打印模板删除          | 陈慧杰  |      |
| [POST]/sys_service/jasreport/update      | 打印模板选择默认项       | 陈慧杰  |      |
| [GET]/sys_service/jasreport/preview      | 打印模板预览          | 陈慧杰  |      |
| [GET]/sys_service/tenant_regapply/docking/list | 服务号对接信息列表查询     | 陈慧杰  |      |
| [POST]/sys_service/tenant_regapply/docking/enable | 服务号对接启用停用       | 陈慧杰  |      |
| [GET]/sys_service/tenant_regapply/docking/info | 服务号对接详情         | 陈慧杰  |      |
| [GET]/sys_service/tenant_regapply/docking/download | 服务号对接网页授权域名文件下载 | 陈慧杰  |      |
| [POST]/sys_service/login_record/maxonline/update | 最大在线用户数修改       | 陈慧杰  |      |

 需要修改的协议

| 协议地址                                   | 协议名称      | 人员   | 备注          |
| -------------------------------------- | --------- | ---- | ----------- |
| [GET]/tenant_service/login_record/list | 租户下用户登陆列表 | 陈慧杰  | 需要添加最大在线用户数 |
| [GET]/tenant_service/tenant            | 租户基本信息协议  | 陈慧杰  | 需要添加登录页背景图片 |
| [GET]/tenant_service/tenant/update_base | 租户基本信息更新协议  | 陈慧杰  | 需要添加登录页背景图片 |



## 设备与自助机管理服务协议.md

协议地址所在位置： seeing\wiki\协议文档\设备与自助机管理服务协议.md

| 协议地址                             | 协议名称         | 人员   | 备注   |
| -------------------------------- | ------------ | ---- | ---- |
| [post]/device/ajax/record/insert | 新增ajax请求记录协议 | 贺志强  |      |
| ...                              | 新增appweb监控异常 | 刘维   |      |

## 报表服务协议.md
协议地址所在位置： seeing\wiki\协议文档\报表服务协议.md

| 协议地址 | 协议名称      | 人员   | 备注   |
| ---- | --------- | ---- | ---- |
|      | 报表打印模板预览流 | 虞鑫杰  |      |

## 用户服务协议.md
协议地址所在位置： seeing\wiki\协议文档\用户服务协议.md

队列名称: USER_MAX_ALIVE

RedisDB: 1



| 协议地址                 | 协议名称   | 人员   | 备注      |
| -------------------- | ------ | ---- | ------- |
| [GET]/userauth/login | 租户登陆协议 | 何志雄  | 最大人数的控制 |