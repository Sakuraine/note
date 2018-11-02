#ERP Web协议规范设计


##公用

### 商品品种列表

```http
[GET]/common_service/variety_list
```

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 返回中增加编码参数 |

#### 请求报文参数

|   参数名    |   类型  | 必填 |        说明        |
|-------------|---------|------|--------------------|
| key         | String  | 否   | 品种代码、品种名称 |
| goods_class | String  | 否   | 商品类别ID         |
| goods_brand | String  | 否   | 商品品种ID         |
| page_num    | Integer | 是   | 当前页             |
| page_size   | Integer | 是   | 每页的数量         |

#### 回复报文参数

|  参数名   |    类型    | 必填 |     说明     |
|-----------|------------|------|--------------|
| page_num  | Integer    | 是   | 当前页       |
| page_size | Integer    | 是   | 每页的数量   |
| total     | Integer    | 是   | 总记录数     |
| pages     | Integer    | 是   | 总页数       |
| list      | ObjectList | 否   | 商品品种列表 |

商品品种列表说明

|  参数名   |  类型  | 必填 |      说明      |
|-----------|--------|------|----------------|
| vari_id   | String | 是   | 内码及品种码ID |
| vari_code | String | 是   | 品种编码       |
| vari_name | String | 是   | 品种名称       |




##系统管理-商品属性

### 获取商品属性信息

> [GET]/sys_service/opto/good_prop

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 增加搜索关键字参数 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| prop_id | String | 是    | 属性ID |
| key | String | 否    | 搜索关键字 模糊匹配code或名称 |

#### 回复报文参数

| 参数名           | 类型         | 必填   | 说明                       |
| ------------- | ---------- | ---- | ------------------------ |
| prop_id       | String     | 是    | 属性ID                     |
| prop_name     | String     | 是    | 属性名称                     |
| prop_type     | Integer    | 是    | 自由录入：1-是;2-否             |
| prop_readonly | Integer    | 是    | 禁止修改标志,默认:0;  0-不禁止;1-禁止 |
| prop_flag | Integer    | 是    | 属性标志 0-普通属性; 1-球面; 2-柱面; 3-规格; 4-颜色;|
| list          | ObjectList | 否    | 参数列表                     |

参数列表结构

| 参数名           | 类型      | 必填   | 说明                     |
| ------------- | ------- | ---- | ---------------------- |
| choi_id       | String  | 是    | 参数ID                   |
| choi_prop_id  | String  | 是    | 属性ID                   |
| choi_code     | String  | 是    | 参数编码                   |
| choi_name     | String  | 是    | 参数名称                   |
| choi_enable   | Integer | 是    | 是否停用；0-停用；1-有效         |
| choi_readonly | Integer | 是    | 禁止修改标志,默认:0;0-不禁止;1-禁止 |



### 通过属性名称查询属性

```http
[GET]/sys_service/opto/good_prop/list
```

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.2 | 协议无修改 处方属性关联时用到该协议 |


#### 请求报文参数

|  参数名   |  类型  | 必填 |   说明   |
|-----------|--------|------|----------|
| prop_name | String | 否   | 属性名称 |

#### 回复报文参数(ObjectList)

|  参数名   |  类型  | 必填 |   说明   |
|-----------|--------|------|----------|
| prop_id   | String | 是   | 属性ID   |
| prop_name | String | 是   | 属性名称 |


### 通过跨度查询属性

```http
[GET]/sys_service/opto/good_prop/list_by_span
```

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.2 | 新增协议 根据开始结束跨度查询属性 |


#### 请求报文参数

|  参数名   |  类型  | 必填 |   说明   |
|-----------|--------|------|----------|
| prop_prop_id   | String | 是    | 属性码ID |
| begin_code    | String  | 是    | 开始编码           |
| end_code    | String  | 是    | 结束编码           |
| span_value    | String  | 是    | 跨度           |

#### 回复报文参数(ObjectList)

|  参数名   |  类型  | 必填 |   说明   |
|-----------|--------|------|----------|
| choi_id   | String | 是   | 候选项ID   |
| choi_name | String | 是   | 候选项名称 |




##系统管理-视光厂商

### 视光厂商——基本信息保存

> [POST]/sys_service/opto/fact/base


####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 增加营业执照 |


#### 请求报文参数

| 参数名                  | 类型      | 必填   | 说明                         |
| -------------------- | ------- | ---- | -------------------------- |
| mfr_code             | String  | 是    | 厂商编码                       |
| mfr_name             | String  | 是    | 厂商名称                       |
| mfr_type             | Integer | 是    | 厂商类型 1:供应商;2:生产商;3:供应商入生产商 |
| mfr_enable           | Integer | 是    | 是否有效 0：停用1：有效              |
| mfr_taxrate          | Integer | 否    | 税率                         |
| mfr_area_code        | String  | 否    | 地市区代码                      |
| mfr_compaddress      | String  | 否    | 公司详细地址                     |
| mfr_biz_licence_code     | String  | 否    | 工商营业执照号   |
| mfr_biz_licence_validity_str | String  | 否    | 工商营业执照有效期    |
| mfr_biz_licence_photo    | String  | 否    |工商营业执照照片，文件资源ID  |
| mfr_licence_code     | String     | 否    | 医疗器械经营许可证号  |
| mfr_licence_validity_str | String     | 否    | 医疗器械经营许可证有效期      |
| mfr_licence_photo    | String  | 否    |医疗器械经营许可证照片，文件资源ID  |
| mfr_production       | String     | 否    | 医疗器械生产许可证号 |
| mfr_produ_validity_str   | String     | 否    | 医疗器械生产许可证有效期    |
| mfr_produ_photo      | String  | 否    |医疗器械生产许可证证照片，文件资源ID     |

#### 回复报文参数

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| mfr_id | String | 是    | 厂商ID |



### 视光厂商——基本信息修改

> [POST]/sys_service/opto/fact/base/update


####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 增加营业执照 |

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
| mfr_biz_licence_code     | String  | 否    | 工商营业执照号   |
| mfr_biz_licence_validity_str | String  | 否    | 工商营业执照有效期    |
| mfr_biz_licence_photo    | String  | 否    |工商营业执照照片，文件资源ID  |
| mfr_licence_code     | String     | 否    | 医疗器械经营许可证号  |
| mfr_licence_validity_str | String     | 否    | 医疗器械经营许可证有效期      |
| mfr_licence_photo    | String  | 否    |医疗器械经营许可证照片，文件资源ID  |
| mfr_production       | String     | 否    | 医疗器械生产许可证号 |
| mfr_produ_validity_str | String     | 否    | 医疗器械生产许可证有效期    |
| mfr_produ_photo      | String  | 否    |医疗器械生产许可证证照片，文件资源ID     |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 视光厂商获取

> [GET]/sys_service/opto/fact

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 增加营业执照 |

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
| mfr_taxno            | String     | 否    | 税号                 |
| mfr_address          | String     | 否    | 单位地址               |
| mfr_tel              | String     | 否    | 公司电话               |
| mfr_bank             | String     | 否    | 开户行                |
| mfr_bankcard         | String     | 否    | 账号                 |
| mfr_biz_licence_code     | String  | 否    | 工商营业执照号   |
| mfr_biz_licence_validity_str | String  | 否    | 工商营业执照有效期    |
| mfr_biz_licence_photo    | String  | 否    |工商营业执照照片，文件资源ID  |
| mfr_biz_licence_photo_url | String  | 否    |工商营业执照照片url路径  |
| mfr_licence_code     | String     | 否    | 医疗器械经营许可证号  |
| mfr_licence_validity_str | String     | 否    | 医疗器械经营许可证有效期      |
| mfr_licence_photo    | String  | 否    |医疗器械经营许可证照片，文件资源ID  |
| mfr_licence_photo_url    | String  | 否    |医疗器械经营许可证照片url路径  |
| mfr_production       | String     | 否    | 医疗器械生产许可证号 |
| mfr_produ_validity_str | String     | 否    | 医疗器械生产许可证有效期    |
| mfr_produ_photo      | String  | 否    |医疗器械生产许可证证照片，文件资源ID     |
| mfr_produ_photo_url      | String  | 否    |医疗器械生产许可证证照片url路径|
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


##系统管理-视光商品


### 获取商品明细

```http
[GET]/opto_service/stock_manage/good
```

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
|V1.2.2.1 | 协议修改 返回中增加了品种编码 |


#### 请求报文参数

| 参数名  |  类型  | 必填 |  说明  |
|---------|--------|------|--------|
| good_id | String | 是   | 商品id |

#### 回复报文参数

|       参数名        |    类型    | 必填 |               说明              |      |
|---------------------|------------|------|---------------------------------|------|
| good_code           | String     | 是   | 商品编码                        |      |
| good_name           | String     | 是   | 商品名称                        |      |
| good_calss          | String     | 是   | 商品类别                        |      |
| good_brand          | String     | 是   | 商品品牌                        |      |
| good_variety        | String     | 否   | 商品品种                        |      |
| good_variety_code        | String     | 否   | 商品品种编码                        |      |
| good_factory        | String     | 是   | 生产厂商                        |      |
| good_supplier       | String     | 是   | 供应商                          |      |
| good_calss_id       | String     | 是   | 商品类别id                      |      |
| good_brand_id       | String     | 是   | 商品品牌id                      |      |
| good_variety_id     | String     | 否   | 商品品种id                      |      |
| good_factory_id     | String     | 是   | 生产厂商id                      |      |
| good_supplier_id    | String     | 是   | 供应商id                        |      |
| good_registrno      | String     | 否   | 注册证号                        |      |
| good_bidprice       | Double     | 否   | 参考成本价                      |      |
| good_price          | Double     | 否   | 售价                            |      |
| good_char_id        | String     | 否   | 收费类别ID                      |      |
| good_unitid         | String     | 否   | 单位id                          |      |
| good_unitname       | String     | 否   | 商品单位名称                    |      |
| good_give           | Integer    | 是   | 允许赠送,默认:0;0-不允许;1-允许 |      |
| status              | Integer    | 是   | 0-不在售;1-在售;停用2           |      |
| stock_list          | ObjectList | 否   | 入库属性列表                    |      |
| list                | ObjectList | 否   | 非入库属性列表                  |      |
| good_regis_validity | String     | 否   | 注册证有效期                    | 新增 |
| good_registr_img    | String     | 否   | 注册证号图片资源ID              | 新增 |
| good_registr_imgurl | String     | 否   | 注册证号图片资源URL地址         | 新增 |
| prop_rule           | String     | 否   | 入库属性拼接规则                | 新增 |


入库属性列表说明

|     参数名     |   类型  | 必填 |   说明   |
|----------------|---------|------|----------|
| prop_id        | Integer | 是   | 属性码ID |
| prop_prop_id   | String  | 是   | 属性码ID |
| prop_prop_name | String  | 是   | 属性名   |

非入库属性列表说明

|     参数名     |   类型  | 必填 |    说明    |
|----------------|---------|------|------------|
| prop_id        | Integer | 是   | 属性码ID   |
| prop_prop_id   | String  | 是   | 属性码ID   |
| prop_prop_name | String  | 是   | 属性名     |
| choi_id        | String  | 否   | 属性值ID   |
| choi_code      | String  | 否   | 属性值代码 |
| choi_value     | String  | 否   | 属性值内容 |

### 新增商品

> [POST]/opto_service/stock_manage/good

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
|V1.2.2.1 | 协议修改 收费类别改为非必填 |

#### 请求报文参数

| 参数名            | 类型         | 必填   | 说明                   |
| -------------- | ---------- | ---- | -------------------- |
| good_code      | String     | 是    | 商品编码                 |
| good_name      | String     | 是    | 商品名称                 |
| good_calss     | String     | 是    | 商品类别id               |
| good_brand     | String     | 是    | 商品品牌id               |
| good_variety   | String     | 否    | 商品品种id               |
| good_factory   | String     | 是    | 生产厂商id               |
| good_supplier  | String     | 是    | 供应商id                |
| good_registrno | String     | 否    | 注册证号                 |
| good_bidprice  | Double     | 否    | 参考成本价                |
| good_price     | Double     | 否    | 售价                   |
| good_char_id   | String     | 否    | 收费类别ID               |
| good_unitid    | String     | 否    | 单位id                 |
| good_unitname  | String     | 否    | 商品单位名称               |
| good_give      | Integer    | 是    | 允许赠送,默认:0;0-不允许;1-允许 |
| status         | Integer    | 是    | 0-不在售;1-在售;停用2       |
| stock_list     | ObjectList | 否    | 入库属性列表               |
| list           | ObjectList | 否    | 非入库属性列表              |

入库属性列表说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | String | 是    | 属性码ID |
| prop_prop_name | String | 是    | 属性码名称 |

非入库属性列表说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | String | 是    | 属性码ID |
| prop_prop_name | String | 是    | 每页的数量 |
| choi_id        | String | 否    | 属性值ID |
| choi_code      | String | 否    | 属性值代码 |
| choi_value     | String | 否    | 属性值内容 |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| good_id | String | 是    | 新增商品id |




### 修改商品

```http
[POST]/opto_service/stock_manage/good/update
```

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
|V1.2.2.1 | 协议修改 收费类别改为非必填 |

#### 请求报文参数

|       参数名        |    类型    | 必填 |               说明              |      |
|---------------------|------------|------|---------------------------------|------|
| good_id             | String     | 是   | 商品id                          |      |
| good_factory_id     | String     | 是   | 生产厂商id                      |      |
| good_supplier_id    | String     | 是   | 供应商id                        |      |
| good_registrno      | String     | 否   | 注册证号                        |      |
| good_unitid         | String     | 否   | 单位id                          |      |
| good_unitname       | String     | 否   | 商品单位名称                    |      |
| good_give           | Integer    | 是   | 允许赠送,默认:0;0-不允许;1-允许 |      |
| status              | Integer    | 是   | 0-不在售;1-在售;停用2           |      |
| stock_list          | ObjectList | 否   | 入库属性列表                    |      |
| list                | ObjectList | 是   | 属性属性                        |      |
| good_bidprice       | String     | 否   | 参考成本价                      |      |
| good_char_id        | String     | 否   | 收费类别ID       |
| good_regis_validity | String     | 否   | 注册证有效期                    | 新增 |
| good_registr_img    | String     | 否   | 注册证号图片资源ID              | 新增 |
| prop_rule           | String     | 否   | 入库属性拼接规则                | 新增 |

修改，添加注册证号，，，

入库属性列表说明

|     参数名     |  类型  | 必填 |   说明   |
|----------------|--------|------|----------|
| prop_prop_id   | Long   | 是   | 属性码ID |
| prop_prop_name | String | 是   | 属性名   |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |



### 批量新增商品

> [POST]/opto_service/stock_manage/good/batch

|  对应版本 | 说明 |
|-----------|------|
|V1.2.2.2 | 协议修改 功能优化 |

#### 请求报文参数

