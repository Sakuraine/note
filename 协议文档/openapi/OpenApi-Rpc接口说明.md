# OPENAPI内部服务接口协议文档

本文档协议使用与平台内部调用，不允许被平台外互联网或医院调用。

## RPC版旧接口（已弃）

已不推荐使用

```java
    /**
     * 通过卡信息查询患者事件
     *
     * @param cardInfo 卡信息，如果卡类型为磁条卡，则卡号，如果是芯片卡，则为刷卡出来的报文信息
     * @param type 卡片类型：1磁条卡 2芯片卡
     * @param tenantId 租户号
     * @since v1.0.6
     */
    void queryPatientByCardInfoEvent(String cardInfo, Integer type, long tenantId) throws Exception;
```

```java
    /**
     * 新增订单事件
     *
     * @param tradeId 订单号
     * @param tenantId 租户号
     * @since v1.0.6
     */
    void addNewOrderEvent(long tradeId, long tenantId) throws Exception;
```

```java
    /**
     * 订单状态查询事件
     *
     * @param tradeId 订单号
     * @param tenantId 租户号
     * @param tradeType 订单类型 直接从订单表查出来
     * @since v1.0.6
     */
    void queryOrderStatusEvent(long tradeId, long tenantId, long tradeType) throws Exception;
```

```java
    /**
     * 优惠信息查询事件
     *
     * @param pid 线上患者id
     * @param tenantId 租户号
     * @since v1.0.6
     */
    void queryDiscountEvent(long pid, long tenantId) throws Exception;
```

```java
    /**
     * 订单作废
     *
     * @param tradeId 订单号
     * @param tenantId 租户号
     * @param tradeType 订单类型 直接从订单表查出来
     * @throws Exception 反序列化异常或者redis入队异常
     * @since v1.0.6
     */
    void invalidOrderEvent(long tradeId, long tenantId, long tradeType) throws Exception;
```

## Http版RPC接口

### 门诊预检信息保存事件

```url
[POST]/events/api/emr/preview/save
```
#### 请求报文参数

| 参数名           | 类型    | 必填 | 说明            |
| ---------------- | ------- | ---- | --------------- |
| trea_id          | String  | 是   | 就诊ID          |
| pati_id          | String  | 是   | 患者ID          |
| operator_id      | String  | 是   | 操作人ID        |
| prev_od_sphere   | String  | 否   | 电脑验光OD-球镜 |
| prev_od_cylinder | String  | 否   | 电脑验光OD-柱镜 |
| prev_od_axis     | String  | 否   | 电脑验光OD-轴向 |
| prev_od_rem      | String  | 否   | 电脑验光OD-备注 |
| prev_os_sphere   | String  | 否   | 电脑验光OS-球镜 |
| prev_os_cylinder | String  | 否   | 电脑验光OS-柱镜 |
| prev_os_axis     | String  | 否   | 电脑验光OS-轴向 |
| prev_os_rem      | String  | 否   | 电脑验光OS-备注 |
| prev_far_pd      | Integer | 否   | 瞳距-远用       |
| prev_near_pd     | Integer | 否   | 瞳距-近用       |
| pd_od            | Integer | 否   | 瞳距-单眼OD     |
| pd_os            | Integer | 否   | 瞳距-单眼OS     |
| prev_pd_rem      | String  | 否   | 瞳距-备注       |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |

### 专科检查-屈光检查保存事件

```http
[POST]/events/api/emr/speciality_check/dioptroscopy/save
```

#### 请求报文参数

