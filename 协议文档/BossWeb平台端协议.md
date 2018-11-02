# BossWeb V0.0.0协议设计

## 协议一览表

| 名称                                | 地址与操作                                    | 描述   |
| --------------------------------- | ---------------------------------------- | ---- |
| 平台管理用户登录                          | [POST]/platform/authent/login            |      |
| 通用仓库列表                            | [GET]/common_service/depot_list          |      |
| 获取导入日志列表信息                        | [GET]/sys_service/user/impt/list         |      |
| 获取科室列表信息                          | [GET]/sys_service/depa/list              |      |
| 获取地址列表                            | [GET]/address_service/address/list       |      |
| 用户账号信息                            | [GET]/sys_service/user/account_info      |      |
| 用户修改密码                            | [POST]/sys_service/user/modify_password  |      |
| 租户申请列表                            | [GET]/tenant_service/tenant_regapply/list |      |
| 登录前查询租户信息                         | [GET]/tenant_service/tenant/query_tenant_before_login |      |
| 新增租户申请                            | [POST]/tenant_service/tenant_regapply    |      |
| 修改租户申请                            | [POST]/tenant_service/tenant_regapply/update |      |
| 获得一个租户申请                          | [GET]/tenant_service/tenant_regapply     |      |
| 审核租户申请                            | [POST]/tenant_service/tenant_regapply/examine |      |
| 关闭租户申请                            | [POST]/tenant_service/tenant_regapply/close |      |
| 官网租户试用申请列表                        | [GET]/tenant_service/website/tenant_trial_application/list |      |
| 租户入驻申请未通过后重新审核协议                  | [POST]/tenant_service/tenant_regapply/rollback_audit |      |
| 租户列表                              | [GET]/tenant_service/tenant/list         |      |
| 全部租户列表                            | [GET]/tenant_service/tenant/all          |      |
| 获得一个租户                            | [GET]/tenant_service/tenant              |      |
| 修改租户基本信息                          | [POST]/tenant_service/tenant/update_base |      |
| 修改租户开票信息                          | [POST]/tenant_service/tenant/update_ticket |      |
| 变更租户联系人                           | [POST]/tenant_service/tenant/change_tenant_contact |      |
| 上传图片                              | [POST]/tenant_service/tenant/upload_picture |      |
| 开发者账号信息获取                         | [GET]/sys_service/deve                   |      |
| 开发者账号信息保存                         | [POST]/sys_service/deve                  |      |
| 开发者账号信息修改                         | [POST]/sys_service/deve/update           |      |
| 登录记录查询                            | [GET]/tenant_service/login_record/list   |      |
| 数据下发列表                            | [GET] /sys_service/down_publish/list     |      |
| 数据下发                              | [POST]/sys_service/down_publish          |      |
| 标准诊断——诊断列表                        | [GET]/sys_service/diag/list              |      |
| 标准诊断——新增诊断                        | [POST]/sys_service/diag                  |      |
| 标准诊断——获取诊断                        | [GET]/sys_service/diag                   |      |
| 标准诊断——修改诊断                        | [POST]/sys_service/diag/update           |      |
| 标志诊断——停用诊断                        | [POST]/sys_service/diag/stop             |      |
| 标志诊断——删除诊断                        | [POST]/sys_service/diag/delete           |      |
| 标准诊断——前后缀列表                       | [GET]/sys_service/pref_suff/list         |      |
| 标志诊断——获得前后缀                       | [GET]/sys_service/pref_suff              |      |
| 标志诊断——新增前后缀                       | [POST]/sys_service/pref_suff             |      |
| 标准诊断——修改前后缀                       | [POST]/sys_service/pref_suff/update      |      |
| 标准诊断——停用前后缀                       | [POST]/sys_service/pref_suff/stop        |      |
| 标准诊断——删除前后缀                       | [POST]/sys_service/pref_suff/delete      |      |
| 标准术式列表                            | [GET]/sys_service/oper/list              |      |
| 新增标准术式                            | [POST]/sys_service/oper                  |      |
| 获取标准术式                            | [GET]/sys_service/oper                   |      |
| 修改标准术式                            | [POST]/sys_service/oper/update           |      |
| 停用标准术式                            | [POST]/sys_service/oper/stop             |      |
| 删除标准术式                            | [POST]/sys_service/oper/delete           |      |
| 过敏源列表                             | [GET]/sys_service/alle/list              |      |
| 新增过敏源                             | [POST]/sys_service/alle                  |      |
| 获取过敏源                             | [GET]/sys_service/alle                   |      |
| 修改过敏源                             | [POST]/sys_service/alle/update           |      |
| 停用过敏源                             | [POST]/sys_service/alle/stop             |      |
| 删除过敏源                             | [POST]/sys_service/alle/delete           |      |
| 计量单位列表                            | [GET]/sys_service/unit/list              |      |
| 获得一个计量单位                          | [GET]/sys_service/unit                   |      |
| 新增计量单位                            | [POST]/sys_service/unit                  |      |
| 修改计量单位                            | [POST]/sys_service/unit/update           |      |
| 停用计量单位                            | [POST]/sys_service/unit/stop             |      |
| 删除计量单位                            | [POST]/sys_service/unit/delete           |      |
| 频次列表                              | [GET]/sys_service/freq/list              |      |
| 获得一个频次                            | [GET]/sys_service/freq                   |      |
| 新增频次                              | [POST]/sys_service/freq                  |      |
| 修改频次                              | [POST]/sys_service/freq/update           |      |
| 停用频次                              | [POST]/sys_service/freq/stop             |      |
| 删除频次                              | [POST]/sys_service/freq/delete           |      |
| 角色列表                              | [GET] /sys_service/platfrom/role/list    |      |
| 租户树                               | [GET]/tenant_service/tenant/tree         |      |
| 新增角色                              | [POST] /sys_service/platform/role        |      |
| 修改角色                              | [POST] /sys_service/platform/role/update |      |
| 获取角色                              | [GET]/sys_service/platform/role          |      |
| 删除角色                              | [POST]/sys_service/platform/role/delete  |      |
| 获取角色功能权限信息                        | [GET]/sys_service/user/func_auth         |      |
| 获取用户信息（新增三个字段 职称、照片url、个人介绍、擅长专科） | [GET]/sys_service/user                   |      |
| 启用停用租户开发者账户                       | [POST]/sys_service/deve/start_stop       |      |
| 用户信息校验                            | [POST]/sys_service/user/info_check       |      |
| 用户注册                              | [POST]/sys_service/user/register         |      |
| 用户重置密码                            | [POST]/sys_service/user/reset_password   |      |
| 用户查询用科室列表                         | [GET]/sys_service/user/depa_list         |      |
| 获取用户列表信息（分页对象）                    | [GET]/sys_service/user/list              |      |
| 用户信息保存                            | [POST]/sys_service/user                  |      |
| 用户信息修改                            | [POST]/sys_service/user/update           |      |
| 启用停用用户                            | [POST]/sys_service/user/status/update    |      |
| 获取管理员信息                           | [GET]/sys_service/admi                   |      |
| 获取管理员列表信息                         | [GET]/sys_service/admi/list              |      |
| 管理员信息保存                           | [POST]/sys_service/admi                  |      |
| 管理员信息修改                           | [POST]/sys_service/admi/update           |      |
| 获取开发者账户列表信息                       | [GET]/sys_service/deve/list              |      |
| 开发者账号信息保存                         | [POST]/sys_service/deve                  |      |
| 文件批量上传                            | [POST]/sys_service/user/file_post        |      |
| 文件模板下载                            | [GET]/sys_service/user/file_temp_down    |      |
| 导入失败原因详情                          | [GET]/sys_service/user/impt/view         |      |
| 功能权限列表                            | [GET] /sys_service/func/platform/list    |      |
| 设备程序版本列表                          | [GET] /sys_service/program_version/list  |      |
| 设备程序信息获取                          | [GET] /sys_service/program_version       |      |
| 设备程序新增                            | [POST] /sys_service/api_program/add      |      |
| 上传版本程序                            | [POST]/sys_service/tenant/upload_version_file |      |
| 功能树                               | [GET] /sys_service/menu/tree             |      |
| 菜单信息获取                            | [GET] /sys_service/menu                  |      |
| 菜单新增                              | [POST] /sys_service/menu/add             |      |
| 菜单修改                              | [POST] /sys_service/menu/update          |      |
| 菜单删除协议                            | [DELETE]/sys_service/menu/{menu_id}      |      |
| 协议选项列表                            | [GET] /sys_service/protocol/option       |      |
| 协议列表                              | [GET] /sys_service/protocol/list         |      |
| 协议新增                              | [POST] /sys_service/protocol/add         |      |
| 协议获取                              | [GET] /sys_service/protocol              |      |
| 协议修改                              | [POST] /sys_service/protocol/update      |      |
| 标志诊断——删除协议                        | [POST] /sys_service/protocol/delete      |      |
| 短信签名保存/修改申请                       | [POST]/sys_service/sms/signature/update  |      |
| 查询短信签名                            | [GET]/sys_service/sms/signature          |      |
| 版本管理信息列表查询                        | [GET]/sys_service/version_mng/list       |      |
| 版本管理信息新增                          | [POST]/sys_service/version_mng/insert    |      |
| 版本管理信息详情查询                        | [GET]/sys_service/version_mng            |      |
| 分页查询ajax监控                        | [GET]/sys_service/ajax/record/list       |      |
| appweb监控异常查询                      | [GET]/sys_service/device/monitoring/exceptions |      |
| appweb监控全部查询                      | [GET]/sys_service/device/monitoring/all  |      |
| 打印模板维护列表查询                        | [GET]/sys_service/jasreport/list         |      |
| 租户个性设置默认打印模板查询                    | [GET]/sys_service/jasreport/tenet_getting |      |
| 租户个性设置默认打印模板                      | [POST]/sys_service/jasreport/tenet_setting |      |
| 打印模板打印类型列表查询                      | [GET]/sys_service/base_settings/printer/list |      |
| 模板文件/预览图片的预上传                     | [POST]/sys_service/jasreport/upload/picture_template |      |
| 打印模板新增                            | [POST]/sys_service/jasreport/insert      |      |
| 打印模板删除                            | [POST]/sys_service/jasreport/delete      |      |
| 打印模板选择默认项                         | [POST]/sys_service/jasreport/update      |      |
| 打印模板预览                            | [GET]/sys_service/jasreport/preview      |      |
| 服务号对接信息列表查询                       | [GET]/sys_service/tenant_regapply/docking/list |      |
| 服务号对接启用停用                         | [POST]/sys_service/tenant_regapply/docking/enable |      |
| 服务号对接详情                           | [GET]/sys_service/tenant_regapply/docking/info |      |
| 网页授权域名文件下载                        | [GET]/sys_service/tenant_regapply/docking/download |      |
| 最大在线用户数修改                         | [POST]/sys_service/login_record/maxonline/update |      |

## 1.0.4新增协议一览表

| 协议地址                                     | 协议名称          | 人员   | 备注   |
| ---------------------------------------- | ------------- | ---- | ---- |
| [GET]/sys_service/eye_examination/list   | 检查项列表查询       | 陈慧杰  |      |
| [GET]/sys_service/eye_examination/indicator/list | 检查项信息-指标项列表查询 | 陈慧杰  |      |
| [GET]/sys_service/eye_examination/indicator/info | 指标项信息查询       | 陈慧杰  |      |
| [GET]/sys_service/sales_personer/list    | 销售人员列表        | 陈慧杰  |      |
| [GET]/sys_service/cs_manager/list        | 客服经理          | 陈慧杰  |      |
| [GET]/sys_service/statistic/tenant/pagelist | 租户统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/patient/pagelist | 患者统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/book/pagelist | 挂号统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/recipe/pagelist | 处方统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/optometr/pagelist | 视光统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/drug/pagelist | 药品统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/drug/list    | 药品列表          | 陈慧杰  |      |
| [GET]/sys_service/statistic/goods/pagelist | 商品统计分页列表      | 陈慧杰  |      |
| [GET]/sys_service/statistic/goods/list   | 商品列表          | 陈慧杰  |      |


#BossWeb公用协议设计

## 登录

### 平台管理用户登录

> [POST]/platform/authent/login

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |

#### 请求报文参数

| 参数名      | 类型     | 必填   | 说明             |
| -------- | ------ | ---- | -------------- |
| account  | String | 是    | 账号，可以是手机号码、工号等 |
| password | String | 是    | 密码             |

header中填写

| 参数名        | 类型     | 必填   | 说明                 |
| ---------- | ------ | ---- | ------------------ |
| tenantId   | Long   | 是    | 租户号                |
| os         | String | 是    | 客户端操作系统，包含操作系统与版本号 |
| device     | String | 是    | 当前设备名称，如iOS的手机设备名称 |
| user_agent | String | 是    | 浏览器 类型             |


#### 回复报文参数

| 参数名             | 类型         | 必填   | 说明                     |
| --------------- | ---------- | ---- | ---------------------- |
| token           | String     | 是    | 令牌，用于标志用户登录的有效性        |
| user_id         | String     | 是    | 用户唯一id                 |
| name            | String     | 是    | 用户姓名                   |
| job_number      | String     | 是    | 工号                     |
| is_admin_change | boolean    | 是    | true 超级管理员 false 普通管理员 |
| funcs           | LongList   | 否    | 权限列表                   |
| tenas           | LongList   | 否    | 关联租户列表                 |
| users           | ObjectList | 否    | 用户列表                   |


funcs结构：

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| func_id | String | 是    | 功能id |

tenas结构：

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| tena_id | Long | 是    | 租户ID |

users结构：

| 参数名             | 类型     | 必填   | 说明   |
| --------------- | ------ | ---- | ---- |
| user_job_number | Long   | 是    | 用户ID |
| user_name       | String | 是    | 用户姓名 |




### 通用仓库列表

> [GET]/common_service/depot_list

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明            |
| ---------- | ------- | ---- | ------------- |
| depo_id    | String  | 否    | 仓库id          |
| depot_type | Integer | 是    | 1:管理仓库 2:销售仓库 |

#### 回复报文参数

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| depo_id   | String | 是    | 仓库id |
| depo_name | String | 是    | 仓库名称 |



### 获取科室列表信息

> [GET]/sys_service/depa/list

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数(ObjectList)

| 参数名          | 类型     | 必填   | 说明     |
| ------------ | ------ | ---- | ------ |
| depa_id      | Long   | 是    | 部门ID   |
| depa_name    | String | 是    | 部门名称   |
| depa_pare_id | Long   | 是    | 上级部门ID |


### 获取地址列表

> [GET]/address_service/address/list

获取地址列表

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数(ObjectList)

| 参数名           | 类型         | 必填   | 说明   |
| ------------- | ---------- | ---- | ---- |
| province_code | String     | No   | 省代码  |
| province_name | String     | No   | 省名称  |
| citylist      | ObjectList |      | 市级列表 |


####市级列表说明
| 参数名        | 类型         | 必填   | 说明    |
| ---------- | ---------- | ---- | ----- |
| city_code  | String     | No   | 城市代码  |
| city_name  | String     | No   | 城市名称  |
| countylist | ObjectList |      | 区县级列表 |

####区县级列表说明
| 参数名         | 类型     | 必填   | 说明   |
| ----------- | ------ | ---- | ---- |
| county_code | String | No   | 区县代码 |
| county_name | String | No   | 区县名称 |


### 用户账号信息    

>  [GET]/sys_service/user/account_info

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数

| 参数名             | 类型     | 必填   | 说明   |
| --------------- | ------ | ---- | ---- |
| user_id         | String | 是    | 用户id |
| user_name       | String | 是    | 用户名字 |
| user_mail       | String | 是    | 用户邮箱 |
| user_job_number | String | 否    | 工号   |
| depa_name       | String | 否    | 科室   |
| user_post       | String | 否    | 岗位   |
| user_phone      | String | 是    | 手机号  |



