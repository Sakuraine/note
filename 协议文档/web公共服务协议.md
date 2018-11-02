# web公共协议

##基本信息

就是原web-restful
无法归到哪个服务的都扔这里
比如基础设置


##电子病历-诊断


### 标准诊断——新增诊断

> [POST]/sys_service/diag

#### 请求报文参数

| 参数名              | 类型         | 必填   | 说明              |
| ---------------- | ---------- | ---- | --------------- |
| diag_icd         | String     | 是    | 诊断ICD编码         |
| diag_attach      | String     | 否    | 附加码             |
| diag_name        | String     | 是    | 诊断名称            |
| diag_hospital_id | String     | 否    | 线下诊断ID,纯兼容温州眼视光 |
| alia_name_list   | ObjectList | 否    | 别名列表            |
| diag_enable      | Integer    | 是    | 是否有效 0：停用1：有效   |

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

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| diag_id | String | 是    | 诊断id |

#### 回复报文参数

| 参数名              | 类型         | 必填   | 说明              |
| ---------------- | ---------- | ---- | --------------- |
| diag_id          | String     | 是    | 诊断id            |
| diag_icd         | String     | 是    | 诊断ICD编码         |
| diag_attach      | String     | 否    | 附加码             |
| diag_name        | String     | 是    | 诊断名称            |
| diag_hospital_id | String     | 否    | 线下诊断ID,纯兼容温州眼视光 |
| alia_name_list   | ObjectList | 否    | 别名列表            |
| diag_enable      | Integer    | 是    | 是否有效 0：停用1：有效   |

别名列表说明

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| alia_id   | String | 是    | 别名id |
| alia_name | String | 是    | 别名   |

### 标准诊断——修改诊断

> [PUT]/sys_service/diag

#### 请求报文参数

| 参数名              | 类型         | 必填   | 说明              |
| ---------------- | ---------- | ---- | --------------- |
| diag_id          | String     | 是    | 诊断id            |
| diag_name        | String     | 是    | 诊断名称            |
| diag_attach      | String     | 否    | 附加码             |
| diag_hospital_id | String     | 否    | 线下诊断ID,纯兼容温州眼视光 |
| alia_name_list   | ObjectList | 是    | 别名列表            |
| diag_enable      | Integer    | 是    | 是否有效 0：停用1：有效   |

别名列表

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| alia_name | String | 是    | 别名   |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

##药品厂商管理

### 厂商列表  

> [GET]/drug_service/opto/fact/list

####修改更新记录

| 对应版本   | 说明             |
| ------ | -------------- |
| V1.3.1 | 修改 增加业务类型，兼容药品 |


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

| 参数名        | 类型      | 必填   | 说明                          |
| ---------- | ------- | ---- | --------------------------- |
| mfr_id     | String  | 是    | 厂商ID                        |
| mfr_code   | String  | 是    | 厂商编码                        |
| mfr_name   | String  | 是    | 厂商名称                        |
| mfr_type   | Integer | 是    | 厂商类型  1:供应商;2:生产商;3:供应商入生产商 |
| mfr_enable | Integer | 是    | 是否有效 0：停用1：有效               |




### 厂商——基本信息保存

新增

> [POST]/drug_service/opto/fact/base

####修改更新记录

| 对应版本   | 说明             |
| ------ | -------------- |
| V1.3.1 | 修改 增加业务类型，兼容药品 |

#### 请求报文参数

| 参数名                  | 类型      | 必填   | 说明                          |
| -------------------- | ------- | ---- | --------------------------- |
| mfr_code             | String  | 是    | 厂商编码                        |
| mfr_name             | String  | 是    | 厂商名称                        |
| mfr_type             | Integer | 是    | 厂商类型  1:供应商;2:生产商;3:供应商入生产商 |
| mfr_enable           | Integer | 是    | 是否有效 0：停用1：有效               |
| mfr_taxrate          | Integer | 否    | 税率                          |
| mfr_area_code        | String  | 否    | 地市区代码                       |
| mfr_compaddress      | String  | 否    | 公司详细地址                      |
| mfr_licence_code     | String  | 否    | 营业执照号                       |
| mfr_licence_validity | String  | 否    | 营业执照有效期                     |
| mfr_production       | String  | 否    | 生产许可证号                      |
| mfr_produ_validity   | String  | 否    | 生产许可证有效期                    |

#### 回复报文参数

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| mfr_id | String | 是    | 厂商ID |



### 厂商——基本信息修改