|        参数名        |    类型    | 必填 |     说明     |    数据去向    |
|----------------------|------------|------|--------------|----------------|
| trea_id              | String     | 是   | 就诊ID       |                |
| operator_id          | String     | 是   | 操作人ID     |                |
| computer_optometry   | Object     | 否   | 电脑验光     | 电脑验光数据表 |
| retinoscopy          | Object     | 否   | 检影验光     | 检影验光数据表 |
| subjective           | Object     | 否   | 主觉验光     | 主觉验光数据表 |
| presbyopicadd        | String     | 否   | 近附加       | 近附加数据表   |
| optometr_framepres   | Object     | 否   | 框架眼镜处方 | 框架眼镜处方   |
| optometr_contactpres | Object     | 否   | 隐形眼镜处方 | 隐形眼镜处方   |
| corneal_curvature    | Object     | 否   | 角膜曲率     | 角膜曲率表     |
| optometr_other       | Objectlist | 否   | 其他视光处方 | 其他视光处方表 |

##### 电脑验光

|      参数名      |  类型  | 必填 |      说明      |
|------------------|--------|------|----------------|
| data_od_sphere   | String | 否   | 电脑验光球镜od |
| data_od_cylinder | String | 否   | 电脑验光柱镜od |
| data_od_axis     | String | 否   | 电脑验光轴向od |
| data_od_rem      | String | 否   | 电脑验光OD备注 |
| data_os_sphere   | String | 否   | 电脑验光球镜os |
| data_os_cylinder | String | 否   | 电脑验光柱镜os |
| data_os_axis     | String | 否   | 电脑验光轴向os |
| data_os_rem      | String | 否   | 电脑验光OS备注 |

##### 检影验光

|      参数名      |  类型  | 必填 |       说明      |
|------------------|--------|------|-----------------|
| data_od_sphere   | String | 否   | 检影验光OD-球镜 |
| data_od_cylinder | String | 否   | 检影验光OD-柱镜 |
| data_od_axis     | String | 否   | 检影验光OD-轴向 |
| data_od_vision   | String | 否   | 检影验光OD-视力 |
| data_od_memo     | String | 否   | 检影验光OD-备注 |
| data_os_sphere   | String | 否   | 检影验光OS-球镜 |
| data_os_cylinder | String | 否   | 检影验光OS-柱镜 |
| data_os_axis     | String | 否   | 检影验光OS-轴向 |
| data_os_vision   | String | 否   | 检影验光OS-视力 |
| data_os_memo     | String | 否   | 检影验光OS-备注 |

##### 主觉验光

|      参数名      |  类型  | 必填 |       说明      |
|------------------|--------|------|-----------------|
| data_od_sphere   | String | 否   | 主觉验光OD-球镜 |
| data_od_cylinder | String | 否   | 主觉验光OD-柱镜 |
| data_od_axis     | String | 否   | 主觉验光OD-轴向 |
| data_od_prism    | String | 否   | 主觉验光OD-棱镜 |
| data_od_vision   | String | 否   | 主觉验光OD-视力 |
| data_od_memo     | String | 否   | 主觉验光OD-备注 |
| data_os_sphere   | String | 否   | 主觉验光OS-球镜 |
| data_os_cylinder | String | 否   | 主觉验光OS-柱镜 |
| data_os_axis     | String | 否   | 主觉验光OS-轴向 |
| data_os_prism    | String | 否   | 主觉验光OS-棱镜 |
| data_os_vision   | String | 否   | 主觉验光OS-视力 |
| data_os_memo     | String | 否   | 主觉验光OS-备注 |

##### 框架眼镜处方