### 用户修改密码

>  [POST]/sys_service/user/modify_password

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |

#### 请求报文参数

| 参数名          | 类型     | 必填   | 说明   |
| ------------ | ------ | ---- | ---- |
| old_password | String | 是    | 旧密码  |
| new_password | String | 是    | 新密码  |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |









# BossWeb租户申请协议设计



### 租户申请列表

> [GET]/tenant_service/tenant_regapply/list


#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |

#### 请求报文参数

| 参数名               | 类型      | 必填   | 说明                      |
| ----------------- | ------- | ---- | ----------------------- |
| appl_audit_status | Integer | 是    | 审核状态,0-未审核；1-审核通过；2-已关闭 |
| key               | String  | 否    | 租户名称模糊搜索                |
| page_size         | Integer | 否    | 每页条数 空表示10条             |
| page_num          | Integer | 否    | 第几页 空表示第1页              |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| wait_num  | Integer    | 是    | 未审核条数       |
| check_num | Integer    | 是    | 审核条数        |
| close_num | Integer    | 是    | 已关闭条数       |
| appl_list | ObjectList | 否    | 租户列表        |

租户列表说明

| 参数名                | 类型      | 必填   | 说明                       |
| ------------------ | ------- | ---- | ------------------------ |
| appl_id            | String  | 是    | 申请ID                     |
| appl_name          | String  | 是    | 租户名称                     |
| appl_linkman_name  | String  | 是    | 联系人                      |
| appl_linkman_phone | String  | 是    | 联系人手机                    |
| appl_linkman_mail  | String  | 是    | 联系人邮箱                    |
| appl_source        | Integer | 是    | 申请来源                     |
| appl_audit_status  | Integer | 是    | 审核状态,0-未审核；1-审核通过；2-审核未通 |
| appl_audit_userid  | String  | 否    | 审核人id                    |
| appl_time          | Date    | 否    | 申请时间                     |
| appl_audit_time    | Date    | 否    | 审核时间                     |
| appl_audit_user    | String  | 否    | 审核人                      |

### 登录前查询租户信息

> [GET]/tenant_service/tenant/query_tenant_before_login


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

#### 回复报文参数

| 参数名           | 类型     | 必填   | 说明     |
| ------------- | ------ | ---- | ------ |
| tena_id       | String | 是    | 租户号    |
| tena_name     | String | 是    | 租户名称   |
| tena_logo_url | String | 否    | 租户logo |



### 新增租户申请

> [POST]/tenant_service/tenant_regapply


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名                   | 类型      | 必填     | 说明                                       |
| --------------------- | ------- | ------ | ---------------------------------------- |
| appl_name             | String  | 是      | 租户名称                                     |
| appl_enname           | String  | 否      | 企业英文名                                    |
| appl_type             | Integer | 是      | 机构类型,1-集团；2-集团下属医院；3-独立专科医院；4-小型诊所       |
| appl_attr             | Integer | 是      | 机构属性,1-公立；2-民营                           |
| appl_level            | Integer | 是      | 医院等级,1-特等;2-三甲;3-三乙;4-三丙;5-二甲;6-二乙;7-二丙;8-一甲;9-一乙;10-一丙; |
| appl_legalname        | String  | 是      | 法人姓名                                     |
| appl_legalmobile      | String  | 是      | 法人手机号                                    |
| appl_citycode         | String  | 是      | 公司省市区,代码                                 |
| appl_address          | String  | 是      | 公司详细地址                                   |
| appl_phone            | String  | 是      | 公司电话                                     |
| tena_licence_validity | Date    | 是      | 营业执照有效期                                  |
| appl_linkman_name     | String  | 是      | 联系人                                      |
| appl_linkman_phone    | String  | 是      | 联系人手机                                    |
| appl_linkman_mail     | String  | 是      | 联系人邮箱                                    |
| appl_source           | Integer | 是      | 申请来源                                     |
| appl_license_image    | String  | 是      | 营业执照照片,资源服务ID                            |
| appl_legalidno_person | String  | 是      | 法人身份证-个人信息页,资源服务ID                       |
| appl_legalidno_emblem | String  | 是      | 法人身份证-国微页,资源服务ID                         |
| appl_logo             | String  | 否      | 公司LOGO,资源服务ID                            |
| sales_id              |         | String | 是                                        |
| customer_service_id   |         | String | 是                                        |

#### 回复报文参数

| 参数名          | 类型      | 必填   | 说明                       |
| ------------ | ------- | ---- | ------------------------ |
| appl_id      | String  | 是    | 申请ID                     |
| phone_active | Integer | 是    | 手机账号是否已经验证激活；0-未激活；1-已激活 |
| email_active | Integer | 是    | 邮箱账号是否已经验证激活；0-未激活；1-已激活 |



### 修改租户申请

> [POST]/tenant_service/tenant_regapply/update


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名                   | 类型      | 必填     | 说明                                       |
| --------------------- | ------- | ------ | ---------------------------------------- |
| appl_id               | String  | 是      | 申请ID                                     |
| appl_name             | String  | 是      | 租户名称                                     |
| appl_enname           | String  | 否      | 企业英文名                                    |
| appl_type             | Integer | 是      | 机构类型,1-集团；2-集团下属医院；3-独立专科医院；4-小型诊所       |
| appl_attr             | Integer | 是      | 机构属性,1-公立；2-民营                           |
| appl_level            | Integer | 是      | 医院等级,1-特等;2-三甲;3-三乙;4-三丙;5-二甲;6-二乙;7-二丙;8-一甲;9-一乙;10-一丙; |
| appl_legalname        | String  | 是      | 法人姓名                                     |
| appl_legalmobile      | String  | 是      | 法人手机号                                    |
| appl_citycode         | String  | 是      | 公司省市区,代码                                 |
| appl_address          | String  | 是      | 公司详细地址                                   |
| appl_phone            | String  | 是      | 公司电话                                     |
| tena_licence_validity | Date    | 是      | 营业执照有效期                                  |
| appl_linkman_name     | String  | 是      | 联系人                                      |
| appl_linkman_phone    | String  | 是      | 联系人手机                                    |
| appl_linkman_mail     | String  | 是      | 联系人邮箱                                    |
| appl_source           | Integer | 是      | 申请来源                                     |
| appl_license_image    | String  | 是      | 营业执照照片,资源服务ID                            |
| appl_legalidno_person | String  | 是      | 法人身份证-个人信息页,资源服务ID                       |
| appl_legalidno_emblem | String  | 是      | 法人身份证-国微页,资源服务ID                         |
| appl_logo             | String  | 否      | 公司LOGO,资源服务ID                            |
| sales_id              |         | String | 是                                        |
| customer_service_id   |         | String | 是                                        |
#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 获得一个租户申请

> [GET]/tenant_service/tenant_regapply


#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| appl_id | String | 是    | 申请ID |

#### 请求报文参数

| 参数名                       | 类型      | 必填     | 说明                                       |
| ------------------------- | ------- | ------ | ---------------------------------------- |
| appl_id                   | String  | 是      | 申请ID                                     |
| appl_tena_id              | String  | 否      | 租户id                                     |
| appl_name                 | String  | 是      | 租户名称                                     |
| appl_enname               | String  | 否      | 企业英文名                                    |
| appl_type                 | Integer | 是      | 机构类型,1-集团；2-集团下属医院；3-独立专科医院；4-小型诊所       |
| appl_attr                 | Integer | 是      | 机构属性,1-公立；2-民营                           |
| appl_level                | Integer | 是      | 医院等级,1-特等;2-三甲;3-三乙;4-三丙;5-二甲;6-二乙;7-二丙;8-一甲;9-一乙;10-一丙; |
| appl_legalname            | String  | 是      | 法人姓名                                     |
| appl_legalmobile          | String  | 是      | 法人手机号                                    |
| appl_provincecode         | String  | 是      | 省                                        |
| appl_areacode             | String  | 是      | 市                                        |
| appl_citycode             | String  | 是      | 区                                        |
| appl_address              | String  | 是      | 公司详细地址                                   |
| appl_phone                | String  | 是      | 公司电话                                     |
| tena_licence_validity     | Date    | 是      | 营业执照有效期                                  |
| appl_linkman_name         | String  | 是      | 联系人                                      |
| appl_linkman_phone        | String  | 是      | 联系人手机                                    |
| phone_active              | Integer | 是      | 手机账号是否已经验证激活；0-未激活；1-已激活                 |
| appl_linkman_mail         | String  | 是      | 联系人邮箱                                    |
| email_active              | Integer | 是      | 邮箱账号是否已经验证激活；0-未激活；1-已激活                 |
| appl_source               | Integer | 是      | 申请来源                                     |
| appl_license_image        | String  | 是      | 营业执照照片,资源服务ID                            |
| appl_license_image_url    | String  | 是      | 营业执照照片,资源服务url                           |
| appl_legalidno_person     | String  | 是      | 法人身份证-个人信息页,资源服务ID                       |
| appl_legalidno_person_url | String  | 是      | 法人身份证-个人信息页,资源服务url                      |
| appl_legalidno_emblem     | String  | 是      | 法人身份证-国微页,资源服务ID                         |
| appl_legalidno_emblem_url | String  | 是      | 法人身份证-国微页,资源服务url                        |
| appl_logo_url             | String  | 否      | 公司LOGO,指向OSS的URL                         |
| appl_audit_status         | Integer | 是      | 审核状态,0-未审核；1-审核通过；2-审核未通                 |
| appl_rem                  | String  | 是      | 不通过原因                                    |
| sales_id                  |         | String | 是                                        |
| customer_service_id       |         | String | 是                                        |



### 审核租户申请

> [POST]/tenant_service/tenant_regapply/examine


#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| appl_id | String | 是    | 租户申请id |

#### 回复报文参数

| 参数名          | 类型     | 必填   | 说明   |
| ------------ | ------ | ---- | ---- |
| appl_tena_id | String | 是    | 租户id |



### 关闭租户申请

> [POST]/tenant_service/tenant_regapply/close


#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名             | 类型     | 必填   | 说明            |
| --------------- | ------ | ---- | ------------- |
| appl_id         | String | 是    | 租户申请idappl_id |
| appl_audit_note | String | 是    | 不通过原因         |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |



### 官网租户试用申请列表

```url
[GET]/tenant_service/website/tenant_trial_application/list
```

#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| key       | String  | 否    | 机构称模糊搜索     |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| appl_list | ObjectList | 否    | 申请列表        |

租户列表说明

| 参数名                | 类型      | 必填   | 说明                                       |
| ------------------ | ------- | ---- | ---------------------------------------- |
| appl_id            | String  | 是    | 申请ID                                     |
| appl_name          | String  | 是    | 机构名称                                     |
| appl_linkman_name  | String  | 是    | 联系人                                      |
| appl_linkman_phone | String  | 是    | 联系人手机                                    |
| appl_type          | Integer | 是    | 机构类型;1-集团；2-集团下属医院；3-独立专科医院；4-眼科诊所;5-综合医院 |
| appl_message       | String  | 否    | 留言信息                                     |
| appl_time          | Date    | 是    | 申请时间                                     |

### 租户入驻申请未通过后重新审核协议

```url
[POST]/tenant_service/tenant_regapply/rollback_audit
```

说明：
1. 给未通过审核的租户再一次机会，把未通过审核的状态修改成未审核。

异常处理
1. 申请不存在；
2. 本次申请不是未通过审核的申请；

#### 修改更新记录

| 对应版本       | 说明   |
| ---------- | ---- |
| BOSSV1.0.2 | 新增   |

#### 修改影响表

租户入驻申请表(com_tena_regapply)

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| appl_id | Long | 是    | 申请ID |

#### 回复报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| appl_id | Long | 是    | 申请ID |





#BossWeb租户管理协议设计



### 租户列表

> [GET]/tenant_service/tenant/list


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| key       | String  | 否    | 租户名称模糊搜索    |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| tena_list | ObjectList | 否    | 租户列表        |

租户列表说明

| 参数名                | 类型     | 必填   | 说明    |
| ------------------ | ------ | ---- | ----- |
| tena_id            | String | 是    | 租户ID  |
| tena_name          | String | 是    | 租户名称  |
| tena_contact_name  | String | 是    | 联系人   |
| tena_contact_phone | String | 是    | 联系人手机 |
| tena_contact_mail  | String | 是    | 联系人邮箱 |
| tena_url           | String | 是    | 租户url |



### 全部租户列表

> [GET]/tenant_service/tenant/all


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明       |
| ---- | ------ | ---- | -------- |
| key  | String | 否    | 租户名称模糊搜索 |


#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明   |
| --------- | ---------- | ---- | ---- |
| total     | Integer    | 是    | 总记录数 |
| tena_list | ObjectList | 否    | 租户列表 |

租户列表说明

| 参数名                | 类型     | 必填   | 说明    |
| ------------------ | ------ | ---- | ----- |
| tena_id            | String | 是    | 租户ID  |
| tena_name          | String | 是    | 租户名称  |
| tena_contact_name  | String | 是    | 联系人   |
| tena_contact_phone | String | 是    | 联系人手机 |
| tena_contact_mail  | String | 是    | 联系人邮箱 |
| tena_url           | String | 是    | 租户url |


### 获得一个租户

> [GET]/tenant_service/tenant


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| tena_id | String | 是    | 租户ID |

#### 回复报文参数

| 参数名                       | 类型         | 必填     | 说明                                       |
| ------------------------- | ---------- | ------ | ---------------------------------------- |
| tena_id                   | String     | 是      | 租户ID                                     |
| tena_name                 | String     | 是      | 租户名                                      |
| tena_enname               | String     | 否      | 租户英文名                                    |
| tena_type                 | Integer    | 是      | 机构类型,1-集团；2-集团下属医院；3-独立专科医院；4-小型诊所       |
| tena_attr                 | Integer    | 是      | 机构属性,1-公立；2-民营                           |
| tena_level                | Integer    | 是      | 医院等级,0-无;1-特等;2-三甲;3-三乙;4-三丙;5-二甲;6-二乙;7-二丙;8-一甲;9-一乙;10-一丙; |
| tena_provincecode         | String     | 是      | 省                                        |
| tena_areacode             | String     | 是      | 市                                        |
| tena_citycode             | String     | 是      | 区                                        |
| tena_address              | String     | 是      | 公司详细地址                                   |
| tena_legalname            | String     | 是      | 法人姓名                                     |
| tena_legalmobile          | String     | 是      | 法人手机号                                    |
| tena_licence_validity     | Date       | 是      | 营业执照有效期                                  |
| tena_licence_resid        | String     | 是      | 营业执照照片,资源服务ID                            |
| tena_licence_resid_url    | String     | 是      | 营业执照照片,资源服务url                           |
| tena_legalidno_person     | String     | 是      | 法人身份证-个人信息页,资源服务ID                       |
| tena_legalidno_person_url | String     | 是      | 法人身份证-个人信息页,资源服务url                      |
| tena_legalidno_emblem     | String     | 是      | 法人身份证-国微页,资源服务ID                         |
| tena_legalidno_emblem_url | String     | 是      | 法人身份证-国微页,资源服务url                        |
| tena_logo_url             | String     | 否      | 公司LOGO,指向OSS的URL                         |
| tena_bgimg_url            | String     | 否      | 租户登陆背景图片url                              |
| tena_taxname              | String     | 否      | 单位名称,开票用                                 |
| tena_taxno                | String     | 否      | 税号                                       |
| tena_bank                 | String     | 否      | 开户银行                                     |
| tena_bankcard             | String     | 否      | 银行卡号                                     |
| tena_taxaddress           | String     | 否      | 公司地址,开票用的                                |
| tena_phone                | String     | 否      | 公司电话                                     |
| tena_contact_name         | String     | 是      | 联系人姓名                                    |
| tena_contact_phone        | String     | 是      | 联系人电话                                    |
| tena_contact_mail         | String     | 是      | 联系人邮箱                                    |
| tena_orgcode              | String     | 是      | 租户组织代码                                   |
| tena_url                  | String     | 是      | 租户url                                    |
| contact_list              | ObjectList | 是      | 联系人列表                                    |
| dev_list                  | ObjectList | 否      | 开发者账户列表                                  |
| sales_id                  |            | String | 是                                        |
| customer_service_id       |            | String | 是                                        |


