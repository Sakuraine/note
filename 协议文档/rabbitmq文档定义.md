## rabbitmq


### 权限设置

| 服务名       | 用户名    | 密码         | 可读队列                                                  | 可写交换机                                                   |
| ------------ | --------- | ------------ | --------------------------------------------------------- | ------------------------------------------------------------ |
| search       | search    | search123       | patient_register_queue                                    | patient_update_exchange                                      |
| schedule     | schedule  | schedule456  | cornea_topog_file_queue                                   |                                                              |
| patient      | patient   | patient123   | patient_initialize_data_queue,patient_sync_update_queue   |                                                              |
| pharmacy     | pharmacy  | pharmacy456  | drug_directory_data_queue,drug_stock_data_queue           |                                                              |
| optometry    | optometry | optometry123 | erp_goods_directory_data_queue,erp_goods_stock_data_queue |                                                              |
| device       | device    | device456    |                                                           | initlalize_data_exchange,cornea_topog_file_exchange          |
| outemr       | outemr    | outemr123    |                                                           | initlalize_data_exchange,patient_exchange,cornea_topog_file_exchange |
| webresultful | web       | web456       |                                                           | initlalize_data_exchange                                     |
| public       | public    | public123    |                                                           | patient_exchange                                             |

#### 设置权限命令

```
rabbitmqctl  add_user  search  search123
rabbitmqctl  set_user_tags  search  none
rabbitmqctl set_permissions -p / search "" "patient_update_exchange" "patient_register_queue"

rabbitmqctl  add_user  schedule  schedule456
rabbitmqctl  set_user_tags  schedule  none
rabbitmqctl set_permissions -p / schedule "" "" "cornea_topog_file_queue"

rabbitmqctl  add_user  patient  patient123
rabbitmqctl  set_user_tags  patient  none
rabbitmqctl set_permissions -p / patient "" "" "patient_initialize_data_queue,patient_sync_update_queue"

rabbitmqctl  add_user  pharmacy  pharmacy456
rabbitmqctl  set_user_tags  pharmacy  none
rabbitmqctl set_permissions -p / pharmacy "" "" "drug_directory_data_queue,drug_stock_data_queue"

rabbitmqctl  add_user  optometry  optometry123
rabbitmqctl  set_user_tags  optometry  none
rabbitmqctl set_permissions -p / optometry "" "" "erp_goods_directory_data_queue,erp_goods_stock_data_queue"

rabbitmqctl  add_user  device  device456
rabbitmqctl  set_user_tags  device  none
rabbitmqctl set_permissions -p / device "" "initlalize_data_exchange,cornea_topog_file_exchange" ""

rabbitmqctl  add_user  outemr  outemr123
rabbitmqctl  set_user_tags  outemr  none
rabbitmqctl set_permissions -p / outemr "" "initlalize_data_exchange,patient_exchange,cornea_topog_file_exchange" ""

rabbitmqctl  add_user  web  web456
rabbitmqctl  set_user_tags  web  none
rabbitmqctl set_permissions -p / web "" "initlalize_data_exchange" ""

rabbitmqctl  add_user  public  public123
rabbitmqctl  set_user_tags  public  none
rabbitmqctl set_permissions -p / public "" "patient_exchange" ""
```

### 开发约定


| 队列                           | 路由键              | 交换机                     | 分发方式 | 消息处理服务 | 说明                             |
| ------------------------------ | ------------------- | -------------------------- | -------- | ------------ | -------------------------------- |
| patient_register_queue         |                     | patient_exchange           | fanout   | search       | 患者建档队列，患者信息同步ES     |
| cornea_topog_file_queue        | cornea_topog        | cornea_topog_file_exchange | direct   | schedule     | 角膜地形图分析                   |
| patient_initialize_data_queue  | patient_initialize  | initlalize_data_exchange   | direct   | patient      | 初始化模板文件分析(患者信息文件) |
| drug_directory_data_queue      | drug_directory      | initlalize_data_exchange   | direct   | pharmacy     | 初始化模板文件分析(药品目录文件) |
| drug_stock_data_queue          | drug_stock          | initlalize_data_exchange   | direct   | pharmacy     | 初始化模板文件分析(药品库存文件) |
| erp_goods_directory_data_queue | erp_goods_directory | initlalize_data_exchange   | direct   | optometry    | 初始化模板文件分析(商品目录文件) |
| erp_goods_stock_data_queue     | erp_goods_stock     | initlalize_data_exchange   | direct   | optometry    | 初始化模板文件分析(商品库存文件) |
| patient_sync_update_queue      | patient_sync        | patient_update_exchange    | direct   | patient      | 患者信息更新同步标志             |


### 涉及的业务

#### 患者信息同步

* public、outemr和patient中所有更新adm_patient的都要发送消息到patient_register_queue队列来更新ES中的患者数据
* 更新完成之后发送消息到patient_sync_update_queue队列来更新数据库的同步标志字段

#### 角膜地形图上传

* device服务中`/device/appweb/file_cornea/pre_upload`角膜地形图上传确认后发送消息到cornea_topog_file_queue队列中来进行分析数据
* outemr服务中`/outemr/file/file_cornea/upload_access`角膜地形图上传确认后发送消息到cornea_topog_file_queue队列中来进行分析数据

#### 模板文件上传

* web-resultful服务中`/template_data/initialize/upload_access`上传完成后发送消息到对应的队列
* 发送完成后不同的消息再对应不同的服务去处理消息；