|        参数名         |  类型  | 必填 |     说明    |
|-----------------------|--------|------|-------------|
| opto_far_pd           | String | 否   | 瞳距-远用   |
| opto_near_pd          | String | 否   | 瞳距-近用   |
| opto_od_pd            | String | 否   | 瞳距-单眼OD |
| opto_os_pd            | String | 否   | 瞳距-单眼OS |
| opto_od_ph            | String | 否   | 瞳高-OD     |
| opto_os_ph            | String | 否   | 瞳高-OS     |
| opto_pd_rem           | String | 否   | 瞳距-备注   |
| opto_far_od_sphere    | String | 否   | 远用OD-球镜 |
| opto_far_od_cylinder  | String | 否   | 远用OD-柱镜 |
| opto_far_od_axis      | String | 否   | 远用OD-轴向 |
| opto_far_od_prism     | String | 否   | 远用OD-棱镜 |
| opto_far_od_vision    | String | 否   | 远用OD-视力 |
| opto_far_od_memo      | String | 否   | 远用OD-备注 |
| opto_far_os_sphere    | String | 否   | 远用OS-球镜 |
| opto_far_os_cylinder  | String | 否   | 远用OS-柱镜 |
| opto_far_os_axis      | String | 否   | 远用OS-轴向 |
| opto_far_os_prism     | String | 否   | 远用OS-棱镜 |
| opto_far_os_vision    | String | 否   | 远用OS-视力 |
| opto_far_os_memo      | String | 否   | 远用OS-备注 |
| opto_near_od_sphere   | String | 否   | 近用OD-球镜 |
| opto_near_od_cylinder | String | 否   | 近用OD-柱镜 |
| opto_near_od_axis     | String | 否   | 近用OD-轴向 |
| opto_near_od_prism    | String | 否   | 近用OD-棱镜 |
| opto_near_od_vision   | String | 否   | 近用OD-视力 |
| opto_near_od_memo     | String | 否   | 近用OD-备注 |
| opto_near_os_sphere   | String | 否   | 近用OS-球镜 |
| opto_near_os_cylinder | String | 否   | 近用OS-柱镜 |
| opto_near_os_axis     | String | 否   | 近用OS-轴向 |
| opto_near_os_prism    | String | 否   | 近用OS-棱镜 |
| opto_near_os_vision   | String | 否   | 近用OS-视力 |
| opto_near_os_memo     | String | 否   | 近用OS-备注 |

##### 隐形眼镜处方

|      参数名      |  类型  | 必填 |       说明      |
|------------------|--------|------|-----------------|
| opto_od_sphere   | String | 否   | 隐形眼镜OD-球镜 |
| opto_od_cylinder | String | 否   | 隐形眼镜OD-柱镜 |
| opto_od_axis     | String | 否   | 隐形眼镜OD-轴向 |
| opto_od_memo     | String | 否   | 隐形眼镜OD-备注 |
| opto_os_sphere   | String | 否   | 隐形眼镜OS-球镜 |
| opto_os_cylinder | String | 否   | 隐形眼镜OS-柱镜 |
| opto_os_axis     | String | 否   | 隐形眼镜OS-轴向 |
| opto_os_memo     | String | 否   | 隐形眼镜OS-备注 |

##### 角膜曲率

|     参数名     |  类型  | 必填 |   说明   |
|----------------|--------|------|----------|
| data_od_cliffy | String | 否   | 右眼陡峭 |
| data_od_flat   | String | 否   | 右眼平坦 |
| data_od_axis   | String | 否   | 右眼轴向 |
| data_os_cliffy | String | 否   | 左眼陡峭 |
| data_os_flat   | String | 否   | 左眼平坦 |
| data_os_axis   | String | 否   | 左眼轴向 |

##### 其他视光处方

|     参数名      |   类型  | 必填 |     说明     |
|-----------------|---------|------|--------------|
| othe_clas_id    | Long    | 否   | 商品类别ID   |
| othe_clas_code  | String  | 否   | 商品类别代码 |
| othe_goods_id   | Long    | 否   | 商品ID       |
| othe_goods_name | String  | 否   | 商品名称     |
| othe_count      | Integer | 否   | 这商品的数量 |
| othe_goods_unit | String  | 否   | 商品单位     |
| othe_rem        | String  | 否   | 备注         |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |

### 专科检查-RGP初检/OK镜（初检|复查）保存事件

```http
[POST]/events/api/emr/speciality_check/rgp/initial/save
```

#### 请求报文参数

|      参数名       |  类型  | 必填 |   说明   |  数据去向  |
|-------------------|--------|------|----------|------------|
| trea_id           | String | 是   | 就诊ID   |            |
| operator_id       | String | 是   | 操作人ID |            |
| subjective        | Object | 是   | 主觉验光 | 主觉验光表 |
| corneal_curvature | Object | 否   | 角膜曲率 | 角膜曲率表 |