> [POST]/drug_service/opto/fact/base/update

####修改更新记录

| 对应版本   | 说明             |
| ------ | -------------- |
| V1.3.1 | 修改 增加业务类型，兼容药品 |

#### 请求报文参数

| 参数名                  | 类型      | 必填   | 说明                 |
| -------------------- | ------- | ---- | ------------------ |
| mfr_id               | String  | 是    | 厂商ID               |
| mfr_code             | String  | 是    | 厂商编码               |
| mfr_name             | String  | 是    | 厂商名称               |
| mfr_type             | Integer | 是    | 厂商类型  1:供应商;2:生产商; |
| mfr_enable           | Integer | 是    | 是否有效 0：停用1：有效      |
| mfr_taxrate          | Integer | 否    | 税率                 |
| mfr_area_code        | String  | 否    | 地市区代码              |
| mfr_compaddress      | String  | 否    | 公司详细地址             |
| mfr_licence_code     | String  | 否    | 营业执照号              |
| mfr_licence_validity | String  | 否    | 营业执照有效期            |
| mfr_production       | String  | 否    | 生产许可证号             |
| mfr_produ_validity   | String  | 否    | 生产许可证有效期           |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

### 厂商——开票信息修改

> [POST]/drug_service/opto/fact/tick/update

####修改更新记录

| 对应版本   | 说明             |
| ------ | -------------- |
| V1.3.1 | 修改 增加业务类型，兼容药品 |

#### 请求报文参数

| 参数名          | 类型     | 必填   | 说明   |
| ------------ | ------ | ---- | ---- |
| mfr_id       | String | 是    | 厂商ID |
| mfr_taxno    | String | 否    | 税号   |
| mfr_address  | String | 否    | 单位地址 |
| mfr_tel      | String | 否    | 公司电话 |
| mfr_bank     | String | 否    | 开户行  |
| mfr_bankcard | String | 否    | 账号   |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 厂商获取

> [GET]/drug_service/opto/fact

####修改更新记录

| 对应版本   | 说明      |
| ------ | ------- |
| V1.3.1 | 修改，兼容药品 |

#### 请求报文参数

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| mfr_id | String | 是    | 厂商ID |


#### 回复报文参数

| 参数名                  | 类型         | 必填   | 说明                 |
| -------------------- | ---------- | ---- | ------------------ |
| mfr_code             | String     | 是    | 厂商编码               |
| mfr_name             | String     | 是    | 厂商名称               |
| mfr_type             | Integer    | 是    | 厂商类型  1:供应商;2:生产商; |
| mfr_enable           | Integer    | 是    | 是否有效 0：停用1：有效      |
| mfr_taxrate          | Integer    | 否    | 税率 3 17 0          |
| mfr_prov_code        | String     | 否    | 省代码                |
| mfr_city_code        | String     | 否    | 市代码                |
| mfr_coun_code        | String     | 否    | 区代码                |
| mfr_compaddress      | String     | 否    | 公司详细地址             |
| mfr_licence_code     | String     | 否    | 营业执照号              |
| mfr_licence_validity | String     | 否    | 营业执照有效期            |
| mfr_production       | String     | 否    | 生产许可证号             |
| mfr_produ_validity   | String     | 否    | 生产许可证有效期           |
| mfr_taxno            | String     | 否    | 税号                 |
| mfr_address          | String     | 否    | 单位地址               |
| mfr_tel              | String     | 否    | 公司电话               |
| mfr_bank             | String     | 否    | 开户行                |
| mfr_bankcard         | String     | 否    | 账号                 |
| list                 | ObjectList | 否    | 联系人列表              |

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



### 厂商联系人保存

> [POST]/drug_service/opto/fact/cont_pers

####修改更新记录

| 对应版本   | 说明      |
| ------ | ------- |
| V1.3.1 | 修改，兼容药品 |

#### 请求报文参数

| 参数名            | 类型     | 必填   | 说明                  |
| -------------- | ------ | ---- | ------------------- |
| mfr_id         | String | 是    | 厂商ID                |
| link_man       | String | 是    | 联系人                 |
| link_area_code | String | 否    | 地址省市区代码             |
| link_address   | String | 否    | 详细地址                |
| link_tel       | String | 否    | 联系电话（联系电话或手机号码必留一个） |
| link_phone     | String | 否    | 手机号码（联系电话或手机号码必留一个） |
| link_fax       | String | 否    | 传真                  |
| link_email     | String | 否    | 邮箱                  |
| link_rem       | String | 否    | 备注                  |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明    |
| ------- | ------ | ---- | ----- |
| link_id | String | 是    | 联系人ID |


