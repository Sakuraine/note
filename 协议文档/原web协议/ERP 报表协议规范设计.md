# ERP 报表协议规范




## 第一期

###获取报表权限列表

> [GET]/common_service/report_list

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


#### 回复报文参数

| 参数名         | 类型     | 必填   | 说明     |
| ----------- | ------ | ---- | ------ |
| func_id     | String | 是    | 功能id   |
| func_parent | String | 是    | 父级功能id |
| func_name   | String | 是    | 功能名称   |
| func_code   | String | 是    | 功能代码   |


### 商品厂商供应商列表

> [GET]/common_service/mfr_list

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                  |
| --------- | ------- | ---- | ------------------- |
| key       | String  | 否    | 厂商名称、厂商代码、名称拼音、名称五笔 |
| type      | String  | 是    | 1:供应商;2:生产商         |
| disable      | Integer  | 是    |  1:显示包含停用的  0或者空 ：只显示启用的          |
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

厂商列表说明

| 参数名         | 类型      | 必填   | 说明    |
| ----------- | ------- | ---- | ----- |
| mfr_id      | String  | 是    | 内码及厂商 |
| mfr_name    | String  | 是    | 厂商名称  |
| mfr_taxrate | Integer | 是    | 税率    |



### 通用运营机构列表

> [GET]/common_service/agency_list

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
|      |      |      |      |

#### 回复报文参数

| 参数名         | 类型         | 必填   | 说明                     |
| ----------- | ---------- | ---- | ---------------------- |
| multiagency | Integer    | 是    | 多运营机构标;0-单运营机构;1-多运营机构 |
| list        | ObjectList | 是    | 运营机构列表说明               |

运营机构列表说明

| 参数名       | 类型     | 必填   | 说明     |
| --------- | ------ | ---- | ------ |
| agen_id   | String | 否    | 运营机构id |
| agen_name | String | 是    | 运营机构名称 |



### 根据运营结构获取销售科室列表

> [GET]/common_service/agency_sale_depa_list

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| agen_id | String | 是    | 运营机构id |
| key     | String | 否    | 搜索关键字  |

#### 回复报文参数

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| depa_id   | String | 是    | 科室id |
| depa_name | String | 是    | 科室名称 |



### 获取对应运营结构下有管理权限的仓库列表

> [GET]/common_service/agency_depo_list_role

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| agen_id | String | 否    | 运营机构id |
| key     | String | 否    | 搜索关键字  |

#### 回复报文参数

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| depo_id   | String | 是    | 仓库id |
| depo_name | String | 是    | 仓库名  |

### 获取对应运营结构下的仓库列表

> [GET]/common_service/agency_depo_list

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| agen_id | String | 否    | 运营机构id |
| key     | String | 否    | 搜索关键字  |

#### 回复报文参数

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| depo_id   | String | 是    | 仓库id |
| depo_name | String | 是    | 仓库名  |



### 商品类别列表

> [GET]/common_service/class_list

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明            |
| ---- | ------ | ---- | ------------- |
| key  | String | 否    | 商品类别名称、商品类别代码 |

#### 回复报文参数

| 参数名         | 类型      | 必填   | 说明                 |
| ----------- | ------- | ---- | ------------------ |
| clas_id     | String  | 是    | 内码及类别ID,uniqueid生成 |
| clas_name   | Integer | 是    | 商品类别名称             |
| clas_parent | String  | 否    | 父级类别ID             |
| clas_level  | String  | 是    | 类别层级,从1记，当前支持三级    |



### 商品品牌列表

> [GET]/common_service/brand_list

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                    |
| --------- | ------- | ---- | --------------------- |
| key       | String  | 否    | 品牌名称、品牌代码、品牌拼音码、品牌五笔码 |
| page_num  | Integer | 是    | 当前页                   |
| page_size | Integer | 是    | 每页的数量                 |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 当前页    |
| page_size | Integer    | 是    | 每页的数量  |
| total     | Integer    | 是    | 总记录数   |
| pages     | Integer    | 是    | 总页数    |
| list      | ObjectList | 否    | 商品品牌列表 |

商品品牌列表说明

| 参数名       | 类型     | 必填   | 说明      |
| --------- | ------ | ---- | ------- |
| bran_id   | String | 是    | 内码及品牌ID |
| bran_name | String | 是    | 品牌名称    |



### 商品品种列表

