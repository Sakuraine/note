# Erp服务协议

## 基本信息

端口号：8015
RedisDB：10
包含眼视相关业务内容

##系统管理-视光厂商

### 视光厂商列表  

> [GET]/erp_service/system/factory/list


####修改更新记录

| 对应版本   | 说明              |
| ------ | --------------- |
| V1.3.3 | 新增 增加证件过期到期提醒时间 |

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明                        |
| ---------- | ------- | ---- | ------------------------- |
| key        | String  | 否    | 关键字                       |
| mfr_enable | Integer | 否    | 是否有效 0：停用1：有效  传空全部       |
| mfr_type   | Integer | 否    | 厂商类型    1:供应商;2:生产商; 传空全部 |
| page_size  | Integer | 否    | 每页条数 空表示10条               |
| page_num   | Integer | 否    | 第几页 空表示第1页                |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 当前页    |
| page_size | Integer    | 是    | 每页的数量  |
| total     | Integer    | 是    | 总记录数   |
| pages     | Integer    | 是    | 总页数    |
| list      | ObjectList | 否    | 视光厂商列表 |

视光厂商列表说明

| 参数名          | 类型      | 必填   | 说明                          |
| ------------ | ------- | ---- | --------------------------- |
| mfr_id       | String  | 是    | 厂商ID                        |
| mfr_code     | String  | 是    | 厂商编码                        |
| mfr_name     | String  | 是    | 厂商名称                        |
| mfr_type     | Integer | 是    | 厂商类型  1:供应商;2:生产商;3:供应商入生产商 |
| mfr_enable   | Integer | 是    | 是否有效 0：停用1：有效               |
| expire_state | Integer | 是    | 过期状态 0正常 1即将到期 2已经过期        |



### 视光厂商——基本信息保存

> [POST]/erp_service/system/factory/base

####修改更新记录

| 对应版本   | 说明              |
| ------ | --------------- |
| V1.3.3 | 新增 增加证件过期到期提醒时间 |


#### 请求报文参数

| 参数名                          | 类型      | 必填   | 说明                         |
| ---------------------------- | ------- | ---- | -------------------------- |
| mfr_code                     | String  | 是    | 厂商编码                       |
| mfr_name                     | String  | 是    | 厂商名称                       |
| mfr_type                     | Integer | 是    | 厂商类型 1:供应商;2:生产商;3:供应商入生产商 |
| mfr_enable                   | Integer | 是    | 是否有效 0：停用1：有效              |
| mfr_taxrate                  | Integer | 否    | 税率                         |
| mfr_area_code                | String  | 否    | 地市区代码                      |
| mfr_compaddress              | String  | 否    | 公司详细地址                     |
| mfr_remind_time              | Integer | 否    | 证件有效期到期时间             单位天  |
| mfr_biz_licence_code         | String  | 否    | 工商营业执照号                    |
| mfr_biz_licence_validity_str | String  | 否    | 工商营业执照有效期                  |
| mfr_biz_licence_photo        | String  | 否    | 工商营业执照照片，文件资源ID            |
| mfr_licence_code             | String  | 否    | 医疗器械经营许可证号                 |
| mfr_licence_validity_str     | String  | 否    | 医疗器械经营许可证有效期               |
| mfr_licence_photo            | String  | 否    | 医疗器械经营许可证照片，文件资源ID         |
| mfr_production               | String  | 否    | 医疗器械生产许可证号                 |
| mfr_produ_validity_str       | String  | 否    | 医疗器械生产许可证有效期               |
| mfr_produ_photo              | String  | 否    | 医疗器械生产许可证证照片，文件资源ID        |

#### 回复报文参数

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| mfr_id | String | 是    | 厂商ID |



### 视光厂商——基本信息修改

> [POST]/erp_service/system/factory/base/update

需要把
`mfr_biz_licence_expire` '工商营业执照有效期到期提醒标志,默认:0;0:未提醒;1:已提醒;',
  `mfr_biz_licence_overdue`  '工商营业执照有效期过期提醒标志,默认:0;0:未提醒;1:已提醒;',
  `mfr_licence_expire`  '医疗器械经营许可证有效期到期提醒标志,默认:0;0:未提醒;1:已提醒;',
  `mfr_licence_overdue`  '医疗器械经营许可证有效期过期提醒标志,默认:0;0:未提醒;1:已提醒;',
  `mfr_production_expire`  '医疗器械生产许可证有效期到期提醒标志,默认:0;0:未提醒;1:已提醒;',
  `mfr_production_overdue`  '医疗器械生产许可证有效期过期提醒标志,默认:0;0:未提醒;1:已提醒;',