### 厂商联系人修改

> [POST]/drug_service/opto/fact/cont_pers/update

####修改更新记录

| 对应版本   | 说明      |
| ------ | ------- |
| V1.3.1 | 修改，兼容药品 |

#### 请求报文参数

| 参数名            | 类型     | 必填   | 说明                  |
| -------------- | ------ | ---- | ------------------- |
| link_id        | String | 是    | 联系人ID               |
| mfr_id         | String | 是    | 厂商ID                |
| link_man       | String | 是    | 联系人                 |
| link_area_code | String | 否    | 地址省市区代码             |
| link_address   | String | 否    | 详细地址                |
| link_tel       | String | 否    | 联系电话（联系电话或手机号码必留一个） |
| link_phone     | String | 否    | 手机号码（联系电话或手机号码必留一个） |
| link_fax       | String | 否    | 传真                  |
| link_email     | String | 否    | 邮箱                  |
| link_rem       | String | 否    | 备注                  |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |



### 厂商联系人删除

> [POST]/drug_service/opto/fact/cont_pers/delete

####修改更新记录

| 对应版本   | 说明      |
| ------ | ------- |
| V1.3.1 | 修改，兼容药品 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明    |
| ------- | ------ | ---- | ----- |
| link_id | String | 是    | 联系人ID |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

### 厂商联系人获取

> [GET]/drug_service/opto/fact/cont_pers

####修改更新记录

| 对应版本   | 说明      |
| ------ | ------- |
| V1.3.1 | 修改，兼容药品 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明    |
| ------- | ------ | ---- | ----- |
| link_id | String | 是    | 联系人ID |

#### 回复报文参数

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| link_id        | String | 是    | 联系人ID |
| link_man       | String | 是    | 联系人   |
| link_prov_code | String | 否    | 地址省代码 |
| link_city_code | String | 否    | 地址市代码 |
| link_coun_code | String | 否    | 地址区代码 |
| link_address   | String | 否    | 详细地址  |
| link_tel       | String | 否    | 联系电话  |
| link_phone     | String | 否    | 手机号码  |
| link_fax       | String | 否    | 传真    |
| link_email     | String | 否    | 邮箱    |
| link_rem       | String | 否    | 备注    |


### 模板数据预上传

```http
[POST]/template_data/initialize/pre_upload
```

说明：
  获取oss地址，文件名等信息

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| Web 1.3.4 | 新增   |


#### 请求报文参数

| 参数名            | 类型      | 必填   | 说明                                       |
| -------------- | ------- | ---- | ---------------------------------------- |
| file_size      | Long    | 否    | 文件内容长度                                   |
| file_extension | String  | 是    | 文件扩展名(不带“.“)                             |
| file_type      | String  | 是    | 文件类型，Content-Type                        |
| source_type    | Integer | 是    | 20:患者信息文件，16:药品目录文件，17:药品库存文件，18:商品目录文件，19:商品库存文件 |



#### 回复报文参数

| 参数名               | 类型     | 必填   | 说明                       |
| ----------------- | ------ | ---- | ------------------------ |
| url               | String | 是    | 文件上传的oss的URL             |
| file_id           | Long   | 是    | 文件资源id                   |
| OSS_access_key_id | String | 是    | Bucket 拥有者的Access Key Id |
| policy            | String | 是    | Base64编码的JSON内容          |
| signature         | String | 是    | 签名                       |
| key               | String | 是    | 上传文件路径                   |


### 模板数据文件 确认已上传

```http
[POST]/template_data/initialize/upload_access
```

说明：
  确认file_id对应的文件

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| Web 1.3.4 | 新增   |


#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明                                       |
| ----------- | ------- | ---- | ---------------------------------------- |
| file_id     | Long    | 是    | 文件资源id                                   |
| source_type | Integer | 是    | 20:患者信息文件，16:药品目录文件，17:药品库存文件，18:商品目录文件，19:商品库存文件 |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 上传完成之后发消息

患者信息文件     队列名称: PATI_INITIALIZE_DATA_IMPT     RedisDB: 13

药品目录文件     队列名称: DRUG_DIRECTORY_DATA_IMPT     RedisDB: 2

药品库存文件     队列名称: DRUG_STOCK_DATA_IMPT     RedisDB: 2