> [GET]/common_service/variety_list

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明        |
| --------- | ------- | ---- | --------- |
| key       | String  | 否    | 品种代码、品种名称 |
| page_num  | Integer | 是    | 当前页       |
| page_size | Integer | 是    | 每页的数量     |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明     |
| --------- | ---------- | ---- | ------ |
| page_num  | Integer    | 是    | 当前页    |
| page_size | Integer    | 是    | 每页的数量  |
| total     | Integer    | 是    | 总记录数   |
| pages     | Integer    | 是    | 总页数    |
| list      | ObjectList | 否    | 商品品种列表 |

商品品种列表说明

| 参数名       | 类型     | 必填   | 说明       |
| --------- | ------ | ---- | -------- |
| vari_id   | String | 是    | 内码及品种码ID |
| vari_name | String | 是    | 品种名称     |



###获取销售报表其他信息

> [GET]/report_service/sale/head

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                   |
| --------- | ------- | ---- | -------------------- |
| agen_id   | String  | 是    | 运营机构                 |
| depa_list | String  | 否    | 销售部门id(不选全部)         |
| begin     | String  | 是    | 开始时间                 |
| end       | String  | 是    | 结束时间                 |
| is_return | Integer | 否    | 是否包含退费:0否,1是         |
| select    | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| title      | String     | 是    | 标题        |
| flag       | String     | 是    | 标记        |
| head       | ObjectList | 是    | 副标题信息     |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |

副标题信息说明

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| prefix | String | 是    | 前缀   |
| suffix | String | 是    | 后缀   |




### 销售报表

> [GET]/report_service/sale

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |


### 销售报表导出EXCEL

> [GET]/report_service/sale/excel

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                   |
| --------- | ------- | ---- | -------------------- |
| agen_id   | String  | 是    | 运营机构                 |
| depa_list | String  | 否    | 销售部门id(不选全部)         |
| begin     | String  | 是    | 开始时间                 |
| end       | String  | 是    | 结束时间                 |
| is_return | Integer | 否    | 是否包含退费               |
| select    | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |
|is_contain_stock|Integet| 是 | 是否包含库存 0:否  1:是 | 
|group_depa|Integet| 是 | 是否按销售部门分组  0:否  1:是 | 

### 销售报表导出html

> [GET]/report_service/sale/html

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                   |
| --------- | ------- | ---- | -------------------- |
| agen_id   | String  | 是    | 运营机构                 |
| depa_list | String  | 否    | 销售部门id(不选全部)         |
| begin     | String  | 是    | 开始时间                 |
| end       | String  | 是    | 结束时间                 |
| is_return | Integer | 否    | 是否包含退费               |
| select    | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |
|is_contain_stock|Integet| 是 | 是否包含库存 0:否  1:是 | 
|group_depa|Integet| 是 | 是否按销售部门分组  0:否  1:是 | 

###获取退费报表其他信息

> [GET]/report_service/sale/return/head

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明                   |
| --------- | ------ | ---- | -------------------- |
| agen_id   | String | 是    | 运营机构                 |
| depa_list | String | 否    | 销售部门id(不选全部)         |
| begin     | String | 是    | 开始时间                 |
| end       | String | 是    | 结束时间                 |
| select    | String | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| title      | String     | 是    | 标题        |
| flag       | String     | 是    | 标记        |
| head       | Object     | 是    | 副标题信息     |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |

副标题信息说明

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| prefix | String | 是    | 前缀   |
| suffix | String | 是    | 后缀   |

### 退费报表

> [GET]/report_service/sale/return

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 退费报表导出EXCEL

> [GET]/report_service/sale/return/excel

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明                   |
| --------- | ------ | ---- | -------------------- |
| agen_id   | String | 是    | 运营机构                 |
| depa_list | String | 否    | 销售部门id(不选全部)         |
| begin     | String | 是    | 开始时间                 |
| end       | String | 是    | 结束时间                 |
| select    | String | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

### 退费报表导出html

> [GET]/report_service/sale/return/html

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明                   |
| --------- | ------ | ---- | -------------------- |
| agen_id   | String | 是    | 运营机构                 |
| depa_list | String | 否    | 销售部门id(不选全部)         |
| begin     | String | 是    | 开始时间                 |
| end       | String | 是    | 结束时间                 |
| select    | String | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

###获取销售总报表其他信息

> [GET]/report_service/sale/total/head

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明                   |
| --------- | ------ | ---- | -------------------- |
| agen_id   | String | 是    | 运营机构                 |
| depa_list | String | 否    | 销售部门id(不选全部)         |
| begin     | String | 是    | 开始时间                 |
| end       | String | 是    | 结束时间                 |
| select    | String | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| title      | String     | 是    | 标题        |
| flag       | String     | 是    | 标记        |
| head       | Object     | 是    | 副标题信息     |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |

副标题信息说明

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| prefix | String | 是    | 前缀   |
| suffix | String | 是    | 后缀   |

### 销售总报表

> [GET]/report_service/sale/total

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |


### 销售总报表导出EXCEL

> [GET]/report_service/sale/total/excel

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明                   |
| --------- | ------ | ---- | -------------------- |
| agen_id   | String | 是    | 运营机构                 |
| depa_list | String | 否    | 销售部门id(不选全部)         |
| begin     | String | 是    | 开始时间                 |
| end       | String | 是    | 结束时间                 |
| select    | String | 是    | 供应商0，类别1，品牌2，品种3，细目4 |
| is_stage  | Integer | 是    | 不分期：0   分期：1  |

### 销售总报表导出html

> [GET]/report_service/sale/total/html

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明                   |
| --------- | ------ | ---- | -------------------- |
| agen_id   | String | 是    | 运营机构                 |
| depa_list | String | 否    | 销售部门id(不选全部)         |
| begin     | String | 是    | 开始时间                 |
| end       | String | 是    | 结束时间                 |
| select    | String | 是    | 供应商0，类别1，品牌2，品种3，细目4 |
| is_stage  | Integer | 是    | 不分期：0   分期：1  |

###获取入库报表其他信息

> [GET]/report_service/stock/in/head

#### 请求报文参数

| 参数名           | 类型      | 必填   | 说明                   |
| ------------- | ------- | ---- | -------------------- |
| agen_id       | String  | 是    | 运营机构                 |
| depo_list     | String  | 否    | 销售仓库id(不选全部)         |
| clas_id       | String  | 否    | 商品类别                 |
| bran_id       | String  | 否    | 商品品牌                 |
| vari_id       | String  | 否    | 商品品种                 |
| begin         | String  | 是    | 开始时间                 |
| end           | String  | 是    | 结束时间                 |
| in_type       | Integer | 是    | 入库类型                 |
| mfr_id        | String  | 否    | 供应商                  |
| out_depo_list | String  | 否    | 出库仓库id               |
| select        | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| title      | String     | 是    | 标题        |
| flag       | String     | 是    | 标记        |
| head       | Object     | 是    | 副标题信息     |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |

副标题信息说明

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| prefix | String | 是    | 前缀   |
| suffix | String | 是    | 后缀   |

### 入库报表

> [GET]/report_service/stock/in

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 入库报表导出EXCEL

> [GET]/report_service/stock/in/excel

#### 请求报文参数

| 参数名           | 类型      | 必填   | 说明                   |
| ------------- | ------- | ---- | -------------------- |
| agen_id       | String  | 是    | 运营机构                 |
| depo_list     | String  | 否    | 销售仓库id(不选全部)         |
| clas_id       | String  | 否    | 商品类别                 |
| bran_id       | String  | 否    | 商品品牌                 |
| vari_id       | String  | 否    | 商品品种                 |
| begin         | String  | 是    | 开始时间                 |
| end           | String  | 是    | 结束时间                 |
| in_type       | Integer | 是    | 入库类型                 |
| mfr_id        | String  | 否    | 供应商                  |
| out_depo_list | String  | 否    | 出库仓库id               |
| select        | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |
| is_stockflush        | Integer  | 否     | 选择采购入库类型时，是否仅统计冲红 0:否 1:是  |


### 入库报表导出html

> [GET]/report_service/stock/in/html

#### 请求报文参数

| 参数名           | 类型      | 必填   | 说明                   |
| ------------- | ------- | ---- | -------------------- |
| agen_id       | String  | 是    | 运营机构                 |
| depo_list     | String  | 否    | 销售仓库id(不选全部)         |
| clas_id       | String  | 否    | 商品类别                 |
| bran_id       | String  | 否    | 商品品牌                 |
| vari_id       | String  | 否    | 商品品种                 |
| begin         | String  | 是    | 开始时间                 |
| end           | String  | 是    | 结束时间                 |
| in_type       | Integer | 是    | 入库类型                 |
| mfr_id        | String  | 否    | 供应商                  |
| out_depo_list | String  | 否    | 出库仓库id               |
| select        | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |
| is_stockflush        | Integer  | 否     | 选择采购入库类型时，是否仅统计冲红 0:否 1:是  |