联系人列表说明

| 参数名                  | 类型      | 必填   | 说明                 |
| -------------------- | ------- | ---- | ------------------ |
| admi_id              | String  | 是    | 管理员id              |
| admi_name            | String  | 是    | 联系人                |
| admi_phone           | String  | 是    | 手机                 |
| admi_email           | String  | 是    | 邮箱（登录账号）           |
| admi_changeuser_name | String  | 是    | 修改人                |
| admi_time            | String  | 是    | 记录变更时间             |
| admi_enable          | Integer | 是    | 禁用状态,默认1；0-停用，1-启用 |

开发者账户列表说明

| 参数名                 | 类型      | 必填   | 说明           |
| ------------------- | ------- | ---- | ------------ |
| deve_id             | Long    | 是    | 开发账号ID       |
| deve_name           | String  | 是    | 账号名称         |
| deve_code           | String  | 是    | 账号编码         |
| deve_memo           | String  | 否    | 备注           |
| deve_audit_username | String  | 是    | 修改人          |
| deve_autid_time     | String  | 是    | 修改时间         |
| deve_enable         | Integer | 是    | 状态；0-停用；1-启用 |



### 修改租户基本信息

> [POST]/tenant_service/tenant/update_base


#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名                   | 类型      | 必填     | 说明                                       |
| --------------------- | ------- | ------ | ---------------------------------------- |
| tena_id               | String  | 是      | 租户ID                                     |
| tena_name             | String  | 是      | 租户名                                      |
| tena_enname           | String  | 否      | 租户英文名                                    |
| tena_type             | Integer | 是      | 机构类型,1-集团；2-集团下属医院；3-独立专科医院；4-小型诊所       |
| tena_attr             | Integer | 是      | 机构属性,1-公立；2-民营                           |
| tena_level            | Integer | 是      | 医院等级,1-特等;2-三甲;3-三乙;4-三丙;5-二甲;6-二乙;7-二丙;8-一甲;9-一乙;10-一丙; |
| tena_provincecode     | String  | 是      | 省                                        |
| tena_areacode         | String  | 是      | 市                                        |
| tena_citycode         | String  | 是      | 区                                        |
| tena_address          | String  | 是      | 公司详细地址                                   |
| tena_legalname        | String  | 是      | 法人姓名                                     |
| tena_legalmobile      | String  | 是      | 法人手机号                                    |
| tena_licence_validity | Date    | 是      | 营业执照有效期                                  |
| tena_license_image    | String  | 是      | 营业执照照片,资源服务ID                            |
| tena_legalidno_person | String  | 是      | 法人身份证-个人信息页,资源服务ID                       |
| tena_legalidno_emblem | String  | 是      | 法人身份证-国微页,资源服务ID                         |
| tena_logo             | String  | 否      | 公司LOGO,资源服务ID                            |
| tena_orgcode          | String  | 否      | 租户组织代码                                   |
| tena_bgimg            | String  | 否      | 租户背景图片,资源服务ID                            |
| sales_id              |         | String | 是                                        |
| customer_service_id   |         | String | 是                                        |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 修改租户开票信息  

> [POST]/tenant_service/tenant/update_ticket


#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名             | 类型     | 必填   | 说明        |
| --------------- | ------ | ---- | --------- |
| tena_id         | String | 是    | 租户ID      |
| tena_taxname    | String | 否    | 单位名称,开票用  |
| tena_taxno      | String | 否    | 税号        |
| tena_bank       | String | 否    | 开户银行      |
| tena_bankcard   | String | 否    | 银行卡号      |
| tena_taxaddress | String | 否    | 公司地址,开票用的 |
| tena_phone      | String | 否    | 公司电话      |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 变更租户联系人   

> [POST]/tenant_service/tenant/change_tenant_contact


#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名                | 类型     | 必填   | 说明    |
| ------------------ | ------ | ---- | ----- |
| tena_id            | String | 是    | 租户ID  |
| tena_contact_name  | String | 是    | 联系人姓名 |
| tena_contact_phone | String | 是    | 联系人电话 |
| tena_contact_mail  | String | 是    | 联系人邮箱 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |




### 上传图片
```http
[POST]/tenant_service/tenant/upload_picture
```


#### 修改更新记录

| 对应版本   | 说明         |
| ------ | ---------- |
| V1.0.1 | 新增         |
| V1.0.2 | 修改  增加资源类型 |



#### 请求报文参数

| 参数名            | 类型      | 必填   | 说明                                       |
| -------------- | ------- | ---- | ---------------------------------------- |
| file_size      | Long    | 否    | 文件内容长度                                   |
| file_extension | String  | 是    | 文件扩展名(不带“.“)                             |
| file_type      | String  | 是    | 文件类型，Content-Type                        |
| file_signature | String  | 否    | 文件的签名值MD5,Base64编码                       |
| work_id        | Long    | 否    | 工作站ID，用户在哪个工作站中上传的                       |
| factory_id     | String  | 否    | 厂商id                                     |
| business_id    | String  | 否    | 业务标志，意义由上传类型确定；9时为商品ID                   |
| source_type    | Integer | 是    | 上传类型 1:logo;</br>2:法人身份证正面;</br>3.法人身份证背面;</br>4:营业执照;</br>5.用户类型</br>6.医生签名</br>7.厂商营业执照</br>8.厂商生产许可证；</br>9.商品目录注册证号文件                          13.设备程序 |

#### 回复报文参数

| 参数名                     | 类型     | 必填   | 说明                       |
| ----------------------- | ------ | ---- | ------------------------ |
| url                     | String | 是    | 操作的URL                   |
| file_id                 | Long   | 是    | 文件资源id                   |
| OSS_access_key_id       | String | 是    | Bucket 拥有者的Access Key Id |
| policy                  | String | 是    | Base64编码的JSON内容          |
| signature               | String | 是    | 签名                       |
| key                     | String | 是    | 上传文件路径                   |
| success_action_redirect | String | 是    | 文件上传成功后的跳转地址             |


### 开发者账号信息获取

> [GET]/sys_service/deve

#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明     |
| ------- | ---- | ---- | ------ |
| deve_id | Long | 是    | 开发账号ID |

#### 回复报文参数

| 参数名              | 类型      | 必填   | 说明           |
| ---------------- | ------- | ---- | ------------ |
| deve_id          | String  | 是    | 开发账号ID       |
| deve_name        | String  | 是    | 账号名称         |
| deve_code        | String  | 是    | 开发账号编码       |
| deve_key_content | String  | 是    | 公钥           |
| deve_use_type    | Integer | 否    | 账号的用途        |
| deve_memo        | Integer | 否    | 备注           |
| deve_enable      | Integer | 否    | 状态；0-停用；1-启用 |



### 登录记录查询

> [GET]/sys_service/login_record/list


#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |



#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明                  |
| ---------- | ------- | ---- | ------------------- |
| tena_id    | String  | 是    | 租户ID                |
| begin_time | String  | 否    | 开始时间  格式 yyyy-mm-dd |
| end_time   | String  | 否    | 结束时间  格式 yyyy-mm-dd |
| page_size  | Integer | 否    | 每页条数 空表示10条         |
| page_num   | Integer | 否    | 第几页 空表示第1页          |

#### 回复报文参数

| 参数名         | 类型         | 必填   | 说明          |
| ----------- | ---------- | ---- | ----------- |
| page_size   | Integer    | 是    | 每页条数 空表示10条 |
| page_num    | Integer    | 是    | 第几页 空表示第1页  |
| total       | Integer    | 是    | 总记录数        |
| pages       | Integer    | 是    | 总页数         |
| max_online  | Integer    | 是    | 在线最大人数      |
| record_list | ObjectList | 否    | 登录记录列表      |

登录记录列表说明

| 参数名         | 类型     | 必填   | 说明     |
| ----------- | ------ | ---- | ------ |
| login_id    | String | 是    | 登录记录ID |
| account     | String | 是    | 用户名    |
| name        | String | 是    | 姓名     |
| login_time  | String | 是    | 登录时间   |
| logout_time | String | 是    | 退出时间   |
| long_time   | String | 是    | 在线时长   |
| client_ip   | String | 是    | IP地址   |

### 最大在线用户数修改
```
[POST]/sys_service/login_record/maxonline/update
```
涉及到的表：
版本管理信息表(pla_tena_maxonline)

说明：

租户配置表（tena_configure）配置项列表

| 配置代码   | 说明     | 默认值   |
| ------ | ------ | ----- |
| 100002 | 最大在线人数 | 10000 |


#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 更新   |

#### 请求报文参数

#### RequestBody
| 参数名        | 长度   | 类型     | 必填   | 说明     |
| ---------- | ---- | ------ | ---- | ------ |
| max_online | 11   | String | 是    | 最大在线人数 |
| tenat_id   |      | String | 是    | 租户id   |

#### 回复报文参数


#BossWeb初始数据下发协议设计


### 数据下发列表

> [GET] /sys_service/down_publish/list

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| tena_id | String | 是    | 租户id |

#### 回复报文参数(Object)

| 参数名             | 类型         | 必填   | 说明      |
| --------------- | ---------- | ---- | ------- |
| to_publish_list | ObjectList | 是    | 待发布项目列表 |
| published_list  | ObjectList | 是    | 已发布项目列表 |


待发布项目列表说明

| 参数名       | 类型      | 必填   | 说明                                       |
| --------- | ------- | ---- | ---------------------------------------- |
| item_type | Integer | 是    | 项目类型  1:常规角色 2:科室组织; 3:标准诊断 4:标准术式   8:过敏原 10:执行频率 |
| item_name | String  | 是    | 项目名称                                     |

已发布项目列表说明

| 参数名          | 类型      | 必填   | 说明                                       |
| ------------ | ------- | ---- | ---------------------------------------- |
| item_type    | Integer | 是    | 项目类型  1:常规角色 2:科室组织; 3:标准诊断 4:标准术式   8:过敏原 10:执行频率 |
| item_name    | String  | 是    | 项目名称                                     |
| operator     | String  | 是    | 下发人                                      |
| operate_time | String  | 是    | 下发时间                                     |




### 数据下发

> [POST]/sys_service/down_publish


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |



#### 请求报文参数

| 参数名            | 类型          | 必填   | 说明     |
| -------------- | ----------- | ---- | ------ |
| tena_id        | String      | 是    | 租户id   |
| item_type_list | IntegerList | 是    | 项目类型列表 |

#### 回复报文参数(ObjectList)

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



#BossWeb初始数据协议设计




##标准诊断


### 标准诊断——诊断列表  

> [GET]/sys_service/diag/list

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| key       | String  | 是    | 关键字         |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 诊断列表  |

诊断列表说明

| 参数名              | 类型      | 必填   | 说明            |
| ---------------- | ------- | ---- | ------------- |
| diag_id          | String  | 是    | 诊断id          |
| diag_icd         | String  | 是    | 诊断ICD编码       |
| diag_attach      | String  | 否    | 附加码           |
| diag_name        | String  | 是    | 诊断名称          |
| alia_names       | String  | 是    | 别名            |
| diag_create_user | String  | 是    | 录入人           |
| diag_enable      | Integer | 是    | 是否有效 0：停用1：有效 |


### 标准诊断——新增诊断

> [POST]/sys_service/diag

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名            | 类型         | 必填   | 说明            |
| -------------- | ---------- | ---- | ------------- |
| diag_icd       | String     | 是    | 诊断ICD编码       |
| diag_attach    | String     | 否    | 附加码           |
| diag_name      | String     | 是    | 诊断名称          |
| alia_name_list | ObjectList | 否    | 别名列表          |
| diag_enable    | Integer    | 是    | 是否有效 0：停用1：有效 |

别名列表说明

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| alia_name | String | 是    | 别名   |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| diag_id | String | 是    | 诊断id |



### 标准诊断——获取诊断

> [GET]/sys_service/diag

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| diag_id | String | 是    | 诊断id |

#### 回复报文参数

| 参数名            | 类型         | 必填   | 说明            |
| -------------- | ---------- | ---- | ------------- |
| diag_id        | String     | 是    | 诊断id          |
| diag_icd       | String     | 是    | 诊断ICD编码       |
| diag_attach    | String     | 否    | 附加码           |
| diag_name      | String     | 是    | 诊断名称          |
| alia_name_list | ObjectList | 否    | 别名列表          |
| diag_enable    | Integer    | 是    | 是否有效 0：停用1：有效 |

别名列表说明

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| alia_id   | String | 是    | 别名id |
| alia_name | String | 是    | 别名   |

### 标准诊断——修改诊断

> [POST]/sys_service/diag/update

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名            | 类型         | 必填   | 说明            |
| -------------- | ---------- | ---- | ------------- |
| diag_id        | String     | 是    | 诊断id          |
| diag_name      | String     | 是    | 诊断名称          |
| alia_name_list | ObjectList | 是    | 别名列表          |
| alia_del_list  | LongList   | 否    | 删除别名列表        |
| diag_enable    | Integer    | 是    | 是否有效 0：停用1：有效 |

别名列表跟删除别名列表说明

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| alia_id   | String | 否    | 别名id |
| alia_name | String | 是    | 别名   |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 标志诊断——停用诊断

> [POST]/sys_service/diag/stop

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| diag_id     | String  | 是    | 诊断id          |
| diag_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

### 标志诊断——删除诊断

> [POST]/sys_service/diag/delete

####修改更新记录

| 对应版本   | 说明        |
| ------ | --------- |
| V1.0.2 | 新增 增加删除功能 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| diag_id | String | 是    | 诊断id |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |



### 标准诊断——前后缀列表  

> [GET]/sys_service/pref_suff/list

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明            |
| --------- | ------- | ---- | ------------- |
| key       | String  | 是    | 关键字           |
| appe_type | String  | 是    | 类型 前缀=1, 后缀=2 |
| page_size | Integer | 否    | 每页条数 空表示10条   |
| page_num  | Integer | 否    | 第几页 空表示第1页    |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 前后缀列表 |

前后缀列表说明

| 参数名              | 类型     | 必填   | 说明            |
| ---------------- | ------ | ---- | ------------- |
| appe_id          | String | 是    | id            |
| appe_name        | String | 是    | 名称            |
| appe_create_user | String | 是    | 录入人           |
| appe_enable      | String | 是    | 是否有效 0：停用1：有效 |



### 标志诊断——获得前后缀

>[GET]/sys_service/pref_suff

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明            |
| --------- | ------ | ---- | ------------- |
| appe_id   | String | 是    | id            |
| appe_type | String | 是    | 类型 前缀=1, 后缀=2 |

#### 回复报文参数

| 参数名         | 类型     | 必填   | 说明            |
| ----------- | ------ | ---- | ------------- |
| appe_id     | String | 是    | id            |
| appe_name   | String | 是    | 名称            |
| appe_enable | String | 是    | 是否有效 0：停用1：有效 |



### 标志诊断——新增前后缀

> [POST]/sys_service/pref_suff

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型     | 必填   | 说明            |
| ----------- | ------ | ---- | ------------- |
| appe_name   | String | 是    | 名称            |
| appe_type   | String | 是    | 类型 前缀=1, 后缀=2 |
| appe_enable | String | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| appe_id | String | 是    | id   |

### 标准诊断——修改前后缀