| 参数名            | 类型         | 必填   | 说明                   |
| -------------- | ---------- | ---- | -------------------- |
| good_code      | String     | 是    | 商品编码                 |
| good_name      | String     | 是    | 商品名称                 |
| good_class     | String     | 是    | 商品类别id               |
| good_brand     | String     | 是    | 商品品牌id               |
| good_variety   | String     | 否    | 商品品种id               |
| good_factory   | String     | 是    | 生产厂商id               |
| good_supplier  | String     | 是    | 供应商id                |
| good_registrno | String     | 否    | 注册证号                 |
| good_bidprice  | Double     | 否    | 参考成本价                |
| good_price     | Double     | 否    | 售价                   |
| good_char_id   | String     | 是    | 收费类别ID               |
| good_unitid    | String     | 否    | 单位id                 |
| good_unitname  | String     | 否    | 商品单位名称               |
| good_give      | Integer    | 是    | 允许赠送,默认:0;0-不允许;1-允许 |
| status         | Integer    | 是    | 0-不在售;1-在售;停用2       |
| good_regis_validity | String     | 否   | 注册证有效期             |  |
| good_registr_img    | String     | 否   | 注册证号图片资源ID          |  |
| stock_list     | ObjectList | 否    | 入库属性列表               |
| batch_list           | ObjectList | 否    | 非入库属性批量参数列表（第一层）  |

入库属性列表说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | String | 是    | 属性码ID |
| prop_prop_name | String | 是    | 属性码名称 |


非入库属性批量参数列表（第一层）说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | String | 是    | 属性码ID |
| choi_id   | String | 是    | 候选码ID |
| props_list        | ObjectList | 否    | 非入库属性批量参数列表（第二层）  |


非入库属性批量参数列表（第二层）说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | String | 是    | 属性码ID |
| choi_id   | String | 是    | 候选码ID |
| props_list        | ObjectList | 否    | 非入库属性批量参数列表（第三层）  |

非入库属性批量参数列表（第三层）说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | String | 是    | 属性码ID |
| choi_id   | String | 是    | 候选码ID |




#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| 无 |  |     |  |


##采购管理-定做查询


### 所有供应商-定做统计导出压缩文件

> [GET]/sale_service/query/custom_statistics/export

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| |  |

#### 请求报文参数

| 参数名        | 类型     | 必填   | 说明                    |
| ---------- | ------ | ---- | --------------------- |
| state      | String | 否    | 到货状态 0未到货 1已到货 不传表示全部 |
| start_time | String | 是    | 开始时间                  |
| end_time   | String | 是    | 结束时间                  |



#### 回复报文参数

| 参数名   | 类型   | 必填   | 说明   |
| ----- | ---- | ---- | ---- |
| zip文件 |      |      |      |


### 指定供应商-定做统计导出压缩文件

> [POST]/sale_service/query/custom_statistics/export

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 增加供应商列表 |

#### 请求报文参数

| 参数名        | 类型     | 必填   | 说明                    |
| ---------- | ------ | ---- | --------------------- |
| state      | String | 否    | 到货状态 0未到货 1已到货 不传表示全部 |
| supplier_list      | ObjectList | 是    | 供应商列表 |
| start_time | String | 是    | 开始时间                  |
| end_time   | String | 是    | 结束时间                  |

供应商列表说明

| 参数名        | 类型     | 必填   | 说明                    |
| ---------- | ------ | ---- | --------------------- |
| supplier      | String | 是    | 供应商id |



#### 回复报文参数

| 参数名   | 类型   | 必填   | 说明   |
| ----- | ---- | ---- | ---- |
| zip文件 |      |      |      |




##库存管理-商品退货


### 获取商品退货单

```http
[GET]/depo_service/retu
```

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
|  |  |

#### 请求报文参数

| 参数名  |  类型  | 必填 |  说明  |
|---------|--------|------|--------|
| retu_id | String | 是   | 退货ID |

#### 回复报文参数Object

|      参数名       |    类型    | 必填 |                         说明                        |      |
|-------------------|------------|------|-----------------------------------------------------|------|
| retu_id           | String     | 是   | 退货ID                                              |      |
| retu_no           | String     | 是   | 退货单号                                            |      |
| retu_mfr_id       | String     | 是   | 供应商ID                                            |      |
| retu_mfr_name     | String     | 是   | 供应商名称                                          |      |
| retu_make_user    | String     | 是   | 制单人                                              |      |
| retu_make_time    | String     | 是   | 制单时间                                            |      |
| retu_state        | Integer    | 是   | 状态,0-退货中;1-已作废;2-已退货;8-已冲红 空代表全部 |      |
| retu_depot        | String     | 是   | 出库仓库ID                                          |      |
| retu_depot_name   | String     | 是   | 出库仓库                                            |      |
| retu_rem          | String     | 否   | 备注                                                |      |
| list              | ObjectList | 否   | 商品列表                                            |      |
| goods_class_names | String     | 是   | 商品类别名称，逗号分隔                              |  |

商品列表说明

|        参数名         |    类型    | 必填 |            说明           |      |
|-----------------------|------------|------|---------------------------|------|
| item_id               | String     | 是   | 子表ID                    |      |
| item_goods_name       | String     | 是   | 商品名称                  |      |
| item_num              | Integer    | 是   | 退货数量                  |      |
| item_price            | Double     | 否   | 进价单价                  |      |
| item_return           | Double     | 否   | 退货单价                  |      |
| mfr_name              | String     | 是   | 生产商                    |      |
| batch_goods_registrno | String     | 否   | 注册证号                  |      |
| batch_id              | String     | 是   | 批次ID                    |      |
| batch_batchno         | String     | 否   | 生产批号                  |      |
| batch_validity        | String     | 否   | 有效期                    |      |
| stoc_waste            | Integer    | 是   | 废料标志 ;0-正常品;1-废料 |      |
| list                  | ObjectList | 否   | 入库属性列表              |      |
| produced_date         | String     | 否   | 生产日期                  | 新增 |
| prop_text             | String     | 否   | 拼接的属性内容            |  |
| goods_class           | String     | 是   | 商品类别                  | 新增 |
| goods_class_name      | String     | 是   | 商品类别名称              | 新增 |

属性列表说明

|     参数名     |   类型  | 必填 |                   说明                   |
|----------------|---------|------|------------------------------------------|
| prop_prop_id   | Integer | 是   | 属性码ID                                 |
| prop_prop_name | String  | 是   | 属性名                                   |
| prop_choi_id   | String  | 否   | 属性值ID                                 |
| prop_choi_code | String  | 否   | 属性值代码                               |
| prop_value     | String  | 否   | 属性值内容                               |
| prop_putinprop | Integer | 是   | 入库属性标志,默认0;  0:非入库;1:入库属性 |



###调拨出库、商品退货批量添加商品      

> [GET]/depo_service/allo/good/batch_list

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 增加库存量字段 |

#### 请求报文参数

| 参数名          | 类型     | 必填   | 说明   |
| ------------ | ------ | ---- | ---- |
| depo_id      | String | 是    | 仓库id |
| good_class   | String | 否    | 商品类别 |
| good_brand   | String | 否    | 商品品牌 |
| good_variety | String | 否    | 商品品种 |

#### 回复报文参数ObjectList

| 参数名                   | 类型         | 必填   | 说明               |
| --------------------- | ---------- | ---- | ---------------- |
| good_id               | String     | 是    | 商品ID             |
| good_name             | String     | 是    | 商品名称             |
| good_price            | Double     | 是    | 售价               |
| batch_batchno         | String     | 否    | 生产批号             |
| batch_id              | String     | 是    | 商品批次             |
| batch_price           | String     | 是    | 商品进价             |
| batch_validity        | String     | 否    | 有效期              |
| stoc_id               | String     | 是    | 库存ID             |
| item_num              | Integer    | 是   | 退货数量                  |
| stoc_num              | Integer    | 是   | 库存数量                  |
| stoc_waste            | Integer    | 是    | 废料标志 ;0-正常品;1-废料 |
| stoc_avail_num        | Integer    | 是    | 库存量              |
| batch_factory         | String     | 是    | 生产商              |
| batch_supplier        | Long       | 是    | 供应商ID            |
| batch_goods_registrno | String     | 否    | 注册证号             |
| prop_list             | ObjectList | 否    | 入库属性列表商品批次列表说明   |
| good_unitname      | String     | 是   | 计量单位    | 新增     |

属性列表说明

| 参数名            | 类型      | 必填   | 说明                        |
| -------------- | ------- | ---- | ------------------------- |
| prop_prop_id   | Integer | 是    | 属性码ID                     |
| prop_prop_name | String  | 是    | 属性名                       |
| choi_id        | String  | 否    | 属性值ID                     |
| choi_code      | String  | 否    | 属性值代码                     |
| choi_value     | String  | 否    | 属性值内容                     |
| prop_putinprop | Integer | 是    | 入库属性标志,默认0;  0:非入库;1:入库属性 |

##库存管理-库存报警


### 库存报警查看列表

> [GET]/depo_service/depot_warn/view_list

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 增加低于上限且高于下限 |
| V1.3.1.1 | 修改 增加对全院告警的支持 |

depo_id  为 0表示全院

#### 请求报文参数

| 参数名      | 类型      | 必填   | 说明                        |
| -------- | ------- | ---- | ------------------------- |
| depo_id  | String  | 否    | 仓库id                      |
| clas_id  | String  | 否    | 类别ID                      |
| bran_id  | String  | 否    | 品牌ID                      |
| vari_id  | String  | 否    | 品种码ID                     |
| key      | String  | 否    | 商品名称或代码                   |
| state    | Integer | 否    | 库存状态:1:低于 2：高于 3零库存 4低于上限且高于下限 空代表全部 |
| pagesize | Integer | 否    | 每页条数 空表示10条               |
| pagenum  | Integer | 否    | 第几页 空表示第1页回复报文参数          |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 当前页    |
| page_size | Integer    | 是    | 每页的数量  |
| total     | Integer    | 是    | 总记录数   |
| pages     | Integer    | 是    | 总页数    |
| list      | ObjectList | 是    | 库存报警列表 |

库存报警列表说明

| 参数名                   | 类型      | 必填   | 说明                    |
| --------------------- | ------- | ---- | --------------------- |
| warn_goods_id         | String  | 是    | 商品id                  |
| good_name             | String  | 是    | 商品名称                  |
| warn_upper            | Integer | 否    | 报警上限                  |
| warn_lower            | Integer | 否    | 报警下限                  |
| depot_stoc_num        | Integer | 是    | 仓库库存                  |
| depot_availa_num        | Integer | 是    | 可用仓库库存          （1.3.9.4追加）        |
| depot_lock_num        | Integer | 是    | 锁定仓库库存       （1.3.9.4追加）           |
| depot_stoc_warn_upper | Integer | 是    | 仓库库存上限超限标志,;0-正常;1-报警 |
| depot_stoc_warn_lower | Integer | 是    | 仓库库存下限超限标志;0-正常;1-报警  |
| all_stoc_num          | Integer | 是    | 总库存                   |
| all_stoc_warn_upper   | Integer | 是    | 总库存上限超限标志,;0-正常;1-报警  |
| all_stoc_warn_lower   | Integer | 是    | 总库存下限超限标志;0-正常;1-报警   |



### 库存报警设置列表

> [GET]/depo_service/depot_warn/list

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.3.1.1 | 修改 增加对全院告警的支持 |

depo_id  为 0表示全院

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明      |
| --------- | ------- | ---- | ------- |
| depo_id   | String  | 否    | 仓库id    |
| clas_id   | String  | 否    | 类别ID    |
| bran_id   | String  | 否    | 品牌ID    |
| vari_id   | String  | 否    | 品种码ID   |
| key       | String  | 否    | 商品名称或代码 |
| page_num  | Integer | 是    | 当前页     |
| page_size | Integer | 是    | 每页的数量   |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 当前页    |
| page_size | Integer    | 是    | 每页的数量  |
| total     | Integer    | 是    | 总记录数   |
| pages     | Integer    | 是    | 总页数    |
| list      | ObjectList | 是    | 库存报警列表 |

库存报警列表说明

| 参数名           | 类型      | 必填   | 说明   |
| ------------- | ------- | ---- | ---- |
| warn_id       | String  | 否    | 报警ID |
| warn_goods_id | String  | 是    | 商品id |
| good_name     | String  | 是    | 商品名称 |
| warn_upper    | Integer | 否    | 报警上限 |
| warn_lower    | Integer | 否    | 报警下限 |



### 新增商品库存报警 

> [POST]/depo_service/depot_warn

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.3.1.1 | 修改 增加对全院告警的支持 |

depo_id  为 0表示全院

#### 请求报文参数

| 参数名           | 类型      | 必填   | 说明   |
| ------------- | ------- | ---- | ---- |
| depo_id       | String  | 是    | 仓库id |
| warn_goods_id | String  | 是    | 商品id |
| warn_upper    | Integer | 否    | 报警上限 |
| warn_lower    | Integer | 否    | 报警下限 |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| warn_id | String | 否    | 报警ID |



### 修改商品库存报警 

> [POST]/depo_service/depot_warn/update

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.3.1.1 | 修改 增加对全院告警的支持 |

depo_id  为 0表示全院

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明   |
| ---------- | ------- | ---- | ---- |
| warn_id    | String  | 是    | 报警ID |
| warn_upper | Integer | 否    | 报警上限 |
| warn_lower | Integer | 否    | 报警下限 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |



### 批量设置库存报警

> [POST]/depo_service/depot_warn/batch_update

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.3.1.1 | 修改 增加对全院告警的支持 |

depo_id  为 0表示全院

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明    |
| ---------- | ------- | ---- | ----- |
| depo_id    | String  | 否    | 仓库id  |
| clas_id    | String  | 否    | 类别ID  |
| bran_id    | String  | 否    | 品牌ID  |
| vari_id    | String  | 否    | 品种码ID |
| warn_upper | Integer | 否    | 报警上限  |
| warn_lower | Integer | 否    | 报警下限  |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |




##库存管理-库存入库

### 获取入库单列表

```http
[GET]/opto_service/stock_manage/arrival_list
```

#### 请求报文参数

|    参数名     |    类型    | 必填 |                 说明                 |      |
|---------------|------------|------|--------------------------------------|------|
| depot_id      | String     | 是   | 入库仓库                             |      |
| begin         | String     | 是   | 开始时间                             |      |
| end           | String     | 是   | 结束时间                             |      |
| arri_supplier | String     | 否   | 供应商id                             |      |
| arri_state    | Integer    | 否   | 状态,默认:1-已入库;2-已冲红 空位全部 |      |
| goods_classs  | StringList | 否   | 以商品类别进行查询                   | 新增 |
| page_num      | Integer    | 是   | 当前页                               |      |
| page_size     | Integer    | 是   | 每页的数量                           |      |

#### 回复报文参数

|  参数名   |    类型    | 必填 |    说明    |
|-----------|------------|------|------------|
| page_num  | Integer    | 是   | 当前页     |
| page_size | Integer    | 是   | 每页的数量 |
| total     | Integer    | 是   | 总记录数   |
| pages     | Integer    | 是   | 总页数     |
| list      | ObjectList | 否   | 入库单列表 |