###获取出库报表其他信息

> [GET]/report_service/stock/out/head

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                   |
| ------------ | ------- | ---- | -------------------- |
| agen_id      | String  | 是    | 运营机构                 |
| depo_list    | String  | 否    | 销售仓库id(不选全部)         |
| clas_id      | String  | 否    | 商品类别                 |
| bran_id      | String  | 否    | 商品品牌                 |
| vari_id      | String  | 否    | 商品品种                 |
| begin        | String  | 是    | 开始时间                 |
| end          | String  | 是    | 结束时间                 |
| in_type      | Integer | 是    | 入库类型                 |
| mfr_id       | String  | 否    | 供应商                  |
| in_depo_list | String  | 否    | 入库仓库id               |
| select       | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| title      | String     | 是    | 标题        |
| flag       | String     | 是    | 标记        |
| head       | Object     | 是    | 副标题信息     |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |

副标题信息说明

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| prefix | String | 是    | 前缀   |
| suffix | String | 是    | 后缀   |

### 出库报表

> [GET]/report_service/stock/out

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 出库报表导出EXCEL

> [GET]/report_service/stock/out/excel

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                   |
| ------------ | ------- | ---- | -------------------- |
| agen_id      | String  | 是    | 运营机构                 |
| depo_list    | String  | 否    | 销售仓库id(不选全部)         |
| clas_id      | String  | 否    | 商品类别                 |
| bran_id      | String  | 否    | 商品品牌                 |
| vari_id      | String  | 否    | 商品品种                 |
| begin        | String  | 是    | 开始时间                 |
| end          | String  | 是    | 结束时间                 |
| in_type      | Integer | 是    | 入库类型                 |
| mfr_id       | String  | 否    | 供应商                  |
| in_depo_list | String  | 否    | 入库仓库id               |
| select       | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

### 出库报表导出html

> [GET]/report_service/stock/out/html

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                   |
| ------------ | ------- | ---- | -------------------- |
| agen_id      | String  | 是    | 运营机构                 |
| depo_list    | String  | 否    | 销售仓库id(不选全部)         |
| clas_id      | String  | 否    | 商品类别                 |
| bran_id      | String  | 否    | 商品品牌                 |
| vari_id      | String  | 否    | 商品品种                 |
| begin        | String  | 是    | 开始时间                 |
| end          | String  | 是    | 结束时间                 |
| in_type      | Integer | 是    | 入库类型                 |
| mfr_id       | String  | 否    | 供应商                  |
| in_depo_list | String  | 否    | 入库仓库id               |
| select       | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

###获取库存报表其他信息

> [GET]/report_service/stock/head

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                   |
| ------------ | ------- | ---- | -------------------- |
| agen_id      | String  | 是    | 运营机构                 |
| depo_list    | String  | 否    | 销售仓库id(不选全部)         |
| clas_id      | String  | 否    | 商品类别                 |
| bran_id      | String  | 否    | 商品品牌                 |
| vari_id      | String  | 否    | 商品品种                 |
| time         | String  | 是    | 时间                   |
| is_now       | Integer | 是    | 是否实时                 |
| in_depo_list | String  | 否    | 入库仓库id               |
| select       | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| title      | String     | 是    | 标题        |
| flag       | String     | 是    | 标记        |
| head       | Object     | 是    | 副标题信息     |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |

副标题信息说明

| 参数名    | 类型     | 必填   | 说明   |
| ------ | ------ | ---- | ---- |
| prefix | String | 是    | 前缀   |
| suffix | String | 是    | 后缀   |

### 库存报表

> [GET]/report_service/stock

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 库存报表导出EXCEL

> [GET]/report_service/stock/excel

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                   |
| ------------ | ------- | ---- | -------------------- |
| agen_id      | String  | 是    | 运营机构                 |
| depo_list    | String  | 否    | 销售仓库id(不选全部)         |
| clas_id      | String  | 否    | 商品类别                 |
| bran_id      | String  | 否    | 商品品牌                 |
| vari_id      | String  | 否    | 商品品种                 |
| time         | String  | 是    | 时间                   |
| is_now       | Integer | 是    | 是否实时                 |
| is_depo_group |Integer | 是    | 是否按仓库分组 0:不分组 1:分组          |
| in_depo_list | String  | 否    | 入库仓库id               |
| select       | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

### 库存报表导出html

> [GET]/report_service/stock/html

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                   |
| ------------ | ------- | ---- | -------------------- |
| agen_id      | String  | 是    | 运营机构                 |
| depo_list    | String  | 否    | 销售仓库id(不选全部)         |
| clas_id      | String  | 否    | 商品类别                 |
| bran_id      | String  | 否    | 商品品牌                 |
| vari_id      | String  | 否    | 商品品种                 |
| time         | String  | 是    | 时间                   |
| is_now       | Integer | 是    | 是否实时                 |
| is_depo_group |Integer | 是    | 是否按仓库分组 0:不分组 1:分组          |
| in_depo_list | String  | 否    | 入库仓库id               |
| select       | String  | 是    | 供应商0，类别1，品牌2，品种3，细目4 |

###获取进销存报表其他信息

> [GET]/report_service/stock/inout/head

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明            |
| --------- | ------- | ---- | ------------- |
| agen_id   | String  | 是    | 运营机构          |
| depo_list | String  | 否    | 销售仓库id(不选全部)  |
| begin     | String  | 是    | 开始时间          |
| end       | String  | 是    | 结束时间          |
| is_stock  | Integer | 是    | 按出入库汇总统计0否，1是 |

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| flag       | String     | 是    | 标记        |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |


### 进销存报表

> [GET]/report_service/stock/inout

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 进销存报表导出EXCEL

> [GET]/report_service/stock/inout/excel

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明            |
| --------- | ------- | ---- | ------------- |
| agen_id   | String  | 是    | 运营机构          |
| depo_list | String  | 否    | 销售仓库id(不选全部)  |
| begin     | String  | 是    | 开始时间          |
| end       | String  | 是    | 结束时间          |
| is_stock  | Integer | 是    | 按出入库汇总统计0否，1是 |
|is_depo_group|Integet| 是 | 是否按仓库分组  0:否  1:是 |

### 进销存报表导出html

> [GET]/report_service/stock/inout/html

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明            |
| --------- | ------- | ---- | ------------- |
| agen_id   | String  | 是    | 运营机构          |
| depo_list | String  | 否    | 销售仓库id(不选全部)  |
| begin     | String  | 是    | 开始时间          |
| end       | String  | 是    | 结束时间          |
| is_stock  | Integer | 是    | 按出入库汇总统计0否，1是 |
|is_depo_group|Integet| 是 | 是否按仓库分组  0:否  1:是 |


###获取进销存报表其他信息（温州）

> [GET]/report_service/stock/inout/head/wenzhou

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明           |
| --------- | ------- | ---- | ------------ |
| agen_id   | String  | 是    | 运营机构         |
| depo_list | String  | 否    | 销售仓库id(不选全部) |
| begin     | String  | 是    | 开始时间         |
| end       | String  | 是    | 结束时间         |
| is_detail | Integer | 是    | 是否为明细版0否，1是  |

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| flag       | String     | 是    | 标记        |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |


### 进销存报表（温州）

> [GET]/report_service/stock/inout/wenzhou

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 进销存报表导出EXCEL（温州）

> [GET]/report_service/stock/inout/excel/wenzhou

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明           |
| --------- | ------- | ---- | ------------ |
| agen_id   | String  | 是    | 运营机构         |
| depo_list | String  | 否    | 销售仓库id(不选全部) |
| begin     | String  | 是    | 开始时间         |
| end       | String  | 是    | 结束时间         |
| is_detail | Integer | 是    | 是否为明细版0否，1是  |

### 进销存报表导出html（温州）

> [GET]/report_service/stock/inout/html/wenzhou

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明           |
| --------- | ------- | ---- | ------------ |
| agen_id   | String  | 是    | 运营机构         |
| depo_list | String  | 否    | 销售仓库id(不选全部) |
| begin     | String  | 是    | 开始时间         |
| end       | String  | 是    | 结束时间         |
| is_detail | Integer | 是    | 是否为明细版0否，1是  |



### 赠送报表

> [GET]/report_service/other/gift

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 赠送报表导出EXCEL

> [GET]/report_service/other/gift/excel

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明           |
| --------- | ------ | ---- | ------------ |
| agen_id   | String | 是    | 运营机构         |
| depa_list | String | 否    | 销售仓库id(不选全部) |
| begin     | String | 是    | 开始时间         |
| end       | String | 是    | 结束时间         |

### 赠送报表导出html

> [GET]/report_service/other/gift/html

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明           |
| --------- | ------ | ---- | ------------ |
| agen_id   | String | 是    | 运营机构         |
| depa_list | String | 否    | 销售仓库id(不选全部) |
| begin     | String | 是    | 开始时间         |
| end       | String | 是    | 结束时间         |


###获取赠送报表其他信息

>  [GET]/report_service/other/gift/head

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明           |
| --------- | ------ | ---- | ------------ |
| agen_id   | String | 是    | 运营机构         |
| depo_list | String | 否    | 销售仓库id(不选全部) |
| begin     | String | 是    | 开始时间         |
| end       | String | 是    | 结束时间         |

#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| flag       | String     | 是    | 标记        |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |


### 工作量报表

> [GET]/report_service/other/work

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 工作量报表导出EXCEL

> [GET]/report_service/other/work/excel

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明           |
| --------- | ------- | ---- | ------------ |
| agen_id   | String  | 是    | 运营机构         |
| depa_list | String  | 否    | 销售仓库id(不选全部) |
| begin     | String  | 是    | 开始时间         |
| end       | String  | 是    | 结束时间         |
| type      | Integer | 是    | 0,1,2        |

### 工作量报表导出html

> [GET]/report_service/other/work/html

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明           |
| --------- | ------- | ---- | ------------ |
| agen_id   | String  | 是    | 运营机构         |
| depa_list | String  | 否    | 销售仓库id(不选全部) |
| begin     | String  | 是    | 开始时间         |
| end       | String  | 是    | 结束时间         |
| type      | Integer | 是    | 0,1,2        |


###获取工作量报表其他信息

>  [GET]/report_service/other/work/head

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明           |
| --------- | ------- | ---- | ------------ |
| agen_id   | String  | 是    | 运营机构         |
| depo_list | String  | 否    | 销售仓库id(不选全部) |
| begin     | String  | 是    | 开始时间         |
| end       | String  | 是    | 结束时间         |
| type      | Integer | 是    | 0,1,2        |


#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| flag       | String     | 是    | 标记        |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |


### 商品折扣报表

> [GET]/report_service/other/discount

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 商品折扣报表导出EXCEL

> [GET]/report_service/other/discount/excel

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明           |
| --------- | ------- | ---- | ------------ |
| agen_id   | String  | 是    | 运营机构         |
| depa_list | String  | 否    | 销售部门id(不选全部) |
| begin     | String  | 是    | 开始时间         |
| end       | String  | 是    | 结束时间         |
| type      | Integer | 是    | 0 明细,1汇总     |

### 商品折扣报表导出html

> [GET]/report_service/other/discount/html

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明           |
| --------- | ------- | ---- | ------------ |
| agen_id   | String  | 是    | 运营机构         |
| depa_list | String  | 否    | 销售部门id(不选全部) |
| begin     | String  | 是    | 开始时间         |
| end       | String  | 是    | 结束时间         |
| type      | Integer | 是    | 0 明细,1汇总     |


###获取商品折扣报表其他信息

>  [GET]/report_service/other/discount/head

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明           |
| --------- | ------- | ---- | ------------ |
| agen_id   | String  | 是    | 运营机构         |
| depa_list | String  | 否    | 销售部门id(不选全部) |
| begin     | String  | 是    | 开始时间         |
| end       | String  | 是    | 结束时间         |
| type      | Integer | 是    | 0 明细,1汇总     |


#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| flag       | String     | 是    | 标记        |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |

### 商品调价报表

> [GET]/report_service/other/adjust

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 商品调价报表导出EXCEL

> [GET]/report_service/other/adjust/excel

#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明       |
| ------- | ------- | ---- | -------- |
| agen_id | String  | 是    | 运营机构     |
| begin   | String  | 是    | 开始时间     |
| end     | String  | 是    | 结束时间     |
| type    | Integer | 是    | 0 清单,1汇总 |

### 商品调价报表导出html

> [GET]/report_service/other/adjust/html

#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明       |
| ------- | ------- | ---- | -------- |
| agen_id | String  | 是    | 运营机构     |
| begin   | String  | 是    | 开始时间     |
| end     | String  | 是    | 结束时间     |
| type    | Integer | 是    | 0 清单,1汇总 |


###获取商品调价报表其他信息

>  [GET]/report_service/other/adjust/head

#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明       |
| ------- | ------- | ---- | -------- |
| agen_id | String  | 是    | 运营机构     |
| begin   | String  | 是    | 开始时间     |
| end     | String  | 是    | 结束时间     |
| type    | Integer | 是    | 0 清单,1汇总 |


#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| flag       | String     | 是    | 标记        |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |

## 第二期

### 商品调价报表