都改为 0 未提醒

####修改更新记录

| 对应版本   | 说明              |
| ------ | --------------- |
| V1.3.3 | 新增 增加证件过期到期提醒时间 |

#### 请求报文参数

| 参数名                          | 类型      | 必填   | 说明                        |
| ---------------------------- | ------- | ---- | ------------------------- |
| mfr_id                       | String  | 是    | 厂商ID                      |
| mfr_code                     | String  | 是    | 厂商编码                      |
| mfr_name                     | String  | 是    | 厂商名称                      |
| mfr_type                     | Integer | 是    | 厂商类型  1:供应商;2:生产商;        |
| mfr_enable                   | Integer | 是    | 是否有效 0：停用1：有效             |
| mfr_taxrate                  | Integer | 否    | 税率                        |
| mfr_area_code                | String  | 否    | 地市区代码                     |
| mfr_compaddress              | String  | 否    | 公司详细地址                    |
| mfr_remind_time              | Integer | 否    | 证件有效期到期时间             单位天 |
| mfr_biz_licence_code         | String  | 否    | 工商营业执照号                   |
| mfr_biz_licence_validity_str | String  | 否    | 工商营业执照有效期                 |
| mfr_biz_licence_photo        | String  | 否    | 工商营业执照照片，文件资源ID           |
| mfr_licence_code             | String  | 否    | 医疗器械经营许可证号                |
| mfr_licence_validity_str     | String  | 否    | 医疗器械经营许可证有效期              |
| mfr_licence_photo            | String  | 否    | 医疗器械经营许可证照片，文件资源ID        |
| mfr_production               | String  | 否    | 医疗器械生产许可证号                |
| mfr_produ_validity_str       | String  | 否    | 医疗器械生产许可证有效期              |
| mfr_produ_photo              | String  | 否    | 医疗器械生产许可证证照片，文件资源ID       |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 视光厂商获取

> [GET]/erp_service/system/factory



####修改更新记录

| 对应版本   | 说明              |
| ------ | --------------- |
| V1.3.3 | 新增 增加证件过期到期提醒时间 |

#### 请求报文参数

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| mfr_id | String | 是    | 厂商ID |


#### 回复报文参数

| 参数名                            | 类型         | 必填   | 说明                               |
| ------------------------------ | ---------- | ---- | -------------------------------- |
| mfr_code                       | String     | 是    | 厂商编码                             |
| mfr_name                       | String     | 是    | 厂商名称                             |
| mfr_type                       | Integer    | 是    | 厂商类型  1:供应商;2:生产商;               |
| mfr_enable                     | Integer    | 是    | 是否有效 0：停用1：有效                    |
| mfr_taxrate                    | Integer    | 否    | 税率 3 17 0                        |
| mfr_prov_code                  | String     | 否    | 省代码                              |
| mfr_city_code                  | String     | 否    | 市代码                              |
| mfr_coun_code                  | String     | 否    | 区代码                              |
| mfr_compaddress                | String     | 否    | 公司详细地址                           |
| mfr_taxno                      | String     | 否    | 税号                               |
| mfr_address                    | String     | 否    | 单位地址                             |
| mfr_tel                        | String     | 否    | 公司电话                             |
| mfr_bank                       | String     | 否    | 开户行                              |
| mfr_bankcard                   | String     | 否    | 账号                               |
| mfr_remind_time                | Integer    | 否    | 证件有效期到期时间             单位天        |
| mfr_biz_licence_code           | String     | 否    | 工商营业执照号                          |
| mfr_biz_licence_validity_str   | String     | 否    | 工商营业执照有效期                        |
| mfr_biz_licence_validity_state | String     | 否    | 工商营业执照有效期状态   0正常 1即将到期 2已经过期    |
| mfr_biz_licence_photo          | String     | 否    | 工商营业执照照片，文件资源ID                  |
| mfr_biz_licence_photo_url      | String     | 否    | 工商营业执照照片url路径                    |
| mfr_licence_code               | String     | 否    | 医疗器械经营许可证号                       |
| mfr_licence_validity_str       | String     | 否    | 医疗器械经营许可证有效期                     |
| mfr_licence_validity_state     | String     | 否    | 医疗器械经营许可证有效期状态   0正常 1即将到期 2已经过期 |
| mfr_licence_photo              | String     | 否    | 医疗器械经营许可证照片，文件资源ID               |
| mfr_licence_photo_url          | String     | 否    | 医疗器械经营许可证照片url路径                 |
| mfr_production                 | String     | 否    | 医疗器械生产许可证号                       |
| mfr_produ_validity_str         | String     | 否    | 医疗器械生产许可证有效期                     |
| mfr_produ_validity_state       | String     | 否    | 医疗器械生产许可证有效期状态   0正常 1即将到期 2已经过期 |
| mfr_produ_photo                | String     | 否    | 医疗器械生产许可证证照片，文件资源ID              |
| mfr_produ_photo_url            | String     | 否    | 医疗器械生产许可证证照片url路径                |
| list                           | ObjectList | 否    | 联系人列表                            |