商品目录文件     队列名称: ERP_GOODS_DIRECTORY_IMPT     RedisDB: 10

商品库存文件     队列名称: ERP_GOODS_STOCK_IMPT     RedisDB: 10

涉及表：tena_initialize_import

消息队列的内容是:

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| impt_id | String | 是    | 导入记录ID |



### 模板数据导入记录

```http
[GET]/template_data/initialize/import/record
```


####修改更新记录

| 对应版本   | 说明             |
| ------ | -------------- |
| V1.3.4 | 新增 增加初始化数据导入记录 |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                                       |
| --------- | ------- | ---- | ---------------------------------------- |
| impt_type | Integer | 是    | 1-患者信息文件;2-药品目录文件;3-药品库存文件;4-商品目录文件;5-商品库存文件; |

#### 回复报文参数ObjectList

| 参数名              | 类型      | 必填   | 说明                                       |
| ---------------- | ------- | ---- | ---------------------------------------- |
| impt_id          | String  | 是    | 导入记录ID                                   |
| impt_time        | String  | 是    | 导入时间                                     |
| impt_success     | String  | 否    | 执行成功的内容文件名称                              |
| impt_success_id  | String  | 否    | 执行成功的内容文件ID                              |
| impt_success_url | String  | 否    | 执行成功的内容文件地址                              |
| impt_failure     | String  | 否    | 执行失败的内容文件名称                              |
| impt_failure_id  | String  | 否    | 执行失败的内容文件ID                              |
| impt_failure_url | String  | 否    | 执行失败的内容文件地址                              |
| impt_type        | Integer | 是    | 1-患者信息文件;2-药品目录文件;3-药品库存文件;4-商品目录文件;5-商品库存文件; |
| impt_status      | Integer | 是    | 导入状态 0:未处理;1:超时未上传;2:无效文件;3:已成功解析        |

### 添加模板数据配置

```http
[POST]/template_data/config
```


####修改更新记录

| 对应版本   | 说明               |
| ------ | ---------------- |
| V1.3.4 | 新增 增加初始化数据导入时的配置 |

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明                                       |
| ---------- | ------- | ---- | ---------------------------------------- |
| impt_type  | Integer | 是    | 1-患者信息文件;2-药品目录文件;3-药品库存文件;4-商品目录文件;5-商品库存文件; |
| conf_value | String  | 是    | 1-显示;2-不显示                               |

#### 回复报文参数ObjectList

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| conf_id | String | 是    | 配置ID |

### 获取模板数据配置

```http
[GET]/template_data/config/list
```


####修改更新记录

| 对应版本   | 说明                 |
| ------ | ------------------ |
| V1.3.4 | 新增 获取初始化数据导入时的配置列表 |

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数

| 参数名        | 类型      | 必填   | 说明                                       |
| ---------- | ------- | ---- | ---------------------------------------- |
| impt_type  | Integer | 是    | 1-患者信息文件;2-药品目录文件;3-药品库存文件;4-商品目录文件;5-商品库存文件; |
| conf_value | String  | 是    | 1-显示;2-不显示                               |

###患者条形码打印配置

```http
[GET]/tena_service/bar_code/print_config
```

####修改更新记录

| 对应版本     | 说明           |
| -------- | ------------ |
| V1.3.4.1 | 新增 患者条形码打印配置 |


#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数


| 参数名        | 类型     | 必填   | 说明       |
| ---------- | ------ | ---- | -------- |
| conf_value | String | 是    | 0不开启，1开启 |



###聊天图片预上传

```http
[POST]/common_service/msg/pre_upload
```

说明：
  获取oss地址，文件名等信息

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| Web 1.3.6 | 新增   |


#### 请求报文参数

| 参数名            | 类型      | 必填   | 说明                |
| -------------- | ------- | ---- | ----------------- |
| file_size      | Long    | 否    | 文件内容长度            |
| file_extension | String  | 是    | 文件扩展名(不带“.“)      |
| file_type      | String  | 是    | 文件类型，Content-Type |
| source_type    | Integer | 是    | 21 聊天图片           |


#### 回复报文参数

| 参数名               | 类型     | 必填   | 说明                       |
| ----------------- | ------ | ---- | ------------------------ |
| url               | String | 是    | 文件上传的oss的URL             |
| file_id           | Long   | 是    | 文件资源id                   |
| OSS_access_key_id | String | 是    | Bucket 拥有者的Access Key Id |
| policy            | String | 是    | Base64编码的JSON内容          |
| signature         | String | 是    | 签名                       |
| key               | String | 是    | 上传文件路径                   |