|    参数名    |   类型  | 必填 |                 说明                 |      |
|--------------|---------|------|--------------------------------------|------|
| arri_id      | String  | 是   | 出入库单ID                           |      |
| arri_no      | String  | 是   | 入库单号                             |      |
| mfr_name     | String  | 否   | 厂商名称                             |      |
| depo_name    | String  | 是   | 制单部门                             |      |
| user_name    | String  | 是   | 制单人                               |      |
| bill_time    | String  | 是   | 制单时间                             |      |
| arri_state   | Integer | 否   | 状态,默认:1-已入库;2-已冲红 空位全部 |      |
| goods_classs | String  | 是   | 商品类别，所逗号分隔                 | 新增 |




### 获取采购入库单明细

```http
[GET]/opto_service/stock_manage/arrival
```

#### 请求报文参数

| 参数名  |  类型  | 必填 |    说明    |
|---------|--------|------|------------|
| arri_id | String | 是   | 出入库单ID |


#### 回复报文参数

|      参数名       |    类型    | 必填 |                   说明                  |      |
|-------------------|------------|------|-----------------------------------------|------|
| arri_id           | String     | 是   | 出入库单ID                              |      |
| arri_no           | String     | 是   | 入库单号                                |      |
| mfr_id            | String     | 是   | 供应商id                                |      |
| depo_id           | String     | 是   | 仓库id                                  |      |
| mfr_name          | String     | 否   | 厂商名称                                |      |
| depo_name         | String     | 是   | 入库仓库                                |      |
| user_name         | String     | 是   | 制单人                                  |      |
| arri_time         | String     | 是   | 制单时间                                |      |
| arri_supplyno     | String     | 是   | 供货单号                                |      |
| arri_rem          | String     | 是   | 备注                                    |      |
| arri_state        | Integer    | 是   | 状态:0待入库；1已入库；2已冲红；9红字单 |      |
| arri_amount       | Integer    | 否   | 数量合计                                |      |
| arri_price        | Double     | 是   | 进价合计                                |      |
| arri_cesse        | Double     | 是   | 税额合计                                |      |
| item              | ObjectList | 是   | 出入库单子列表                          |      |
| goods_class_names | String     | 是   | 商品类别名称，以逗号分隔                | 新增 |

出入库单子表列表说明

|        参数名         |    类型    | 必填 |      说明      | 修改标志 |
|-----------------------|------------|------|----------------|----------|
| item_id               | String     | 是   | 出入库商品ID   |          |
| item_goods_name       | String     | 否   | 商品名称       |          |
| item_num              | Integer    | 是   | 入库数量       |          |
| batch_price           | Double     | 是   | 进价单价       |          |
| item_bidamount        | Double     | 是   | 进价合计       |          |
| item_taxrate          | Integer    | 否   | 税率           |          |
| item_cesse            | Double     | 否   | 税额           |          |
| batch_batchno         | String     | 否   | 商品批号       |          |
| batch_validity        | String     | 否   | 有效期         |          |
| batch_factory_name    | String     | 是   | 生产商         |          |
| batch_goods_registrno | String     | 否   | 注册证号       |          |
| list                  | ObjectList | 否   | 属性列表       |          |
| produced_date         | String     | 否   | 生产日期       | 新增     |
| prop_text             | String     | 否   | 拼接的属性内容 | 新增     |
| goods_class           | String     | 是   | 商品类别       | 新增     |
| goods_class_name      | String     | 是   | 商品类别名称   | 新增     |
| good_unitname      | String     | 是   | 计量单位    | 新增     |

属性列表说明

|     参数名     |   类型  | 必填 |    说明    |
|----------------|---------|------|------------|
| prop_id        | Integer | 是   | 属性码ID   |
| prop_prop_name | String  | 是   | 属性名     |
| prop_choi_id   | String  | 否   | 属性值ID   |
| prop_choi_code | String  | 否   | 属性值代码 |
| prop_value     | String  | 否   | 属性值内容 |


### 新增采购入库单

```http
[POST]/opto_service/stock_manage/arrival
```

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.2 | 修改 增加注册证号 |
| V1.3.1 | 修改 去除对入库属性的校验 |
| V1.3.5 | 修改 对于没有进阶权限的用户，可以不传进价，取商品的默认进价 |
| V1.3.6 | 修改 如果是定做入库，并且对应的有制镜单，并且本次入库后 |

基于两个原因：
销售单开商品时没有填的入库属性，不需要必填
批量入库时不需要检验入库属性


#### 请求报文参数

|    参数名     |    类型    | 必填 |      说明      |
|---------------|------------|------|----------------|
| mfr_id        | String     | 是   | 供应商id       |
| depo_id       | String     | 是   | 仓库id         |
| arri_supplyno | String     | 是   | 供货单号       |
| arri_rem      | String     | 是   | 备注           |
| arri_amount   | Integer    | 否   | 数量合计       |
| arri_price    | Double     | 是   | 进价合计       |
| arri_cesse    | Double     | 是   | 税额合计       |
| item          | ObjectList | 是   | 出入库单子列表 |

出入库单子列表说明

|        参数名         |    类型    | 必填 |         说明         | 修改标志 |
|-----------------------|------------|------|----------------------|----------|
| goods_id              | String     | 是   | 商品id               |          |
| item_num              | Integer    | 是   | 入库数量             |          |
| batch_price           | Double     | 是   | 进价单价             |          |
| item_bidamount        | Double     | 是   | 进价合计             |          |
| item_taxrate          | Integer    | 否   | 税率                 |          |
| item_cesse            | Double     | 否   | 税额                 |          |
| batch_batchno         | String     | 否   | 商品批号             |          |
| batch_validity        | String     | 否   | 有效期               |          |
| batch_goods_registrno | String     | 否   | 注册证号             |          |
| stat_id               | String     | 否   | 物资id（定做入库用） |          |
| list                  | ObjectList | 否   | 属性列表             |          |
| produced_date         | String     | 否   | 生产日期,yyyy-MM-dd  | 新增     |

属性列表说明

|     参数名     |   类型  | 必填 |                   说明                   |
|----------------|---------|------|------------------------------------------|
| prop_prop_id   | Integer | 是   | 属性码ID                                 |
| prop_prop_name | String  | 是   | 属性名                                   |
| choi_id        | String  | 否   | 属性值ID                                 |
| choi_code      | String  | 否   | 属性值代码                               |
| choi_value     | String  | 否   | 属性值内容                               |
| prop_putinprop | Integer | 是   | 入库属性标志,默认0;  0:非入库;1:入库属性 |

#### 回复报文参数

| 参数名  |  类型  | 必填 |    说明    |
|---------|--------|------|------------|
| arri_id | String | 是   | 出入库单ID |


##销售管理-视光销售


### 销售单列表

> [GET]/sale_service/sales_order/list

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.3.2 | 修改 为再开一单 |
| V1.3.9.2 | 修改 增加金额，销售备注，病历号 |
| V1.3.9.4 | 修改 订单状态|

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明                                    |
| ---------- | ------- | ---- | ------------------------------------- |
| key        | String  | 否    | 订单号、客户姓名、手机号码                         |
| pati_id        | String  | 否    | 患者id 刷卡查询时用该字段  |
| state      | Integer | 否    | 收费状态;1-待付款;2-已付款;3-已撤销;4-待退费;5-已退费 空为全部 |
| order_state    | Integer    | 否    |订单状态  0：待取件、1：已取件 2：部分取件，3：未到货、4：已到货 5：已退货 空全部（1.3.9.4追加） |
| sale_user_id      | String | 否    |销售员id  新增|
| start_time | String  | 是    | 开始时间                                  |
| end_time   | String  | 是    | 结束时间                                  |
| page_size  | Integer | 否    | 每页条数 空表示10条                           |
| page_num   | Integer | 否    | 第几页 空表示第1页                            |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 是    | 销售单列表 |

销售单列表说明

| 参数名            | 类型      | 必填   | 说明                               |
| -------------- | ------- | ---- | -------------------------------- |
| sale_id        | String  | 是    | 销售单id                            |
| sale_no        | String  | 是    | 订单号                              |
| sale_time      | String  | 是    | 订单时间                             |
| sale_real_price      | String  | 是    | 订单实际价格   （1.3.9.2追加）                 |
| order_state    | Integer    | 否    |订单状态  0：待取件、1：已取件 2：部分取件，3：未到货、4：已到货 5：已退货 （1.3.9.4追加） |
| sale_pati_id   | String  | 是    | 客户id                             |
| pait_name      | String  | 是    | 客户名称                             |
| pati_gender      | String  | 是    | 客户性别  性别代码 0 未知 1男  2 女                           |
| pati_age      | String  | 是    | 客户年龄                           |
| opto_id      | String  | 是    | 处方ID                             |
| opto_type    | Integer    | 是   | 处方类型包含：0 远视处方 1-近视处方、2-隐形眼镜处方、3-RGP处方、4-OK镜处方、9-其他处方 |      |
| sale_user_id   | String  | 是    | 制单人id                            |
| sale_user_name | String  | 是    | 制单人                              |
| sale_state     | Integer | 是    | 收费状态;1-待付款;2-已付款;3-已撤销;4-待退费;5-已退费 ;7-退费待申请 V1.3.8追加状态 7-退费待申请|


### 获得一个销售订单

```http
[GET]/sale_service/sales_order
```

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.3.2 | 修改 隐形眼镜处方数据有修改 去掉lens |
| V1.3.9.2 | 修改 增加病历号 |

#### 请求报文参数

| 参数名  |  类型  | 必填 |   说明   |
|---------|--------|------|----------|
| sale_id | String | 是   | 销售单id |

#### 回复报文参数

|     参数名      |    类型    | 必填 |                        说明                       |
|-----------------|------------|------|---------------------------------------------------|
| sale_id         | String     | 是   | 销售单id                                          |
| treatment       | Object     | 否   | 就诊信息                                          |
| opto_id         | String     | 否   | 处方id                                            |
| rgp             | Object     | 否   | rgp处方                                           |
| contactpres     | Object     | 否   | 隐形眼镜处方                                      |
| ok              | Object     | 否   | ok镜处方                                          |
| other           | Object     | 否   | 其他处方                                          |
| frame           | Object     | 否   | 框架眼镜处方                                      |
| sale_no         | String     | 是   | 订单号                                            |
| sale_time       | String     | 是   | 订单时间                                          |
| sale_user_id    | String     | 是   | 客户id                                            |
| sale_user_name  | String     | 是   | 客户名称                                          |
| sale_state      | Integer    | 是   | 状态;1-待付款;2-已付款;3-已撤销;4-待退费;5-已退费 |
| return_state      | Integer    | 是   | 是否申请退货状态;0-未申请;1-已申请|
| full            | Double     | 否   | 整单优惠满                                        |
| cat             | Double     | 否   | 整单优惠减                                        |
| sale_price      | Double     | 是   | 商品总额                                          |
| sale_favor      | Double     | 是   | 优惠                                              |
| sale_real_price | Double     | 是   | 实付款                                            |
| sale_rem        | String     | 是   | 备注                                              |
| sale_state_time       | String     | 是   | 状态变更时间                                          |
| sale_pay_time       | String     | 是   |  付款时间                                       |
| list            | ObjectList | 是   | 销售单细目列表                                    |

销售单细目说明

|       参数名        |    类型    | 必填 |                    说明                   |      |
|---------------------|------------|------|-------------------------------------------|------|
| item_id             | String     | 是   | 细目id                                    |      |
| item_goodsid        | String     | 是   | 商品id                                    |      |
| item_goods_name     | String     | 是   | 商品名称                                  |      |
| item_batchid        | String     | 是   | 批次id                                    |      |
| stoc_waste          | Integer    | 是   | 废料标志 ;0-正常品;1-废料                 |      |
| batch_no            | String     | 否   | 批号                                      |      |
| batch_validity      | String     | 否   | 有效期                                    |      |
| is_give             | Integer    | 是   | 赠送标志 0-非赠送;1-活动赠送;2-业务员赠送 |      |
| item_purchase       | Integer    | 是   | 定购标志 0-不定做;1-定做;                 |      |
| item_purc_prop      | String     | 否   | 定做属性                                  |      |
| item_purc_prop_list | ObjectList | 否   | 定做属性列表                              |      |
| item_size           | Integer    | 是   | 销售数量                                  |      |
| good_price          | Double     | 是   | 零售价                                    |      |
| good_total_price    | Double     | 是   | 小计                                      |      |
| depot_id            | String     | 是   | 仓库id                                    |      |
| depo_name           | String     | 是   | 出库位置                                  |      |
| list                | ObjectList | 否   | 优惠列表                                  |      |
| prop_list           | ObjectList | 否   | 属性列表                                  |      |
| produced_date       | String     | 否   | 生产日期                                  | 新增 |
| prop_text           | String     | 否   | 拼接的属性内容                            | 新增 |

就诊信息

|    参数名    |  类型  | 必填 |      说明      |
|--------------|--------|------|----------------|
| visit_time   | String | 否   | 接诊时间       |
| visit_depa   | String | 否   | 接诊科室或部门 |
| visit_doctor | String | 否   | 接诊医生       |
| finish_time  | String | 否   | 结束就诊时间   |

框架处方说明

|        参数名         |   类型  | 必填 |     说明    |
|-----------------------|---------|------|-------------|
| opto_far_pd           | Integer | 否   | 瞳距-远用   |
| opto_near_pd          | Integer | 否   | 瞳距-近用   |
| opto_od_pd            | Integer | 否   | 瞳距-单眼OD |
| opto_os_pd            | Integer | 否   | 瞳距-单眼OS |
| opto_od_ph            | Integer | 否   | 瞳高-OD     |
| opto_os_ph            | Integer | 否   | 瞳高-OS     |
| opto_far_od_sphere    | Double  | 否   | 远用OD-球镜 |
| opto_far_od_cylinder  | Double  | 否   | 远用OD-柱镜 |
| opto_far_od_axis      | Double  | 否   | 远用OD-轴向 |
| opto_far_od_prism     | Double  | 否   | 远用OD-棱镜 |
| opto_far_od_vision    | Double  | 否   | 远用OD-视力 |
| opto_far_od_memo      | String  | 否   | 远用OD-备注 |
| opto_far_os_sphere    | Double  | 否   | 远用OS-球镜 |
| opto_far_os_cylinder  | Double  | 否   | 远用OS-柱镜 |
| opto_far_os_axis      | Double  | 否   | 远用OS-轴向 |
| opto_far_os_prism     | Double  | 否   | 远用OS-棱镜 |
| opto_far_os_vision    | Double  | 否   | 远用OS-视力 |
| opto_far_os_memo      | String  | 否   | 远用OS-备注 |
| opto_near_od_sphere   | Double  | 否   | 近用OD-球镜 |
| opto_near_od_cylinder | Double  | 否   | 近用OD-柱镜 |
| opto_near_od_axis     | Double  | 否   | 近用OD-轴向 |
| opto_near_od_prism    | Double  | 否   | 近用OD-棱镜 |
| opto_near_od_vision   | Double  | 否   | 近用OD-视力 |
| opto_near_od_memo     | String  | 否   | 近用OD-备注 |
| opto_near_os_sphere   | Double  | 否   | 近用OS-球镜 |
| opto_near_os_cylinder | Double  | 否   | 近用OS-柱镜 |
| opto_near_os_axis     | Double  | 否   | 近用OS-轴向 |
| opto_near_os_prism    | Double  | 否   | 近用OS-棱镜 |
| opto_near_os_vision   | Double  | 否   | 近用OS-视力 |
| opto_near_os_memo     | String  | 否   | 近用OS-备注 |
| opto_data_add     | String  | 否   | 近附加 |

隐形眼镜处方说明

|        参数名         |  类型  | 必填 |       说明      |
|-----------------------|--------|------|-----------------|
| opto_od_sphere   | Double | 否   | 隐形眼镜OD-球镜 |
| opto_od_cylinder | Double | 否   | 隐形眼镜OD-柱镜 |
| opto_od_axis     | Double | 否   | 隐形眼镜OD-轴向 |
| opto_od_memo     | String | 否   | 隐形眼镜OD-备注 |
| opto_os_sphere   | Double | 否   | 隐形眼镜OS-球镜 |
| opto_os_cylinder | Double | 否   | 隐形眼镜OS-柱镜 |
| opto_os_axis     | Double | 否   | 隐形眼镜OS-轴向 |
| opto_os_memo     | String | 否   | 隐形眼镜OS-备注 |
| od_cliffy             | String | 否   | 右眼陡峭        |
| od_flat               | String | 否   | 右眼平坦        |
| od_axis               | String | 否   | 右眼轴向        |
| os_cliffy             | String | 否   | 左眼陡峭        |
| os_flat               | String | 否   | 左眼平坦        |
| os_axis               | String | 否   | 左眼轴向        |

rgp处方说明

|       参数名       |  类型  | 必填 |             说明            |
|--------------------|--------|------|-----------------------------|
| rgp_od_brand_id    | Long   | 否   | 右眼镜片品牌ID              |
| rgp_od_brand       | String | 否   | 右眼镜片品牌                |
| rgp_od_material_id | Long   | 否   | 右眼镜片材质ID              |
| rgp_od_material    | String | 否   | 右眼镜片材质                |
| rgp_od_curve       | Double | 否   | 右眼镜片基弧，单位：mm毫米  |
| rgp_od_diameter    | Double | 否   | 右眼镜片直径，单位：mm毫米  |
| rgp_od_degree      | Double | 否   | 右眼镜片度数，单位：D屈光度 |
| rgp_od_memo        | String | 否   | 右眼备注                    |
| rgp_os_brand_id    | Long   | 否   | 左眼镜片品牌ID              |
| rgp_os_brand       | String | 否   | 左眼镜片品牌                |
| rgp_os_material_id | Long   | 否   | 左眼镜片材质ID              |
| rgp_os_material    | String | 否   | 左眼镜片材质                |
| rgp_os_curve       | Double | 否   | 左眼镜片基弧，单位：mm毫米  |
| rgp_os_diameter    | Double | 否   | 左眼镜片直径，单位：mm毫米  |
| rgp_os_degree      | Double | 否   | 左眼镜片度数，单位：D屈光度 |
| rgp_os_memo        | String | 否   | 左眼备注                    |

其他处方列表说明

|     参数名      |  类型  | 必填 |      说明      |
|-----------------|--------|------|----------------|
| othe_id         | String | 是   | 其他处方处方id |
| othe_clas_id    | String | 是   | 类别id         |
| othe_clas_code  | String | 是   | 商品类别代码   |
| othe_goods_id   | String | 是   | 商品id         |
| othe_goods_name | String | 否   | 商品名称       |
| othe_count      | String | 是   | 数量           |
| othe_goods_unit | String | 否   | 单位           |
| othe_rem        | String | 否   | 备注           |

ok镜参数对象

|    参数名    |    类型    | 必填 |       说明       |
|--------------|------------|------|------------------|
| od_brand_id  | String     | 否   | 右眼品牌id       |
| od_brand     | String     | 否   | 右眼品牌         |
| od_para_list | ObjectList | 是   | 右眼品牌参数列表 |
| os_brand_id  | String     | 否   | 左眼品牌id       |
| os_brand     | String     | 否   | 左眼品牌         |
| os_para_list | ObjectList | 是   | 左眼品牌参数列表 |

定做属性跟入库属性说明

|     参数名     |  类型  | 必填 |    说明    |
|----------------|--------|------|------------|
| para_id        | String | 是   | 处方参数id |
| para_prop_id   | String | 是   | 属性id     |
| para_prop_name | String | 是   | 属性名称   |
| para_choi_id   | String | 否   | 属性值ID   |
| para_choi_code | String | 否   | 属性值代码 |
| para_value     | String | 否   | 属性值     |

优惠列表说明

|    参数名    |  类型  | 必填 |   说明   |
|--------------|--------|------|----------|
| favo_prom_id | String | 是   | 优惠id   |
| prom_memo    | String | 是   | 优惠说明 |

属性列表说明

|     参数名     |   类型  | 必填 |                   说明                   |
|----------------|---------|------|------------------------------------------|
| prop_prop_id   | Integer | 是   | 属性码ID                                 |
| prop_prop_name | String  | 是   | 属性名                                   |
| choi_id        | String  | 否   | 属性值ID                                 |
| choi_code      | String  | 否   | 属性值代码                               |
| choi_value     | String  | 否   | 属性值内容                               |
| prop_putinprop | Integer | 是   | 入库属性标志,默认0;  0:非入库;1:入库属性 |



### 销售非定做商品列表

```http
[GET]/sale_service/sale/good/list
```

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 增加是否设置收费类别标志 |
| V1.2.2.2 | 修改 增加品种过滤 |
| V1.3.9.2 | 修改 查询科室关联的销售仓库的商品 |


#### 请求报文参数

|   参数名   |   类型  | 必填 |         说明        |
|------------|---------|------|---------------------|
| good_class | String  | 否   | 商品类别            |
| good_brand | String  | 否   | 商品品牌            |
| good_variety | String  | 否    | 商品品种id      |
| key        | String  | 否   | 商品编码或名称      |
| batch_no   | String  | 否   | 生产批号            |
| page_size  | Integer | 否   | 每页条数 空表示10条 |
| page_num   | Integer | 否   | 第几页 空表示第1页  |

#### 回复报文参数Object

|  参数名   |    类型    | 必填 |             说明            |
|-----------|------------|------|-----------------------------|
| page_num  | Integer    | 是   | 当前页                      |
| page_size | Integer    | 是   | 每页的数量                  |
| total     | Integer    | 是   | 总记录数                    |
| pages     | Integer    | 是   | 总页数                      |
| is_hidden | Integer    | 是   | 是否隐藏过多按钮 0:否 1：是 |
| list      | ObjectList | 否   | 商品列表                    |

商品列表说明

|      参数名      |    类型    | 必填 |              说明              |      |
|------------------|------------|------|--------------------------------|------|
| good_id          | String     | 是   | 商品ID                         |      |
| good_class       | String     | 否   | 商品类别                       |      |
| good_brand       | String     | 否   | 商品品牌                       |      |
| good_variety     | String     | 否   | 商品品种                       |      |
| good_name        | String     | 是   | 商品名称                       |      |
| good_price       | Double     | 是   | 售价                           |      |
| clas_process     | Integer    | 是   | 是否可加工 0-不可加工;1-可加工 |      |
| batch_list       | ObjectList | 否   | 商品批次列表                   |      |
| goods_class_name | String     | 是   | 商品类别名称                   | 新增 |
| good_registrno  | String     | 否   | 注册证号                       | 新增 |
| has_char   | Integer  | 是    | 是否设置收费类别 0没有 1有             |

商品批次列表说明

|        参数名         |    类型    | 必填 |            说明           |      |
|-----------------------|------------|------|---------------------------|------|
| batch_batchno         | String     | 否   | 生产批号                  |      |
| batch_id              | String     | 是   | 商品批次                  |      |
| batch_validity        | String     | 否   | 有效期                    |      |
| stoc_waste            | Integer    | 是   | 废料标志 ;0-正常品;1-废料 |      |
| stoc_avail_num        | Integer    | 是   | 库存量                    |      |
| batch_factory         | String     | 是   | 生产商                    |      |
| batch_goods_registrno | String     | 否   | 注册证号                  |      |
| depot_id              | String     | 是   | 仓库id                    |      |
| depot_name            | String     | 是   | 出库仓库名称              |      |
| stock_list            | ObjectList | 否   | 入库属性列表              |      |
| produced_date         | String     | 否   | 生产日期                  | 新增 |
| prop_text             | String     | 否   | 拼接的属性内容            | 新增 |

属性列表说明

|     参数名     |   类型  | 必填 |                   说明                   |
|----------------|---------|------|------------------------------------------|
| prop_prop_id   | Integer | 是   | 属性码ID                                 |
| prop_prop_name | String  | 是   | 属性名                                   |
| choi_id        | String  | 否   | 属性值ID                                 |
| choi_code      | String  | 否   | 属性值代码                               |
| choi_value     | String  | 否   | 属性值内容                               |
| prop_putinprop | Integer | 是   | 入库属性标志,默认0;  0:非入库;1:入库属性 |




### 根据商品获取属性列表

> [GET]/opto_service/stock_manage/good_prop

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.2 | 修改 参数增加处方id,返回数据根据处方和属性关联，获得默认数据 |

#### 请求报文参数

| 参数名      | 类型     | 必填   | 说明   |
| -------- | ------ | ---- | ---- |
| goods_id | String | 是    | 商品id |
| opto_id | String | 是    | 处方id |
| show_rem | Integer | 否    | 0:不显示备注；1:显示备注 |

#### 回复报文参数ObjectList

| 参数名            | 类型      | 必填   | 说明                        |
| -------------- | ------- | ---- | ------------------------- |
| prop_prop_id   | Integer | 是    | 属性码ID                     |
| prop_prop_name | String  | 是    | 属性名                       |
| type           | Integer | 是    | 1：球镜 2：柱镜 3：其他            |
| choi_id | String | 否    | 属性值id 处方关联获得  |
| choi_value | String | 否    | 属性值内容 处方关联获得  |
| od_choi_id | String | 否    | od属性值id 处方关联获得  |
| od_choi_value | String | 否    | od属性值内容 处方关联获得  |
| os_choi_id | String | 否    | os属性值id 处方关联获得  |
| os_choi_value | String | 否    | os属性值内容 处方关联获得  |
| prop_prop_type| Integer | 是    | 1 自有输入 2 候选项            |
| prop_putinprop | Integer | 是    | 入库属性标志,默认0;  0:非入库;1:入库属性 |
| list           | Object  | 否    | 属性列表                      |

属性列表说明

| 参数名        | 类型     | 必填   | 说明    |
| ---------- | ------ | ---- | ----- |
| choi_id    | String | 否    | 属性值ID |
| choi_code  | String | 否    | 属性值代码 |
| choi_value | String | 否    | 属性值内容 |


注： 如果有choi_value而没有choi_id，说明匹配不到



### 根据患者查询处方列表

```http
[GET]/sale_service/patient/query_opto_list
```

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.3.5 | 修改 增加外来处方支持，增加导入数据支持 |


#### 请求报文参数

|  参数名   |   类型  | 必填 |                            说明                            |
|-----------|---------|------|------------------------------------------------------------|
| pati_id   | String  | 否   | 患者id                                                     |
| opto_flag | Integer | 否   | 处方时间 1：一月内 2：三月内 3：半年内 4：一年内  空为全部 |

#### 回复报文参数

|   参数名    |    类型    | 必填 |   说明   |
|-------------|------------|------|----------|
| trea_id     | String     | 否   | 就诊号   |
| opto_time   | String     | 否   | 就诊时间 |
| opto_doctor | String     | 否   | 验光医生 |
| list        | ObjectList | 否   | 处方就诊列表 |

处方就诊列表说明

|    参数名    |    类型    | 必填 |     说明     |      |
|--------------|------------|------|---------------------------|------|
| trea_id    | String    | 是   | 就诊ID |      |
| opto_doctor    | String    | 是   | 处方医生 |      |
| opto_time    | String    | 是   | 处方时间 |      |
| opto_doctor    | String    | 是   | 处方医生 |      |
| list        | ObjectList | 否   |  处方列表  |

处方列表说明

|    参数名    |    类型    | 必填 |                                          说明                                          |      |
|--------------|------------|------|---------------------------|------|
| opto_type    | Integer    | 是   | 处方类型包含：0 远视处方 1-近视处方、2-隐形眼镜处方、3-RGP处方、4-OK镜处方、9-其他处方 |      |
| opto_para    | String     | 否   | 其他处方字符串                                                                         |      |
| od           | String     | 否   | od参数                                                                                 |      |
| os           | String     | 否   | os参数                                                                                 |      |
| opto_far_pd  | String     | 否   | 瞳距远用                                                                               |      |
| opto_near_pd | String     | 否   | 瞳距近用                                                                               |      |
| opto_od_pd   | String     | 否   | 单眼od                                                                                 |      |
| opto_os_pd   | String     | 否   | 单眼os                                                                                 |      |
| opto_od_ph   | String     | 否   | 右眼瞳高                                                                               |      |
| opto_os_ph   | String     | 否   | 左眼瞳高                                                                               |      |
| data_add            | String | 否    | 近附加     |
| od_para_list     | ObjectList | 否   | OK镜，od属性列表                                                                       |  |
| os_para_list     | ObjectList | 否   | OK镜，os属性列表                                                                       |  |

属性列表说明

|     参数名     |   类型  | 必填 |    说明    |
|----------------|---------|------|------------|
| prop_id        | Integer | 是   | 属性ID     |
| prop_prop_id   | String  | 是   | 属性码ID   |
| prop_prop_name | String  | 是   | 属性名     |
| choi_id        | String  | 否   | 属性值ID   |
| choi_code      | String  | 否   | 属性值代码 |
| choi_value     | String  | 否   | 属性值内容 |



##商品列表



### 商品列表

> [GET]/opto_service/price/good/list

采购时商品列表，商品目录

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.2 | 修改 增加品种过滤 |


#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                   |
| ------------ | ------- | ---- | -------------------- |
| good_class   | String  | 否    | 商品类别                 |
| good_brand   | String  | 否    | 商品品牌                 |
| good_variety | String  | 否    | 商品品种id               |
| is_send      | Integer | 否    | 是否允许赠送 0-不允许;1-允许    |
| have_price   | Integer | 否    | 是否已有售价 0：否 1：是 全部则为空 |
| key          | String  | 否    | 商品编码或名称              |
| page_size    | Integer | 否    | 每页条数 空表示10条          |
| page_num     | Integer | 否    | 第几页 空表示第1页           |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 商品列表  |

商品列表说明

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
| good_class     | String | 是    | 商品分类id 新增的字段    |


### 采购入库定做商品列表

> [GET]/opto_service/stock_manage/custom_good/list

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.2 | 修改 增加品种过滤 |

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明          |
| ------------ | ------- | ---- | ----------- |
| depo_id      | String  | 是    | 当前仓库        |
| good_class   | String  | 否    | 商品类别        |
| good_brand   | String  | 否    | 商品品牌        |
| good_variety | String  | 否    | 商品品种id      |
| key          | String  | 否    | 商品编码或名称     |
| page_size    | Integer | 否    | 每页条数 空表示10条 |
| page_num     | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 商品列表  |

商品列表说明

| 参数名                | 类型         | 必填   | 说明          |
| ------------------ | ---------- | ---- | ----------- |
| good_id            | String     | 是    | 商品ID        |
| good_name          | String     | 是    | 商品名称        |
| good_code          | String     | 是    | 商品编码        |
| good_bidprice      | Double     | 是    | 商品进价        |
| good_price         | Double     | 是    | 原售价         |
| good_unit          | String     | 是    | 商品单位        |
| good_supplier      | String     | 是    | 商品供应商id     |
| good_supplier_name | String     | 是    | 商品供应商名称     |
| good_factory       | String     | 是    | 商品厂商id      |
| good_factory_name  | String     | 是    | 商品厂商名称      |
| good_registrno     | String     | 是    | 注册证号        |
| stat_id            | String     | 否    | 物资id（定做入库用） |
| stat_num           | Integer    | 是    | 数量          |
| sale_no            | String     | 是    | 订单号         |
| good_class     | String | 是    | 商品分类id 新增的字段    |
| good_props         | ObjectList | 否    | 定做属性列表      |

属性列表说明

| 参数名            | 类型      | 必填   | 说明                        |
| -------------- | ------- | ---- | ------------------------- |
| prop_prop_id   | Integer | 是    | 属性码ID                     |
| prop_prop_name | String  | 是    | 属性名                       |
| choi_id        | String  | 否    | 属性值ID                     |
| choi_code      | String  | 否    | 属性值代码                     |
| choi_value     | String  | 否    | 属性值内容                     |
| prop_putinprop | Integer | 是    | 入库属性标志,默认0;  0:非入库;1:入库属性 |

### 库存商品列表

> [GET]/depo_service/allo/good/list

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.2 | 修改 增加品种过滤 注册证号移至批次信息|

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明           |
| ---------- | ------- | ---- | ------------ |
| depo_id    | String  | 是    | 仓库id         |
| good_class | String  | 否    | 商品类别         |
| good_brand | String  | 否    | 商品品牌         |
| good_variety | String  | 否    | 商品品种id      |
| batch_no | String  | 否    | 生产批号/序列号      |
| key        | String  | 否    | 商品编码或名称或生产批号 |
| page_size  | Integer | 否    | 每页条数 空表示10条  |
| page_num   | Integer | 否    | 第几页 空表示第1页   |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明               |
| --------- | ---------- | ---- | ---------------- |
| page_num  | Integer    | 是    | 当前页              |
| page_size | Integer    | 是    | 每页的数量            |
| total     | Integer    | 是    | 总记录数             |
| pages     | Integer    | 是    | 总页数              |
| is_hidden | Integer    | 是    | 是否隐藏过多按钮 0:否 1：是 |
| list      | ObjectList | 否    | 商品列表             |

商品列表说明

| 参数名        | 类型         | 必填   | 说明     |
| ---------- | ---------- | ---- | ------ |
| good_id    | String     | 是    | 商品ID   |
| good_name  | String     | 是    | 商品名称   |
| good_price | Double     | 是    | 售价     |
| batch_goods_registrno | String  | 否    | 注册证号             |
| good_class     | String | 是    | 商品分类id 新增的字段    |
| batc_list  | ObjectList | 否    | 商品批次列表 |
| prop_list  | ObjectList | 否    | 入库属性列表 |

商品批次列表说明

| 参数名                   | 类型      | 必填   | 说明               |
| --------------------- | ------- | ---- | ---------------- |
| batch_batchno         | String  | 否    | 生产批号             |
| batch_id              | String  | 是    | 商品批次             |
| batch_price           | String  | 是    | 商品进价             |
| batch_validity        | String  | 否    | 有效期              |
| produced_date         | String     | 否   | 生产日期                  |
| batch_goods_registrno | String  | 否    | 注册证号             |
| stoc_id               | String  | 是    | 库存ID             |
| stoc_waste            | Integer | 是    | 废料标志 ;0-正常品;1-废料 |
| stoc_avail_num        | Integer | 是    | 库存量              |
| batch_factory         | String  | 是    | 生产商              |
| batch_supplier        | Long    | 是    | 供应商ID            |


属性列表说明

|     参数名     |   类型  | 必填 |                   说明                   |
|----------------|---------|------|------------------------------------------|
| prop_prop_id   | Integer | 是   | 属性码ID                                 |
| prop_prop_name | String  | 是   | 属性名                                   |
| choi_id        | String  | 否   | 属性值ID                                 |
| choi_code      | String  | 否   | 属性值代码                               |
| choi_value     | String  | 否   | 属性值内容                               |
| prop_putinprop | Integer | 是   | 入库属性标志,默认0;  0:非入库;1:入库属性 |



###  系统管理商品目录

```http
[GET]/opto_service/stock_manage/good_list
```

|  对应版本 | 说明 |
|-----------|------|
|V1.3.3 | 新增排序规则 |


#### 请求报文参数

| 参数名    | 类型    | 必填 | 说明                                       |
| --------- | ------- | ---- | ------------------------------------------ |
| clas_id   | String  | 否   | 商品类别id（全部为空）                     |
| bran_id   | String  | 否   | 内码及品牌                                 |
| key       | String  | 否   | 商品名称、商品编码、商品拼音码、商品五笔码 |
| type      | Integer | 否   | 0-不在售;1-在售;停用2;全部为空             |
| order     | Integer | 否   | 0或者不传按照名称排序，1:按照时间排序      |
| page_num  | Integer | 是   | 当前页                                     |
| page_size | Integer | 是   | 每页的数量                                 |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 商品列表  |
商品列表说明
| 参数名           | 类型      | 必填   | 说明                      |
| ------------- | ------- | ---- | ----------------------- |
| good_id       | String  | 是    | 内码及商品ID                 |
| good_code     | String  | 是    | 商品编码                    |
| good_name     | String  | 是    | 商品名称                    |
| good_unitname | String  | 否    | 商品单位名称                  |
| good_bidprice | Double  | 否    | 参考成本价                   |
| good_price    | Double  | 否    | 售价                      |
| status        | Integer | 是    | 商品状态0-不在售;1-在售;停用2;全部为空 |





##处方关联


### 处方属性关联获取

> [GET]/sys_service/opto_prop

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.2 | 增加 对应系统管理中的处方关联 |

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明           |
| ---------- | ------- | ---- | ------------ |
| 无    |   |     |          |


#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明               |
| --------- | ---------- | ---- | ---------------- |
| far_list  | ObjectList    | 是    | 远用处方参数列表              |
| near_list  | ObjectList    | 是    | 近用处方参数列表              |
| contact_list  | ObjectList    | 是    | 隐形处方参数列表              |
| rgp_list  | ObjectList    | 是    | rgp处方参数列表              |

各个参数列表结构一样，说明如下

| 参数名       | 类型         | 必填   | 说明               |
| --------- | ---------- | ---- | ---------------- |
| optoprop_name  | String    | 是    | 参数名称 比如 “球镜”              |
| optoprop_type  | Integer    | 是    | 视光处方参数类型              |
| goodsprop_id  | String    | 否    | 商品属性ID              |
| goodsprop_name  | String    | 否    | 	商品属性名称              |


### 处方属性关联保存

> [POST]/sys_service/opto_prop

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.2 | 增加 对应系统管理中的处方关联 |

#### 请求报文参数

| 参数名       | 类型         | 必填   | 说明               |
| --------- | ---------- | ---- | ---------------- |
| far_list  | ObjectList    | 是    | 远用处方参数列表              |
| near_list  | ObjectList    | 是    | 近用处方参数列表              |
| contact_list  | ObjectList    | 是    | 隐形处方参数列表              |
| rgp_list  | ObjectList    | 是    | rgp处方参数列表              |

各个参数列表结构一样，说明如下

| 参数名       | 类型         | 必填   | 说明               |
| --------- | ---------- | ---- | ---------------- |
| optoprop_type  | Integer    | 是    | 视光处方参数类型              |
| goodsprop_id  | String    | 是    | 商品属性ID              |



#### 回复报文参数ObjectList

| 参数名        | 类型      | 必填   | 说明           |
| ---------- | ------- | ---- | ------------ |
| 无    |   |     |          |


### 制镜加工单详情

> [GET]/process_service/glass

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明    |
| ------- | ------ | ---- | ----- |
| proc_id | String | 是    | 制镜单id |

#### 回复报文参数

| 参数名         | 类型         | 必填   | 说明                                       |
| ----------- | ---------- | ---- | ---------------------------------------- |
| proc_id     | String     | 是    | 制镜单id                                    |
| proc_no     | String     | 是    | 加工单号                                     |
| sale_no     | String     | 是    | 销售单号                                     |
| proc_flag   | Integer    | 是    | 加工标志;0-内加工;1-外加工                         |
| proc_state  | Integer    | 是    | 状态:0-待受理; 1-已受理;2-待磨镜;3-待检测;4-待签收;5-待取件;6-已取件（完成） |
| opto_id     | String     | 否    | 处方id                                     |
| bracket_type    | Integer    | 否    | 框架类型  0：全框架、1：半框架、2：无框架、3：拉丝框、4：渐变镜、5：高档框 空的时候，整个显示模板隐藏掉（1.3.9.4追加）|
| machining_name    | String    | 否    |磨镜人 外加工 磨镜人不显示 （1.3.9.4追加） |
| machining_time    | String    | 否    |磨镜时间 外加工 磨镜时间不显示 （1.3.9.4追加） |
| test_name    | String    | 否    |检测人 （1.3.9.4追加） |
| test_time    | String    | 否    |检测时间 （1.3.9.4追加） |
| rgp         | Object     | 否    | rgp处方                                    |
| contactpres | Object     | 否    | 隐形眼镜处方                                   |
| ok          | Object     | 否    | ok镜处方                                    |
| other       | Object     | 否    | 其他处方                                     |
| frame       | Object     | 否    | 框架眼镜处方                                   |
| pati_id     | String     | 是    | 患者id                                     |
| rem     | String     | 否    | 销售单备注      （1.3.9.4追加）                               |
| opto_doctor | String     | 否    | 接诊医生                                     |
| opto_time   | String     | 否    | 接诊时间                                     |
| is_return   | Integer    | 是    | 退货标志 0:正常 1已申请退货                         |
| has_bad     | Integer    | 是    | 是否有坏品 0:无 1有                             |
| list        | ObjectList | 是    | 制镜物品列表                                   |

制镜物品列表说明

| 参数名             | 类型         | 必填   | 说明                                       |
| --------------- | ---------- | ---- | ---------------------------------------- |
| item_id         | String     | 是    | 制镜物品细目id                                 |
| item_goods_id   | String     | 是    | 商品id                                     |
| item_goods_name | String     | 是    | 商品名称                                     |
| item_batchid    | String     | 否    | 批次id                                     |
| stoc_waste      | Integer    | 是    | 废料标志 ;0-正常品;1-废料                         |
| batch_no        | String     | 否    | 批号                                       |
| batch_validity  | String     | 否    | 有效期                                      |
| item_size       | Integer    | 是    | 销售数量                                     |
| proc_state      | Integer    | 否    | 加工状态,默认:0;0-正常;1-报损                      |
| goods_state     | Integer    | 否    | 取件状态,默认:0;0-未领用;2-已领用;3-报损中;4-待退货 ;5-已回收; |
| depot_id        | String     | 是    | 出库仓库id                                   |
| depot_name      | String     | 是    | 出库仓库名称                                   |
| purc_prop_list  | ObjectList | 否    | 定做属性                                     |
| prop_list       | ObjectList | 否    | 属性列表                                     |

定做属性跟属性列表说明

| 参数名            | 类型      | 必填   | 说明                        |
| -------------- | ------- | ---- | ------------------------- |
| prop_prop_id   | Integer | 是    | 属性码ID                     |
| prop_prop_name | String  | 是    | 属性名                       |
| choi_id        | String  | 否    | 属性值ID                     |
| choi_code      | String  | 否    | 属性值代码                     |
| choi_value     | String  | 否    | 属性值内容                     |
| prop_putinprop | Integer | 是    | 入库属性标志,默认0;  0:非入库;1:入库属性 |



### 制镜加工单列表

> [GET]/process_service/glass/list

|  对应版本 | 说明 |
|-----------|------|
| hotfix/V1.2.3.3.01 | 增加请求参数pati_id |

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明                                       |
| ---------- | ------- | ---- | ---------------------------------------- |
| key        | String  | 否    | 订单号、客户姓名、手机号码                            |
| pati_id    | String  | 否    | 患者id                            		|
| proc_state | Integer | 否    | 状态:0-待受理; 1-已受理;2-待磨镜;3-待检测;4-待签收;5-待取件;6-已取件（完成）; 空为全部 |
| start_time | String  | 是    | 开始时间                                     |
| end_time   | String  | 是    | 结束时间                                     |
| page_size  | Integer | 否    | 每页条数 空表示10条                              |
| page_num   | Integer | 否    | 第几页 空表示第1页                               |

#### 回复报文参数

| 参数名        | 类型      | 必填   | 说明                                       |
| ---------- | ------- | ---- | ---------------------------------------- |
| proc_id    | String  | 是    | 制镜单id                                    |
| proc_no    | String  | 是    | 制镜单号                                     |
| sale_no    | String  | 是    | 销售单号                                     |
| pay_time   | String  | 是    | 付费时间                                     |
| proc_state | Integer | 是    | 状态:0-待受理; 1-已受理;2-待磨镜;3-待检测;4-待签收;5-待取件;6-已取件（完成） |
| pati_id    | String  | 是    | 患者id                                     |
| pati_name  | String  | 是    | 客户姓名                                     |


##销售提货


### 库存商品销售提货单列表

```http
[GET]/depo_service/pick/stock_pick/list
```


注意：为了支持页面指针
[增加页面指针，销售提货界面，在第4页批量取件后，页面自动会跳转到第1页，批量取件后停留在当前页面，不跳转。若最后一页取件完，就跳到前一页]

后端只需实现“大页码转小页”码机制
比如，前端获取 第5页数据，后端发现总共只有3页数据，则返回第3页数据，并且告诉前端这是第3页

#### 修改更新记录

| 对应版本     | 说明         |
| -------- | ---------- |
| V1.3.3 | 新增   |


#### 请求报文参数

|    参数名     |   类型  | 必填 |                说明               |
|---------------|---------|------|-----------------------------------|
| start_date    | String  | 否   | 开始日期                          |
| end_date      | String  | 否   | 结束日期                          |
| key           | String  | 否   | 订单号/商品名称/客户姓名/手机号码 |
| stat_pickup   | Integer | 否   | 取件状态：0-未取件，1-已取件      |
| stat_depo_id  | Long    | 是   | 仓库ID                            |
| page_size     | Integer | 否   | 每页条数 空表示10条               |
| page_num      | Integer | 否   | 第几页 空表示第1页                |

#### 回复报文参数Object

|  参数名   |    类型    | 必填 |       说明       |
|-----------|------------|------|------------------|
| page_num  | Integer    | 是   | 当前页           |
| page_size | Integer    | 是   | 每页的数量       |
| total     | Integer    | 是   | 总记录数         |
| pages     | Integer    | 是   | 总页数           |
| list      | ObjectList | 否   | 销售提货商品列表 |

销售提货商品说明

|     参数名      |    类型    | 必填 |            说明           |      |
|-----------------|------------|------|---------------------------|------|
| sale_id         | String     | 是   | 销售订单ID                    |      |
| trad_time       | String     | 是   | 收费日期                  |      |
| sale_no         | String     | 是   | 订单号                    |      |
| sale_user_name  | String     | 是   | 制单人                    |      |
| sale_real_price  | String     | 是   | 订单金额         （1.3.9.4追加）           |      |
| trad_payuser    | String     | 是   | 客户姓名                  |      |
| user_phone    | String     | 是   | 客户手机号码            |      |
| item_size       | Integer    | 是   | 总量    |      |



### 库存商品提货销售单详情

> [GET]/depo_service/pick/stock_pick/sale_detail

列出该销售单下的物资列表

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明          |
| ------------ | ------- | ---- | ----------- |
| sale_id         | String     | 是   | 销售订单ID                    |
| stat_depo_id | String     | 是   | 仓库柜台id                    |
| stat_pickup   | Integer | 否   | 取件状态：0-未取件，1-已取件      |

#### 回复报文参数Object

|     参数名      |    类型    | 必填 |            说明           |      |
|-----------------|------------|------|---------------------------|------|
| stat_id         | String     | 是   | 销售物资状态表ID          |      |
| item_goods_id   | String     | 是   | 商品id                    |      |
| item_goods_name | String     | 是   | 商品名称                  |      |
| item_size       | Integer    | 是   | 数量    |      |
| is_pickup       | Integer    | 是   | 是否已取件 ;0-否;1-是   |      |
| batch_id         | String  | 是    | 商品批次ID           |
| can_fetch       | Integer    | 否   | 是否能取件 ;0-不能;1-能   |      |
| produced_date   | String     | 否   | 生产日期                  | 新增 |
| prop_text       | String     | 否   | 拼接的属性内容            | 新增 |
| list            | ObjectList | 否   | 库存入库属性列表          |      |
| purc_prop_list  | ObjectList | 否   | 定做入库属性列表          |      |

库存入库属性列表跟定做入库属性列表说明

|     参数名     |   类型  | 必填 |                   说明                   |
|----------------|---------|------|------------------------------------------|
| prop_prop_id   | Integer | 是   | 属性码ID                                 |
| prop_prop_name | String  | 是   | 属性名                                   |
| choi_id        | String  | 否   | 属性值ID                                 |
| choi_code      | String  | 否   | 属性值代码                               |
| choi_value     | String  | 否   | 属性值内容                               |
| prop_putinprop | Integer | 是   | 入库属性标志,默认0;  0:非入库;1:入库属性 |


### 库存商品按销售单批量取件  

> [POST]/depo_service/pick/stock_pick/sale_batch_fetch


#### 请求报文参数ObjectList

| 参数名  | 类型         | 必填   | 说明     |
| ---- | ---------- | ---- | ------ |
| sale_id         | String     | 是   | 销售订单ID                    |      |
| depo_id         | String     | 是   | 仓库柜台id                    |      |


#### 回复报文参数Object

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|   无   |      |      |      |


### 库存商品销售单全部取件  

> [POST]/depo_service/pick/stock_pick/sale_fetch_all


#### 请求报文参数

| 参数名  | 类型         | 必填   | 说明     |
| ---- | ---------- | ---- | ------ |
| sale_id         | String     | 是   | 销售订单ID                    |      |
| depo_id         | String     | 是   | 仓库柜台id                    |      |

#### 回复报文参数Object

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|   无   |      |      |      |



### 销售（定做）提货单列表

```http
[GET]/depo_service/pick/list
```

#### 修改更新记录

| 对应版本     | 说明         |
| -------- | ---------- |
| V1.3.3 | 修改 由原来的“销售提货单列表” 变为 定做商品的提货单列表 去掉定做条件 |

#### 请求报文参数

|    参数名     |   类型  | 必填 |                说明               |
|---------------|---------|------|-----------------------------------|
| start_date    | String  | 否   | 开始日期                          |
| end_date      | String  | 否   | 结束日期                          |
| key           | String  | 否   | 订单号/商品名称/客户姓名/手机号码 |
| stat_pickup   | Integer | 否   | 取件状态：0-未取件，1-已取件      |
| stat_depo_id  | Long    | 是   | 仓库ID                            |
| page_size     | Integer | 否   | 每页条数 空表示10条               |
| page_num      | Integer | 否   | 第几页 空表示第1页                |

#### 回复报文参数Object

|  参数名   |    类型    | 必填 |       说明       |
|-----------|------------|------|------------------|
| page_num  | Integer    | 是   | 当前页           |
| page_size | Integer    | 是   | 每页的数量       |
| total     | Integer    | 是   | 总记录数         |
| pages     | Integer    | 是   | 总页数           |
| list      | ObjectList | 否   | 销售提货商品列表 |

销售提货商品说明

|     参数名      |    类型    | 必填 |            说明           |      |
|-----------------|------------|------|---------------------------|------|
| stat_id         | String     | 是   | 销售物资状态表ID          |      |
| trad_time       | String     | 是   | 收费日期                  |      |
| sale_no         | String     | 是   | 订单号                    |      |
| sale_user_name  | String     | 是   | 制单人                    |      |
| trad_payuser    | String     | 是   | 客户姓名                  |      |
| item_goods_id   | String     | 是   | 商品id                    |      |
| item_goods_name | String     | 是   | 商品名称                  |      |
| item_size       | Integer    | 是   | 数量                      |      |
| batch_id        | String     | 是   | 商品批次ID                |      |
| batch_batchno   | String     | 否   | 生产批号                  |      |
| batch_validity  | String     | 否   | 有效期                    |      |
| stoc_waste      | Integer    | 是   | 废料标志 ;0-正常品;1-废料 |      |
| can_fetch       | Integer    | 是   | 是否能取件 ;0-不能;1-能   |      |
| is_bind       | Integer    | 否   | 是否已绑定 ;0-没有;1-已绑定  已绑定的出现绑定按钮   |      |
| list            | ObjectList | 否   | 库存入库属性列表          |      |
| purc_prop_list  | ObjectList | 否   | 定做入库属性列表          |      |
| produced_date   | String     | 否   | 生产日期                  | 新增 |
| prop_text       | String     | 否   | 拼接的属性内容            | 新增 |

库存入库属性列表跟定做入库属性列表说明

|     参数名     |   类型  | 必填 |                   说明                   |
|----------------|---------|------|------------------------------------------|
| prop_prop_id   | Integer | 是   | 属性码ID                                 |
| prop_prop_name | String  | 是   | 属性名                                   |
| choi_id        | String  | 否   | 属性值ID                                 |
| choi_code      | String  | 否   | 属性值代码                               |
| choi_value     | String  | 否   | 属性值内容                               |
| prop_putinprop | Integer | 是   | 入库属性标志,默认0;  0:非入库;1:入库属性 |



###解绑

> [POST]/depo_service/pick/un_bind

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明        |
| ------- | ------ | ---- | --------- |
| stat_id | String | 是    | 销售物资状态表ID |


#### 回复报文参数Object

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


##其他

### 商品列表

> [GET]/diag_service/special_check/goods_list

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| clas_id   | String     | 是    | 商品类别ID |
| clas_code | String     | 是    | 商品类别代码 |
| clas_name | String     | 是    | 类别名称   |
| list      | ObjectList | 是    | 商品列表   |

商品列表说明

| 参数名        | 类型     | 必填   | 说明   |
| ---------- | ------ | ---- | ---- |
| goods_id   | String | 是    | 商品ID |
| goods_name | String | 是    | 商品名称 |
| goods_unit | String | 是    | 商品单位 |


##视光后台参数


### 获得视光后台参数设置

```http
[GET]/sys_service/optometry_settings/onoff/list
```

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.3.5 | 修改 增加是否打印体检报告 |

#### 请求报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
|        |      |      |      |

#### 回复报文参数Object

|       参数名        |   类型  | 必填 |            说明            |
|---------------------|---------|------|----------------------------|
| auto_printer        | boolean | 是   | 销售单是否自动打印         |
| check_goods_class   | boolean | 是   | 出入库单据是否判断同一类别 |
| salesman_gift       | boolean | 是   | 允许销售直接赠送           |
| goods_linkage_query | boolean | 是   | 商品联级查询               |
| goods_price_modify | boolean | 是   | 商品小级修改               |
| print_check | boolean | 是   | 是否打印体检报告 0否1是               |
| point_handle | Integer | 是   | 小数点处理方式 小数点到分（0），到角（1），到元（2）   （1.3.9.4追加）    |

### 修改视光后台参数设置

```http
[POST]/sys_service/optometry_settings/onoff
```

#### 请求报文参数

|       参数名        |   类型  | 必填 |            说明            |
|---------------------|---------|------|----------------------------|
| auto_printer        | boolean | 否   | 销售单是否自动打印         |
| check_goods_class   | boolean | 否   | 出入库单据是否判断同一类别 |
| salesman_gift       | boolean | 否   | 允许销售直接赠送           |
| goods_linkage_query | boolean | 否   | 商品联级查询               |
| goods_price_modify | boolean | 否   | 商品小级修改               |
| point_handle | Integer | 否   | 小数点处理方式 小数点到分（0），到角（1），到元（2）   （1.3.9.4追加）    |

#### 回复报文参数Object

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
|        |      |      |      |


##制镜单（for 微信）


### 获取制镜加工订单列表

```http
[GET]/process_service/wechat/glass_process/list
```

#### 修改更新记录

| 对应版本 | 说明                      |
| -------- | ------------------------- |
| V1.3.6   | 新增 获取制镜加工订单列表 |


#### 请求报文参数

| 参数名    | 类型       | 必填 | 说明         |
| --------- | ---------- | ---- | ------------ |
| page_num  | Integer    | 是   | 当前页       |
| page_size | Integer    | 是   | 每页的数量   |

#### 回复报文参数

| 参数名    | 类型       | 必填 | 说明         |
| --------- | ---------- | ---- | ------------ |
| page_num  | Integer    | 是   | 当前页       |
| page_size | Integer    | 是   | 每页的数量   |
| total     | Integer    | 是   | 总记录数     |
| pages     | Integer    | 是   | 总页数       |
| list      | ObjectList | 否   | 制镜加工订单列表 |

制镜加工订单列表

| 参数名    | 类型       | 必填 | 说明         |
| --------- | ---------- | ---- | ------------ |
| proc_id | String | 是   | 制镜加工单ID |
| pati_id | String    | 是   | 患者ID  |
| pati_name | String    | 是   | 患者姓名 |
| flow_type_name | String | 是   | 加工当前步骤名称 |


### 获取制镜加工订单详情

```http
[GET]/process_service/wechat/glass_process
```

#### 修改更新记录

| 对应版本 | 说明                      |
| -------- | ------------------------- |
| V1.3.6   | 新增 获取制镜加工订单列表 |


#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| proc_id | String | 是    | 制镜加工单ID |

#### RequestPara
| 参数名    | 类型    | 必填 | 说明       |
| --------- | ------- | ---- | ---------- |
| 无        |         |      |            |

#### 回复报文参数

| 参数名    | 类型       | 必填 | 说明         |
| --------- | ---------- | ---- | ------------ |
| bill_No | String | 是    | 订单号 |
| proc_state | Integer | 是    | 制镜加工单状态 0:正常;4:待退货;5:已退货; |
| list      | ObjectList | 否   | 制镜加工进度列表 |

制镜加工订单列表

| 参数名    | 类型       | 必填 | 说明         |
| --------- | ---------- | ---- | ------------ |
| flow_type | Integer    | 是 | 类型名称，1:待支付,2:已支付,3:未到货,4:已到货；5:制镜开始；6:制镜完成；7:待取镜；8:已取镜|
| flow_time | String    | 否   | 流程状态时间 |


###收费账户列表 
>[GET]/sys_service/charg_account/list
>

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明                |
| ---------- | ------- | ---- | ----------------- |
| query_type | Integer | 是    | 查询类型 1:所有 2只查询启用的 |


#### 回复报文参数Object

| 参数名          | 类型      | 必填   | 说明                   |
| ------------ | ------- | ---- | -------------------- |
| account_id   | String  | 是    | 账户ID  也就是agency_id   |
| account_name | String  | 是    | 账户名称  也就是agency_name |
| enable       | Integer | 是    | 是否有效,  0：停用  1：有效    |


### 商品属性——参数保存

> [POST]/sys_service/opto/good_prop/para

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明             |
| ------------ | ------- | ---- | -------------- |
| choi_prop_id | String  | 是    | 属性ID           |
| choi_code    | String  | 是    | 参数编码           |
| choi_name    | String  | 是    | 参数名称           |
| choi_enable  | Integer | 是    | 是否停用；0-停用；1-有效 |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| choi_id | String | 是    | 参数ID |


###  商品目录
> [GET]/opto_service/stock_manage/good_list

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                    |
| --------- | ------- | ---- | --------------------- |
| clas_id   | String  | 否    | 商品类别id（全部为空）          |
| bran_id   | String  | 否    | 内码及品牌                 |
| vari_id   | String  | 否    | 商品品种id V1.3.8追加                |
| key       | String  | 否    | 商品名称、商品编码、商品拼音码、商品五笔码 |
| type      | Integer | 否    | 0-不在售;1-在售;停用2;全部为空   |
| page_num  | Integer | 是    | 当前页                   |
| page_size | Integer | 是    | 每页的数量                 |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 商品列表  |
商品列表说明
| 参数名           | 类型      | 必填   | 说明                      |
| ------------- | ------- | ---- | ----------------------- |
| good_id       | String  | 是    | 内码及商品ID                 |
| good_code     | String  | 是    | 商品编码                    |
| good_name     | String  | 是    | 商品名称                    |
| good_unitname | String  | 否    | 商品单位名称                  |
| good_bidprice | Double  | 否    | 参考成本价                   |
| good_price    | Double  | 否    | 售价                      |
| status        | Integer | 是    | 商品状态0-不在售;1-在售;停用2;全部为空 |


###  商品属性码表列表(带翻页)
> [GET]/opto_service/good/good_propcode_list/page

#### 请求报文参数


| 参数名    | 类型       | 必填 | 说明         |
| --------- | ---------- | ---- | ------------ |
| type  | Integer    | 否   | 1:自由录入属性; 2:候选选择属性。 空全部      |
| page_num  | Integer    | 是   | 当前页       |
| page_size | Integer    | 是   | 每页的数量   |

#### 回复报文参数

| 参数名    | 类型       | 必填 | 说明         |
| --------- | ---------- | ---- | ------------ |
| page_num  | Integer    | 是   | 当前页       |
| page_size | Integer    | 是   | 每页的数量   |
| total     | Integer    | 是   | 总记录数     |
| pages     | Integer    | 是   | 总页数       |
| list      | ObjectList | 否   | 制镜加工订单列表 |

#### 回复报文参数ObjectList

| 参数名       | 类型     | 必填   | 说明       |
| --------- | ------ | ---- | -------- |
| prop_id   | String | 是    | 内码及属性码ID |
| prop_name | String | 是    | 属性名称     |
| prop_flag | Integer    | 是    | 属性标志 0-普通属性; 1-球面; 2-柱面; 3-规格; 4-颜色;【增加】|
| prop_type | Integer    | 是    | 属性类型,1-自由录入属性;2-候选选择属性|

###  商品报损记录
> [GET]/opto_service/good/bad_reasons_list

#### 请求报文参数


| 参数名    | 类型       | 必填 | 说明         |
| --------- | ---------- | ---- | ------------ |
| goods_id  | String    | 是   | 商品id    |


#### 回复报文参数ObjectList

| 参数名       | 类型     | 必填   | 说明       |
| --------- | ------ | ---- | -------- |
| bad_reasons   | String | 是    | 报损原因 |



### 获得一个销售订单

```http
[GET]/sale_service/sales_order
```

#### 请求报文参数

| 参数名  |  类型  | 必填 |   说明   |
|---------|--------|------|----------|
| sale_id | String | 是   | 销售单id |

#### 回复报文参数

|     参数名      |    类型    | 必填 |                        说明                       |
|-----------------|------------|------|---------------------------------------------------|
| sale_id         | String     | 是   | 销售单id                                          |
| treatment       | Object     | 否   | 就诊信息                                          |
| opto_id         | String     | 否   | 处方id                                            |
| rgp             | Object     | 否   | rgp处方                                           |
| contactpres     | Object     | 否   | 隐形眼镜处方                                      |
| ok              | Object     | 否   | ok镜处方                                          |
| other           | Object     | 否   | 其他处方                                          |
| frame           | Object     | 否   | 框架眼镜处方                                      |
| sale_no         | String     | 是   | 订单号                                            |
| sale_time       | String     | 是   | 订单时间                                          |
| sale_user_id    | String     | 是   | 客户id                                            |
| sale_user_name  | String     | 是   | 客户名称                                          |
| bracket_type    | Integer    | 否    | 框架类型  0：全框架、1：半框架、2：无框架、3：拉丝框、4：渐变镜、5：高档框 空的时候，整个显示模板隐藏掉（1.3.9.4追加） |
| order_state    | Integer    | 否    |订单状态  0：待取件、1：已取件 2：部分取件，3：未到货、4：已到货 5：已退货 （1.3.9.4追加） |
| state_time    | String    | 否    |状态时间 （1.3.9.4追加） |
| sale_state      | Integer    | 是   | 状态;1-待付款;2-已付款;3-已撤销;4-待退费;5-已退费 7:退费待申请(V1.3.8追加)  |
| return_state      | Integer    | 是   | 是否申请退货状态;0-未申请;1-已申请|
| full            | Double     | 否   | 整单优惠满                                        |
| cat             | Double     | 否   | 整单优惠减                                        |
| sale_price      | Double     | 是   | 商品总额                                          |
| sale_favor      | Double     | 是   | 优惠                                              |
| sale_real_price | Double     | 是   | 实付款                                            |
| sale_rem        | String     | 是   | 备注                                              |
| sale_state_time       | String     | 是   | 状态变更时间                                          |
| sale_pay_time       | String     | 是   |  付款时间                                       |
| list            | ObjectList | 是   | 销售单细目列表                                    |

销售单细目说明

|       参数名        |    类型    | 必填 |                    说明                   |      |
|---------------------|------------|------|-------------------------------------------|------|
| item_id             | String     | 是   | 细目id                                    |      |
| item_goodsid        | String     | 是   | 商品id                                    |      |
| item_goods_name     | String     | 是   | 商品名称                                  |      |
| item_batchid        | String     | 是   | 批次id                                    |      |
| stoc_waste          | Integer    | 是   | 废料标志 ;0-正常品;1-废料                 |      |
| batch_no            | String     | 否   | 批号                                      |      |
| batch_validity      | String     | 否   | 有效期                                    |      |
| is_give             | Integer    | 是   | 赠送标志 0-非赠送;1-活动赠送;2-业务员赠送 |      |
| item_purchase       | Integer    | 是   | 定购标志 0-不定做;1-定做;                 |      |
| item_purc_prop      | String     | 否   | 定做属性                                  |      |
| item_purc_prop_list | ObjectList | 否   | 定做属性列表                              |      |
| item_size           | Integer    | 是   | 销售数量                                  |      |
| good_price          | Double     | 是   | 零售价                                    |      |
| good_total_price    | Double     | 是   | 小计                                      |      |
| depot_id            | String     | 是   | 仓库id                                    |      |
| depo_name           | String     | 是   | 出库位置                                  |      |
| list                | ObjectList | 否   | 优惠列表                                  |      |
| prop_list           | ObjectList | 否   | 属性列表                                  |      |
| produced_date       | String     | 否   | 生产日期                                  | 新增 |
| prop_text           | String     | 否   | 拼接的属性内容                            | 新增 |

就诊信息

|    参数名    |  类型  | 必填 |      说明      |
|--------------|--------|------|----------------|
| visit_time   | String | 否   | 接诊时间       |
| visit_depa   | String | 否   | 接诊科室或部门 |
| visit_doctor | String | 否   | 接诊医生       |
| finish_time  | String | 否   | 结束就诊时间   |

框架处方说明

|        参数名         |   类型  | 必填 |     说明    |
|-----------------------|---------|------|-------------|
| opto_far_pd           | Integer | 否   | 瞳距-远用   |
| opto_near_pd          | Integer | 否   | 瞳距-近用   |
| opto_od_pd            | Integer | 否   | 瞳距-单眼OD |
| opto_os_pd            | Integer | 否   | 瞳距-单眼OS |
| opto_od_ph            | Integer | 否   | 瞳高-OD     |
| opto_os_ph            | Integer | 否   | 瞳高-OS     |
| opto_far_od_sphere    | Double  | 否   | 远用OD-球镜 |
| opto_far_od_cylinder  | Double  | 否   | 远用OD-柱镜 |
| opto_far_od_axis      | Double  | 否   | 远用OD-轴向 |
| opto_far_od_prism     | Double  | 否   | 远用OD-棱镜 |
| opto_far_od_vision    | Double  | 否   | 远用OD-视力 |
| opto_far_od_memo      | String  | 否   | 远用OD-备注 |
| opto_far_os_sphere    | Double  | 否   | 远用OS-球镜 |
| opto_far_os_cylinder  | Double  | 否   | 远用OS-柱镜 |
| opto_far_os_axis      | Double  | 否   | 远用OS-轴向 |
| opto_far_os_prism     | Double  | 否   | 远用OS-棱镜 |
| opto_far_os_vision    | Double  | 否   | 远用OS-视力 |
| opto_far_os_memo      | String  | 否   | 远用OS-备注 |
| opto_near_od_sphere   | Double  | 否   | 近用OD-球镜 |
| opto_near_od_cylinder | Double  | 否   | 近用OD-柱镜 |
| opto_near_od_axis     | Double  | 否   | 近用OD-轴向 |
| opto_near_od_prism    | Double  | 否   | 近用OD-棱镜 |
| opto_near_od_vision   | Double  | 否   | 近用OD-视力 |
| opto_near_od_memo     | String  | 否   | 近用OD-备注 |
| opto_near_os_sphere   | Double  | 否   | 近用OS-球镜 |
| opto_near_os_cylinder | Double  | 否   | 近用OS-柱镜 |
| opto_near_os_axis     | Double  | 否   | 近用OS-轴向 |
| opto_near_os_prism    | Double  | 否   | 近用OS-棱镜 |
| opto_near_os_vision   | Double  | 否   | 近用OS-视力 |
| opto_near_os_memo     | String  | 否   | 近用OS-备注 |

隐形眼镜处方说明

|        参数名         |  类型  | 必填 |       说明      |
|-----------------------|--------|------|-----------------|
| opto_lens_od_sphere   | Double | 否   | 隐形眼镜OD-球镜 |
| opto_lens_od_cylinder | Double | 否   | 隐形眼镜OD-柱镜 |
| opto_lens_od_axis     | Double | 否   | 隐形眼镜OD-轴向 |
| opto_lens_od_memo     | String | 否   | 隐形眼镜OD-备注 |
| opto_lens_os_sphere   | Double | 否   | 隐形眼镜OS-球镜 |
| opto_lens_os_cylinder | Double | 否   | 隐形眼镜OS-柱镜 |
| opto_lens_os_axis     | Double | 否   | 隐形眼镜OS-轴向 |
| opto_lens_os_memo     | String | 否   | 隐形眼镜OS-备注 |
| od_cliffy             | String | 否   | 右眼陡峭        |
| od_flat               | String | 否   | 右眼平坦        |
| od_axis               | String | 否   | 右眼轴向        |
| os_cliffy             | String | 否   | 左眼陡峭        |
| os_flat               | String | 否   | 左眼平坦        |
| os_axis               | String | 否   | 左眼轴向        |

rgp处方说明

|       参数名       |  类型  | 必填 |             说明            |
|--------------------|--------|------|-----------------------------|
| rgp_od_brand_id    | Long   | 否   | 右眼镜片品牌ID              |
| rgp_od_brand       | String | 否   | 右眼镜片品牌                |
| rgp_od_material_id | Long   | 否   | 右眼镜片材质ID              |
| rgp_od_material    | String | 否   | 右眼镜片材质                |
| rgp_od_curve       | Double | 否   | 右眼镜片基弧，单位：mm毫米  |
| rgp_od_diameter    | Double | 否   | 右眼镜片直径，单位：mm毫米  |
| rgp_od_degree      | Double | 否   | 右眼镜片度数，单位：D屈光度 |
| rgp_od_memo        | String | 否   | 右眼备注                    |
| rgp_os_brand_id    | Long   | 否   | 左眼镜片品牌ID              |
| rgp_os_brand       | String | 否   | 左眼镜片品牌                |
| rgp_os_material_id | Long   | 否   | 左眼镜片材质ID              |
| rgp_os_material    | String | 否   | 左眼镜片材质                |
| rgp_os_curve       | Double | 否   | 左眼镜片基弧，单位：mm毫米  |
| rgp_os_diameter    | Double | 否   | 左眼镜片直径，单位：mm毫米  |
| rgp_os_degree      | Double | 否   | 左眼镜片度数，单位：D屈光度 |
| rgp_os_memo        | String | 否   | 左眼备注                    |

其他处方列表说明

|     参数名      |  类型  | 必填 |      说明      |
|-----------------|--------|------|----------------|
| othe_id         | String | 是   | 其他处方处方id |
| othe_clas_id    | String | 是   | 类别id         |
| othe_clas_code  | String | 是   | 商品类别代码   |
| othe_goods_id   | String | 是   | 商品id         |
| othe_goods_name | String | 否   | 商品名称       |
| othe_count      | String | 是   | 数量           |
| othe_goods_unit | String | 否   | 单位           |
| othe_rem        | String | 否   | 备注           |

ok镜参数对象

|    参数名    |    类型    | 必填 |       说明       |
|--------------|------------|------|------------------|
| od_brand_id  | String     | 否   | 右眼品牌id       |
| od_brand     | String     | 否   | 右眼品牌         |
| od_para_list | ObjectList | 是   | 右眼品牌参数列表 |
| os_brand_id  | String     | 否   | 左眼品牌id       |
| os_brand     | String     | 否   | 左眼品牌         |
| os_para_list | ObjectList | 是   | 左眼品牌参数列表 |

定做属性跟入库属性说明

|     参数名     |  类型  | 必填 |    说明    |
|----------------|--------|------|------------|
| para_id        | String | 是   | 处方参数id |
| para_prop_id   | String | 是   | 属性id     |
| para_prop_name | String | 是   | 属性名称   |
| para_choi_id   | String | 否   | 属性值ID   |
| para_choi_code | String | 否   | 属性值代码 |
| para_value     | String | 否   | 属性值     |

优惠列表说明

|    参数名    |  类型  | 必填 |   说明   |
|--------------|--------|------|----------|
| favo_prom_id | String | 是   | 优惠id   |
| prom_memo    | String | 是   | 优惠说明 |

属性列表说明

|     参数名     |   类型  | 必填 |                   说明                   |
|----------------|---------|------|------------------------------------------|
| prop_prop_id   | Integer | 是   | 属性码ID                                 |
| prop_prop_name | String  | 是   | 属性名                                   |
| choi_id        | String  | 否   | 属性值ID                                 |
| choi_code      | String  | 否   | 属性值代码                               |
| choi_value     | String  | 否   | 属性值内容                               |
| prop_putinprop | Integer | 是   | 入库属性标志,默认0;  0:非入库;1:入库属性 |


### 商品品牌列表

> [GET]/common_service/brand_list_his

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                    |
| --------- | ------- | ---- | --------------------- |
| key       | String  | 否    | 品牌名称、品牌代码、品牌拼音码、品牌五笔码 |
| goods_class       | Long  | 否    | 商品类别id   |

商品品牌列表说明ObjectList

| 参数名       | 类型     | 必填   | 说明      |
| --------- | ------ | ---- | ------- |
| bran_id   | String | 是    | 内码及品牌ID |
| bran_name | String | 是    | 品牌名称    |



### 商品品种列表

> [GET]/common_service/variety_list_his

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明        |
| --------- | ------- | ---- | --------- |
| key       | String  | 否    | 品种代码、品种名称 |
| goods_class       | Long  | 否    | 商品类别id   |
| goods_brand       | Long  | 否    | 商品品种id  |

商品品种列表说明ObjectList

| 参数名       | 类型     | 必填   | 说明       |
| --------- | ------ | ---- | -------- |
| vari_id   | String | 是    | 内码及品种码ID |
| vari_code   | String | 是    | 品种代码（1.3.9.2追加） |
| vari_name | String | 是    | 品种名称     |



###  商品属性候选值列表

> [GET]/opto_service/good/good_propchoice_list

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明       |
| ------- | ------ | ---- | -------- |
| prop_id | String | 是    | 内码及属性码ID |
| key     | String | 否    | 关键字      |
| page_num  | Integer    | 否    | 当前页      |
| page_size | Integer    | 否    | 每页的数量    |
| is_all  | Integer| 否    | 是否返回所有值，0:否，1:是      |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明       |
| --------- | ---------- | ---- | -------- |
| page_num  | Integer    | 是    | 当前页      |
| page_size | Integer    | 是    | 每页的数量    |
| total     | Integer    | 是    | 总记录数     |
| pages     | Integer    | 是    | 总页数      |
| list      | ObjectList | 否    | 商品备选属性列表 |
商品备选属性列表说明
| 参数名        | 类型     | 必填   | 说明    |
| ---------- | ------ | ---- | ----- |
| choi_id    | String | 是    | 内码    |
| choi_code  | String | 否    | 属性值代码 |
| choi_value | String | 是    | 名称    |



### 获得一个销售退货单

```http
[GET]/sale_service/sales_refund
```

#### 请求报文参数

| 参数名  | 类型 | 必填 |     说明     |
|---------|------|------|--------------|
| refu_id | Long | 是   | 退货单子表ID |
| depo_id | Long | 是   | 仓库id       |

#### 回复报文参数Object

|       参数名        |    类型    | 必填 |     说明     |
|---------------------|------------|------|--------------|
| refu_id             | String     | 是   | 退货单子表ID |
| refu_make_user_name | String     | 是   | 制单人       |
| refu_make_time      | String     | 是   | 制单日期     |
| refu_sale_no        | String     | 是   | 退货单号     |
| sale_no             | String     | 是   | 销售单号     |
| pay_time            | String     | 是   | 付费时间     |
| sale_user_name      | String     | 是   | 销售单制单人 |
| list                | ObjectList | 是   | 退货商品列表 |