##### 主觉验光

|      参数名      |  类型  | 必填 |       说明      |
|------------------|--------|------|-----------------|
| data_od_sphere   | String | 否   | 主觉验光OD-球镜 |
| data_od_cylinder | String | 否   | 主觉验光OD-柱镜 |
| data_od_axis     | String | 否   | 主觉验光OD-轴向 |
| data_od_prism    | String | 否   | 主觉验光OD-棱镜 |
| data_od_vision   | String | 否   | 主觉验光OD-视力 |
| data_od_memo     | String | 否   | 主觉验光OD-备注 |
| data_os_sphere   | String | 否   | 主觉验光OS-球镜 |
| data_os_cylinder | String | 否   | 主觉验光OS-柱镜 |
| data_os_axis     | String | 否   | 主觉验光OS-轴向 |
| data_os_prism    | String | 否   | 主觉验光OS-棱镜 |
| data_os_vision   | String | 否   | 主觉验光OS-视力 |
| data_os_memo     | String | 否   | 主觉验光OS-备注 |

##### 角膜曲率

|     参数名     |  类型  | 必填 |   说明   |
|----------------|--------|------|----------|
| data_od_cliffy | String | 否   | 右眼陡峭 |
| data_od_flat   | String | 否   | 右眼平坦 |
| data_od_axis   | String | 否   | 右眼轴向 |
| data_os_cliffy | String | 否   | 左眼陡峭 |
| data_os_flat   | String | 否   | 左眼平坦 |
| data_os_axis   | String | 否   | 左眼轴向 |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |

### 专科检查-RGP试戴,分发,复查保存事件

```http
[POST]/events/api/emr/speciality_check/rgp/try/save
```

#### 请求报文参数

| 参数名           | 类型    | 必填 | 说明        | 数据去向                              |
| ---------------- | ------- | ---- | ----------- | ------------------------------------- |
| trea_id          | String  | 是   | 就诊ID      |                                       |
| visi_id          | String  | 否   | 门诊ID      |                                       |
| operator_id      | String  | 是   | 操作人ID    |                                       |
| operation_type   | Integer | 否   | RGP操作类型 | 1.初检2.试戴3.分发4.复查；默认是2试戴 |
| rgp_prescription | Object  | 是   | RGP处方     | RGP处方表                             |

##### RGP处方

|       参数名       |  类型  | 必填 |    说明   |
|--------------------|--------|------|-----------|
| rgp_od_brand_id    | Long   | 否   | OD-品牌id |
| rgp_od_brand       | String | 否   | OD-品牌   |
| rgp_od_material_id | Long   | 否   | OD-材质id |
| rgp_od_material    | String | 否   | OD-材质   |
| rgp_od_curve       | String | 否   | OD-基弧   |
| rgp_od_curve2      | String | 否   | OD-基弧2  |
| rgp_od_diameter    | String | 否   | OD-直径   |
| rgp_od_degree      | String | 否   | OD-度数   |
| rgp_od_degree2     | String | 否   | OD-度数2  |
| rgp_od_rem         | String | 否   | OD-备注   |
| rgp_os_brand_id    | Long   | 否   | OS-品牌id |
| rgp_os_brand       | String | 否   | OS-品牌   |
| rgp_os_material_id | Long   | 否   | OS-材质id |
| rgp_os_material    | String | 否   | OS-材质   |
| rgp_os_curve       | String | 否   | OS-基弧   |
| rgp_os_curve2      | String | 否   | OS-基弧2  |
| rgp_os_diameter    | String | 否   | OS-直径   |
| rgp_os_degree      | String | 否   | OS-度数   |
| rgp_os_degree2     | String | 否   | OS-度数2  |
| rgp_os_rem         | String | 否   | OD-备注   |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |

### 专科检查-OK镜试戴,分发,复查保存事件

```http
[POST]/events/api/emr/speciality_check/rtho-k_lenses/try/save
```

#### 请求报文参数

