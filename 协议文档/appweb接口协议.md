[TOC]

# appweb接口协议  

## 版本说明

* 2018.05.22 v1.0.0
  新建文档
* 2018.08.21 v1.1.0
  1. 获得版本号内容修改为获得appweb信息
  2. 获得注册信息(主要作用为页面注册后返回注册信息给appweb)

## 状态码

| 状态码 | 说明              |
|-----|-----------------|
| 000 | 成功              |
| 300 | 下载PDF文件出错       |
| 403 | 打印机名字为空或没有打印机名字 |
| 501 | 无该类型的设备         |
| 502 | 无该设备            |
| 502 | 打开设备失败          |
| 503 | 获得数据失败          |
| 999 | 失败              |

## 设备类型

| 类型码 | 说明  |
|-----|-----|
| 1   | 验光机 |
| 2   | 眼压机 |

## 协议地址  

| 请求方式  | 默认地址                                | 说明       |
|-------|-------------------------------------|----------|
| http  | http://127.0.0.1:38785              | V1.0.0新增 |
| https | https://appweb.best-seeing.cn:38786 | V1.2.4新增 |

* 注1：实际端口号可以配置，默认的http为38785，https为38786。

## 接口协议

### 获得版本

```http
[GET]/api/version
```

#### 修改更新记录

| 对应业务   | 说明 |
|--------|----|
| V1.0.0 | 新增 |

#### 请求参数

| 参数名 | 必选 | 类型 | 说明 |
|-----|----|----|----|
|     |    |    |    |

#### 返回参数

| 参数名    | 类型     | 说明     |
|--------|--------|--------|
| status | string | 状态码    |
| data   | object | 返回版本数据 |

##### 返回版本数据

| 参数名        | 类型     | 说明              |
|------------|--------|-----------------|
| version    | string | 版本号             |
| appwebcode | string | appweb唯一标识      |
| status     | bool   | appweb是否已经注册的标志 |

#### 返回示例

```json
{
    "status": "000",
    "data": {
        "version": "1.0.0",
        "appwebcode": "********",
        "status": true
    }
}
```

### 注册appweb

```http
[POST]/api/register
```

#### 修改更新记录

| 对应业务   | 说明                        |
|--------|---------------------------|
| V1.2.4 | 新增(提供appweb注册结果信息给appweb) |

#### 请求参数  

| 参数名        | 必选 | 类型     | 说明                              |
|------------|----|--------|---------------------------------|
| status     | 是  | bool   | 注册状态(true-已注册或注册成功, false-注册失败) |
| url        | 是  | string | 提供url等给appweb使用                 |
| appwebcode | 是  | string | appwebcode唯一标识                  |
| error      | 否  | string | 注册失败原因                          |

#### 返回参数

| 参数名    | 类型     | 说明  |
|--------|--------|-----|
| status | string | 状态码 |

#### 返回示例

```json
{
    "status": "000"
}
```

###  读芯片卡信息

```http
[GET]/api/read_card
```

#### 修改更新记录

| 对应业务   | 说明 |
|--------|----|
| V1.0.0 | 新增 |

#### 请求参数  

| 参数名 | 必选 | 类型 | 说明 |
|-----|----|----|----|
|     |    |    |    |

#### 返回参数

| 参数名     | 类型     | 说明              |
|---------|--------|-----------------|
| status  | string | 状态码             |
| message | string | 错误信息，状态为999时候必选 |
| data    | object | 返回芯片卡信息         |

##### 芯片卡信息

| 参数名            | 类型     | 说明     |
|----------------|--------|--------|
| return_message | string | 读卡返回信息 |

#### 返回示例

```json
{
    "status": "999",
    "message": "$$-1~1050%读卡实现函数(f_ReadCard):(读卡操作错误码[-2]:无卡！)%0%错误原因:$$"
}

{
    "status": "000",
    "data": {
        "return_message": "****||***||***||||"
    }
}
```

###  获得打印机列表

```http
[GET]/api/list_printers  
``` 

#### 修改更新记录

| 对应业务   | 说明 |
|--------|----|
| V1.0.0 | 新增 |

#### 请求参数

| 参数名 | 必选 | 类型 | 说明 |
|-----|----|----|----|
|     |    |    |    |

#### 返回参数

| 参数名    | 类型     | 说明      |
|--------|--------|---------|
| status | string | 状态码     |
| data   | array  | 打印机列表数据 |