##微信资源位


### 获取微信资源位信息

```http
[GET]/tena_service/pati_service_info
```

> 涉及表pati_service_info，主键为header中的租户号

####修改更新记录

| 对应版本   | 说明   |
| ------ | ---- |
| V1.3.6 | 新增   |

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数

| 参数名         | 类型     | 必填   | 说明   |
| ----------- | ------ | ---- | ---- |
| appo_notice | String | 是    | 预约须知 |
| phone       | String | 是    | 客服热线 |


### 微信资源位修改

```http
[POST]/tena_service/pati_service_info
```

> 涉及表pati_service_info

####修改更新记录

| 对应版本   | 说明               |
| ------ | ---------------- |
| V1.3.6 | 新增  患者就诊人和患者信息关联 |

#### 请求报文参数

| 参数名         | 类型           | 必填   | 说明               |
| ----------- | ------------ | ---- | ---------------- |
| appo_notice | String(1000) | 是    | 预约须知             |
| phone       | String       | 是    | 客服热线             |
| type        | int          | 是    | 类型 1为预约须知 2为客服热线 |
#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



##基础设置-科室设置


### 获取科室列表信息

> [GET]/sys_service/depa/list

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

### 获取科室信息

> [GET]/sys_service/depa

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| depa_id | Long | 是    | 部门ID |

#### 回复报文参数

| 参数名                | 类型      | 必填   | 说明                                       |
| ------------------ | ------- | ---- | ---------------------------------------- |
| depa_id            | Long    | 是    | 部门ID                                     |
| depa_name          | String  | 是    | 部门名称                                     |
| depa_code          | String  | 是    | 部门编码                                     |
| depa_alias         | String  | 是    | 部门别名                                     |
| depa_pare_id       | Long    | 否    | 上级部门ID                                   |
| depa_pare_name     | Long    | 否    | 上级部门名称                                   |
| depa_address       | String  | 否    | 位置                                       |
| depa_clinical_type | Integer | 是    | 临床科室属性,1-临床；2-辅诊；3-护理单元；4-行政机关；5-其他;6-销售 |
| depa_flag          | Integer | 否    | 门诊/住院科室标志，1-门诊；2-住院                      |
| depa_enable        | Integer | 是    | 是否停用；0-停用；1-有效                           |

### 科室信息保存

> [POST]/sys_service/depa

#### 请求报文参数

| 参数名                | 类型      | 必填   | 说明                                       |
| ------------------ | ------- | ---- | ---------------------------------------- |
| depa_name          | String  | 是    | 部门名称                                     |
| depa_code          | String  | 是    | 部门编码                                     |
| depa_alias         | String  | 否    | 部门别名                                     |
| depa_pare_id       | Long    | 否    | 上级部门ID                                   |
| depa_address       | String  | 否    | 位置                                       |
| depa_clinical_type | Integer | 是    | 临床科室属性,1-临床；2-辅诊；3-护理单元；4-行政机关；5-其他;6-销售 |
| depa_flag          | Integer | 否    | 门诊/住院科室标志，1-门诊；2-住院                      |
| depa_enable        | Integer | 是    | 是否停用；0-停用；1-有效                           |

#### 回复报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| depa_id | Long | 是    | 部门ID |

### 科室信息修改

> [POST]/sys_service/depa/update

#### 请求报文参数

| 参数名                | 类型      | 必填   | 说明                                       |
| ------------------ | ------- | ---- | ---------------------------------------- |
| depa_id            | Long    | 是    | 部门ID                                     |
| depa_name          | String  | 是    | 部门名称                                     |
| depa_code          | String  | 是    | 部门编码                                     |
| depa_alias         | String  | 否    | 部门别名                                     |
| depa_pare_id       | Long    | 否    | 上级部门ID                                   |
| depa_address       | String  | 否    | 位置                                       |
| depa_clinical_type | Integer | 是    | 临床科室属性,1-临床；2-辅诊；3-护理单元；4-行政机关；5-其他;6-销售 |
| depa_flag          | Integer | 否    | 门诊/住院科室标志，1-门诊；2-住院                      |
| depa_enable        | Integer | 是    | 是否停用；0-停用；1-有效                           |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

### 科室信息删除

> [POST]/sys_service/depa/dele

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| depa_id | Long | 是    | 部门ID |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


##基础设置-标准诊断