联系人列表说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| link_id        | String | 否    | 联系人ID |
| link_man       | String | 是    | 联系人   |
| link_prov_code | String | 否    | 省代码   |
| link_city_code | String | 否    | 市代码   |
| link_coun_code | String | 否    | 区代码   |
| link_address   | String | 否    | 详细地址  |
| link_tel       | String | 否    | 联系电话  |
| link_phone     | String | 否    | 手机号码  |
| link_fax       | String | 否    | 传真    |
| link_email     | String | 否    | 邮箱    |
| link_rem       | String | 否    | 备注    |


##商品相关

### 复制新增商品

```http
[GET]/erp_service/goods/copy/{good_id}
```

####修改更新记录

| 对应版本   | 说明     |
| ------ | ------ |
| V1.3.3 | 商品复制新增 |

#### 请求报文参数

####PathVariable
| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| good_id | String | 是    | 商品ID |

#### 回复报文参数

| 参数名            | 类型         | 说明                   |
| -------------- | ---------- | -------------------- |
| good_calss     | String     | 商品类别id               |
| good_brand     | String     | 商品品牌id               |
| good_variety   | String     | 商品品种id               |
| good_factory   | String     | 生产厂商id               |
| good_supplier  | String     | 供应商id                |
| good_registrno | String     | 注册证号                 |
| good_bidprice  | Double     | 参考成本价                |
| good_price     | Double     | 售价                   |
| good_char_id   | String     | 收费类别ID               |
| good_unitid    | String     | 单位id                 |
| good_unitname  | String     | 商品单位名称               |
| good_give      | Integer    | 允许赠送,默认:0;0-不允许;1-允许 |
| status         | Integer    | 0-不在售;1-在售;停用2       |
| stock_list     | ObjectList | 入库属性列表               |
| list           | ObjectList | 非入库属性列表              |

入库属性列表说明

| 参数名            | 类型     | 说明    |
| -------------- | ------ | ----- |
| prop_prop_id   | String | 属性码ID |
| prop_prop_name | String | 属性码名称 |

非入库属性列表说明

| 参数名            | 类型     | 说明    |
| -------------- | ------ | ----- |
| prop_prop_id   | String | 属性码ID |
| prop_prop_name | String | 属性码名称 |
| choi_id        | String | 属性值ID |
| choi_code      | String | 属性值代码 |
| choi_value     | String | 属性值内容 |


## 批量入库相关


### 批量入库时商品族列表

   > [GET]/erp_service/arrival/batch_add/same_nation_list

#### 修改更新记录

| 对应版本     | 说明             |
| -------- | -------------- |
| V1.3.1.1 | 新增  批量新增时选择商品族 |

#### 请求报文参数

#### RequestBody

| 参数名           | 类型     | 必填   | 说明      |
| ------------- | ------ | ---- | ------- |
| good_class    | String | 是    | 商品类别    |
| good_brand    | String | 是    | 商品品牌    |
| good_variety  | String | 是    | 商品品种id  |
| good_factory  | String | 否    | 商品厂商id  |
| good_supplier | String | 否    | 商品供应商id |

#### 回复报文参数

| 参数名         | 类型      | 必填   | 说明                |
| ----------- | ------- | ---- | ----------------- |
| nation_id   | String  | 是    | 商品族ID             |
| nation_name | String  | 是    | 商品族名称             |
| bid_price   | Double  | 是    | 进价 单位元            |
| unit        | String  | 是    | 计量单位              |
| enable      | Integer | 是    | 是否可选   0 不可选 1 可选 |



### 批量入库时某族商品详细

   > [GET]/erp_service/arrival/batch_add/nation_view