##### 打印机列表数据

| 参数名      | 类型     | 说明      |
|----------|--------|---------|
| name     | string | 打印机名称   |
| selected | bool   | 是否默认打印机 |

#### 返回示例  

```json
{
    "status": "000",
    "data": [
        {
            "name": "hpprinter",
            "selected": true
        },
        {
            "name": "Foxit Reader PDF Printer"
        },
        {
            "name": "Fax"
        },
        {
            "name": "epson"
        }
    ]
}
```

###  获得默认打印机名称

```http
[GET]/api/get_default_printer  
```

#### 修改更新记录

| 对应业务   | 说明 |
|--------|----|
| V1.0.0 | 新增 |

#### 请求参数

| 参数名 | 必选 | 类型 | 说明 |
|-----|----|----|----|
|     |    |    |    |

#### 返回参数

| 参数名    | 类型     | 说明        |
|--------|--------|-----------|
| status | string | 状态码       |
| data   | object | 返回默认打印机名称 |

##### 默认打印机名称

| 参数名  | 类型     | 说明      |
|------|--------|---------|
| name | string | 默认打印机名称 |

#### 返回示例

```json
{
    "status": "000",
    "data": {
        "printer": "hpprinter"
    }
}
```

### 设置默认打印机

```http
[POST]/api/set_default_printer
``` 

#### 修改更新记录

| 对应业务   | 说明            |
|--------|---------------|
| V1.0.0 | 新增(实际中该接口未使用) |

#### 请求参数

| 参数名     | 必选 | 类型     | 说明    |
|---------|----|--------|-------|
| printer | 是  | string | 打印机名称 |

#### 返回参数

| 参数名    | 类型     | 说明  |
|--------|--------|-----|
| status | string | 状态码 |

#### 返回示例

```json
{
    "status": "000"
}
{
    "status": "999"
}
```

### 打印文档  

```http
[POST,OPTIONS]/api/start_print  
```

* OPTIONS请求仅仅用来表示支持重定向的内容，并不会执行实际的打印动作。  

#### 修改更新记录

| 对应业务   | 说明 |
|--------|----|
| V1.0.0 | 新增 |

#### 请求参数

| 参数名       | 必选 | 类型     | 说明      |
|-----------|----|--------|---------|
| url       | 是  | string | pdf文件地址 |
| printer   | 是  | string | 打印机名称   |
| paperSize | 是  | string | 纸张大小    |

##### 纸张大小

输入参数2种格式：  
1. paperSize: "宽,高,方向"   
2. paperSize: "A4"   

| 参数 | 说明            |
|----|---------------|
| ,  | 参数间的分隔符       |
| 宽高 | 采用cm为单位的大小    |
| 方向 | 0-表示纵向，1-表示横向 |

例子：  
1. A4纸张打印  
paperSize: "A4"  
2. A5纸张打印  
paperSize: "A4"  
3. 纸张大小：19.1cm *11.4cm 纵向  
pagerSize: "19.1,11.4,0"  
4. 纸张大小：19.1cm *11.4cm 横向  
pagerSize: "19.1,11.4,1"  

**注意**  
* A4,A5纸张大小打印方向采用打印机自适应的的方向。   

#### 返回参数

| 参数名    | 类型     | 说明  |
|--------|--------|-----|
| status | string | 状态码 |

#### 返回示例  

```json
{
    "status": "000"
}
```

###  获得医疗设备列表   

```http
[POST]/api/list_medical_devices   
``` 

#### 修改更新记录

| 对应业务     | 说明       |
|----------|----------|
| V1.1.4.3 | 新增       |
| V1.2.0   | 自该版本废弃接口 |

#### 请求参数

| 参数名  | 必选 | 类型     | 说明       |
|------|----|--------|----------|
| type | 是  | string | 参考设备类型说明 |

#### 返回参数

| 参数名     | 类型     | 说明   |
|---------|--------|------|
| status  | string | 状态码  |
| message | string | 错误信息 |
| data    | array  | 医疗设备 |

##### 医疗设备

| 参数名  | 类型     | 说明       |
|------|--------|----------|
| id   | string | 设备唯一标识符  |
| name | string | 设备名称     |
| type | string | 参考设备类型说明 |

#### 返回示例

```json
{
    "status": "000",
    "data": [
        {
            "id": "1", 
            "name": "KR-8900", 
            "type": "1"
        },
        {
            "id": "2", 
            "name": "KR-8800", 
            "type": "2"
        }
    ]
}

{
    "status": "501",
    "message": "无该类型的设备"
}
```

### 获得医疗设备数据

```http
[POST]/api/get_medical_device_data 
```

| 对应业务     | 说明       |
|----------|----------|
| V1.1.4.3 | 新增       |
| V1.2.0   | 自该版本废弃接口 |

#### 请求参数

| 参数名 | 必选 | 类型     | 说明    |
|-----|----|--------|-------|
| id  | 是  | string | 设备标识符 |

#### 返回参数

| 参数名     | 类型     | 说明   |
|---------|--------|------|
| status  | string | 状态码  |
| message | string | 错误信息 |
| data    | array  | 设备数据 |

##### 设备数据

| 参数名        | 类型     | 说明      |
|------------|--------|---------|
| odSphere   | string | 验光OD-球镜 |
| odCylinder | string | 验光OD-柱镜 |
| odAxis     | string | 验光OD-轴向 |
| osSphere   | string | 验光Os-球镜 |
| osCylinder | string | 验光Os-柱镜 |
| osAxis     | string | 验光Os-柱镜 |
| nearPd     | string | 瞳距-近用   |

#### 返回示例

```json
{
    "status": "000",
    "data": [
        {
            "odSphere": "-13.25", 
            "odCylinder": "-0.75", 
            "odAxis": "20",
            "osSphere": "-12.50", 
            "osCylinder": "-1.25", 
            "osAxis": "130",
            "nearPd": "62"
        }
    ]
}

{
    "status": "502",
    "message": "无该设备"
}
```

### 获得验光设备数据

```http
[GET]/api/optometry 
``` 

| 对应业务   | 说明                        |
|--------|---------------------------|
| V1.2.4 | 新增                        |
| V1.2.5 | 修改，返回的验光数据中增加(附加、瞳距、瞳高数据) |

#### 请求参数

| 参数名 | 必选 | 类型     | 说明    |
|-----|----|--------|-------|
|||||

#### 返回参数

| 参数名     | 类型     | 说明   |
|---------|--------|------|
| status  | string | 状态码  |
| message | string | 错误信息 |
| data    | object | 验光数据 |

#### 验光数据

| 参数名                    | 类型     | 必填 | 说明        |
|------------------------|--------|----|-----------|
| --- 电脑验光-----          |        |    |           |
| data_od_sphere         | String | 否  | 电脑验光球镜od  |
| data_od_cylinder       | String | 否  | 电脑验光柱镜od  |
| data_od_axis           | String | 否  | 电脑验光轴向od  |
| data_os_sphere         | String | 否  | 电脑验光球镜os  |
| data_os_cylinder       | String | 否  | 电脑验光柱镜os  |
| data_os_axis           | String | 否  | 电脑验光轴向os  |
| --- 主觉验光 ---           |        |    |           |
| subjective_od_sphere   | String | 否  | 主觉验光OD-球镜 |
| subjective_od_cylinder | String | 否  | 主觉验光OD-柱镜 |
| subjective_od_axis     | String | 否  | 主觉验光OD-轴向 |
| subjective_od_prism    | String | 否  | 主觉验光OD-棱镜 |
| subjective_od_vision   | String | 否  | 主觉验光OD-视力 |
| subjective_os_sphere   | String | 否  | 主觉验光OS-球镜 |
| subjective_os_cylinder | String | 否  | 主觉验光OS-柱镜 |
| subjective_os_axis     | String | 否  | 主觉验光OS-轴向 |
| subjective_od_prism    | String | 否  | 主觉验光OS-棱镜 |
| subjective_os_vision   | String | 否  | 主觉验光OS-视力 |
| ---附加---               |        |    |           |
| presbyopicadd          | String | 否  | 附近加       |
| ---瞳距---               |        |    |           |
| opto_far_pd            | String | 否  | 瞳距-远用     |
| opto_near_pd           | String | 否  | 瞳距-近用     |
| opto_od_pd             | String | 否  | 瞳距-单眼OD   |
| opto_os_pd             | String | 否  | 瞳距-单眼OS   |
| ---瞳高---               |        |    |           |
| opto_od_ph             | String | 否  | 瞳高-OD     |
| opto_os_ph             | String | 否  | 瞳高-OS     |