退货商品列表说明

|     参数名      |    类型    | 必填 |                 说明                |      |
|-----------------|------------|------|-------------------------------------|------|
| stat_id         | String     | 是   | 物资细目id                          |      |
| stat_goodsid    | String     | 是   | 商品id                              |      |
| stat_goods_name | String     | 是   | 商品名称                            |      |
| stat_batchid    | String     | 否   | 批次id                              |      |
| refund_reason   | String     | 否   | 退货原因 V1.3.8追加                               |      |
| batch_no        | String     | 否   | 批号                                |      |
| batch_validity  | String     | 否   | 有效期                              |      |
| stoc_waste      | Integer    | 是   | 废料标志 ;0-正常品;1-废料           |      |
| stat_purc_prop  | String     | 否   | 定做属性                            |      |
| stat_size       | Integer    | 是   | 销售数量                            |      |
| stat_pickup     | Integer    | 是   | 出库状态 0未取件 1:已回收 2：未回收 |      |
| is_return       | Integer    | 是   | 是否可回收 0：不可 1：可以          |      |
| prop_list       | ObjectList | 否   | 属性列表                            |      |
| produced_date   | String     | 否   | 生产日期                            | 新增 |
| prop_text       | String     | 否   | 拼接的属性内容                      | 新增 |

定做属性跟属性列表说明

|     参数名     |   类型  | 必填 |                   说明                   |
|----------------|---------|------|------------------------------------------|
| prop_prop_id   | Integer | 是   | 属性码ID                                 |
| prop_prop_name | String  | 是   | 属性名                                   |
| choi_id        | String  | 否   | 属性值ID                                 |
| choi_code      | String  | 否   | 属性值代码                               |
| choi_value     | String  | 否   | 属性值内容                               |
| prop_putinprop | Integer | 是   | 入库属性标志,默认0;  0:非入库;1:入库属性 |



### 新增商品

> [POST]/opto_service/stock_manage/good

#### 请求报文参数

| 参数名            | 类型         | 必填   | 说明                   |
| -------------- | ---------- | ---- | -------------------- |
| good_code      | String     | 是    | 商品编码                 |
| good_name      | String     | 是    | 商品名称                 |
| good_calss     | String     | 是    | 商品类别id               |
| good_brand     | String     | 是    | 商品品牌id               |
| good_variety   | String     | 否    | 商品品种id               |
| good_factory   | String     | 是    | 生产厂商id               |
| good_supplier  | String     | 是    | 供应商id                |
| good_registrno | String     | 否    | 注册证号                 |
| good_bidprice  | Double     | 否    | 参考成本价                |
| good_price     | Double     | 否    | 售价                   |
| good_char_id   | String     | 是    | 收费类别ID               |
| good_unitid    | String     | 否    | 单位id                 |
| good_unitname  | String     | 否    | 商品单位名称               |
| good_give      | Integer    | 是    | 允许赠送,默认:0;0-不允许;1-允许 |
| status         | Integer    | 是    | 0-不在售;1-在售;停用2       |
| stock_list     | ObjectList | 否    | 入库属性列表               |
| list           | ObjectList | 否    | 非入库属性列表              |

入库属性列表说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | String | 是    | 属性码ID |
| prop_prop_name | String | 是    | 属性码名称 |

非入库属性列表说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | String | 是    | 属性码ID |
| prop_prop_name | String | 是    | 每页的数量 |
| choi_id        | String | 否    | 属性值ID |
| choi_code      | String | 否    | 属性值代码 |
| choi_value     | String | 否    | 属性值内容 |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| good_id | String | 是    | 新增商品id |



### 修改商品

> [POST]/opto_service/stock_manage/good/update

#### 请求报文参数

| 参数名              | 类型         | 必填   | 说明                   |
| ---------------- | ---------- | ---- | -------------------- |
| good_id          | String     | 是    | 商品id                 |
| good_code      | String     | 是    | 商品编码                 |
| good_name      | String     | 是    | 商品名称                 |
| good_class_id     | String     | 是    | 商品类别id               |
| good_brand_id     | String     | 是    | 商品品牌id               |
| good_variety_id   | String     | 否    | 商品品种id               |
| good_factory_id  | String     | 是    | 生产厂商id               |
| good_supplier_id | String     | 是    | 供应商id                |
| good_registrno   | String     | 否    | 注册证号                 |
| good_unitid      | String     | 否    | 单位id                 |
| good_unitname    | String     | 否    | 商品单位名称               |
| good_char_id     | String     | 是    | 收费类别ID               |
| good_give        | Integer    | 是    | 允许赠送,默认:0;0-不允许;1-允许 |
| status           | Integer    | 是    | 0-不在售;1-在售;停用2       |
| stock_list       | ObjectList | 否    | 入库属性列表               |

入库属性列表说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | Long   | 是    | 属性码ID |
| prop_prop_name | String | 是    | 属性名   |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 退货（带备注）

> [POST]/depo_service/sales_order/add_return_withreasons

#### 请求报文参数

| 参数名            | 类型         | 必填   | 说明                   |
| -------------- | ---------- | ---- | -------------------- |
| sales_id      | String     | 是    | 销售单id                 |
| refund_reasons     | ObjectList | 否    | 退货备注（退货原因）               |

入库属性列表说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| statId   | Long | 是    | 物资状态id |
| reason | String | 是    | 退货原因（备注） |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
|  |  |     |  |

### 获得商品名称跟商品编码

> [GET]/opto_service/stock_manage/good_name_code

#### 请求报文参数

| 参数名          | 类型         | 必填   | 说明      |
| ------------ | ---------- | ---- | ------- |
| good_calss   | String     | 是    | 商品类别id  |
| good_brand   | String     | 是    | 商品品牌id  |
| good_variety | String     | 否    | 商品品种id  |
| list         | ObjectList | 否    | 非入库属性列表 |

非入库属性列表说明

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| prop_prop_id   | String | 是    | 属性码ID |
| prop_prop_name | String | 是    | 每页的数量 |
| choi_id        | String | 否    | 属性值ID |
| choi_code      | String | 否    | 属性值代码 |
| choi_value     | String | 否    | 属性值内容 |

#### 回复报文参数

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| good_code | String | 是    | 商品编码 |
| good_name | String | 是    | 商品名称 |



### 获得视光后台参数设置

```http
[GET]/sys_service/optometry_settings/onoff/list
```

#### 请求报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
|        |      |      |      |

#### 回复报文参数Object

|       参数名        |   类型  | 必填 |            说明            |
|---------------------|---------|------|----------------------------|
| auto_printer        | boolean | 是   | 销售单是否自动打印         |
| check_goods_class   | boolean | 是   | 出入库单据是否判断同一类别 |
| salesman_gift       | boolean | 是   | 允许销售直接赠送           |
| goods_linkage_query | boolean | 是   | 商品联级查询               |
| goods_price_modify | boolean | 是   | 商品小级修改               |



### 销售退货回收

>[POST]/sale_service/sales_order/return

#### 请求报文参数ObjuectList
| 参数名     | 类型     | 必填   | 说明    |
| ------- | ------ | ---- | ----- |
| stat_id | String | 是    | 物资表id |
| reason | String | 否    | 退货原因  V1.3.8追加|

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |


### 通用仓库列表

> [GET]/common_service/depot_list

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


### 根据手机号、姓名、首字母获取患者列表

总共返回50条暂时不做排序处理

> [GET]/patient_service/patient/list/for_preview

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.3.9.2 | 修改 增加病历号 |


#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明                               |
| ---- | ------ | ---- | -------------------------------- |
| key  | String | 是    | 手机号、姓名、首字母（手机号全匹配、姓名模糊匹配、首字母左匹配）病历号精确匹配 |

#### 回复报文参数ObjectList

| 参数名            | 类型     | 必填   | 说明                |
| -------------- | ------ | ---- | ----------------- |
| pati_id        | Long   | 是    | 患者ID              |
| pati_name      | String | 是    | 姓名                |
| pati_mrno      | String | 否    | 病历号  （1.3.9.2追加） |
| pati_py        | String | 否    | 姓名拼音首字母           |
| pati_gender    | String | 是    | 性别代码 0 未知 1男  2 女 |
| pati_age       | String | 是    | 年龄                |
| pati_birthday  | Date   | 是    | 出生年月              |
| pati_phone     | String | 是    | 手机号码              |
| pati_id_number | String | 是    | 身份证               |
| pati_address   | String | 否    | 地址                |


### 提交销售订单
> [POST]/sale_service/sales_order

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.3.9.2 | 修改 增加备注 |
| V1.3.9.4 | 修改 增加框架类型 |


#### 请求报文参数

| 参数名             | 类型         | 必填   | 说明      |
| --------------- | ---------- | ---- | ------- |
| pati_id         | String     | 是    | 患者id    |
| opto_id         | String     | 否    | 处方id    |
| pati_mrno         | String     | 否    | 病历号  （1.3.9.2追加）  |
| sale_rem         | String     | 否    | 备注  （1.3.9.2追加）  |
| bracket_type         | Integer     | 否    | 框架类型  0：全框架、1：半框架、2：无框架、3：拉丝框、4：渐变镜、5：高档框 （1.3.9.4追加） |
| prom_id         | String     | 否    | 整单优惠id  |
| sale_price      | Double     | 是    | 商品总额    |
| sale_favor      | Double     | 是    | 优惠      |
| sale_real_price | Double     | 是    | 实付款     |
| fave_list       | ObjectList | 否    | 优惠列表    |
| list            | ObjectList | 是    | 销售单细目列表 |

销售单细目说明

| 参数名              | 类型         | 必填   | 说明                        |
| ---------------- | ---------- | ---- | ------------------------- |
| item_goodsid     | String     | 是    | 商品id                      |
| item_batchid     | String     | 否    | 批次id                      |
| stoc_id          | String     | 是    | 库存id                      |
| item_purc_prop   | String     | 否    | 定做属性                      |
| item_size        | Integer    | 是    | 销售数量                      |
| is_give          | Integer    | 是    | 赠送标志 0-非赠送;1-活动赠送;2-业务员赠送 |
| item_purchase    | Integer    | 是    | 定购标志 ;0-不需定购;1-需定购        |
| item_odos        | Integer    | 否    | 定做眼别0-无眼别;1-OD;2-OS       |
| item_process     | Integer    | 是    | 加工标志 0-不需加工;1-需内加工;3-需外加工 |
| discount         | Integer    | 是    | 折扣                        |
| good_price       | Double     | 是    | 零售价                       |
| good_total_price | Double     | 是    | 小计                        |
| depot_id         | String     | 是    | 仓库id                      |
| fave_list        | ObjectList | 否    | 优惠列表                      |

优惠列表说明

| 参数名          | 类型     | 必填   | 说明   |
| ------------ | ------ | ---- | ---- |
| favo_prom_id | String | 是    | 优惠id |

#### 回复报文参数

| 参数名     | 类型     | 必填   | 说明    |
| ------- | ------ | ---- | ----- |
| sale_id | String | 是    | 销售单id |


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
| depa_stocks   | ObjectList | 是  | 仓库ID       V1.3.9.2追加               |

仓库ID说明

| 参数名          | 类型     | 必填   | 说明   |
| ------------ | ------ | ---- | ---- |
| depa_stock | String | 是    | 仓库ID V1.3.9.2追加|

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
| depa_stocks   | ObjectList | 是  | 仓库ID  销售类型时候，非空   V1.3.9.2追加                 |

仓库ID说明

| 参数名          | 类型     | 必填   | 说明   |
| ------------ | ------ | ---- | ---- |
| depa_stock | String | 是    | 仓库ID V1.3.9.2追加|


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 患者信息详情

> [GET]/sale_service/patient/for_sale

获取某就诊患者的信息详情

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.3.9.2 | 修改 增加病历号 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| pati_id | String | 是    | 患者id |

#### 回复报文参数

| 参数名            | 类型     | 必填   | 说明                |
| -------------- | ------ | ---- | ----------------- |
| pati_id        | String | 是    | 患者ID              |
| pati_name      | String | 是    | 姓名                |
| pati_gender    | String | 是    | 性别代码 0 未知 1男  2 女 |
| pati_mrno      | String | 是    | 病历号  （1.3.9.2追加）               |
| pati_age       | String | 是    | 年龄                |
| pati_birthday  | Date   | 是    | 出生年月              |
| pati_phone     | String | 是    | 手机号码              |
| pati_id_number | String | 是    | 身份证               |
| pati_address   | String | 否    | 地址                |

### 销售/管理 仓库列表

> [GET]/common_service/depot_list_new

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明            |
| ---------- | ------- | ---- | ------------- |
| depot_type | Integer | 是    | 0:非销售库 1:销售库 2：所有 不传默认销售库 |
| enable | Integer | 否    | 0:无效 1:有效 2：所有 不传默认有效 |

#### 回复报文参数

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| depo_id   | String | 是    | 仓库id |
| depo_name | String | 是    | 仓库名称 |



### 销售定做商品列表

> [GET]/sale_service/sale/custom_good/list

####修改更新记录

|  对应版本 | 说明 |
|-----------|------|
| V1.2.2.1 | 修改 增加是否设置收费类别标志 |
| V1.2.2.2 | 修改 增加品种过滤 |
| V1.3.9.2 | 修改 查询科室关联的销售仓库的商品 |

#### 请求报文参数

| 参数名        | 类型      | 必填   | 说明          |
| ---------- | ------- | ---- | ----------- |
| good_class | String  | 否    | 商品类别        |
| good_brand | String  | 否    | 商品品牌        |
| good_variety | String  | 否    | 商品品种id      |
| key        | String  | 否    | 商品编码或名称     |
| page_size  | Integer | 否    | 每页条数 空表示10条 |
| page_num   | Integer | 否    | 第几页 空表示第1页  |

#### 回复报文参数Object

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 商品列表  |

商品列表说明

| 参数名          | 类型      | 必填   | 说明                 |
| ------------ | ------- | ---- | ------------------ |
| good_id      | String  | 是    | 商品ID               |
| good_class   | String  | 否    | 商品类别               |
| good_brand   | String  | 否    | 商品品牌               |
| good_variety | String  | 否    | 商品品种               |
| good_name    | String  | 是    | 商品名称               |
| good_price   | Double  | 是    | 售价                 |
| clas_process | Integer | 是    | 是否可加工 0-不可加工;1-可加工 |
| good_give    | Integer | 是    | 允许赠送 0-不允许;1-允许    |
| depot_id     | String  | 是    | 仓库id               |
| depot_name   | String  | 是    | 出库仓库名称             |
| has_char   | Integer  | 是    | 是否设置收费类别 0没有 1有             |



### 商品厂商供应商列表

> [GET]/common_service/mfr_list

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                  |
| --------- | ------- | ---- | ------------------- |
| key       | String  | 否    | 厂商名称、厂商代码、名称拼音、名称五笔 |
| type      | String  | 是    | 1:供应商;2:生产商         |
| relation      | String  | 否    | 1:关联;2:不关联 空：不关联  （1.3.9.4追加）        |
| page_num  | Integer | 是    | 当前页                 |
| page_size | Integer | 是    | 每页的数量               |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 否    | 厂商列表  |