#### 修改更新记录

| 对应版本     | 说明             |
| -------- | -------------- |
| V1.3.1.1 | 新增  批量新增时选择商品族 |

#### 请求报文参数

#### RequestBody

| 参数名       | 类型     | 必填   | 说明    |
| --------- | ------ | ---- | ----- |
| nation_id | String | 是    | 商品族ID |

#### 回复报文参数 ObjectList

| 参数名           | 类型         | 必填   | 说明                   |
| ------------- | ---------- | ---- | -------------------- |
| sphere_value  | String     | 是    | 球面 值                 |
| goods         | Object     | 否    | 商品对象 有柱面列表对象时 商品对象为空 |
| cylinder_list | ObjectList | 是    | 柱面列表对象               |

柱面列表对象说明

| 参数名            | 类型     | 必填   | 说明                    |
| -------------- | ------ | ---- | --------------------- |
| cylinder_value | String | 是    | 柱面 值                  |
| goods          | Object | 否    | 商品对象     为空表示没有商品，不可填 |

商品对象说明

| 参数名                | 类型     | 必填   | 说明      |
| ------------------ | ------ | ---- | ------- |
| good_id            | String | 是    | 商品ID    |
| good_name          | String | 是    | 商品名称    |
| good_code          | String | 是    | 商品编码    |
| good_bidprice      | Double | 是    | 商品进价    |
| good_price         | Double | 是    | 原售价     |
| good_now_price     | Double | 是    | 现售价     |
| good_unit          | String | 是    | 商品单位    |
| good_supplier      | String | 是    | 商品供应商id |
| good_supplier_name | String | 是    | 商品供应商名称 |
| good_factory       | String | 是    | 商品厂商id  |
| good_factory_name  | String | 是    | 商品厂商名称  |
| good_registrno     | String | 是    | 注册证号    |
| good_class         | String | 是    | 商品分类id  |



## 批量修改商品


### 批量修改时查询商品列表

   > [GET]/erp_service/system/goods/batch_update/goods_list

#### 修改更新记录

| 对应版本     | 说明         |
| -------- | ---------- |
| V1.3.1.1 | 新增  批量修改商品 |

#### 请求报文参数

#### RequestBody

| 参数名           | 类型      | 必填   | 说明                    |
| ------------- | ------- | ---- | --------------------- |
| good_class    | String  | 是    | 商品类别                  |
| good_brand    | String  | 是    | 商品品牌                  |
| good_variety  | String  | 是    | 商品品种id                |
| good_factory  | String  | 否    | 商品厂商id                |
| good_supplier | String  | 否    | 商品供应商id               |
| char_id       | String  | 否    | 收费类别ID 不传全部           |
| unitid        | String  | 否    | 计量单位ID  不传全部          |
| good_give     | Integer | 否    | 允许赠送  不传全部            |
| registrno     | String  | 否    | 注册证号                  |
| good_sell     | Integer | 否    | 在售状态  0-不在售;1-在售;2-停用  不传全部 |
| good_price    | Double  | 否    | 商品售价                  |
| good_bidprice | Double  | 否    | 参考成本价                 |
| page_size     | Integer | 否    | 每页条数 空表示10条           |
| page_num      | Integer | 否    | 第几页 空表示第1页            |

#### 回复报文参数


| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 是    | 商品列表  |


商品列表说明

| 参数名           | 类型      | 必填   | 说明               |
| ------------- | ------- | ---- | ---------------- |
| good_id       | String  | 是    | 商品ID             |
| good_name     | String  | 是    | 商品名称             |
| good_code     | String  | 是    | 商品编码             |
| good_bidprice | Double  | 是    | 商品进价（成本价）        |
| good_price    | Double  | 否    | 商品售价             |
| good_unit     | String  | 是    | 商品单位             |
| good_sell     | Integer | 是    | 在售状态  0-不在售;1-在售;2-停用 |


### 批量修改商品

   > [POST]/erp_service/system/goods/batch_update

#### 修改更新记录

| 对应版本     | 说明         |
| -------- | ---------- |
| V1.3.1.1 | 新增  批量修改商品 |

#### 请求报文参数

#### RequestBody