> [GET]/report_service/other/adjust

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

### 商品调价报表导出EXCEL

> [GET]/report_service/other/adjust/excel

#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明       |
| ------- | ------- | ---- | -------- |
| agen_id | String  | 是    | 运营机构     |
| begin   | String  | 是    | 开始时间     |
| end     | String  | 是    | 结束时间     |
| type    | Integer | 是    | 0 清单,1汇总 |

### 商品调价报表导出html

> [GET]/report_service/other/adjust/html

#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明       |
| ------- | ------- | ---- | -------- |
| agen_id | String  | 是    | 运营机构     |
| begin   | String  | 是    | 开始时间     |
| end     | String  | 是    | 结束时间     |
| type    | Integer | 是    | 0 清单,1汇总 |


###获取商品调价报表其他信息

>  [GET]/report_service/other/adjust/head

#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明       |
| ------- | ------- | ---- | -------- |
| agen_id | String  | 是    | 运营机构     |
| begin   | String  | 是    | 开始时间     |
| end     | String  | 是    | 结束时间     |
| type    | Integer | 是    | 0 清单,1汇总 |


#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| flag       | String     | 是    | 标记        |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |

### 净入库报表

> [GET]/report_service/other/net_storage

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明   |
| ---- | ------ | ---- | ---- |
| flag | String | 是    | 标记   |

###  净入库报表导出EXCEL

> [GET]/report_service/other/net_storage/excel

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| depo_list | String  | 否    | 仓库id(不选全部) |
| begin     | String  | 是    | 开始时间       |
| end       | String  | 是    | 结束时间       |
| clas_id   | String  | 否    | 商品类别       |
| bran_id   | String  | 否    | 商品品牌       |
| vari_id   | String  | 否    | 商品品种       |
| select    | Integer | 是    | 分组小计       |

###  净入库报表导出html

> [GET]/report_service/other/net_storage/html

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| depo_list | String  | 否    | 仓库id(不选全部) |
| begin     | String  | 是    | 开始时间       |
| end       | String  | 是    | 结束时间       |
| clas_id   | String  | 否    | 商品类别       |
| bran_id   | String  | 否    | 商品品牌       |
| vari_id   | String  | 否    | 商品品种       |
| select    | Integer | 是    | 分组小计       |


###获取净入库报表其他信息

>  [GET]/report_service/other/net_storage/head

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| depo_list | String  | 否    | 仓库id(不选全部) |
| begin     | String  | 是    | 开始时间       |
| end       | String  | 是    | 结束时间       |
| clas_id   | String  | 否    | 商品类别       |
| bran_id   | String  | 否    | 商品品牌       |
| vari_id   | String  | 否    | 商品品种       |
| select    | Integer | 是    | 分组小计       |


#### 回复报文参数

| 参数名        | 类型         | 必填   | 说明        |
| ---------- | ---------- | ---- | --------- |
| flag       | String     | 是    | 标记        |
| table_head | ObjectList | 是    | 表的列头信息    |
| is_child   | Integer    | 是    | 是否存在单元格合并 |

表的列头信息说明

| 参数名    | 类型         | 必填   | 说明         |
| ------ | ---------- | ---- | ---------- |
| name   | String     | 是    | 名称         |
| width  | Integer    | 是    | 宽度         |
| is_sum | Integer    | 是    | 是否是参与合计的字段 |
| sum    | String     | 否    | 合计值        |
| child  | ObjectList | 否    | 子列头        |


### 销售退货报表导出EXCEL

> [GET]/report_service/other/sale_return/excel

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| depa_list | String  | 否    | 销售部门id(不选全部) |
| begin     | String  | 是    | 开始时间       |
| end       | String  | 是    | 结束时间       |


###  销售退货报表导出html

> [GET]/report_service/other/sale_return/html

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| depa_list | String  | 否    | 销售部门id(不选全部) |
| begin     | String  | 是    | 开始时间       |
| end       | String  | 是    | 结束时间       |

### 库存批次报表导出EXCEL

> [GET]/report_service/other/batch_stock/excel

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| depo_list | String  | 否    | 仓库id(不选全部) |
| is_now     | Integer  | 是    | 0实时，1历史       |
| time       | String  | 否    | 时间       |
| clas_id   | String  | 否    | 商品类别       |
| bran_id   | String  | 否    | 商品品牌       |
| vari_id   | String  | 否    | 商品品种       |
| is_depo_group |Integer | 是    | 是否按仓库分组 0:不分组 1:分组          |