> [POST]/sys_service/pref_suff/update

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型     | 必填   | 说明            |
| ----------- | ------ | ---- | ------------- |
| appe_id     | String | 是    | id            |
| appe_name   | String | 是    | 名称            |
| appe_type   | String | 是    | 类型 前缀=1, 后缀=2 |
| appe_enable | String | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

### 标准诊断——停用前后缀

> [POST]/sys_service/pref_suff/stop

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型     | 必填   | 说明            |
| ----------- | ------ | ---- | ------------- |
| appe_id     | String | 是    | id            |
| appe_enable | String | 是    | 是否有效 0：停用1：有效 |
| appe_type   | String | 是    | 类型 前缀=1, 后缀=2 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 标准诊断——删除前后缀

> [POST]/sys_service/pref_suff/delete

####修改更新记录

| 对应版本   | 说明        |
| ------ | --------- |
| V1.0.2 | 新增 增加删除功能 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| appe_id | String | 是    | id   |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |



##标准术式

### 标准术式列表  

> [GET]/sys_service/oper/list

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| key       | String  | 是    | 关键字         |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 当前页    |
| page_size | Integer    | 是    | 每页的数量  |
| total     | Integer    | 是    | 总记录数   |
| pages     | Integer    | 是    | 总页数    |
| list      | ObjectList | 否    | 标准术式列表 |

标准术式列表说明

| 参数名              | 类型      | 必填   | 说明            |
| ---------------- | ------- | ---- | ------------- |
| oper_id          | String  | 是    | 术式id          |
| oper_code        | String  | 是    | 术式编码          |
| oper_name        | String  | 是    | 术式名称          |
| alia_names       | String  | 是    | 别名            |
| oper_create_user | String  | 是    | 录入人           |
| oper_enable      | Integer | 是    | 是否有效 0：停用1：有效 |


### 新增标准术式

> [POST]/sys_service/oper

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名            | 类型         | 必填   | 说明            |
| -------------- | ---------- | ---- | ------------- |
| oper_code      | String     | 是    | 术式编码          |
| oper_name      | String     | 是    | 术式名称          |
| alia_name_list | ObjectList | 否    | 别名列表          |
| oper_enable    | Integer    | 是    | 是否有效 0：停用1：有效 |

别名列表说明

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| alia_name | String | 是    | 别名   |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| oper_id | String | 是    | id   |



### 获取标准术式

> [GET]/sys_service/oper

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| oper_id | String | 是    | id   |

#### 回复报文参数

| 参数名            | 类型         | 必填   | 说明            |
| -------------- | ---------- | ---- | ------------- |
| oper_id        | String     | 是    | id            |
| oper_code      | String     | 是    | 术式编码          |
| oper_name      | String     | 是    | 术式名称          |
| alia_name_list | ObjectList | 否    | 别名列表          |
| oper_enable    | Integer    | 是    | 是否有效 0：停用1：有效 |

别名列表说明

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| alia_id   | String | 是    | 别名id |
| alia_name | String | 是    | 别名   |


### 修改标准术式

> [POST]/sys_service/oper/update

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名            | 类型         | 必填   | 说明            |
| -------------- | ---------- | ---- | ------------- |
| oper_id        | String     | 是    | id            |
| oper_code      | String     | 是    | 术式编码          |
| oper_name      | String     | 是    | 术式名称          |
| alia_name_list | ObjectList | 否    | 别名列表          |
| alia_del_list  | LongList   | 否    | 删除别名列表        |
| oper_enable    | Integer    | 是    | 是否有效 0：停用1：有效 |

别名列表跟删除别名列表说明

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| alia_id   | String | 否    | 别名id |
| alia_name | String | 是    | 别名   |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 停用标准术式

> [POST]/sys_service/oper/stop

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| oper_id     | String  | 是    | id            |
| oper_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

### 删除标准术式

> [POST]/sys_service/oper/delete

####修改更新记录

| 对应版本   | 说明        |
| ------ | --------- |
| V1.0.2 | 新增 增加删除功能 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| oper_id | String | 是    | id   |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


##过敏源


### 过敏源列表  

> [GET]/sys_service/alle/list

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| key       | String  | 是    | 关键字         |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 过敏源列表 |

过敏源列表说明

| 参数名              | 类型      | 必填   | 说明                      |
| ---------------- | ------- | ---- | ----------------------- |
| alle_id          | String  | 是    | 过敏原id                   |
| alle_code        | String  | 是    | 过敏原编码                   |
| alle_name        | String  | 是    | 过敏原名称                   |
| alle_type        | Integer | 是    | 过敏类别；1-食物过敏；2-药物过敏；3-环境 |
| alle_create_user | String  | 是    | 录入人                     |
| alle_enable      | Integer | 是    | 是否有效 0：停用1：有效           |


### 新增过敏源

> [POST]/sys_service/alle

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| alle_code   | String  | 是    | 过敏原编码         |
| alle_name   | String  | 是    | 过敏原名称         |
| alle_type   | Integer | 是    | 过敏类别          |
| alle_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| alle_id | String | 是    | id   |



### 获取过敏源

> [GET]/sys_service/alle

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| alle_id | String | 是    | id   |

#### 回复报文参数

| 参数名         | 类型      | 必填   | 说明                      |
| ----------- | ------- | ---- | ----------------------- |
| alle_id     | String  | 是    | id                      |
| alle_code   | String  | 是    | 过敏原编码                   |
| alle_name   | String  | 是    | 过敏原名称                   |
| alle_type   | Integer | 是    | 过敏类别；1-食物过敏；2-药物过敏；3-环境 |
| alle_enable | Integer | 是    | 是否有效 0：停用1：有效           |


### 修改过敏源

> [POST]/sys_service/alle/update

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明                      |
| ----------- | ------- | ---- | ----------------------- |
| alle_id     | String  | 是    | id                      |
| alle_code   | String  | 是    | 过敏原编码                   |
| alle_name   | String  | 是    | 过敏原名称                   |
| alle_type   | Integer | 是    | 过敏类别；1-食物过敏；2-药物过敏；3-环境 |
| alle_enable | Integer | 是    | 是否有效 0：停用1：有效           |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 停用过敏源

> [POST]/sys_service/alle/stop

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| alle_id     | String  | 是    | id            |
| alle_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


###删除过敏源

> [POST]/sys_service/alle/delete

####修改更新记录

| 对应版本   | 说明        |
| ------ | --------- |
| V1.0.2 | 新增 增加删除功能 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| alle_id | String | 是    | id   |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


## 计量单位


### 计量单位列表  

> [GET]/sys_service/unit/list

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| key       | String  | 是    | 关键字         |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 当前页    |
| page_size | Integer    | 是    | 每页的数量  |
| total     | Integer    | 是    | 总记录数   |
| pages     | Integer    | 是    | 总页数    |
| list      | ObjectList | 否    | 计量单位列表 |

计量单位列表说明

| 参数名              | 类型      | 必填   | 说明            |
| ---------------- | ------- | ---- | ------------- |
| unit_id          | String  | 是    | 计量单位id        |
| unit_name        | String  | 是    | 计量单位名称        |
| unit_create_user | String  | 是    | 录入人           |
| unit_enable      | Integer | 是    | 是否有效 0：停用1：有效 |

### 获得一个计量单位

>[GET]/sys_service/unit

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| unit_id | String | 是    | 计量单位id |

#### 回复报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| unit_id     | String  | 是    | 计量单位id        |
| unit_name   | String  | 是    | 计量单位名称        |
| unit_enable | Integer | 是    | 是否有效 0：停用1：有效 |



### 新增计量单位

> [POST]/sys_service/unit

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| unit_name   | String  | 是    | 计量单位名称        |
| unit_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| unit_id | String | 是    | 计量单位id |


### 修改计量单位

> [POST]/sys_service/unit/update

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| unit_id     | String  | 是    | 计量单位id        |
| unit_name   | String  | 是    | 计量单位名称        |
| unit_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 停用计量单位

> [POST]/sys_service/unit/stop

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| unit_id     | String  | 是    | 计量单位id        |
| unit_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

### 删除计量单位

> [POST]/sys_service/unit/delete

####修改更新记录

| 对应版本   | 说明        |
| ------ | --------- |
| V1.0.2 | 新增 增加删除功能 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| unit_id | String | 是    | 计量单位id |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


## 频次

### 频次列表  

> [GET]/sys_service/freq/list

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |


#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| key       | String  | 是    | 关键字         |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 频次列表  |

计量单位列表说明

| 参数名                | 类型      | 必填   | 说明            |
| ------------------ | ------- | ---- | ------------- |
| freq_id            | String  | 是    | 频率id          |
| freq_describe      | String  | 是    | 频率描述          |
| freq_counter       | Integer | 是    | 次数            |
| freq_interval      | Integer | 是    | 间隔            |
| freq_interval_unit | String  | 是    | 间隔单位          |
| freq_enable        | Integer | 是    | 是否有效 0：停用1：有效 |



### 获得一个频次

> [GET]/sys_service/freq

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |


#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| freq_id | String | 是    | 频率id |

回复报文参数Object

| 参数名                | 类型      | 必填   | 说明            |
| ------------------ | ------- | ---- | ------------- |
| freq_id            | String  | 是    | 频率id          |
| freq_describe      | String  | 是    | 频率描述          |
| freq_counter       | Integer | 是    | 次数            |
| freq_interval      | Integer | 是    | 间隔            |
| freq_interval_unit | String  | 是    | 间隔单位          |
| freq_enable        | Integer | 是    | 是否有效 0：停用1：有效 |

### 新增频次

> [POST]/sys_service/freq

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |


#### 请求报文参数

| 参数名                | 类型      | 必填   | 说明            |
| ------------------ | ------- | ---- | ------------- |
| freq_describe      | String  | 是    | 频率描述          |
| freq_counter       | Integer | 是    | 次数            |
| freq_interval      | Integer | 是    | 间隔            |
| freq_interval_unit | String  | 是    | 间隔单位          |
| freq_enable        | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| freq_id | String | 是    | 频率id |


### 修改频次

> [POST]/sys_service/freq/update

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |


#### 请求报文参数

| 参数名                | 类型      | 必填   | 说明            |
| ------------------ | ------- | ---- | ------------- |
| freq_id            | String  | 是    | 频率id          |
| freq_describe      | String  | 是    | 频率描述          |
| freq_counter       | Integer | 是    | 次数            |
| freq_interval      | Integer | 是    | 间隔            |
| freq_interval_unit | String  | 是    | 间隔单位          |
| freq_enable        | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

### 停用频次

> [POST]/sys_service/freq/stop

####修改更新记录

| 对应版本 | 说明   |
| ---- | ---- |
|      |      |


#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| freq_id     | String  | 是    | 频率id          |
| freq_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 删除频次

> [POST]/sys_service/freq/delete

####修改更新记录

| 对应版本  | 说明   |
| ----- | ---- |
| 1.0.2 |      |


#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| freq_id | String | 是    | 频率id |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |








#BossWeb平台权限协议设计

### 角色列表

> [GET] /sys_service/platfrom/role/list

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数(ObjectList)

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| role_id   | Long   | 是    | 角色ID |
| role_name | String | 是    | 角色名称 |






### 租户树 

> [GET]/tenant_service/tenant/tree

获取地址列表


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| role_id | Long | 否    |      |

#### 回复报文参数(ObjectList)

| 参数名  | 类型         | 必填   | 说明   |
| ---- | ---------- | ---- | ---- |
| list | ObjectList |      | 集合   |

#### 集合说明

| 参数名          | 类型      | 必填   | 说明                          |
| ------------ | ------- | ---- | --------------------------- |
| tena_id      | String  | yes  | nodeId                      |
| tena_pare_id | String  | yes  | pareNodeId                  |
| tena_name    | String  | yes  | 节点名称                        |
| is_tena      | boolean |      | true is tena ;false is city |



### 新增角色

> [POST] /sys_service/platform/role


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名       | 类型       | 必填   | 说明     |
| --------- | -------- | ---- | ------ |
| role_name | String   | 是    | 角色名称   |
| funcs     | LongList | 否    | 功能权限列表 |
| tenas     | LongList | 否    | 关联租户列表 |

funcs结构：

| 参数名     | 类型   | 必填   | 说明     |
| ------- | ---- | ---- | ------ |
| func_id | Long | 是    | 模块功能ID |


 tenas结构：

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| tena_id | Long | 是    | 租户ID |




#### 回复报文参数(ObjectList)

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| role_id | Long | 是    | 角色ID |

### 修改角色

> [POST] /sys_service/platform/role/update


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名       | 类型       | 必填   | 说明     |
| --------- | -------- | ---- | ------ |
| role_id   | Long     | 是    | 角色ID   |
| role_name | String   | 是    | 角色名称   |
| funcs     | LongList | 否    | 功能权限列表 |
| tenas     | LongList | 否    | 关联租户列表 |

funcs结构：

| 参数名     | 类型   | 必填   | 说明     |
| ------- | ---- | ---- | ------ |
| func_id | Long | 否    | 模块功能ID |

 tenas结构：

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| tena_id | Long | 是    | 租户ID |

#### 回复报文参数(ObjectList)

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

### 获取角色

> [GET]/sys_service/platform/role


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| role_id | Long | 是    | 角色ID |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| role_id   | Long       | 是    | 角色ID   |
| role_name | String     | 是    | 角色名称   |
| funcs     | LongList   | 否    | 权限列表   |
| tenas     | LongList   | 否    | 关联租户列表 |
| users     | ObjectList | 否    | 用户列表   |

funcs结构：

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| func_id | String | 是    | 功能id |

tenas结构：

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| tena_id | Long | 是    | 租户ID |

users结构：

| 参数名             | 类型     | 必填   | 说明   |
| --------------- | ------ | ---- | ---- |
| user_job_number | Long   | 是    | 用户ID |
| user_name       | String | 是    | 用户姓名 |


### 删除角色

> [POST]/sys_service/platform/role/delete


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| role_id | Long | 是    | 角色ID |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |



### 获取角色功能权限信息

> [GET]/sys_service/user/func_auth


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| role_id | Long | 是    | 角色ID |

#### 回复报文参数(ObjectList)

| 参数名         | 类型      | 必填   | 说明             |
| ----------- | ------- | ---- | -------------- |
| func_id     | Integer | 是    | 模块功能ID         |
| func_name   | String  | 是    | 模块功能名称         |
| func_parent | Integer | 否    | 父级模块ID,父级只能是模块 |



### 获取用户信息（新增三个字段 职称、照片url、个人介绍、擅长专科）

> [GET]/sys_service/user


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| user_id | Long | 是    | 员工ID |

#### 回复报文参数

| 参数名             | 类型         | 必填   | 说明              |
| --------------- | ---------- | ---- | --------------- |
| user_id         | String     | 是    | 员工ID            |
| user_name       | String     | 是    | 姓名              |
| user_job_number | String     | 是    | 工号              |
| user_phone      | String     | 是    | 手机号             |
| user_email      | String     | 否    | 电子邮箱            |
| depa_id         | String     | 是    | 科室ID            |
| user_post       | String     | 否    | 岗位              |
| user_sex        | Integer    | 否    | 性别              |
| user_duty_code  | Integer    | 否    | 职称代码            |
| user_photo      | String     | 否    | 照片url           |
| user_memo       | String     | 否    | 个人介绍            |
| user_expert     | String     | 否    | 擅长专科            |
| status          | Integer    | 是    | 0-未审核；1-启用；2-停用 |
| role_list       | ObjectList | 否    | 员工角色列表          |

员工角色列表说明

| 参数名        | 类型     | 必填   | 说明     |
| ---------- | ------ | ---- | ------ |
| role_id    | Long   | 是    | 角色ID   |
| role_name  | String | 是    | 角色名称   |
| tena_names | String | 否    | 租户权限列表 |



### 开发者账号信息修改

> [POST]/sys_service/deve/update

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名              | 类型      | 必填   | 说明           |
| ---------------- | ------- | ---- | ------------ |
| tena_id          | String  | 是    | 租户ID         |
| deve_id          | String  | 是    | 开发者账号ID      |
| deve_name        | String  | 是    | 账号名称         |
| deve_key_content | String  | 是    | 公钥           |
| deve_use_type    | String  | 否    | 账号的用途        |
| deve_memo        | String  | 否    | 备注           |
| deve_enable      | Integer | 否    | 状态；0-停用；1-启用 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 启用停用租户开发者账户

> [POST]/sys_service/deve/start_stop


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明           |
| ----------- | ------- | ---- | ------------ |
| tena_id     | String  | 是    | 租户ID         |
| deve_id     | String  | 是    | 开发者账号ID      |
| deve_enable | Integer | 是    | 状态；0-停用；1-启用 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 用户信息校验

> [POST]/sys_service/user/info_check


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名             | 类型     | 必填   | 说明   |
| --------------- | ------ | ---- | ---- |
| user_job_number | String | 是    | 工号   |
| phone           | String | 是    | 手机号码 |
| auth_code       | String | 是    | 验证码  |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 用户注册

> [POST]/sys_service/user/register


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名             | 类型     | 必填   | 说明   |
| --------------- | ------ | ---- | ---- |
| user_name       | String | 是    | 姓名   |
| user_job_number | String | 是    | 工号   |
| user_post       | String | 否    | 岗位   |
| phone           | String | 是    | 手机号码 |
| auth_code       | String | 是    | 验证码  |
| password        | String | 是    | 密码   |

#### 回复报文参数

| 参数名        | 类型     | 必填   | 说明    |
| ---------- | ------ | ---- | ----- |
| admi_email | String | 是    | 管理员邮箱 |


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |




### 用户重置密码   

> [POST]/sys_service/user/reset_password


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名          | 类型     | 必填   | 说明        |
| ------------ | ------ | ---- | --------- |
| account      | String | 否    | 账号（手机或邮箱） |
| auth_code    | String | 是    | 验证码       |
| new_password | String | 是    | 新密码       |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

### 用户查询用科室列表

> [GET]/sys_service/user/depa_list


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| depa_id   | String | 是    | 科室id |
| depa_name | String | 是    | 科室名称 |



### 获取用户列表信息（分页对象）

> [GET]/sys_service/user/list


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |




#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                                       |
| --------- | ------- | ---- | ---------------------------------------- |
| key       | String  | 否    | 工号（模糊）、姓名（模糊）、手机号（左匹配）、姓名拼音或五笔首字母（左匹配，大小写都支持） |
| depa_id   | Long    | 否    | 科室ID                                     |
| page_size | Integer | 否    | 每页条数 空表示10条                              |
| page_num  | Integer | 否    | 第几页 空表示第1页                               |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 是    | 员工列表  |

员工列表说明

| 参数名             | 类型      | 必填   | 说明                   |
| --------------- | ------- | ---- | -------------------- |
| depa_id         | String  | 是    | 科室id                 |
| depa_name       | String  | 是    | 科室名称                 |
| user_id         | String  | 是    | 员工ID                 |
| user_name       | String  | 是    | 姓名                   |
| user_job_number | String  | 是    | 工号                   |
| user_phone      | String  | 是    | 手机号                  |
| user_email      | String  | 否    | 电子邮箱                 |
| user_regsource  | Integer | 否    | 用户登记源,1-后台添加  2 平台注册 |
| status          | Integer | 是    | 0-未审核；1-启用；2-停用      |





### 用户信息保存

> [POST]/sys_service/user


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名             | 类型         | 必填   | 说明              |
| --------------- | ---------- | ---- | --------------- |
| user_name       | String     | 是    | 姓名              |
| user_job_number | String     | 是    | 工号              |
| user_phone      | String     | 是    | 手机号             |
| user_email      | String     | 否    | 电子邮箱            |
| depa_id         | String     | 是    | 科室ID            |
| user_post       | String     | 否    | 岗位              |
| user_sex        | Integer    | 否    | 性别              |
| status          | Integer    | 是    | 0-未审核；1-启用；2-停用 |
| role_list       | ObjectList | 否    | 员工角色列表          |

员工角色列表说明

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| role_id | String | 是    | 角色ID |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| user_id | String | 是    | 员工ID |


### 启用停用用户

> [POST]/sys_service/user/status/update


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明        |
| ------- | ------- | ---- | --------- |
| user_id | String  | 是    | 员工ID      |
| status  | Integer | 是    | 1-启用；2-停用 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 获取管理员信息

> [GET]/sys_service/admi


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明    |
| ------- | ---- | ---- | ----- |
| admi_id | Long | 是    | 管理员ID |

#### 回复报文参数

| 参数名               | 类型      | 必填   | 说明           |
| ----------------- | ------- | ---- | ------------ |
| admi_id           | String  | 是    | 管理员ID        |
| admi_name         | String  | 是    | 姓名           |
| admi_phone        | String  | 是    | 手机号          |
| admi_email        | String  | 是    | 电子邮箱         |
| admi_phone_active | Integer | 是    | 手机账号激活标志     |
| admi_email_active | Integer | 是    | 邮箱账号激活标志     |
| admi_rem          | String  | 否    | 岗位           |
| admi_sex          | Integer | 否    | 性别           |
| admi_enable       | Integer | 否    | 状态；0-启用；1-停用 |



### 获取管理员列表信息

> [GET]/sys_service/admi/list


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名  | 类型      | 必填   | 说明           |
| ---- | ------- | ---- | ------------ |
| type | Integer | 是    | 状态；0-停用；1-启用 |

#### 回复报文参数（ObjectList）

| 参数名         | 类型      | 必填   | 说明    |
| ----------- | ------- | ---- | ----- |
| admi_id     | String  | 是    | 管理员ID |
| admi_name   | String  | 是    | 姓名    |
| admi_phone  | String  | 是    | 手机号   |
| admi_email  | String  | 是    | 电子邮箱  |
| admi_enable | Integer | 是    | 状态    |

### 管理员信息保存

> [POST]/sys_service/admi


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明           |
| ----------- | ------- | ---- | ------------ |
| admi_name   | String  | 是    | 姓名           |
| admi_phone  | String  | 是    | 手机号          |
| admi_email  | String  | 是    | 电子邮箱         |
| admi_rem    | String  | 否    | 岗位           |
| admi_sex    | Integer | 否    | 性别           |
| admi_enable | Integer | 是    | 状态；0-停用；1-启用 |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明    |
| ------- | ------ | ---- | ----- |
| admi_id | String | 是    | 管理员ID |

### 管理员信息修改

> [POST]/sys_service/admi/update


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明           |
| ----------- | ------- | ---- | ------------ |
| admi_id     | String  | 是    | 管理员ID        |
| admi_name   | String  | 是    | 姓名           |
| admi_phone  | String  | 是    | 手机号          |
| admi_email  | String  | 是    | 电子邮箱         |
| admi_rem    | String  | 否    | 岗位           |
| admi_sex    | Integer | 否    | 性别           |
| admi_enable | Integer | 否    | 状态；0-停用；1-启用 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

### 获取开发者账号信息

> [GET]/sys_service/deve


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明     |
| ------- | ---- | ---- | ------ |
| deve_id | Long | 是    | 开发账号ID |

#### 回复报文参数

| 参数名              | 类型      | 必填   | 说明           |
| ---------------- | ------- | ---- | ------------ |
| deve_id          | String  | 是    | 开发账号ID       |
| deve_name        | String  | 是    | 账号名称         |
| deve_code        | String  | 是    | 开发账号编码       |
| deve_key_content | String  | 是    | 公钥           |
| deve_use_type    | Integer | 否    | 账号的用途        |
| deve_memo        | Integer | 否    | 备注           |
| deve_enable      | Integer | 否    | 状态；0-停用；1-启用 |

 

### 获取开发者账户列表信息

> [GET]/sys_service/deve/list


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名  | 类型      | 必填   | 说明           |
| ---- | ------- | ---- | ------------ |
| type | Integer | 是    | 状态；0-停用；1-启用 |

#### 回复报文参数（ObjectList）

| 参数名         | 类型      | 必填   | 说明           |
| ----------- | ------- | ---- | ------------ |
| deve_id     | Long    | 是    | 开发账号ID       |
| deve_name   | String  | 是    | 账号名称         |
| deve_code   | String  | 是    | 账号编码         |
| deve_enable | Integer | 是    | 状态；0-停用；1-启用 |



### 开发者账号信息保存

> [POST]/sys_service/deve


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名              | 类型      | 必填   | 说明           |
| ---------------- | ------- | ---- | ------------ |
| deve_name        | String  | 是    | 账号名称         |
| deve_key_content | String  | 是    | 公钥           |
| deve_use_type    | String  | 否    | 账号的用途        |
| deve_memo        | String  | 否    | 备注           |
| deve_enable      | Integer | 否    | 状态；0-停用；1-启用 |

#### 回复报文参数

| 参数名       | 类型     | 必填   | 说明      |
| --------- | ------ | ---- | ------- |
| deve_id   | String | 是    | 开发者账号ID |
| deve_code | String | 是    | 开发账号编码  |


### 开发者账号信息修改

> [POST]/sys_service/user/update


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名              | 类型      | 必填   | 说明           |
| ---------------- | ------- | ---- | ------------ |
| deve_id          | String  | 是    | 开发者账号ID      |
| deve_name        | String  | 是    | 账号名称         |
| deve_key_content | String  | 是    | 公钥           |
| deve_use_type    | String  | 否    | 账号的用途        |
| deve_memo        | String  | 否    | 备注           |
| deve_enable      | Integer | 否    | 状态；0-停用；1-启用 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |





### 获取导入日志列表信息（分页对象）

> [GET]/sys_service/user/impt/list


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 是    | 日志列表  |

日志列表说明

| 参数名                | 类型      | 必填   | 说明                                       |
| ------------------ | ------- | ---- | ---------------------------------------- |
| impt_id            | String  | 是    | 导入记录ID                                   |
| impt_operator_name | String  | 是    | 导入人                                      |
| impt_time_for_date | String  | 是    | 导入时间                                     |
| impt_result        | String  | 是    | 导入结果                                     |
| impt_status        | Integer | 是    | 默认0;0-还未处理;1-正在导入;2-导入完成;3-有失败内容;4-用户未上传 |




### 文件批量上传

> [POST]/sys_service/user/file_post


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明   |
| --------- | ------- | ---- | ---- |
| file_name | String  | 是    | 文件名  |
| file_type | String  | 是    | 文件类型 |
| file_size | Integer | 是    | 文件尺寸 |

#### 回复报文参数

| 参数名                     | 类型     | 必填   | 说明                       |
| ----------------------- | ------ | ---- | ------------------------ |
| fileId                  | Long   | 是    | 文件资源唯一标识                 |
| url                     | String | 是    | 操作的URL                   |
| OSSAccessKeyId          | String | 是    | Bucket 拥有者的Access Key Id |
| policy                  | String | 是    | Base64编码的JSON内容          |
| Signature               | String | 是    | 签名                       |
| key                     | String | 是    | 上传文件路径                   |
| success_action_redirect | String | 是    | 文件上传成功后的跳转地址             |

### 文件模板下载

> [GET]/sys_service/user/file_temp_down


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| file_id | String | 是    | 文件资源id |

#### 回复报文参数

| 参数名  | 类型     | 必填   | 说明     |
| ---- | ------ | ---- | ------ |
| url  | String | 是    | 文件下载地址 |



### 导入失败原因详情

> [GET]/sys_service/user/impt/view


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明     |
| ------- | ---- | ---- | ------ |
| impt_id | Long | 是    | 导入记录ID |

#### 回复报文参数ObjectList

| 参数名            | 类型      | 必填   | 说明   |
| -------------- | ------- | ---- | ---- |
| deta_row       | Integer | 是    | 第几条  |
| deta_name      | String  | 是    | 姓名   |
| deta_jobnumber | String  | 是    | 工号   |
| deta_error     | String  | 是    | 错误内容 |

### 功能权限列表


####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.1 | 新增   |



> [GET] /sys_service/func/platform/list

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数(ObjectList)

| 参数名         | 类型      | 必填   | 说明       |
| ----------- | ------- | ---- | -------- |
| work_id     | Integer | 是    | 工作站ID    |
| work_code   | String  | 是    | 工作站代码    |
| work_name   | String  | 是    | 工作站名称    |
| func_id     | Long    | 是    | 模块功能ID   |
| func_code   | String  | 是    | 功能代码     |
| func_name   | String  | 是    | 模块功能名称   |
| func_module | Integer | 是    | 模块还是功能标志 |
| func_parent | Long    | 否    | 父级模块ID   |







#BossWeb设备程序版本管理协议设计

### 设备程序版本列表

> [GET] /sys_service/program_version/list

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 否    | 每页条数 空表示10条 |
| page_num  | Integer    | 否    | 第几页 空表示第1页  |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 是    | 设备程序列表      |

设备程序列表说明

| 参数名           | 类型     | 必填   | 说明     |
| ------------- | ------ | ---- | ------ |
| version_id    | String | 是    | 程序版本ID |
| version_no    | String | 是    | 版本号    |
| chan_time     | String | 是    | 上传时间   |
| chan_name     | String | 是    | 操作人    |
| version_notes | String | 否    | 更新说明   |

### 设备程序信息获取

>  [GET] /sys_service/program_version

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名        | 类型     | 必填   | 说明     |
| ---------- | ------ | ---- | ------ |
| version_id | String | 是    | 程序版本ID |

#### 回复报文参数(ObjectList)

| 参数名           | 类型     | 必填   | 说明     |
| ------------- | ------ | ---- | ------ |
| version_id    | String | 是    | 程序版本ID |
| version_no    | String | 是    | 版本号    |
| program_name  | String | 是    | 程序文件名  |
| download_url  | String | 是    | 下载地址   |
| chan_time     | String | 是    | 上传时间   |
| chan_name     | String | 是    | 操作人    |
| version_notes | String | 否    | 更新说明   |
| version_md5   | String | 是    | md5码   |



### 设备程序新增

>  [POST] /sys_service/api_program/add

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名             | 类型     | 必填   | 说明     |
| --------------- | ------ | ---- | ------ |
| version_no      | String | 是    | 版本号    |
| version_file_id | String | 是    | 文件资源ID |
| version_notes   | String | 否    | 更新说明   |
| version_md5     | String | 是    | md5码   |


#### 回复报文参数(ObjectList)

| 参数名        | 类型     | 必填   | 说明     |
| ---------- | ------ | ---- | ------ |
| version_id | String | 是    | 程序版本ID |




### 上传版本程序

```http
[POST]/sys_service/tenant/upload_version_file
```


####修改更新记录

| 对应版本   | 说明         |
| ------ | ---------- |
| V1.0.2 | 修改  增加资源类型 |



#### 请求报文参数

| 参数名            | 类型      | 必填   | 说明                                       |
| -------------- | ------- | ---- | ---------------------------------------- |
| version_no     | String  | 否    | 版本号                                      |
| file_size      | Long    | 否    | 文件内容长度                                   |
| file_extension | String  | 是    | 文件扩展名(不带“.“)                             |
| file_type      | String  | 是    | 文件类型，Content-Type                        |
| file_signature | String  | 否    | 文件的签名值MD5,Base64编码                       |
| work_id        | Long    | 否    | 工作站ID，用户在哪个工作站中上传的                       |
| factory_id     | String  | 否    | 厂商id                                     |
| business_id    | String  | 否    | 业务标志，意义由上传类型确定；9时为商品ID                   |
| source_type    | Integer | 是    | 上传类型 1:logo;</br>2:法人身份证正面;</br>3.法人身份证背面;</br>4:营业执照;</br>5.用户类型</br>6.医生签名</br>7.厂商营业执照</br>8.厂商生产许可证；</br>9.商品目录注册证号文件                          13.设备程序 |

#### 回复报文参数

| 参数名                     | 类型     | 必填   | 说明                       |
| ----------------------- | ------ | ---- | ------------------------ |
| url                     | String | 是    | 操作的URL                   |
| file_id                 | Long   | 是    | 文件资源id                   |
| OSS_access_key_id       | String | 是    | Bucket 拥有者的Access Key Id |
| policy                  | String | 是    | Base64编码的JSON内容          |
| signature               | String | 是    | 签名                       |
| key                     | String | 是    | 上传文件路径                   |
| success_action_redirect | String | 是    | 文件上传成功后的跳转地址             |







# BossWeb菜单管理协议设计

## 菜单管理

菜单对应于 
工作站work_station 或 功能function

### 功能树

> [GET] /sys_service/menu/tree

#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


#### 回复报文参数ObjectList

| 参数名        | 类型         | 必填   | 说明                 |
| ---------- | ---------- | ---- | ------------------ |
| menu_id    | String     | 是    | 菜单ID               |
| menu_type  | Integer    | 是    | 菜单类型  1工作站 2 功能    |
| menu_name  | String     | 是    | 菜单名称               |
| child_list | ObjectList | 否    | 子菜单列表     为空则没有子菜单 |

其中子菜单列表中的Object和上面的结构相同。这是一个递归结构。



### 菜单信息获取

>  [GET] /sys_service/menu

#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明              |
| --------- | ------ | ---- | --------------- |
| menu_id   | String | 是    | 菜单ID            |
| menu_type | String | 是    | 菜单类型  1工作站 2 功能 |

#### 回复报文参数(ObjectList)

| 参数名              | 类型      | 必填   | 说明                                |
| ---------------- | ------- | ---- | --------------------------------- |
| menu_id          | String  | 是    | 菜单ID                              |
| menu_type        | Integer | 是    | 菜单类型  1工作站 2 功能                   |
| parent_menu_id   | String  | 是    | 上级菜单ID                            |
| parent_menu_type | Integer | 是    | 上级菜单类型  1工作站 2 功能                 |
| menu_name        | String  | 是    | 菜单名称                              |
| menu_code        | String  | 是    | 菜单代码                              |
| menu_module      | Integer | 是    | 模块还是功能标志，1:模块菜单；2:功能菜单；3:功能点（非菜单） |


### 菜单新增

>  [POST] /sys_service/menu/add

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名              | 类型         | 必填   | 说明                                |
| ---------------- | ---------- | ---- | --------------------------------- |
| parent_menu_id   | String     | 是    | 上级菜单ID                            |
| parent_menu_type | Integer    | 是    | 上级菜单类型  1工作站 2 功能                 |
| menu_name        | String     | 是    | 菜单名称                              |
| menu_code        | String     | 是    | 菜单代码                              |
| menu_module      | Integer    | 是    | 模块还是功能标志，1:模块菜单；2:功能菜单；3:功能点（非菜单） |
| protocol_list    | StringList | 是    | 协议列表  关联的协议列表                     |


#### 回复报文参数(ObjectList)

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| menu_id | String | 是    | 菜单ID |


### 菜单修改

>  [POST] /sys_service/menu/update

#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名              | 类型         | 必填   | 说明                                |
| ---------------- | ---------- | ---- | --------------------------------- |
| menu_id          | String     | 是    | 菜单ID                              |
| parent_menu_id   | String     | 是    | 上级菜单ID                            |
| parent_menu_type | Integer    | 是    | 上级菜单类型  1工作站 2 功能                 |
| menu_name        | String     | 是    | 菜单名称                              |
| menu_code        | String     | 是    | 菜单代码                              |
| menu_module      | Integer    | 是    | 模块还是功能标志，1:模块菜单；2:功能菜单；3:功能点（非菜单） |
| protocol_list    | StringList | 是    | 协议列表  关联的协议列表                     |


#### 回复报文参数(ObjectList)

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 菜单删除协议

```url
[DELETE]/sys_service/menu/{menu_id}
```

#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

#### PathVariable

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| menu_id | String | 是    | 菜单ID |


#### 回复报文参数(ObjectList)

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| menu_id | String | 是    | 菜单ID |


### 协议选项列表

> [GET] /sys_service/protocol/option

在菜单新增，或修改，选择协议时使用

#### 修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名           | 类型     | 必填   | 说明         |
| ------------- | ------ | ---- | ---------- |
| protocol_name | String | 否    | 协议名称  模糊查询 |

#### 回复报文参数

| 参数名              | 类型      | 必填   | 说明                                       |
| ---------------- | ------- | ---- | ---------------------------------------- |
| protocol_id      | String  | 是    | 协议ID                                     |
| protocol_name    | String  | 是    | 协议名称  对应 grou_memo                       |
| protocol_address | String  | 是    | 协议地址  对应  grou_name                      |
| protocol_type    | Integer | 是    | 协议类型  对应  chan_type  0-通用渠道;1-WEB;2-移动;3-API;4-公共服务 |




##协议管理

对应协议组

###协议列表

> [GET] /sys_service/protocol/list

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明          |
| --------- | ------- | ---- | ----------- |
| page_size | Integer | 否    | 每页条数 空表示10条 |
| page_num  | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 否    | 每页条数 空表示10条 |
| page_num  | Integer    | 否    | 第几页 空表示第1页  |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 是    | 协议列表        |

协议列表

| 参数名              | 类型      | 必填   | 说明                                       |
| ---------------- | ------- | ---- | ---------------------------------------- |
| protocol_id      | String  | 是    | 协议ID                                     |
| protocol_name    | String  | 是    | 协议名称  对应 grou_memo                       |
| protocol_address | String  | 是    | 协议地址  对应  grou_name                      |
| protocol_type    | Integer | 是    | 协议类型  对应  chan_type  0-通用渠道;1-WEB;2-移动;3-API;4-公共服务 |
| operate_name     | String  | 是    | 录入人                                      |


### 协议新增

>  [POST] /sys_service/protocol/add

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名              | 类型      | 必填   | 说明                                       |
| ---------------- | ------- | ---- | ---------------------------------------- |
| protocol_name    | String  | 是    | 协议名称  对应 grou_memo                       |
| protocol_address | String  | 是    | 协议地址  对应  grou_name                      |
| protocol_type    | Integer | 是    | 协议类型  对应  chan_type  0-通用渠道;1-WEB;2-移动;3-API;4-公共服务 |

#### 回复报文参数(ObjectList)

| 参数名         | 类型     | 必填   | 说明   |
| ----------- | ------ | ---- | ---- |
| protocol_id | String | 是    | 协议ID |


### 协议获取

>  [GET] /sys_service/protocol

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名         | 类型     | 必填   | 说明   |
| ----------- | ------ | ---- | ---- |
| protocol_id | String | 是    | 协议ID |


#### 回复报文参数(ObjectList)

| 参数名              | 类型      | 必填   | 说明                                       |
| ---------------- | ------- | ---- | ---------------------------------------- |
| protocol_id      | String  | 是    | 协议ID                                     |
| protocol_name    | String  | 是    | 协议名称  对应 grou_memo                       |
| protocol_address | String  | 是    | 协议地址  对应  grou_name                      |
| protocol_type    | Integer | 是    | 协议类型  对应  chan_type  0-通用渠道;1-WEB;2-移动;3-API;4-公共服务 |




### 协议修改

>  [POST] /sys_service/protocol/update

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.0.2 | 新增   |

#### 请求报文参数

| 参数名              | 类型      | 必填   | 说明                                       |
| ---------------- | ------- | ---- | ---------------------------------------- |
| protocol_id      | String  | 是    | 协议ID                                     |
| protocol_name    | String  | 是    | 协议名称  对应 grou_memo                       |
| protocol_address | String  | 是    | 协议地址  对应  grou_name                      |
| protocol_type    | Integer | 是    | 协议类型  对应  chan_type  0-通用渠道;1-WEB;2-移动;3-API;4-公共服务 |

#### 回复报文参数(ObjectList)

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 标志诊断——删除协议

>  [POST] /sys_service/protocol/delete

####修改更新记录

| 对应版本   | 说明        |
| ------ | --------- |
| V1.0.2 | 新增 增加删除功能 |

#### 请求报文参数

| 参数名         | 类型     | 必填   | 说明   |
| ----------- | ------ | ---- | ---- |
| protocol_id | String | 是    | 协议id |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |





# 个性化配置
## 短信签名模板申请

### 短信签名保存/修改申请

```
[POST]/sys_service/sms/signature/update/{tena_id}
```
涉及到的表：
短信签名表(notify_sms_signature)
短信模板表(notify_sms_template)

说明：
1. 发送短信签名内容并定时获取申请审核的通知。
2. 拿到审核通知（成功或者失败）则调用修改数据库的状态修改接口
3. 审核通过时通知：“【盼盼视界】您申请的短信签名“XXX”审核通过，请及时配置到对应机构的个性化配置中。”   
   审核不通过时通知：“【盼盼视界】您申请的短信签名“XXX”审核失败，请核实相关信息的准确性后重新提交申请。”
4. 审核通过发送短信后：1，把数据库中整套的短信模板和短信签名在数据库中生成映射2，去云片申请短信模板，并定时获取申请审核的通知，获取到申请审核则调用修改数据库的状态修改接口

#### 修改更新记录

| 对应业务        | 说明   |
| ----------- | ---- |
| WEBV1.0.2.1 | 新增   |

#### 请求报文参数
####RequestHeader
| 参数名                 | 长度   | 类型     | 必填   | 说明                |
| ------------------- | ---- | ------ | ---- | ----------------- |
| Env.HEAD_USERID_KEY |      | String | 是    | 用户ID ，实现值是：userid |
####PathVariable
| 参数名     | 长度   | 类型     | 必填   | 说明   |
| ------- | ---- | ------ | ---- | ---- |
| tena_id |      | String | 是    | 租户ID |

#### RequestBody

| 参数名          | 长度   | 类型     | 必填   | 说明                                       |
| ------------ | ---- | ------ | ---- | ---------------------------------------- |
| sms_id       |      | String | 否    | 签名ID,为空则视为新增                             |
| sms_name     |      | String | 是    | 签名名称,规则：1.不能包含【】；2.不能是“云片网”；3. 3-8个字；4.不能是纯英文和数字 |
| sms_phone    |      | String | 是    | 发送短信通知租户成功或者失败的电话号码                      |
| success_sign |      | String | 否    | 如果当前的签名是审核中，则返回之前成功的签名                   |



#### 回复报文参数

### 查询短信签名

```
[GET]/sys_service/sms/signature/tena_id
```

短信签名表(notify_sms_signature)
说明：
刚开始没有短信签名时直接展示“申请短信签名”的按钮，申请成功后直接将申请的结果反选出来展示，并保留“申请短信签名”按钮。

#### 修改更新记录

| 对应业务        | 说明   |
| ----------- | ---- |
| WEBV1.0.2.1 | 查询   |

#### 请求报文参数
PathVariable
| 参数名     | 长度   | 类型     | 必填   | 说明   |
| ------- | ---- | ------ | ---- | ---- |
| tena_id |      | String | 是    | 租户ID |
#### 回复报文参数
| 参数名        | 长度   | 类型      | 必填   | 说明                         |
| ---------- | ---- | ------- | ---- | -------------------------- |
| sms_id     |      | String  | 是    | 签名ID,为空则视为新增               |
| sms_name   |      | String  | 是    | 签名名称                       |
| sms_status |      | Integer | 是    | 申请标志 默认:0;0-申请中;1-成功;2-失败; |
| sms_remark |      | String  | 否    | 审核结果解释：客服给的审核结果解释，一般见于审核失败 |



## 版本管理

### 版本管理信息列表查询

```
[GET]/sys_service/version_mng/list
```
涉及到的表：
版本管理信息表(pla_version_info)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 列表查询 |

#### 请求报文参数
#### RequestParameter

| 参数名       | 类型      | 必选   | 说明            |
| --------- | ------- | ---- | ------------- |
| page_num  | Integer | 否    | 页码 （默认为 1）    |
| page_size | Integer | 否    | 每页数量 （默认为 10） |
#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 页码     |
| page_size | Integer    | 是    | 每页数量   |
| pages     | Integer    | 是    | 总页数    |
| total     | Integer    | 是    | 总数量    |
| list      | ObjectList | 是    | 版本管理列表 |
#### 版本管理列表
| 参数名                    | 长度   | 类型     | 必填   | 说明       |
| ---------------------- | ---- | ------ | ---- | -------- |
| mng_id                 |      | String | 是    | 版本管理信息ID |
| mng_content            |      | String | 否    | 版本内容     |
| mng_version_outside_no |      | String | 是    | 版本号（对外）  |
| mng_version_no         |      | String | 是    | 版本号      |
| mng_user               |      | String | 是    | 操作人      |
| mng_release_time       |      | String | 是    | 发布时间     |

### 版本管理信息新增

```
[POST]/sys_service/version_mng/insert
```

版本管理信息表(pla_version_info)
说明：


#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 新增   |

#### 请求报文参数

#### RequestBody
| 参数名                    | 长度   | 类型     | 必填   | 说明      |
| ---------------------- | ---- | ------ | ---- | ------- |
| mng_content            | 200  | String | 否    | 版本内容    |
| mng_version_outside_no |      | String | 是    | 版本号（对外） |
| mng_version_no         |      | String | 是    | 版本号     |
| mng_release_time       |      | String | 是    | 发布时间    |
#### 回复报文参数
| 参数名    | 长度   | 类型     | 必填   | 说明       |
| ------ | ---- | ------ | ---- | -------- |
| mng_id |      | String | 是    | 版本管理信息ID |

### 版本管理信息详情查询

```
[GET]/sys_service/version_mng
```
涉及到的表：
版本管理信息表(pla_version_info)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 查询   |

#### 请求报文参数
| 参数名    | 长度   | 类型     | 必填   | 说明   |
| ------ | ---- | ------ | ---- | ---- |
| mng_id |      | String | 是    | 版本id |

#### 回复报文参数
| 参数名                    | 长度   | 类型     | 必填   | 说明      |
| ---------------------- | ---- | ------ | ---- | ------- |
| mng_content            |      | String | 否    | 版本内容    |
| mng_version_outside_no |      | String | 是    | 版本号（对外） |
| mng_version_no         |      | String | 是    | 版本号     |
| mng_release_time       |      | String | 是    | 发布时间    |

## ajax监控协议

### 分页查询ajax监控

```
[GET]/sys_service/ajax/record/list
```

涉及到的表：
ajax请求记录表(adm_request_record)

#### 分页查询ajax监控

| 对应版本        | 说明         |
| ----------- | ---------- |
| BOSS-V1.0.3 | 分页查询ajax监控 |

#### 请求参数报文：

##### requestParam:

| 参数名       | 类型      | 必填   | 说明                 |
| --------- | ------- | ---- | ------------------ |
| tenat_id  | String  | 否    | 租户：租户ID或租户名称，不填为全部 |
| user_id   | String  | 否    | 用户：用户ID或用户名称，不填为全部 |
| page_size | Integer | 是    | 每页条数 空表示10条        |
| page_num  | Integer | 是    | 第几页 空表示第1页         |

#### 回复参数报文（ObjectList）：

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 否    | 监控列表        |

Object:

| 参数名             | 类型      | 必填   | 说明                                |
| --------------- | ------- | ---- | --------------------------------- |
| monitoring_date | Long    | 是    | 日期                                |
| record_id       | String  | 是    | 监控记录ID                            |
| request_id      | Long    | 是    | 全局唯一的requestId                    |
| request_url     | String  | 是    | 请求地址                              |
| request_method  | Integer | 是    | 请求方式：0-get；1-post；2-put；3:-delete |
| request_header  | String  | 否    | 请求头                               |
| request_body    | String  | 否    | 请求参数                              |
| status_code     | Integer | 是    | 响应状态码（如：200、404等）。响应超时为-1         |
| request_time    | String  | 是    | 请求时间，单位：毫秒                        |
| response_time   | String  | 是    | 响应时间，单位：毫秒                        |
| cost            | Long    | 是    | 请求耗时，单位：毫秒，响应超时时传超时耗时             |
| error_message   | String  | 否    | 异常信息                              |
| page_url        | String  | 否    | 页面地址                              |
| source          | Integer | 是    | 请求来源：0-web；1-app；2：微信             |
| source_ip       | String  | 否    | 请求端IP地址                           |
| user_id         | String  | 是    | 用户ID                              |
| user_name       | String  | 是    | 用户名称                              |
| tenat_id        | String  | 是    | 租户ID                              |
| tenant_name     | String  | 是    | 租户名称                              |


## appweb监控

###  appweb终端编号查询 
```
 [GET]/sys_service/device/monitoring/webcode 
```
涉及到的表：
版本管理信息表(appweb_state_info)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 列表查询 |

#### 请求报文参数

#### RequestParameter

| 参数名      | 类型     | 必选   | 说明         |
| -------- | ------ | ---- | ---------- |
| tenat_id | String | 否    | 租户id，不填为全部 |
#### 回复报文参数
#### 终端编号列表
| 参数名         | 长度   | 类型     | 必填   | 说明   |
| ----------- | ---- | ------ | ---- | ---- |
| appweb_id   |      | String | 是    | 主键id |
| appweb_code |      | String | 是    | 终端编号 |


###  appweb监控异常查询 
```
 [GET]/sys_service/device/monitoring/exceptions 
```
涉及到的表：
版本管理信息表(appweb_state_info)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 列表查询 |

#### 请求报文参数

#### RequestParameter

| 参数名         | 类型      | 必选   | 说明                  |
| ----------- | ------- | ---- | ------------------- |
| appweb_code | String  | 否    | 终端编号，不填为全部          |
| end_time    | String  | 否    | 异常结束时间 如:2018-10-23 |
| begin_time  | String  | 否    | 异常发生时间 如:2018-10-23 |
| page_num    | Integer | 否    | 页码 （默认为 1）          |
| page_size   | Integer | 否    | 每页数量 （默认为 10）       |
| tenat_id    | String  | 否    | 租户id，不填为全部          |
#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明   |
| --------- | ---------- | ---- | ---- |
| page_num  | Integer    | 是    | 页码   |
| page_size | Integer    | 是    | 每页数量 |
| pages     | Integer    | 是    | 总页数  |
| total     | Integer    | 是    | 总数量  |
| list      | ObjectList | 是    | 异常列表 |
#### 异常列表
| 参数名                   | 长度   | 类型     | 必填   | 说明                    |
| --------------------- | ---- | ------ | ---- | --------------------- |
| appweb_id             |      | String | 是    | 主键id                  |
| appweb_tena_id        |      | String | 是    | 租户号                   |
| appweb_tena_name      |      | String | 是    | 租户名称                  |
| appweb_code           |      | String | 是    | 终端编号                  |
| appweb_version        |      | String | 是    | 版本号                   |
| appweb_status         |      | String | 是    | 设备通信时间超时状态 0:异常；1:正常; |
| appweb_active_time    |      | String | 是    | 最后一次通讯时间(单位毫秒)        |
| appweb_device_name    |      | String | 否    | 连接设备（异常）              |
| device_exception_time |      | String | 否    | 异常发生时间（最后一个异常设备时间）    |



###  appweb监控全部查询 
```
 [GET]/sys_service/device/monitoring/all 
```
涉及到的表：
版本管理信息表(appweb_state_info)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 列表查询 |

#### 请求报文参数

#### RequestParameter

| 参数名         | 类型      | 必选   | 说明            |
| ----------- | ------- | ---- | ------------- |
| appweb_code | String  | 否    | 终端编号  （不填为全部） |
| page_num    | Integer | 否    | 页码 （默认为 1）    |
| page_size   | Integer | 否    | 每页数量 （默认为 10） |
| tenat_id    | String  | 是    | 租户id，不填为全部    |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 页码     |
| page_size | Integer    | 是    | 每页数量   |
| pages     | Integer    | 是    | 总页数    |
| total     | Integer    | 是    | 总数量    |
| list      | ObjectList | 是    | 全部设备列表 |
#### 全部设备列表
| 参数名                      | 长度   | 类型         | 必填   | 说明                 |
| ------------------------ | ---- | ---------- | ---- | ------------------ |
| appweb_id                |      | String     | 是    | 主键id               |
| appweb_tena_id           |      | String     | 是    | 租户号                |
| appweb_tena_name         |      | String     | 是    | 租户名称               |
| appweb_code              |      | String     | 是    | 终端编号               |
| appweb_version           |      | String     | 是    | 版本号                |
| appweb_status            |      | String     | 是    | 终端状态 0:异常；1:正常;    |
| appweb_active_time       |      | String     | 是    | 最后一次通讯时间(单位毫秒)     |
| appweb_device_all        |      | ObjectList | 是    | 连接设备列表（全部）         |
| appweb_device_exceptions |      | ObjectList | 否    | 连接设备列表（异常）         |
| device_exception_time    |      | String     | 否    | 异常发生时间（最后一个异常设备时间） |
#### 连接设备列表（全部）
| 参数名              | 长度   | 类型     | 必填   | 说明                        |
| ---------------- | ---- | ------ | ---- | ------------------------- |
| appweb_device_id |      | String | 是    | 设备Id主要用于后期扩展appweb与设备对应关系 |
| appweb_device    |      | String | 是    | 设备名称                      |
#### 连接设备列表（异常）
| 参数名              | 长度   | 类型     | 必填   | 说明                        |
| ---------------- | ---- | ------ | ---- | ------------------------- |
| appweb_device_id |      | String | 是    | 设备Id主要用于后期扩展appweb与设备对应关系 |
| appweb_device    |      | String | 否    | 设备名称                      |


## 打印模板
### 打印模板打印类型列表查询
```
[GET]/sys_service/base_settings/printer/list
```
租户打印设置及模板表(web_print_template)
说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 查询   |

#### 请求报文参数

#### 回复报文参数（ObjectList）
| 参数名  | 长度   | 类型      | 必填   | 说明       |
| ---- | ---- | ------- | ---- | -------- |
| type |      | Integer | 是    | 打印模板类型id |
| name |      | String  | 是    | 打印模板类型名称 |

### 打印模板维护列表查询
```
[GET]/sys_service/jasreport/list  
```
租户打印设置及模板表(web_print_template)
说明：


#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 查询   |

#### 请求报文参数
#### RequestBody
| 参数名        | 长度   | 类型      | 必填   | 说明   |
| ---------- | ---- | ------- | ---- | ---- |
| temp_event |      | Integer | 是    | 打印类型 |

#### 回复报文参数ObjectList
| 参数名         | 长度   | 类型     | 必填   | 说明                  |
| ----------- | ---- | ------ | ---- | ------------------- |
| temp_id     |      | String | 是    | 模板id                |
| temp_code   |      | String | 是    | 模板编码                |
| temp_name   |      | String | 是    | 模板名称                |
| temp_time   |      | String | 是    | 添加日期                |
| temp_enable |      | String | 是    | 有效标志,1：默认模板，2：非默认模板 |


### 租户个性设置默认打印模板查询

```
[GET]/sys_service/jasreport/tenet_getting
```
涉及到的表：
版本管理信息表(web_print_template)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 新增   |

#### 请求报文参数

| 参数名        | 长度   | 类型      | 必填   | 说明   |
| ---------- | ---- | ------- | ---- | ---- |
| temp_event |      | Integer | 是    | 打印类型 |
| tenat_id   |      | String  | 是    | 租户id |
#### 回复报文参数Object List
| 参数名         | 长度   | 类型     | 必填   | 说明                            |
| ----------- | ---- | ------ | ---- | ----------------------------- |
| temp_id     |      | String | 否    | 模板id                          |
| temp_name   |      | String | 是    | 模板名称                          |
| temp_enable |      | String | 是    | 有效标志,1：租户个性设置得模板，2：非租户个性设置得模板 |
| temp_code   |      | String | 是    | 模板编号                          |

### 租户个性设置默认打印模板
```
[POST]/sys_service/jasreport/tenet_setting
```
涉及到的表：
版本管理信息表(web_print_template)
租户打印模板表(tena_print_template)
说明：tena_print_template为租户和模板得关系表（全局默认打印模板的租户为0，租户个性设置得打印模板的为租户号）


#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 新增   |

#### 请求报文参数

#### RequestBody
| 参数名      | 长度   | 类型     | 必填   | 说明   |
| -------- | ---- | ------ | ---- | ---- |
| temp_id  |      | String | 否    | 模板id |
| tenat_id |      | String | 是    | 租户id |




### 模板文件/预览图片的预上传
```
[POST]/sys_service/jasreport/upload/picture_template
```
涉及到的表：
版本管理信息表(web_print_template)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 修改   |

#### 请求报文参数
#### RequestBody
| 参数名            | 长度   | 类型      | 必填     | 说明                                       |
| -------------- | ---- | ------- | ------ | ---------------------------------------- |
| temp_event     |      | Integer | 是      | 打印类型                                     |
| temp_file_type |      | Integer | 是      | 扩展名类型标志位，模板文件后缀为1:jrxml 2:jasper   预览图片后缀为 3:jpg/jpeg 4:png |
| unique_value   |      | String  | 是      | 时间戳                                      |
| file_extension |      | String  | 是      | 文件扩展名                                    |
| file_type      |      | String  | 是      | 文件类型                                     |
| file_size      | Long | 否       | 文件内容长度 |                                          |

#### 回复报文参数
| 参数名            | 长度   | 类型     | 必填   | 说明      |
| -------------- | ---- | ------ | ---- | ------- |
| file_id        |      | String | 否    | file_id |
| ossaccessKeyId |      | String | 否    | 模板图片id  |
| signature      |      | String | 否    | 模板图片id  |
| key            |      | String | 否    | 模板图片id  |
| policy         |      | String | 否    | 模板图片id  |
| url            |      | String | 否    | 文件得url  |


### 打印模板新增

```
[POST]/sys_service/jasreport/insert
```
涉及到的表：
版本管理信息表(web_print_template)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 查询   |

#### 请求报文参数
#### RequestBody
| 参数名                | 长度   | 类型      | 必填   | 说明                                  |
| ------------------ | ---- | ------- | ---- | ----------------------------------- |
| temp_file_id       |      | String  | 是    | 模板文件id                              |
| temp_img_file_id   |      | String  | 是    | 模板文件图片id                            |
| temp_file_type     |      | Integer | 是    | 模板文件类型，模板文件后缀，1:jrxml 2:jasper      |
| temp_img_file_type |      | Integer | 是    | 模板文件图片类型 ，模板图片文件后缀，1:jpg/jpeg 2:png |
| temp_file_url      |      | String  | 是    | 模板文件url                             |
| temp_img_file_url  |      | String  | 是    | 模板文件图片url                           |
| temp_name          |      | String  | 是    | 模板名称                                |
| temp_direction     |      | Integer | 是    | 模板方向0-竖;1-横;2-自适应;                  |
| temp_size          |      | Integer | 是    | 模板尺寸0-A4 1-A5 2-销售单(192x115)        |
| temp_event         |      | Integer | 是    | 打印类型  如 注1                          |
| temp_diy_size      |      | String  | 是    | 自定义尺寸，格式：高*宽  227*554  中间只能用*或x     |

#### 回复报文参数
| 参数名     | 长度   | 类型     | 必填   | 说明   |
| ------- | ---- | ------ | ---- | ---- |
| temp_id |      | String | 否    | 模板id |

注1:不同的打印类型有自己的默认纸张方向与纸张大小，如果查询不存在时请使用如下规则：
类型	类型名				方向	大小	模板文件
1	 小病历	    		 横	    A5	clinic_print.jasper
2	 医嘱处方	  		      竖	      A5	doctor_advice_print.jasper
3	 停诊患者列表			竖	  A4	book.jasper
4	 视光销售单	 		   横	配镜单(192x115)	
5	 采购入库单	 		   横	A4	
6	 调拨单	    		 横	    A4	
7	 采购退货单	 		   横	A4	
8	 其他出库单	 		   横	A4	
9	 收费系统收费单		横	A4	
10	 收费系统退费单		竖	A4	
11	 定做查询供应商明细	    横	   A4	
12	 视光销售单显示处方	     横	   配镜单(192x115)	
13	 采购入库单不显示进价	   横	A4	
14	 其他出库单不显示进价	   横	A4	




### 打印模板删除
```
[POST]/sys_service/jasreport/delete
```
涉及到的表：
版本管理信息表(web_print_template)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 修改   |

#### 请求报文参数
#### RequestBody
| 参数名     | 长度   | 类型     | 必填   | 说明   |
| ------- | ---- | ------ | ---- | ---- |
| temp_id |      | String | 是    | 模板文件 |
#### 回复报文参数


### 打印模板选择默认项
```
[POST]/sys_service/jasreport/update
```
涉及到的表：
版本管理信息表(web_print_template)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 修改   |

#### 请求报文参数
#### RequestBody
| 参数名     | 长度   | 类型     | 必填   | 说明   |
| ------- | ---- | ------ | ---- | ---- |
| temp_id |      | String | 是    | 模板文件 |
#### 回复报文参数



### 打印模板预览
```
[GET]/sys_service/jasreport/preview 
```
涉及到的表：
版本管理信息表(web_print_template)

说明：前端获取到打印模版url，再去请求url的资源

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 查询   |

#### 请求报文参数
#### RequestBody
| 参数名     | 长度   | 类型     | 必填   | 说明   |
| ------- | ---- | ------ | ---- | ---- |
| temp_id |      | String | 是    | 模板文件 |
#### 回复报文参数
| 参数名      | 长度     | 类型   | 必填        | 说明   |
| -------- | ------ | ---- | --------- | ---- |
| temp_url | String | 是    | 模板图片文件url |      |


## 服务号对接信息
### 服务号对接信息列表查询
```
[GET]/sys_service/tenant_regapply/docking/list
```
涉及到的表：
租户微信网页授权认证文件表(bas_tenant_wechat_webauth)

说明：


#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 查询   |

#### 请求报文参数
| 参数名       | 长度      | 类型     | 必填            | 说明   |
| --------- | ------- | ------ | ------------- | ---- |
| tenat_id  |         | String | 是             | 租户id |
| page_num  | Integer | 否      | 页码 （默认为 1）    |      |
| page_size | Integer | 否      | 每页数量 （默认为 10） |      |

#### 回复报文参数
| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 页码     |
| page_size | Integer    | 是    | 每页数量   |
| pages     | Integer    | 是    | 总页数    |
| total     | Integer    | 是    | 总数量    |
| list      | ObjectList | 是    | 对接信息列表 |

#### 对接信息列表ObjectList

| 参数名          | 类型      | 必填   | 说明           |
| ------------ | ------- | ---- | ------------ |
| docking_id   | String  | 是    | 对接信息id       |
| tenat_id     | String  | 是    | 租户号          |
| tenant_name  | String  | 是    | 租户名称         |
| docking_time | String  | 是    | 对接日期         |
| status       | Integer | 是    | 状态 0-停用;1-启用 |


### 服务号对接启用停用
```
[POST]/sys_service/tenant_regapply/docking/enable
```
涉及到的表：
租户微信网页授权认证文件表(bas_tenant_wechat_webauth)

说明：当前页面显示为启用，调用这个接口则为停用，反之则为启用

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 更新   |

#### 请求报文参数
| 参数名      | 长度   | 类型     | 必填   | 说明   |
| -------- | ---- | ------ | ---- | ---- |
| tenat_id |      | String | 是    | 租户id |