| 参数名            | 类型         | 必填   | 说明                                       |
| -------------- | ---------- | ---- | ---------------------------------------- |
| good_factory   | String     | 否    | 商品厂商id                                   |
| good_supplier  | String     | 否    | 商品供应商id                                  |
| char_id        | String     | 否    | 收费类别ID                                   |
| good_bidprice  | Double     | 否    | 参考成本价                                    |
| unitid         | String     | 否    | 计量单位ID                                   |
| good_give      | Integer    | 否    | 允许赠送  0-不允许;1-允许                     |
| registrno      | String     | 否    | 注册证号                                     |
| good_sell      | Integer    | 否    | 在售状态  0-不在售;1-在售;2-停用                |
| regis_validity | String     | 否    | 医疗器械证书有效期,小时部分用0                         |
| registr_img    | String     | 否    | 注册证照片文件，上传路径: ${租户号}/goods/registrno/${商品ID}_${RequestID}.${扩展名} |
| good_list      | ObjectList | 否    | 商品列表                                     |

商品列表说明

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| good_id | String | 是    | 商品ID |




##养护记录

### 新增养护记录

```http
[POST]/erp_service/maintain
```

####修改更新记录

| 对应业务   | 说明     |
| ------ | ------ |
| V1.3.3 | 新增养护记录 |

#### 请求报文参数

<<<<<<< HEAD
| 参数名            | 类型      | 必填   | 说明          |
| -------------- | ------- | ---- | ----------- |
| goods_id       | Long    | 是    | 商品ID        |
| main_time      | String  | 是    | 养护日期        |
| goods_batchno  | String  | 否    | 生产批号        |
| goods_validity | String  | 否    | 有效期         |
| goods_quality  | String  | 是    | 外包装质量情况     |
| is_sale        | Integer | 是    | 是否继续销售 0否1是 |
=======
| 参数名            | 类型     | 必填   | 说明      |
| -------------- | ------ | ---- | ------- |
| goods_id       | String   | 是    | 商品ID    |
| main_time      | String | 是    | 养护日期    |
| goods_batchno  | String | 否    | 生产批号    |
| goods_validity | String | 否    | 有效期     |
| goods_quality  | String | 是    | 外包装质量情况 |
| is_sale  | Integer | 是    | 是否继续销售 0否1是 |

>>>>>>> ed82b085c7f133437e705dee71ae79075d1b40d3

#### 回复报文参数

| 参数名     | 类型   | 说明   |
| ------- | ---- | ---- |
| main_id | Long | 记录ID |


### 修改养护记录

```http
[POST]/erp_service/maintain/{main_id}
```

####修改更新记录

| 对应业务   | 说明     |
| ------ | ------ |
| V1.3.3 | 养护记录修改 |

#### 请求报文参数

####PathVariable
| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| main_id | String | 是    | 养护记录ID |

<<<<<<< HEAD

| 参数名           | 类型      | 必填   | 说明          |
| ------------- | ------- | ---- | ----------- |
| main_time     | String  | 是    | 养护日期        |
| goods_quality | String  | 是    | 外包装质量情况     |
| is_sale       | Integer | 是    | 是否继续销售 0否1是 |
=======
###RequestPara
| 参数名           | 类型     | 必填   | 说明      |
| ------------- | ------ | ---- | ------- |
| main_time     | String | 是    | 养护日期    |
| goods_quality | String | 是    | 外包装质量情况 |
| is_sale  | Integer | 是    | 是否继续销售 0否1是 |
>>>>>>> ed82b085c7f133437e705dee71ae79075d1b40d3

#### 回复报文参数

| 参数名  | 类型   | 说明   |
| ---- | ---- | ---- |
| 无    |      |      |


### 删除养护记录

```http
[DELETE]/erp_service/maintain/{main_id}
```

####修改更新记录

| 对应业务   | 说明     |
| ------ | ------ |
| V1.3.3 | 删除养护记录 |

#### 请求报文参数

####PathVariable
| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| main_id | String | 是    | 养护记录ID |


| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数

| 参数名  | 类型   | 说明   |
| ---- | ---- | ---- |
| 无    |      |      |


### 养护记录列表

```http
[GET]/erp_service/maintain/list
```

####修改更新记录

| 对应业务   | 说明       |
| ------ | -------- |
| V1.3.3 | 新增养护记录列表 |

#### 请求报文参数

| 参数名            | 类型     | 必填   | 说明   |
| -------------- | ------ | ---- | ---- |
| goods_id       | Long   | 是    | 商品ID |
| goods_batchno  | String | 否    | 生产批号 |
| goods_validity | String | 否    | 有效期  |


#### 回复报文参数

| 参数名          | 类型      | 说明      |
| ------------ | ------- | ------- |
| main_id      | Long    | 记录ID    |
| main_time    | String  | 养护日期    |
| main_quality | String  | 外包装质量情况 |
| is_sale      | Integer | 是       |

### 养护记录商品列表

```http
[GET]/erp_service/maintain/goods/list
```

####修改更新记录

| 对应业务   | 说明       |
| ------ | -------- |
| V1.3.3 | 新增养护记录列表 |

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明               |
| ---------- | ------- | ---- | ---------------- |
| clas_id    | Long    | 否    | 类别ID，不传为全部       |
| bran_id    | Long    | 否    | 品牌ID，不传为全部       |
| vari_id    | Long    | 否    | 品种ID，不传为全部       |
| depot_id   | Long    | 是    | 仓库ID             |
| start_time | String  | 否    | 最后一次养护开始时间       |
| end_time   | String  | 否    | 最后一次养护结束时间       |
| page_size  | Integer | 否    | 每页条数 空表示10条      |
| page_num   | Integer | 否    | 第几页 空表示第1页回复报文参数 |


#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明       |
| --------- | ---------- | ---- | -------- |
| page_num  | Integer    | 是    | 当前页      |
| page_size | Integer    | 是    | 每页的数量    |
| total     | Integer    | 是    | 总记录数     |
| pages     | Integer    | 是    | 总页数      |
| list      | ObjectList | 是    | 养护记录商品列表 |

养护记录商品列表

| 参数名                | 类型      | 说明          |
| ------------------ | ------- | ----------- |
| goods_intime       | String  | 购入日期        |
| goods_supplier     | String  | 供应商         |
| goods_id           | Long    | 商品ID        |
| goods_name         | String  | 商品名称        |
| goods_factory      | String  | 生产厂家        |
| goods_stoc_num     | Integer | 库存数量        |
| goods_unit         | String  | 库存单位        |
| goods_batch        | String  | 生产批号        |
| goods_validity     | String  | 有效期         |
| goods_registrno    | String  | 注册证号        |
| goods_main_count   | Integer | 养护次数        |
| goods_main_time    | String  | 最后一次养护日期    |
| goods_main_quality | String  | 最后一次外包装质量情况 |


##库存详情

### 库存详情商品列表

```http
[GET]/erp_service/stock_info/goods/list
```

####修改更新记录

| 对应业务   | 说明       |
| ------ | -------- |
| V1.3.3 | 库存详情商品列表 |

#### 请求报文参数

| 参数名               | 类型      | 必填   | 说明               |
| ----------------- | ------- | ---- | ---------------- |
| clas_id           | String  | 否    | 类别ID，不传为全部       |
| bran_id           | String  | 否    | 品牌ID，不传为全部       |
| vari_id           | String  | 否    | 品种ID，不传为全部       |
| depot_id          | String  | 否    | 仓库ID，不传为全部       |
| goods_factory_id  | String  | 否    | 生产厂家             |
| goods_supplier_id | String  | 否    | 供应商              |
| key               | String  | 否    | 商品编码或者商品名称       |
| page_size         | Integer | 否    | 每页条数 空表示10条      |
| page_num          | Integer | 否    | 第几页 空表示第1页回复报文参数 |


#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明       |
| --------- | ---------- | ---- | -------- |
| page_num  | Integer    | 是    | 当前页      |
| page_size | Integer    | 是    | 每页的数量    |
| total     | Integer    | 是    | 总记录数     |
| pages     | Integer    | 是    | 总页数      |
| list      | ObjectList | 是    | 库存详情商品列表 |

库存详情商品列表

| 参数名              | 类型     | 说明     |
| ---------------- | ------ | ------ |
| depot_name       | String | 仓库名称   |
| depot_id         | String | 仓库名称   |
| goods_id         | Long   | 商品ID   |
| goods_name       | String | 商品名称   |
| goods_factory_id | String | 生产厂家id |
| goods_factory    | String | 生产厂家   |
| goods_stoc_name  | String | 库存数量值  |
| goods_src_price  | double | 原售价    |

### 商品进销存详情列表

```http
[GET]/erp_service/stock_info/goods/changes
```

####修改更新记录

| 对应业务   | 说明                                       |
| ------ | ---------------------------------------- |
| V1.3.3 | 新增商品进销存详情列表<br />总行数和页码数为批号相关的信息值（batch_list） |

#### 请求报文参数