### 标准诊断——诊断列表  

> [GET]/sys_service/diag/list

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

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| diag_id     | String  | 是    | 诊断id          |
| diag_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

### 标准诊断——前后缀列表  

> [GET]/sys_service/pref_suff/list

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


##基础设置-标准术士


### 新增标准术式

> [POST]/sys_service/oper

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

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| oper_id     | String  | 是    | id            |
| oper_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


##基础设置-过敏源



### 过敏源列表  

> [GET]/sys_service/alle/list

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

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| alle_id     | String  | 是    | id            |
| alle_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

### 微信获取租户有关参数设置

```http
[GET]sys_service/tenant/wx_parameter
```

####修改更新记录

| 对应版本     | 说明           |
| -------- | ------------ |
| V1.3.9.1 | 新增  微信获取租户有关参数设置 |

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |
#### 回复报文参数

| 参数名           | 类型   | 必填   | 说明                     |
| ------------- | ---- | ---- | ---------------------- |
| auto_show_fee | int  | 是    | 患者端预约挂号费用是否显示0-显示 1-隐藏 |



##基础设置-计量单位

### 计量单位列表  

> [GET]/sys_service/unit/list

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

#### 请求报文参数

| 参数名         | 类型      | 必填   | 说明            |
| ----------- | ------- | ---- | ------------- |
| unit_id     | String  | 是    | 计量单位id        |
| unit_enable | Integer | 是    | 是否有效 0：停用1：有效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

##基础设置-运营机构


### 通用运营机构列表

> [GET]/common_service/agency_list

#### 请求报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
|        |      |      |      |

#### 回复报文参数

|   参数名    |    类型    | 必填 |                  说明                  |
|-------------|------------|------|----------------------------------------|
| multiagency | Integer    | 是   | 多运营机构标;0-单运营机构;1-多运营机构 |
| list        | ObjectList | 是   | 运营机构列表说明                       |

运营机构列表说明

|   参数名   |   类型  | 必填 |      说明      |
|------------|---------|------|----------------|
| agen_id    | String  | 否   | 运营机构id     |
| agen_name  | String  | 是   | 运营机构名称   |
| have_sales | boolean | 是   | 是否有销售部门 |


### 运营机构列表

> [GET]/sys_service/agency/list

#### 请求报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
|        |      |      |      |

#### 回复报文参数

|   参数名   |   类型  | 必填 |      说明      |
|------------|---------|------|----------------|
| agen_id    | String  | 是   | 运营机构id     |
| agen_name  | String  | 是   | 运营机构名称   |
| have_sales | boolean | 是   | 是否有销售部门 |

### 获得一个运营机构

> [GET]/sys_service/agency

#### 请求报文参数

| 参数名  |  类型  | 必填 |    说明    |
|---------|--------|------|------------|
| agen_id | String | 是   | 运营机构id |

#### 回复报文参数

|   参数名    |   类型   | 必填 |             说明            |
|-------------|----------|------|-----------------------------|
| agen_id     | String   | 是   | 运营机构id                  |
| agen_name   | String   | 是   | 运营机构名称                |
| agen_enable | Integer  | 是   | 有效标志,默认:1;  0:否;1:是 |
| have_sales  | boolean  | 是   | 是否有销售部门              |
| list        | LongList | 否   | 销售部门列表                |


### 新增运营机构

> [POST]/sys_service/agency

#### 请求报文参数

|   参数名    |   类型   | 必填 |             说明            |
|-------------|----------|------|-----------------------------|
| agen_name   | String   | 是   | 运营机构名称                |
| agen_enable | Integer  | 是   | 有效标志,默认:1;  0:否;1:是 |
| have_sales  | boolean  | 是   | 是否有销售部门              |
| list        | LongList | 否   | 销售部门列表                |

#### 回复报文参数

| 参数名  |  类型  | 必填 |    说明    |
|---------|--------|------|------------|
| agen_id | String | 是   | 运营机构id |



### 修改运营机构

> [POST]/sys_service/agency/update

#### 请求报文参数

|   参数名    |   类型   | 必填 |             说明            |
|-------------|----------|------|-----------------------------|
| agen_id     | String   | 是   | 运营机构id                  |
| agen_name   | String   | 是   | 运营机构名称                |
| agen_enable | Integer  | 是   | 有效标志,默认:1;  0:否;1:是 |
| have_sales  | boolean  | 是   | 是否有销售部门              |
| list        | LongList | 否   | 销售部门列表                |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |





