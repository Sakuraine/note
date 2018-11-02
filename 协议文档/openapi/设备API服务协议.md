# 设备服务协议

版本：V1.0(20190910)

## 说明

本文档用于描述提供给 APPWEB 使用的接口协议，本文档协议为OpenApi协议族的子集，所有通讯规范请遵守《OpenApi接口说明》。

## 协议内容

### AppWeb最新版本

```url
[GET]/device/appweb/last/version
```

说明：
1. 由WEB页面反APPWEB注册到服务端上。

#### 修改更新记录

|    对应业务    | 说明 |
|----------------|------|
| 后台服务V1.0.3 | 新增 |

#### 请求报文参数

| 参数名 | 长度 | 类型 | 必填 | 说明 |
|--------|------|------|------|------|
|        |      |      |      |      |

#### 回复报文参数

| 参数名  |  类型  | 必填 |   说明   |
|---------|--------|------|----------|
| version | String | 是   | 版本     |
| time    | String | 是   | 发布时间 |
| url     | String | 是   | 下载地址 |

### AppWeb状态上报协议

```url
[POST]/device/appweb/status
```

说明：
1. 上报appweb的状态，说自己还活着。
2. 如果appweb未注册，那么打回。
3. 租户ID可以不传，但如果传了就必须与注册时使用的租户号一致。

#### 修改更新记录

|    对应业务    | 说明 |
|----------------|------|
| 后台服务V1.0.3 | 新增 |

#### 影响的表

AppWeb信息状态表(appweb_state_info)

#### 请求报文参数

|     参数名      | 长度 |   类型  | 必填 |           说明           |
|-----------------|------|---------|------|--------------------------|
| appweb_code     |   64 | String  | 是   | 程序标识，从APPWEB中获取 |
| appweb_version  |      | String  | 否   | 程序版本，从APPWEB中获取 |
| appweb_host     |      | String  | 否   | 所在主机地址             |
| appweb_port     |      | Integer | 否   | 服务端口                 |
| appweb_ssl_port |      | Integer | 否   | 服务HTTPS端口            |
| appweb_tena_id  |      | String  | 否   | 租户ID                   |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
|        |      |      |      |

### AppWeb操作记录协议

```url
[POST]/device/appweb/operating_record
```

说明：
1. 上报appweb的操作记录，现阶段并不落地。

#### 修改更新记录

|    对应业务    | 说明 |
|----------------|------|
| 后台服务V1.0.3 | 新增 |

#### 影响的表

暂不落地

#### 请求报文参数

|     参数名      |  类型  | 必填 |        说明        |
|-----------------|--------|------|--------------------|
| appweb_code     | String | 是   | 程序标识           |
| appweb_url      | String | 是   | 操作的地址         |
| appweb_user     | String | 是   | 操作的人           |
| appweb_request  | String | 否   | 操作请求报文       |
| appweb_response | String | 是   | 操作回复报文       |
| appweb_time     | String | 否   | 操作时间，单位毫秒 |
| appweb_tena_id  | String | 否   | 租户ID             |

#### 回复报文参数

|   参数名    | 长度 |  类型  | 必填 |   说明   |
|-------------|------|--------|------|----------|
| appweb_code |   64 | String | 否   | 程序标识 |


### 角膜地形图文件预上传

```http
[POST]/device/appweb/file_cornea/pre_upload
```

说明：
  获取oss地址，文件名等信息
  设备未注册，不允许调用协议

#### 修改更新记录

|   对应业务  | 说明 |
|-------------|------|
| Web 1.3.3.1 | 新增 |


#### 请求报文参数

|     参数名     |   类型  | 必填 |              说明              |
|----------------|---------|------|--------------------------------|
| appweb_code    | String  | 是   | 程序标识                       |
| file_size      | Long    | 否   | 文件内容长度                   |
| file_extension | String  | 是   | 文件扩展名(不带“.“)            |
| file_type      | String  | 是   | 文件类型，Content-Type         |
| source_type    | Integer | 是   | 14 角膜地形图导出的MXF文件     |
| tenant_id      | String  | 否   | 租户id 为空 由 appweb_code决定 |


#### 回复报文参数

|      参数名       |  类型  | 必填 |             说明             |
|-------------------|--------|------|------------------------------|
| url               | String | 是   | 文件上传的oss的URL           |
| file_id           | Long   | 是   | 文件资源id                   |
| OSS_access_key_id | String | 是   | Bucket 拥有者的Access Key Id |
| policy            | String | 是   | Base64编码的JSON内容         |
| signature         | String | 是   | 签名                         |
| key               | String | 是   | 上传文件路径                 |


### 角膜地形图文件 确认已上传

```http
[POST]/device/appweb/file_cornea/pre_upload
```

说明：
  确认file_id对应的文件

#### 修改更新记录

|   对应业务  | 说明 |
|-------------|------|
| Web 1.3.3.1 | 新增 |


#### 请求报文参数

|   参数名    |  类型  | 必填 |              说明              |
|-------------|--------|------|--------------------------------|
| appweb_code | String | 是   | 程序标识                       |
| file_id     | Long   | 是   | 文件资源id                     |
| tenant_id   | String | 否   | 租户id 为空 由 appweb_code决定 |


#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |

#### 上传完成之后发消息

队列名称: SC_CORNEA_ANALYSIS

RedisDB: 15

涉及表：check_cornea_topog_file

消息队列的内容是:

| 参数名  |  类型  | 必填 |     说明     |
|---------|--------|------|--------------|
| file_id | String | 是   | 地形图文件ID |