| 参数名             | 类型      | 必填   | 说明               |
| --------------- | ------- | ---- | ---------------- |
| goods_id        | Long    | 是    | 商品ID             |
| depot_id        | Long    | 是    | 仓库ID             |
| good_factory_id | Long    | 是    | 生产厂家id           |
| mode_id         | Integer | 否    | 业务ID             |
| start_time      | String  | 否    | 开始时间             |
| end_time        | String  | 否    | 结束时间             |
| key             | String  | 否    | 入库属性或者产品批号       |
| change_no       | String  | 否    | 单号               |
| page_size       | Integer | 否    | 每页条数 空表示10条      |
| page_num        | Integer | 否    | 第几页 空表示第1页回复报文参数 |


#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明        |
| --------- | ---------- | ---- | --------- |
| page_num  | Integer    | 是    | 当前页       |
| page_size | Integer    | 是    | 每页的数量     |
| total     | Integer    | 是    | 总记录数      |
| pages     | Integer    | 是    | 总页数       |
| list      | ObjectList | 是    | 商品进销存详情列表 |

商品进销存详情列表

| 参数名         | 类型         | 说明         |
| ----------- | ---------- | ---------- |
| change_time | String     | 日期         |
| change_no   | String     | 单号         |
| change_name | String     | 业务名称       |
| batch_list  | ObjectList | 产品批号相关信息列表 |

产品批号相关信息列表

| 参数名            | 类型     | 说明     |
| -------------- | ------ | ------ |
| goods_prop     | String | 商品入库属性 |
| goods_batch    | String | 商品批号   |
| goods_validity | String | 商品有效期  |
| change_num     | String | 变更数量   |
| goods_bidprice | double | 商品成本价  |
| goods_price    | double | 商品售价   |


### 进销存详情业务列表

```http
[GET]/erp_service/stock_info/goods/modes
```

包含 “全部业务”   0

####修改更新记录

| 对应业务   | 说明       |
| ------ | -------- |
| V1.3.3 | 新增养护记录列表 |

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


#### 回复报文参数

| 参数名       | 类型      | 说明   |
| --------- | ------- | ---- |
| mode_id   | Integer | 业务ID |
| mode_name | String  | 业务名称 |



### 新增成本调整记录

```http
[POST]/erp_service/stock_info/goods/adjustment
```

####修改更新记录

| 对应业务   | 说明       |
| ------ | -------- |
| V1.3.3 | 新增成本调整记录 |

#### 请求报文参数

| 参数名        | 类型         | 必填   | 说明   |
| ---------- | ---------- | ---- | ---- |
| goods_agen_id           | Long    | 是    | 运营机构id  1.3.8追加 |
| goods_agen_name     | String  | 是   | 运营机构名称    1.3.8追加|
| adju_goods | ObjectList | 是    | 商品列表 |

商品列表

| 参数名                | 类型      | 必填   | 说明     |
| ------------------ | ------- | ---- | ------ |
| goods_id           | Long    | 是    | 商品ID   |
| goods_src_bidprice | double  | 是    | 原进价    |
| goods_num          | Integer | 是    | 数量     |
| goods_bill_price   | double  | 是    | 开票进价   |
| goods_price        | double  | 是    | 现售价    |
| goods_supplyno     | String  | 否    | 供货单号   |
| goods_total        | double  | 是    | 进价差额总价 |
| goods_rem          | String  | 否    | 备注     |


#### 回复报文参数

| 参数名     | 类型   | 说明       |
| ------- | ---- | -------- |
| adju_id | Long | 成本调整记录ID |


### 成本调整记录列表

```http
[GET]/erp_service/stock_info/goods/adjustments
```

####修改更新记录

| 对应业务   | 说明       |
| ------ | -------- |
| V1.3.3 | 成本调整记录列表 |

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明               |
| ---------- | ------- | ---- | ---------------- |
| start_time | String  | 否    | 开始时间             |
| end_time   | String  | 否    | 结束时间             |
| adju_no    | String  | 否    | 单据编号             |
| page_size  | Integer | 否    | 每页条数 空表示10条      |
| page_num   | Integer | 否    | 第几页 空表示第1页回复报文参数 |


#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明       |
| --------- | ---------- | ---- | -------- |
| page_num  | Integer    | 是    | 当前页      |
| page_size | Integer    | 是    | 每页的数量    |
| total     | Integer    | 是    | 总记录数     |
| pages     | Integer    | 是    | 总页数      |
| list      | ObjectList | 是    | 成本调整记录列表 |

商品进销存详情列表