| 参数名         | 类型    | 必填 | 说明         |                                         |
| -------------- | ------- | ---- | ------------ | --------------------------------------- |
| trea_id        | String  | 是   | 就诊ID       |                                         |
| operator_id    | String  | 是   | 操作人ID     |                                         |
| prescription   | Object  | 是   | 最终处方     | OK镜处方                                |
| orth_od_paras  | List    | 是   | 右眼处方参数 |                                         |
| orth_os_paras  | List    | 是   | 左眼处方参数 |                                         |
| operation_type | Integer | 否   | RGP操作类型  | 1.初检2.试戴3.分发4.复查；默认为：2试戴 |

##### 最终处方

|      参数名      |   类型  | 必填 |                   说明                  |
|------------------|---------|------|-----------------------------------------|
| orth_times       | Integer | 是   | 哪次试戴，第几次试镜得结果，从1开始记的 |
| orth_od_brand_id | String  | 否   | OD-品牌id，右眼镜片品牌id               |
| orth_od_brand    | String  | 否   | OD-品牌，右眼镜片品牌名称               |
| orth_od_rem      | String  | 否   | OD-备注                                 |
| orth_os_brand_id | String  | 否   | OS-品牌id，左眼镜片品牌id               |
| orth_os_brand    | String  | 否   | OS-品牌，左眼镜片品牌名称               |
| orth_os_rem      | String  | 否   | OS-备注                                 |

###### 最终处方品牌属性参数

|     参数名     |  类型  | 必填 |    说明    |
|----------------|--------|------|------------|
| para_prop_id   | Long   | 是   | 属性码ID   |
| para_prop_name | String | 是   | 属性名称   |
| para_choi_id   | Long   | 否   | 属性值ID   |
| para_choi_code | String | 否   | 属性值代码 |
| para_value     | String | 否   | 属性值     |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |

### 专科检查-双眼视功能首诊/随访保存

```http
[POST]/events/api/emr/speciality_check/binocular_visual/first/save
```

#### 请求报文参数

|   参数名    |  类型  | 必填 |   说明   |  数据去向  |
|-------------|--------|------|----------|------------|
| trea_id     | String | 是   | 就诊ID   |            |
| operator_id | String | 是   | 操作人ID |            |
| subjective  | Object | 否   | 主觉验光 | 主觉验光表 |
| pd          | Object | 否   | 瞳距     | 框架处方   |

###### 眼屈光检查-瞳距

|    参数名    |  类型  | 必填 |     说明    |
|--------------|--------|------|-------------|
| opto_far_pd  | String | 否   | 瞳距-远用   |
| opto_near_pd | String | 否   | 瞳距-近用   |
| opto_od_pd   | String | 否   | 瞳距-单眼OD |
| opto_os_pd   | String | 否   | 瞳距-单眼OS |
| opto_pd_rem  | String | 否   | 瞳距-备注   |

###### 眼屈光检查-主觉验光

|      参数名      |  类型  | 必填 |       说明      |
|------------------|--------|------|-----------------|
| data_od_sphere   | String | 否   | 主觉验光OD-球镜 |
| data_od_cylinder | String | 否   | 主觉验光OD-柱镜 |
| data_od_axis     | String | 否   | 主觉验光OD-轴向 |
| data_od_prism    | String | 否   | 主觉验光OD-棱镜 |
| data_od_vision   | String | 否   | 主觉验光OD-视力 |
| data_od_memo     | String | 否   | 主觉验光OD-备注 |
| data_os_sphere   | String | 否   | 主觉验光OS-球镜 |
| data_os_cylinder | String | 否   | 主觉验光OS-柱镜 |
| data_os_axis     | String | 否   | 主觉验光OS-轴向 |
| data_os_prism    | String | 否   | 主觉验光OS-棱镜 |
| data_os_vision   | String | 否   | 主觉验光OS-视力 |
| data_os_memo     | String | 否   | 主觉验光OS-备注 |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |

### 专科检查-低视力首诊/随访保存