### 库存批次报表导出html

> [GET]/report_service/other/batch_stock/html

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| depo_list | String  | 否    | 仓库id(不选全部) |
| is_now     | Integer  | 是    | 0实时，1历史       |
| time       | String  | 否    | 时间       |
| clas_id   | String  | 否    | 商品类别       |
| bran_id   | String  | 否    | 商品品牌       |
| vari_id   | String  | 否    | 商品品种       |
| is_depo_group |Integer | 是    | 是否按仓库分组 0:不分组 1:分组          |


## 第三期


###视光数据对比报表导出EXCEL

> [GET]/report_service/other/data_compare/excel

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.1 | 新增 |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| clas_id       | String  | 否    | 商品类别    可以多个 |
| type     | Integer  | 是    | 1库存，2销售额 3采购量       |
| begin_time1       | String  | 是    | 时段1 开始时间       |
| end_time1       | String  | 是    | 时段1 结束时间      |
| begin_time2       | String  | 是    | 时段2 开始时间       |
| end_time2       | String  | 是    | 时段2 结束时间      |


###视光数据对比报表导出html

> [GET]/report_service/other/data_compare/html

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.1 | 新增 |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| clas_id       | String  | 否    | 商品类别    可以多个 |
| type     | Integer  | 是    | 1库存，2销售额 3采购量       |
| begin_time1       | String  | 是    | 时段1 开始时间       |
| end_time1       | String  | 是    | 时段1 结束时间      |
| begin_time2       | String  | 是    | 时段2 开始时间       |
| end_time2       | String  | 是    | 时段2 结束时间      |

###视光数据对比报表导出pdf

> [GET]/report_service/other/data_compare/pdf

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.1 | 新增 |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| clas_id       | String  | 否    | 商品类别    可以多个 |
| type     | Integer  | 是    | 1库存，2销售额 3采购量       |
| begin_time1       | String  | 是    | 时段1 开始时间       |
| end_time1       | String  | 是    | 时段1 结束时间      |
| begin_time2       | String  | 是    | 时段2 开始时间       |
| end_time2       | String  | 是    | 时段2 结束时间      |


###供应商销售报表导出EXCEL

> [GET]/report_service/other/supplier_sale/excel

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.1 | 新增 |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| clas_id       | String  | 否    | 商品类别    可以多个 |
| supplier_id       | String  | 否    | 供应商    可以多个 |
| begin_time1       | String  | 是    | 时段1 开始时间       |
| end_time1       | String  | 是    | 时段1 结束时间      |
| begin_time2       | String  | 是    | 时段2 开始时间       |
| end_time2       | String  | 是    | 时段2 结束时间      |


###供应商销售报表导出html

> [GET]/report_service/other/supplier_sale/html

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.1 | 新增 |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| clas_id       | String  | 否    | 商品类别    可以多个 |
| supplier_id       | String  | 否    | 供应商    可以多个 |
| begin_time1       | String  | 是    | 时段1 开始时间       |
| end_time1       | String  | 是    | 时段1 结束时间      |
| begin_time2       | String  | 是    | 时段2 开始时间       |
| end_time2       | String  | 是    | 时段2 结束时间      |


###供应商销售报表导出pdf

> [GET]/report_service/other/supplier_sale/pdf

####修改更新记录

|  对应业务 | 说明 |
|-----------|------|
| V1.2.2.1 | 新增 |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| clas_id       | String  | 否    | 商品类别    可以多个 |
| supplier_id       | String  | 否    | 供应商    可以多个 |
| begin_time1       | String  | 是    | 时段1 开始时间       |
| end_time1       | String  | 是    | 时段1 结束时间      |
| begin_time2       | String  | 是    | 时段2 开始时间       |
| end_time2       | String  | 是    | 时段2 结束时间      |



## hotfix/V1.2.3.1


### 供应商采购流水导出

> [GET]/report_service/other/supplier_buy/{mode}

#### 请求报文参数

####PathVariable

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| mode   | String  | 是    | 模式 pdf/excel/html       |


####RequestBody

| 参数名       | 类型      | 必填   | 说明         |
| --------- | ------- | ---- | ---------- |
| agen_id   | String  | 是    | 运营机构       |
| depo_list | String  | 否    | 仓库id(不选全部 可以多个) |
| supplier_id       | String  | 否    | 供应商  (不选全部 可以多个) |
| begin       | String  | 是    | 开始时间       |
| end       | String  | 是    | 结束时间      |