#### 回复报文参数



### 服务号对接详情
```
[GET]/sys_service/tenant_regapply/docking/info
```
涉及到的表：
租户微信网页授权认证文件表(bas_tenant_wechat_webauth)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 更新   |

#### 请求报文参数
| 参数名      | 长度   | 类型     | 必填   | 说明   |
| -------- | ---- | ------ | ---- | ---- |
| tenat_id |      | String | 是    | 租户id |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明        |
| --------- | ---------- | ---- | --------- |
| page_num  | Integer    | 是    | 页码        |
| page_size | Integer    | 是    | 每页数量      |
| pages     | Integer    | 是    | 总页数       |
| total     | Integer    | 是    | 总数量       |
| appid     | Integer    | 是    | appid     |
| appSecret | Integer    | 是    | appSecret |
| list      | ObjectList | 是    | 消息模板列表    |

#### 消息模板列表ObjectList

| 参数名        | 类型     | 必填   | 说明     |
| ---------- | ------ | ---- | ------ |
| templateId | String | 是    | 微信模板ID |
| title      | String | 是    | 模板标题   |
| content    | String | 是    | 模板内容   |

### 网页授权域名文件下载
```
[GET]/sys_service/tenant_regapply/docking/download
```
涉及到的表：
租户微信网页授权认证文件表(bas_tenant_wechat_webauth)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.3 | 更新   |

#### 请求报文参数
| 参数名      | 长度   | 类型     | 必填   | 说明   |
| -------- | ---- | ------ | ---- | ---- |
| tenat_id |      | String | 是    | 租户id |

#### 回复报文参数
| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 文件流  |      |      |      |




## 检查项

### 检查项列表查询

```
[GET]/sys_service/eye_examination/list 
```
涉及到的表：
检查项表(pla_eye_examination_items)

说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.4 | 列表查询 |

#### 请求报文参数

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明     |
| ---------- | ---------- | ---- | ------ |
| exam_name  | Integer    | 是    | 检查项目名称 |
| items_list | ObjectList | 否    | 检查项列表  |
#### 版本管理列表
| 参数名       | 长度   | 类型     | 必填   | 说明    |
| --------- | ---- | ------ | ---- | ----- |
| item_name |      | String | 是    | 检查项名称 |
| item_id   |      | String | 是    | 检查项id |


### 检查项-指标项信息查询

```
[GET]/sys_service/eye_examination/indicator_info    
```
涉及到的表：
检查项表(pla_eye_examination_items)
指标项表(pla_indicator_item)
说明：


#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.4 | 新增   |

#### 请求报文参数
#### RequestBody
| 参数名     | 长度   | 类型     | 必填   | 说明    |
| ------- | ---- | ------ | ---- | ----- |
| exam_id |      | String | 是    | 检查项id |


#### 回复报文参数
| 参数名       | 长度   | 类型         | 必填   | 说明       |
| --------- | ---- | ---------- | ---- | -------- |
| exam_id   |      | String     | 是    | 检查项id    |
| exam_code |      | String     | 是    | 检查项编号    |
| exam_key  |      | String     | 是    | 检查项key   |
| exam_name |      | String     | 是    | 检查项名称    |
| indi_list |      | ObjectList | 是    | 检查指标list |
#### 检查指标list （indi_list）
| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| indi_id   |      | String | 是    | 检查指标id |
| indi_name |      | String | 是    | 检查指标名称 |


### 指标项信息查询
```
[GET]/sys_service/eye_examination/indicator/info  
```
涉及到的表：
指标项表(pla_indicator_item)
说明：
#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.4 | 查询   |

#### 请求报文参数
| 参数名     | 长度   | 类型     | 必填   | 说明     |
| ------- | ---- | ------ | ---- | ------ |
| indi_id |      | String | 是    | 检查指标id |
#### 回复报文参数
| 参数名       | 长度   | 类型     | 必填   | 说明       |
| --------- | ---- | ------ | ---- | -------- |
| indi_id   |      | String | 是    | 检查指标项id  |
| indi_code |      | String | 是    | 检查指标项编码  |
| indi_key  |      | String | 是    | 检查指标项key |
| indi_name |      | String | 是    | 检查指标项名称  |


### 平台人员列表

```
[GET]/sys_service/platform_personer/list  
```
涉及到的表：
用户角色分配表(com_user_role)
角色资源分配表(com_role_resource)
租户用户信息表(com_tena_user)
管理员表(com_tena_admin)
说明：

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.0.4 | 查询   |

#### 请求报文参数
##### requestParam:

| 参数名     | 类型     | 必填   | 说明      |
| ------- | ------ | ---- | ------- |
| tena_id | String | 否    | 租户：租户ID |

#### 回复报文参数
| 参数名       | 长度   | 类型     | 必填   | 说明   |
| --------- | ---- | ------ | ---- | ---- |
| user_id   |      | String | 否    | 用户id |
| user_name |      | String | 是    | 用户名称 |



# 租户报表

### 租户统计分页列表

```
[GET]/sys_service/statistic/tenant/pagelist
```
涉及到的表：
租户信息表(pla_tenant)
租户用户信息表(com_tena_user)
#### 修改更新记录

| 对应版本        | 说明   |
| ----------- | ---- |
| BOSS-V1.0.4 | 查询   |

#### 请求参数报文：

##### requestParam:

| 参数名     | 类型     | 必填   | 说明           |
| ------- | ------ | ---- | ------------ |
| statistic_type | String | 是    | 0:全部租户；1：昨日新增；2：本月新增；3：日期区间的新增 |
| end_time    | String  | 否    | 结束时间        |
| begin_time  | String  | 否    | 发生时间        |
| page_num    | Integer | 否    | 页码 （默认为 1）    |
| page_size   | Integer | 否    | 每页数量 （默认为 10） |
#### 回复参数报文

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| platform_statis | Integer    | 是    | 平台总数       |
| yesterday_statis | Integer    | 是    | 昨日新增数     |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 否    | 统计列表        |

#### 统计列表 （list）
| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| tena_id   |      | String | 是    |  租户id  |
| tena_name   |      | String | 是    | 租户名称 |
| multiagency |      | Integer | 是    | '多运营机构标志,默认:0;0-单运营机构;1-多运营机构' |
| start_time    |      | String | 是    | 开通时间    |
| sales    |      | String | 是    | 销售人员  |
| customer_service    |      | String | 是    | 客服经理  |


### 患者统计分页列表

```
[GET]/sys_service/statistic/patient/pagelist
```
涉及到的表：
租户信息表(pla_tenant)
租户患者用户信息表(com_tena_patiuser）
#### 修改更新记录

| 对应版本        | 说明   |
| ----------- | ---- |
| BOSS-V1.0.4 | 查询   |

#### 请求参数报文：

##### requestParam:

| 参数名     | 类型     | 必填   | 说明           |
| ------- | ------ | ---- | ------------ |
| tena_id | String | 否    | 租户ID,不填为全部|
| end_time    | String  | 否    | 结束时间        |
| begin_time  | String  | 否    | 发生时间        |
| page_num    | Integer | 否    | 页码 （默认为 1）    |
| page_size   | Integer | 否    | 每页数量 （默认为 10） |
#### 回复参数报文

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| platform_statis | Integer    | 是    | 平台总数       |
| yesterday_statis | Integer    | 是    | 昨日新增数     |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 否    | 统计列表        |

#### 统计列表 （list）
| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| tena_id   |      | String | 是    |  租户id  |
| tena_name   |      | String | 是    |  租户名称  |
| tena_statis |      | Integer | 是    | 租户患者总数 |
| tena_yesterday_statis    |      | String | 是    | 昨日新增数    |



### 挂号统计分页列表

```
[GET]/sys_service/statistic/book/pagelist
```
涉及到的表：
租户信息表(pla_tenant)
租户收费订单表(com_tena_trade)  
说明：
租户收费订单表(com_tena_trade)   的字段trad_biztype为2

#### 修改更新记录

| 对应版本        | 说明   |
| ----------- | ---- |
| BOSS-V1.0.4 | 查询   |

#### 请求参数报文：

##### requestParam:

| 参数名     | 类型     | 必填   | 说明           |
| ------- | ------ | ---- | ------------ |
| tena_id | String | 否    | 租户ID,不填为全部|
| end_time    | String  | 否    | 结束时间        |
| begin_time  | String  | 否    | 发生时间        |
| page_num    | Integer | 否    | 页码 （默认为 1）    |
| page_size   | Integer | 否    | 每页数量 （默认为 10） |
#### 回复参数报文

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| platform_statis | Integer    | 是    | 平台总数       |
| yesterday_statis | Integer    | 是    | 昨日新增数     |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 否    | 统计列表        |

#### 统计列表 （list）
| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| tena_id   |      | String | 是    |  租户id  |
| tena_name   |      | String | 是    |  租户名称  |
| tena_statis |      | Integer | 是    | 租户挂号总数 |
| tena_yesterday_statis    |      | String | 是    | 昨日新增数    |




### 处方统计分页列表

```
[GET]/sys_service/statistic/recipe/pagelist
```
涉及到的表：
租户信息表(pla_tenant)
租户收费订单表(com_tena_trade)  
说明：
租户收费订单表(com_tena_trade)   的字段trad_biztype为4

#### 修改更新记录

| 对应版本        | 说明   |
| ----------- | ---- |
| BOSS-V1.0.4 | 查询   |

#### 请求参数报文：

##### requestParam:

| 参数名     | 类型     | 必填   | 说明           |
| ------- | ------ | ---- | ------------ |
| tena_id | String | 否    | 租户ID,不填为全部|
| end_time    | String  | 否    | 结束时间        |
| begin_time  | String  | 否    | 发生时间        |
| page_num    | Integer | 否    | 页码 （默认为 1）    |
| page_size   | Integer | 否    | 每页数量 （默认为 10） |
#### 回复参数报文

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| platform_statis | Integer    | 是    | 平台总数       |
| yesterday_statis | Integer    | 是    | 昨日新增数     |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 否    | 统计列表        |

#### 统计列表 （list）
| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| tena_id   |      | String | 是    |  租户id  |
| tena_name   |      | String | 是    |  租户名称  |
| tena_statis |      | Integer | 是    | 租户处方总数 |
| tena_yesterday_statis    |      | String | 是    | 昨日新增数    |




### 视光统计分页列表

```
[GET]/sys_service/statistic/optometr/pagelist
```
涉及到的表：
租户信息表(pla_tenant)
租户收费订单表(com_tena_trade)  
说明：
租户收费订单表(com_tena_trade)   的字段trad_biztype为1

#### 修改更新记录

| 对应版本        | 说明   |
| ----------- | ---- |
| BOSS-V1.0.4 | 查询   |

#### 请求参数报文：

##### requestParam:

| 参数名     | 类型     | 必填   | 说明           |
| ------- | ------ | ---- | ------------ |
| tena_id | String | 否    | 租户ID,不填为全部|
| end_time    | String  | 否    | 结束时间        |
| begin_time  | String  | 否    | 发生时间        |
| page_num    | Integer | 否    | 页码 （默认为 1）    |
| page_size   | Integer | 否    | 每页数量 （默认为 10） |
#### 回复参数报文

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| platform_statis | Integer    | 是    | 平台总数       |
| yesterday_statis | Integer    | 是    | 昨日新增数     |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 否    | 统计列表        |

#### 统计列表 （list）
| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| tena_id   |      | String | 是    |  租户id  |
| tena_name   |      | String | 是    |  租户名称  |
| tena_statis |      | Integer | 是    | 租户视光单总数 |
| tena_yesterday_statis    |      | String | 是    | 昨日新增数    |



### 药品统计分页列表

```
[GET]/sys_service/statistic/drug/pagelist
```
涉及到的表：
租户信息表(pla_tenant)
药品信息表(drug_directory)
说明：


#### 修改更新记录

| 对应版本        | 说明   |
| ----------- | ---- |
| BOSS-V1.0.4 | 查询   |

#### 请求参数报文：

##### requestParam:

| 参数名     | 类型     | 必填   | 说明           |
| ------- | ------ | ---- | ------------ |
| drug_id | String | 否    | 药品ID,不填为全部|
| end_time    | String  | 否    | 结束时间        |
| begin_time  | String  | 否    | 发生时间        |
| page_num    | Integer | 否    | 页码 （默认为 1）    |
| page_size   | Integer | 否    | 每页数量 （默认为 10） |
#### 回复参数报文

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| platform_statis | Integer    | 是    | 平台总数       |
| yesterday_statis | Integer    | 是    | 昨日新增数     |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 否    | 统计列表        |

#### 统计列表 （list）
| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| drug_id   |      | String | 是    |  药品id  |
| drug_name   |      | String | 是    |  药品名称  |
| drug_pack_spec_id   |      | String | 是    |  药品规格id  |
| drug_pack_spec |      | String | 是    | 药品规格 |
| drugs_mfr_id    |      | String | 是    | 生产厂商ID    |
| drugs_mfr_name |      | String | 是    | 生产厂商 |
| drugs_pack_spec_id |      | String | 是    | 包装规格ID |
| drugs_pack_spec |      | String | 是    | 包装规格 |
| drugs_statis |      | Integer | 是    |  药品总销量 |
| drugs_yesterday_statis    |      | String | 是    | 昨日新增    |


### 药品列表

```
[GET]/sys_service/statistic/drug/list
```
涉及到的表：
药品信息表(drug_directory)
说明：

#### 修改更新记录

| 对应版本        | 说明   |
| ----------- | ---- |
| BOSS-V1.0.4 | 查询   |

#### 请求参数报文：
#### 回复参数报文

| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| drug_id   |      | String | 是    |  药品id  |
| drug_name   |      | String | 是    |  药品名称  |




### 商品统计分页列表

```
[GET]/sys_service/statistic/goods/pagelist
```
涉及到的表：
租户信息表(pla_tenant)
商品目录表(erp_goods)

说明：


#### 修改更新记录

| 对应版本        | 说明   |
| ----------- | ---- |
| BOSS-V1.0.4 | 查询   |

#### 请求参数报文：

##### requestParam:

| 参数名     | 类型     | 必填   | 说明           |
| ------- | ------ | ---- | ------------ |
| goods_id | String | 否    | 商品ID,不填为全部|
| end_time    | String  | 否    | 结束时间        |
| begin_time  | String  | 否    | 发生时间        |
| page_num    | Integer | 否    | 页码 （默认为 1）    |
| page_size   | Integer | 否    | 每页数量 （默认为 10） |
#### 回复参数报文

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| platform_statis | Integer    | 是    | 平台总数       |
| yesterday_statis | Integer    | 是    | 昨日新增数     |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 否    | 统计列表        |

#### 统计列表 （list）
| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| goods_id   |      | String | 是    |  商品ID  |
| goods_name   |      | String | 是    |  商品名称  |
| goods_mfr_id    |      | String | 是    | 生产厂家ID    |
| goods_mfr_name |      | String | 是    | 生产厂家 |
| tena_id   |      | String | 是    |  租户id  |
| tena_name   |      | String | 是    |  租户名称  |
| tena_statis |      | Integer | 是    |  药品总销量 |
| tena_yesterday_statis    |      | String | 是    | 昨日新增    |


### 商品列表

```
[GET]/sys_service/statistic/goods/list
```
涉及到的表：
商品目录表(erp_goods)
说明：

#### 修改更新记录

| 对应版本        | 说明   |
| ----------- | ---- |
| BOSS-V1.0.4 | 查询   |

#### 请求参数报文：
#### 回复参数报文

| 参数名       | 长度   | 类型     | 必填   | 说明     |
| --------- | ---- | ------ | ---- | ------ |
| goods_id   |      | String | 是    |  商品id  |
| goods_name   |      | String | 是    |  商品名称  |