```http
[POST]/events/api/emr/speciality_check/low_vision/first/save
```

#### 请求报文参数

|       参数名       |  类型  | 必填 |   说明   |    数据去向    |
|--------------------|--------|------|----------|----------------|
| trea_id            | String | 是   | 就诊ID   |                |
| operator_id        | String | 是   | 操作人ID |                |
| computer_optometry | Object | 否   | 电脑验光 | 电脑验光数据表 |
| pd                 | Object | 否   | 瞳距     | 框架眼镜处方   |
| retinoscopy        | Object | 否   | 检影验光 | 检影验光数据表 |
| subjective         | Object | 否   | 主觉验光 | 主觉验光数据表 |
| presbyopicadd      | String | 否   | 近附加   | 近附加数据表   |

###### 临床检查结果-视功能-电脑验光

|      参数名      |  类型  | 必填 |      说明      |
|------------------|--------|------|----------------|
| data_od_sphere   | String | 否   | 电脑验光球镜od |
| data_od_cylinder | String | 否   | 电脑验光柱镜od |
| data_od_axis     | String | 否   | 电脑验光轴向od |
| data_od_rem      | String | 否   | 电脑验光OD备注 |
| data_os_sphere   | String | 否   | 电脑验光球镜os |
| data_os_cylinder | String | 否   | 电脑验光柱镜os |
| data_os_axis     | String | 否   | 电脑验光轴向os |
| data_os_rem      | String | 否   | 电脑验光OS备注 |

###### 临床检查结果-视功能-瞳距

|    参数名    |  类型  | 必填 |     说明    |
|--------------|--------|------|-------------|
| opto_far_pd  | String | 否   | 瞳距-远用   |
| opto_near_pd | String | 否   | 瞳距-近用   |
| opto_od_pd   | String | 否   | 瞳距-单眼OD |
| opto_os_pd   | String | 否   | 瞳距-单眼OS |
| opto_pd_rem  | String | 否   | 瞳距-备注   |

###### 临床检查结果-视功能-检影验光

|      参数名      |  类型  | 必填 |       说明      |
|------------------|--------|------|-----------------|
| data_od_sphere   | String | 否   | 检影验光OD-球镜 |
| data_od_cylinder | String | 否   | 检影验光OD-柱镜 |
| data_od_axis     | String | 否   | 检影验光OD-轴向 |
| data_od_vision   | String | 否   | 检影验光OD-视力 |
| data_od_memo     | String | 否   | 检影验光OD-备注 |
| data_os_sphere   | String | 否   | 检影验光OS-球镜 |
| data_os_cylinder | String | 否   | 检影验光OS-柱镜 |
| data_os_axis     | String | 否   | 检影验光OS-轴向 |
| data_os_vision   | String | 否   | 检影验光OS-视力 |
| data_os_memo     | String | 否   | 检影验光OS-备注 |

###### 临床检查结果-视功能-主觉验光

|      参数名      |  类型  | 必填 |       说明      |
|------------------|--------|------|-----------------|
| data_od_sphere   | String | 否   | 主觉验光OD-球镜 |
| data_od_cylinder | String | 否   | 主觉验光OD-柱镜 |
| data_od_axis     | String | 否   | 主觉验光OD-轴向 |
| data_od_prism    | String | 否   | 主觉验光OD-棱镜 |
| data_od_vision   | String | 否   | 主觉验光OD-视力 |
| data_od_memo     | String | 否   | 主觉验光OD-备注 |
| data_os_sphere   | String | 否   | 主觉验光OS-球镜 |
| data_os_cylinder | String | 否   | 主觉验光OS-柱镜 |
| data_os_axis     | String | 否   | 主觉验光OS-轴向 |
| data_os_prism    | String | 否   | 主觉验光OS-棱镜 |
| data_os_vision   | String | 否   | 主觉验光OS-视力 |
| data_os_memo     | String | 否   | 主觉验光OS-备注 |

#### 回复报文参数

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| 无     |      |      |      |