| 参数名            | 类型     | 说明    |
| -------------- | ------ | ----- |
| adju_id        | String | 记录ID  |
| adju_time      | String | 制单日期  |
| adju_no        | String | 单据编号  |
| adju_user_name | String | 制单人姓名 |

### 成本调整记录详情

```http
[GET]/erp_service/stock_info/goods/adjustment/{adju_id}
```

####修改更新记录

| 对应业务   | 说明       |
| ------ | -------- |
| V1.3.3 | 成本调整记录详情 |

#### 请求报文参数

####PathVariable
| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| adju_id | String | 是    | 成本调整ID |

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


#### 回复报文参数

| 参数名                | 类型         | 必填   | 说明                         |
| ------------------ | ---------- | ---- | -------------------------- |
| total_src_bidprice | double     | 是    | 原进价总价                      |
| total_src_price    | double     | 是    | 原售价总价                      |
| total_num          | Integer    | 是    | 数量总数                       |
| total_bill_price   | double     | 是    | 开票进价总价                     |
| total_price        | double     | 是    | 现售价总价                      |
| total              | double     | 是    | 进价差额总价                     |
| item_list          | ObjectList | 是    | 记录明细列表                     |
| adju_time          | String     | 是    | 调整时间                       |
| adju_user_name     | String     | 是    | 制单人姓名                      |
| adjustment_name    | String     | 是    | 商品成本调整单名称：#{租户名}+"商品成本调整单" |


成本调整记录明细列表

| 参数名                | 类型      | 说明    |
| ------------------ | ------- | ----- |
| item_id            | String  | 记录ID  |
| item_goods_id      | String  | 商品ID  |
| item_goods_name    | String  | 商品名称  |
| item_src_bidprice  | double  | 原进价   |
| item_src_price     | double  | 原售价   |
| item_num           | Integer | 数量    |
| item_bill_bidprice | double  | 开票进价  |
| item_price         | double  | 现售价   |
| item_supplyno      | String  | 供货单号  |
| item_rem           | String  | 备注    |
| item_total         | double  | 进价差额价 |

### 删除成本调整记录

```http
[DELETE]/erp_service/stock_info/goods/adjustment/{adju_id}
```

####修改更新记录

| 对应业务   | 说明       |
| ------ | -------- |
| V1.3.3 | 删除成本调整记录 |

#### 请求报文参数

####PathVariable
| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| adju_id | String | 是    | 成本调整ID |

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数

| 参数名  | 类型   | 说明   |
| ---- | ---- | ---- |
| 无    |      |      |


### 批次库存数量列表  

```http
[POST]/erp_service/batch_stock/list
```

####修改更新记录

| 对应版本 | 说明                          |
| -------- | ----------------------------- |
| V1.3.3   | 新增 根据批次和库存列表获取对应的正常品的库存数量 |

#### 请求报文参数ObjectList

| 参数名     | 类型    | 必填 | 说明                                    |
| ---------- | ------- | ---- | --------------------------------------- |
| batch_id  | String | 是 | 批次ID                     |
| depo_id   | String | 是  | 仓库ID                      |

#### 回复报文参数ObjectList

| 参数名     | 类型    | 必填 | 说明                                    |
| ---------- | ------- | ---- | --------------------------------------- |
| stoc_id | String | 是 | 库存ID |
| batch_id  | String | 是  | 批次ID                     |
| depo_id   | String | 是  | 仓库ID                      |
| stoc_num | Integer | 是 | 库存数量 |
| stoc_lock_num | Integer | 是 | 锁定数量 |
| stoc_avail_num | Integer | 是 | 可用数量 |

### 根据类别获取折扣权限

```http
[GET]/erp_service/discount/{clas_id}
```

####修改更新记录

| 对应版本 | 说明                          |
| -------- | ----------------------------- |
| V1.3.3.1   | 新增 根据类别获取折扣权限 |

#### PathVariable

| 参数名     | 类型    | 必填 | 说明                                    |
| ---------- | ------- | ---- | --------------------------------------- |
| clas_id | String | 是 | 类别ID |


#### 请求报文参数

| 参数名     | 类型    | 必填 | 说明                                    |
| ---------- | ------- | ---- | --------------------------------------- |
| 无  |  |  |                      |


#### 回复报文参数

| 参数名     | 类型    | 必填 | 说明                                    |
| ---------- | ------- | ---- | --------------------------------------- |
| disc_rate | Integer | 是 | 折扣值 |




