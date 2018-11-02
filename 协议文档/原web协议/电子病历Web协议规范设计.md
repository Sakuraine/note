#电子病历Web协议规范设计


注意： 

箭头符合统一为 1上 2下 3左 4右
即 1 ↑ 2↓ 3← 4→


##预检


### 门诊服务预检列表  
```url
[GET]/treat_service/preview/list
```
####修改更新记录

| 对应业务     | 说明             |
| -------- | -------------- |
| V1.2.3   | 修改 重新实现        |
| V1.3.4.1 | 新增 添加患者ID的检索条件 |

说明：预检状态根据查询预检信息表判断本次就诊是否已预检

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明             |
| --------- | ------- | ---- | -------------- |
| state     | Integer | 否    | 状态 1 待预检 全部则不传 |
| key       | String  | 否    | 姓名、手机号、门诊号     |
| page_size | Integer | 否    | 每页条数 空表示10条    |
| page_num  | Integer | 否    | 第几页 空表示第1页     |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| wait_num  | Integer    | 是    | 待预检数量       |
| total_num | Integer    | 是    | 全部数量        |
| list      | ObjectList | 否    | 预检列表        |

预检列表说明

| 参数名           | 类型      | 必填   | 说明                |
| ------------- | ------- | ---- | ----------------- |
| trea_id       | String  | 是    | 就诊号               |
| state         | Integer | 否    | 预检状态 1 待预检  2已预检  |
| depa_id       | String  | 是    | 挂号就诊科室            |
| depa_name     | String  | 是    | 挂号就诊科室名称          |
| visi_serialno | String  | 是    | 就诊序号              |
| pati_name     | String  | 是    | 姓名                |
| pati_gender   | String  | 是    | 性别代码 0 未知 1男  2 女 |
| pati_age      | String  | 是    | 年龄                |
| pati_phone    | String  | 是    | 手机号               |
| doct_id       | String  | 否    | 挂号就诊医生            |
| doct_name     | String  | 是    | 挂号就诊医生姓名          |
| visi_no       | String  | 是    | 门诊号               |
| fee_type      | String  | 是    | 费用类型 1-自费，2- 市医保  |
| trea_status   | Integer | 是    | 就诊状态              |
| prev_event    | String  | 是    | 就诊事项（拼接展示）        |
| trea_visi_time    | String  | 是    | 接诊时间        |
|book_time    | String  | 是    | 挂号时间        |
| head_photo_url    | String  | 是    | 患者头像地址        |



###门诊预检信息获取

```url
[GET] /treat_service/preview
```

####修改更新记录

| 对应业务   | 说明      |
| ------ | ------- |
| V1.2.3 | 修改 实现修改 |

####请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数

| 参数名                       | 类型         | 必填   | 说明         |
| ------------------------- | ---------- | ---- | ---------- |
| trea_id                   | String     | 是    | 就诊ID       |
| pati_id                   | String     | 是    | 患者ID       |
| visi_id                   | String     | 是    | 门诊ID       |
| prev_od_sphere            | String     | 否    | 电脑验光OD-球镜  |
| prev_od_cylinder          | String     | 否    | 电脑验光OD-柱镜  |
| prev_od_axis              | String     | 否    | 电脑验光OD-轴向  |
| prev_od_rem               | String     | 否    | 电脑验光OD-备注  |
| prev_os_sphere            | String     | 否    | 电脑验光OS-球镜  |
| prev_os_cylinder          | String     | 否    | 电脑验光OS-柱镜  |
| prev_os_axis              | String     | 否    | 电脑验光OS-轴向  |
| prev_os_rem               | String     | 否    | 电脑验光OS-备注  |
| prev_mydri_od_sphere      | String     | 否    | 睫麻后验光OD-球镜 |
| prev_mydri_od_cylinder    | String     | 否    | 睫麻后验光OD-柱镜 |
| prev_mydri_od_axis        | String     | 否    | 睫麻后验光OD-轴向 |
| prev_mydri_od_rem         | String     | 否    | 睫麻后验光OD-备注 |
| prev_mydri_os_sphere      | String     | 否    | 睫麻后验光OS-球镜 |
| prev_mydri_os_cylinder    | String     | 否    | 睫麻后验光OS-柱镜 |
| prev_mydri_os_axis        | String     | 否    | 睫麻后验光OS-轴向 |
| prev_mydri_os_rem         | String     | 否    | 睫麻后验光OS-备注 |
| prev_far_pd               | Integer    | 否    | 瞳距-远用      |
| prev_near_pd              | Integer    | 否    | 瞳距-近用      |
| prev_pd_od                | Integer    | 否    | 瞳距-单眼OD    |
| prev_pd_os                | Integer    | 否    | 瞳距-单眼OS    |
| prev_pd_rem               | String     | 否    | 瞳距-备注      |
| 眼压                        |            |      |            |
| data_od_iop               | String     | 否    | OD-眼压      |
| data_os_iop               | String     | 否    | OS-眼压      |
| 原镜                        |            |      |            |
| data_od_sphere            | String     | 否    | 近用OD-球镜    |
| data_od_cylinder          | String     | 否    | 近用OD-柱镜    |
| data_od_axis              | String     | 否    | 近用OD-轴向    |
| data_od_vision            | String     | 否    | 近用OD-视力    |
| data_od_rem               | String     | 否    | 近用OD-备注    |
| data_os_sphere            | String     | 否    | 近用OS-球镜    |
| data_os_cylinder          | String     | 否    | 近用OS-柱镜    |
| data_os_axis              | String     | 否    | 近用OS-轴向    |
| data_os_vision            | String     | 否    | 近用OS-视力    |
| data_os_rem               | String     | 否    | 近用OS-备注    |
| 视力数据                      |            |      |            |
| data_od_distance_vision   | String     | 否    | 裸眼远用OD-视力  |
| data_os_distance_vision   | String     | 否    | 裸眼远用OS-视力  |
| data_ou_distance_vision   | String     | 否    | 裸眼远用OU-视力  |
| data_od_near_vision       | String     | 否    | 裸眼近用OD-视力  |
| data_os_near_vision       | String     | 否    | 裸眼近用OS-视力  |
| data_ou_near_vision       | String     | 否    | 裸眼近用OU-视力  |
| data_od_distance_original | String     | 否    | 原镜远用OD-视力  |
| data_os_distance_original | String     | 否    | 原镜远用OS-视力  |
| data_ou_distance_original | String     | 否    | 原镜远用OU-视力  |
| data_od_near_original     | String     | 否    | 原镜近用OD-视力  |
| data_os_near_original     | String     | 否    | 原镜近用OS-视力  |
| data_ou_near_original     | String     | 否    | 原镜近用OU-视力  |
| 近附加                       |            |      |            |
| data_add                  | String     | 否    | 近附加数据      |
| 就诊事项                      |            |      |            |
| event_list                | ObjectList | 是    | 就诊事项列表     |


就诊事项说明

| 参数名         | 类型      | 必填   | 说明                                       |
| ----------- | ------- | ---- | ---------------------------------------- |
| event_id    | Integer | 是    | 就诊事项,0-未知；1-验光；2-配镜；3-复诊;4-视力检查;5-验光检查;99-其它 |
| event_other | String  | 否    | 其它事项，当事项为其它时不为空                          |

### 获取预检拼接后的信息

>  [GET] /treat_service/preview_info   

| 对应业务   | 说明          |
| ------ | ----------- |
| V1.2.3 | 增加近附加、视力数据等 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明     |
| ------- | ------ | ---- | ------ |
| trea_id | String | 是    | 就诊记录ID |


#### 回复报文参数

| 参数名                       | 类型      | 必填   | 说明          |
| ------------------------- | ------- | ---- | ----------- |
| trea_id                   | String  | 是    | 就诊记录ID      |
| prev_id                   | String  | 是    | 预检记录ID      |
| visi_id                   | String  | 是    | 门诊号         |
| pati_id                   | String  | 是    | 患者ID        |
| prev_od_str               | String  | 否    | 验光OD-字符串    |
| prev_os_str               | String  | 否    | 验光OS-字符串    |
| prev_mydri_od_str         | String  | 否    | 睫麻后验光OD-字符串 |
| prev_mydri_os_str         | String  | 否    | 睫麻后验光OS-字符串 |
| 眼压                        |         |      |             |
| data_od_iop               | String  | 否    | OD-眼压       |
| data_os_iop               | String  | 否    | OS-眼压       |
| 原镜                        |         |      |             |
| data_od_original_str      | String  | 否    | OD-数据       |
| data_os_original_str      | String  | 否    | OD-数据       |
| 近附加                       |         |      |             |
| data_add                  | String  | 否    | 近附加数据       |
| 视力数据                      |         |      |             |
| data_od_distance_vision   | String  | 否    | 裸眼远用OD-视力   |
| data_os_distance_vision   | String  | 否    | 裸眼远用OS-视力   |
| data_ou_distance_vision   | String  | 否    | 裸眼远用OU-视力   |
| data_od_near_vision       | String  | 否    | 裸眼近用OD-视力   |
| data_os_near_vision       | String  | 否    | 裸眼近用OS-视力   |
| data_ou_near_vision       | String  | 否    | 裸眼近用OU-视力   |
| data_od_distance_original | String  | 否    | 原镜远用OD-视力   |
| data_os_distance_original | String  | 否    | 原镜远用OS-视力   |
| data_ou_distance_original | String  | 否    | 原镜远用OU-视力   |
| data_od_near_original     | String  | 否    | 原镜近用OD-视力   |
| data_os_near_original     | String  | 否    | 原镜近用OS-视力   |
| data_ou_near_original     | String  | 否    | 原镜近用OU-视力   |
| 瞳距                        |         |      |             |
| prev_far_pd               | Integer | 否    | 瞳距-远用       |
| prev_near_pd              | Integer | 否    | 瞳距-近用       |
| prev_pd_od                | Integer | 否    | 瞳距-单眼OD     |
| prev_pd_os                | Integer | 否    | 瞳距-单眼OS     |
| prev_pd_rem               | String  | 否    | 瞳距-备注       |
| prev_user_name            | String  | 是    | 预检护士        |
| prev_time                 | String  | 是    | 预检时间        |
| event                     | String  | 是    | 就诊事项 逗号分隔   |

###门诊预检信息保存

```url
[POST]/treat_service/preview
```

####修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

####请求报文参数

| 参数名                       | 类型         | 必填   | 说明         |
| ------------------------- | ---------- | ---- | ---------- |
| trea_id                   | String     | 是    | 就诊ID       |
| prev_od_sphere            | String     | 否    | 电脑验光OD-球镜  |
| prev_od_cylinder          | String     | 否    | 电脑验光OD-柱镜  |
| prev_od_axis              | String     | 否    | 电脑验光OD-轴向  |
| prev_od_rem               | String     | 否    | 电脑验光OD-备注  |
| prev_os_sphere            | String     | 否    | 电脑验光OS-球镜  |
| prev_os_cylinder          | String     | 否    | 电脑验光OS-柱镜  |
| prev_os_axis              | String     | 否    | 电脑验光OS-轴向  |
| prev_os_rem               | String     | 否    | 电脑验光OS-备注  |
| prev_mydri_od_sphere      | String     | 否    | 睫麻后验光OD-球镜 |
| prev_mydri_od_cylinder    | String     | 否    | 睫麻后验光OD-柱镜 |
| prev_mydri_od_axis        | String     | 否    | 睫麻后验光OD-轴向 |
| prev_mydri_od_rem         | String     | 否    | 睫麻后验光OD-备注 |
| prev_mydri_os_sphere      | String     | 否    | 睫麻后验光OS-球镜 |
| prev_mydri_os_cylinder    | String     | 否    | 睫麻后验光OS-柱镜 |
| prev_mydri_os_axis        | String     | 否    | 睫麻后验光OS-轴向 |
| prev_mydri_os_rem         | String     | 否    | 睫麻后验光OS-备注 |
| prev_far_pd               | Integer    | 否    | 瞳距-远用      |
| prev_near_pd              | Integer    | 否    | 瞳距-近用      |
| prev_pd_od                | Integer    | 否    | 瞳距-单眼OD    |
| prev_pd_os                | Integer    | 否    | 瞳距-单眼OS    |
| prev_pd_rem               | String     | 否    | 瞳距-备注      |
| 眼压                        |            |      |            |
| data_od_iop               | String     | 否    | OD-眼压      |
| data_os_iop               | String     | 否    | OS-眼压      |
| 原镜                        |            |      |            |
| data_od_sphere            | String     | 否    | 近用OD-球镜    |
| data_od_cylinder          | String     | 否    | 近用OD-柱镜    |
| data_od_axis              | String     | 否    | 近用OD-轴向    |
| data_od_vision            | String     | 否    | 近用OD-视力    |
| data_od_rem               | String     | 否    | 近用OD-备注    |
| data_os_sphere            | String     | 否    | 近用OS-球镜    |
| data_os_cylinder          | String     | 否    | 近用OS-柱镜    |
| data_os_axis              | String     | 否    | 近用OS-轴向    |
| data_os_vision            | String     | 否    | 近用OS-视力    |
| data_os_rem               | String     | 否    | 近用OS-备注    |
| 视力数据                      |            |      |            |
| data_od_distance_vision   | String     | 否    | 裸眼远用OD-视力  |
| data_os_distance_vision   | String     | 否    | 裸眼远用OS-视力  |
| data_ou_distance_vision   | String     | 否    | 裸眼远用OU-视力  |
| data_od_near_vision       | String     | 否    | 裸眼近用OD-视力  |
| data_os_near_vision       | String     | 否    | 裸眼近用OS-视力  |
| data_ou_near_vision       | String     | 否    | 裸眼近用OU-视力  |
| data_od_distance_original | String     | 否    | 原镜远用OD-视力  |
| data_os_distance_original | String     | 否    | 原镜远用OS-视力  |
| data_ou_distance_original | String     | 否    | 原镜远用OU-视力  |
| data_od_near_original     | String     | 否    | 原镜近用OD-视力  |
| data_os_near_original     | String     | 否    | 原镜近用OS-视力  |
| data_ou_near_original     | String     | 否    | 原镜近用OU-视力  |
| 近附加                       |            |      |            |
| data_add                  | String     | 否    | 近附加数据      |
| 就诊事项                      |            |      |            |
| event_list                | ObjectList | 是    | 就诊事项列表     |


就诊事项说明

| 参数名         | 类型      | 必填   | 说明                                       |
| ----------- | ------- | ---- | ---------------------------------------- |
| event_id    | Integer | 是    | 就诊事项,0-未知；1-验光；2-配镜；3-复诊;4-视力检查;5-验光检查;99-其它 |
| event_other | String  | 否    | 其它事项，当事项为其它时不为空                          |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

### 门诊预检评估-双眼视功能首诊/随访获取

```http
[GET]/treat_service/preview/evaluation/binocular_visual
```
说明
1. 首诊时 is_first_follow 值为 1;
2. 随访时 is_first_follow 值为 2;
#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名             | 类型      | 必填   | 说明         |
| --------------- | ------- | ---- | ---------- |
| trea_id         | String  | 是    | 就诊ID       |
| is_first_follow | Integer | 是    | 1-首诊;2-随访; |

#### 回复报文参数

| 参数名                             | 类型      | 必填   | 说明                                       |
| ------------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                         | String  | 是    | 就诊ID                                     |
| is_first_follow                 | Integer | 是    | 1-首诊;2-随访;                               |
| ---个人史(personal_history)----    |         |      |                                          |
| history_diagnosis               | Integer | 否    | 医疗诊治史:<br/>1-正常;<br/>2-有;                |
| history_diagnosis_list          | String  | 否    | 医疗诊治史列表:<br/>1-过敏史;<br/>2-鼻窦炎;<br/>3-枯草热;<br/>4-眼、口或粘膜干燥症;<br/>5-抽搐或癫痫;<br/>6-昏厥;<br/>7-糖尿病;<br/>8-怀孕;<br/>9-甲状腺功能异常;<br/>10-精神治疗史; |
| visual_training                 | Integer | 否    | 是否接受过视觉训练:<br/>1-无;<br/>2-有;             |
| visual_training_time            | String  | 否    | 视觉训练时间，单位周                               |
| is_squint_correction            | Integer | 否    | 是否斜视矫正术后                                 |
| squint_correction               | String  | 否    | 斜视矫正术后情况:<br/>1-间接性外斜视矫正术后;<br/>2-恒定性外斜视矫正术后;<br/>3-急性共同性内科视矫正术后;<br/>4-部分调节性内斜视矫正术后;<br/>5-麻痹性斜视矫正术后; |
| --随访时间(follow_up_time)--        |         |      |                                          |
| follow_up_time                  | Integer | 是    | 双眼视随访时间选项:<br/>1-一周;<br/>2-1月;<br/>3-3月;<br/>4-6月;<br/>5-12月;<br/>6-不定期; |
| follow_up                       | String  | 否    | 双眼视随访                                    |
| --症状问卷(symptom_questionnaire)-- |         |      |                                          |
| question_01                     | Integer | 否    | 阅读或近距离工作时你是否觉得眼部疲劳或不适:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_02                     | Integer | 否    | 阅读或近距离工作时你是否头痛:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_03                     | Integer | 否    | 阅读或近距离工作时你是否觉得易困乏:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_04                     | Integer | 否    | 阅读或近距离工作时，你的注意力是否不集中:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_05                     | Integer | 否    | 你是否对记住读过的东西感到困难:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_06                     | Integer | 否    | 阅读或近距离工作时是否出现双影:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_07                     | Integer | 否    | 阅读或近距离工作时你是否觉得文字移动、跳动、游动或在纸面上漂浮:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_08                     | Integer | 否    | 你是否觉得阅读速度慢:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_09                     | Integer | 否    | 阅读或近距离工作时你是否眼痛、眼酸:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_10                     | Integer | 否    | 阅读或近距离工作时有一种眼球牵拉感:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_11                     | Integer | 否    | 阅读或近距离工作时你是否出现视物模糊或聚焦不准确:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_12                     | Integer | 否    | 阅读或近距离工作时你是否会出现串行:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_13                     | Integer | 否    | 阅读或近距离工作时你是否不得不重复读同一行:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_14                     | Integer | 否    | 你是否回避阅读或近距离工作:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_15                     | Integer | 否    | 你是否从视远转到视近或从视近转到视远聚焦困难:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_16                     | Integer | 否    | 阅读疲劳的症状是否在夜晚会更为明显:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |


###门诊预检评估-双眼视功能首诊/随访保存

```http
[POST]/treat_service/preview/evaluation/binocular_visual
```
说明
1. 首诊时 is_first_follow 值为 1;
2. 随访时 is_first_follow 值为 2;

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数


| 参数名                             | 类型      | 必填   | 说明                                       |
| ------------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                         | String  | 是    | 就诊ID                                     |
| is_first_follow                 | Integer | 是    | 1-首诊;2-随访;                               |
| ---个人史(personal_history)----    |         |      |                                          |
| history_diagnosis               | Integer | 否    | 医疗诊治史:<br/>1-正常;<br/>2-有;                |
| history_diagnosis_list          | String  | 否    | 医疗诊治史列表:<br/>1-过敏史;<br/>2-鼻窦炎;<br/>3-枯草热;<br/>4-眼、口或粘膜干燥症;<br/>5-抽搐或癫痫;<br/>6-昏厥;<br/>7-糖尿病;<br/>8-怀孕;<br/>9-甲状腺功能异常;<br/>10-精神治疗史; |
| visual_training                 | Integer | 否    | 是否接受过视觉训练:<br/>1-无;<br/>2-有;             |
| visual_training_time            | String  | 否    | 视觉训练时间，单位周                               |
| is_squint_correction            | Integer | 否    | 是否斜视矫正术后                                 |
| squint_correction               | String  | 否    | 斜视矫正术后情况:<br/>1-间接性外斜视矫正术后;<br/>2-恒定性外斜视矫正术后;<br/>3-急性共同性内科视矫正术后;<br/>4-部分调节性内斜视矫正术后;<br/>5-麻痹性斜视矫正术后; |
| --随访时间(follow_up_time)--        |         |      |                                          |
| follow_up_time                  | Integer | 是    | 双眼视随访时间选项:<br/>1-一周;<br/>2-1月;<br/>3-3月;<br/>4-6月;<br/>5-12月;<br/>6-不定期; |
| follow_up                       | String  | 否    | 双眼视随访                                    |
| --症状问卷(symptom_questionnaire)-- |         |      |                                          |
| question_01                     | Integer | 否    | 阅读或近距离工作时你是否觉得眼部疲劳或不适:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_02                     | Integer | 否    | 阅读或近距离工作时你是否头痛:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_03                     | Integer | 否    | 阅读或近距离工作时你是否觉得易困乏:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_04                     | Integer | 否    | 阅读或近距离工作时，你的注意力是否不集中:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_05                     | Integer | 否    | 你是否对记住读过的东西感到困难:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_06                     | Integer | 否    | 阅读或近距离工作时是否出现双影:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_07                     | Integer | 否    | 阅读或近距离工作时你是否觉得文字移动、跳动、游动或在纸面上漂浮:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_08                     | Integer | 否    | 你是否觉得阅读速度慢:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_09                     | Integer | 否    | 阅读或近距离工作时你是否眼痛、眼酸:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_10                     | Integer | 否    | 阅读或近距离工作时有一种眼球牵拉感:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_11                     | Integer | 否    | 阅读或近距离工作时你是否出现视物模糊或聚焦不准确:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_12                     | Integer | 否    | 阅读或近距离工作时你是否会出现串行:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_13                     | Integer | 否    | 阅读或近距离工作时你是否不得不重复读同一行:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_14                     | Integer | 否    | 你是否回避阅读或近距离工作:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_15                     | Integer | 否    | 你是否从视远转到视近或从视近转到视远聚焦困难:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_16                     | Integer | 否    | 阅读疲劳的症状是否在夜晚会更为明显:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



##门诊

### 就诊患者信息详情

> [GET]/patient_service/patient/for_treatment 

获取某就诊患者的信息详情

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊号  |

#### 回复报文参数

| 参数名            | 类型      | 必填   | 说明                  |
| -------------- | ------- | ---- | ------------------- |
| trea_id        | String  | 是    | 就诊号                 |
| trea_status    | Integer | 是    | 就诊状态,1-候诊；2-诊中；3-已诊 |
| pati_id        | String  | 是    | 患者id                |
| id_type        | String  | 是    | 患者类型  空时为身份证    1:身份证;2:台湾居民来往大陆通行证;3:港澳居民身份证;4:居民户口簿;5:护照;6:军官证;7:文职干部证;8:士兵证;9:驾驶执照;10:残疾证;11:医疗保险证;12:出生证明; 20 就诊卡; 21 医保卡; 98:其它;99:身份证(兼容旧数据);            |
| id_number        | String  | 是    | 患者身份证号                |
| pati_id        | String  | 是    | 患者id                |
| visi_no        | Long    | 是    | 门诊号                 |
| visi_serialno  | String  | 是    | 就诊序号                |
| pati_name      | String  | 是    | 姓名                  |
| pati_gender    | String  | 是    | 性别代码 0 未知 1男  2 女   |
| pati_birthday  | date    | 是    | 出生年月                |
| age            | String  | 是    | 年龄                  |
| pati_phone     | String  | 是    | 手机号码                |
| prev_event     | String  | 是    | 就诊事项                |
| fee_type       | String  | 是    | 费用类型                |
| depa_name      | String  | 否    | 就诊科室                |
| trea_visi_user | String  | 否    | 接诊医生                |
| trea_book_doct | String  | 否    | 挂号医生                |
| trea_visi_time | String  | 否    | 接诊时间                |

### 门诊小病历界面获取

```url
[GET]/diag_service/clin_reco/emr_treatment
```

#### 修改更新记录

|  对应业务 	| 说明 					|
|-----------|---------------------	|
| V1.2.3 	| 修改 重新实现 			|
| V1.2.3.2 	| 新增不定期随访数据类型 	|

#### 请求报文参数

| 参数名 				 | 类型 		  | 必填 | 说明 											|
|------------------------|------------|------|-------------------------------------------	|
| trea_id                | String     | 是   | 就诊记录id                                		|

#### 回复报文参数

| 参数名                    | 类型         | 必填   | 说明                        |
| ---------------------- | ---------- | ---- | ------------------------- |
| trea_id                | String     | 是    | 就诊记录id                    |
| comp_id                | String     | 否    | 主诉ID                      |
| comp_content           | String     | 否    | 主诉内容                      |
| illn_id                | String     | 否    | 现病史模板ID                   |
| illn_content           | String     | 否    | 现病史内容                     |
| emr_trea_suggestion    | String     | 否    | 处理意见                      |
| emr_spec_text          | String     | 否    | 专科检查正文，方便界面展示             |
| emr_disease_negation   | Integer    | 是    | 疾病史否认;0-未询问;1-患者否认;2-患者承认 |
| past_disease_list      | ObjectList | 否    | 患者疾病史列表                   |
| emr_allergic_negation  | Integer    | 是    | 过敏史否认;0-未询问;1-患者否认;2-患者承认 |
| past_allergic_list     | ObjectList | 否    | 患者过敏史列表                   |
| emr_operation_negation | Integer    | 是    | 手术史否认;0-未询问;1-患者否认;2-患者承认 |
| past_operation_list    | ObjectList | 否    | 患者手术史列表                   |
| emr_family_negation    | Integer    | 是    | 家族史否认;0-未询问;1-患者否认;2-患者承认 |
| past_family_list       | ObjectList | 否    | 患者家族史列表                   |
| personal_list          | ObjectList | 否    | 其他个人史列表                   |
| diag_list              | ObjectList | 是    | 诊断列表 本次就诊的诊断列表            |
| emr_followup_type      | Integer    | 否    | 随访时间类型；0:定期;1:不定期         |
| emr_followup_number    | Integer    | 否    | 随访时间值                     |
| emr_followup_unit      | Integer    | 否    | 随访时间单位；1-天;2-周;3-月;4-年    |
| emr_followup_notfixed  | Integer    | 否    | 不定期随访时间                   |



患者疾病史列表说明

| 参数名                 | 类型      | 必填   | 说明              |
| ------------------- | ------- | ---- | --------------- |
| diag_id             | String  | 是    | 对应诊断记录的ID       |
| diag_name           | String  | 是    | 诊断名称            |
| diag_icd            | String  | 是    | 诊断ICD编码，剑形编码，病因 |
| diag_attach         | String  | 是    | 附加码，星形编码，临床表现   |
| reco_persistence    | Integer | 否    | 疾病持续时间          |
| reco_pers_unit_name | String  | 否    | 疾病持续时间单位        |
| reco_pers_unit_code | String  | 否    | 疾病持续时间单位代码      |
| reco_describe       | String  | 是    | 描述信息，扩展描述       |

患者过敏史列表说明

| 参数名           | 类型      | 必填   | 说明        |
| ------------- | ------- | ---- | --------- |
| alle_id       | String  | 否    | 过敏原主键     |
| alle_code     | String  | 否    | 过敏原编码     |
| alle_name     | String  | 是    | 过敏原名称     |
| alle_type     | Integer | 是    | 过敏类别      |
| reco_describe | String  | 否    | 描述信息，扩展描述 |

患者手术史列表说明

| 参数名           | 类型     | 必填   | 说明        |
| ------------- | ------ | ---- | --------- |
| oper_id       | String | 否    | 术式主键      |
| oper_name     | String | 是    | 术式名称      |
| oper_code     | String | 否    | 术式编码      |
| oper_date     | Date   | 否    | 手术日期      |
| reco_describe | String | 否    | 描述信息，扩展描述 |

患者家族史列表说明

| 参数名          | 类型     | 必填   | 说明           |
| ------------ | ------ | ---- | ------------ |
| reco_id      | String | 否    | 记录ID  没有表示新增 |
| reco_content | String | 否    | 家族史内容        |

其他个人史列表说明


| 参数名          | 类型     | 必填   | 说明    |
| ------------ | ------ | ---- | ----- |
| reco_content | String | 否    | 个人史内容 |

诊断列表说明

| 参数名            | 类型     | 必填   | 说明              |
| -------------- | ------ | ---- | --------------- |
| diag_pre_id    | String | 否    | 前缀ID            |
| diag_pre_name  | String | 是    | 前缀内容            |
| diag_id        | String | 是    | 诊断id            |
| diag_name      | String | 是    | 诊断名称            |
| diag_icd       | String | 是    | 诊断ICD编码，剑形编码，病因 |
| diag_attach    | String | 否    | 附加码             |
| diag_sufx_id   | String | 否    | 后缀ID            |
| diag_sufx_name | String | 是    | 后缀内容            |


### 门诊小病历界面保存协议

```url
[POST]/diag_service/clin_reco/emr_treatment
```

#### 修改更新记录

|  对应业务 	| 说明 					|
|-----------|---------------------	|
| V1.2.3 	| 修改 重新实现 			|
| V1.2.3.2 	| 新增不定期随访数据类型 	|

#### 请求报文参数

| 参数名                    | 类型         | 长度   | 必填   | 说明                        | 变更          |
| ---------------------- | ---------- | ---- | ---- | ------------------------- | ----------- |
| trea_id                | String     |      | 是    | 就诊记录id                    |             |
| comp_id                | String     |      | 是    | 主诉ID                      |             |
| comp_content           | String     |      | 是    | 主诉内容                      |             |
| illn_id                | String     |      | 是    | 现病史模板ID                   |             |
| illn_content           | String     |      | 是    | 现病史内容                     |             |
| emr_trea_suggestion    | String     |      | 是    | 处理意见                      |             |
| emr_spec_text          | String     |      | 是    | 专科检查正文，方便界面展示             |             |
| emr_disease_negation   | Integer    |      | 是    | 疾病史否认;0-未询问;1-患者否认;2-患者承认 |             |
| past_disease_list      | ObjectList |      | 是    | 患者疾病史列表                   |             |
| emr_allergic_negation  | Integer    |      | 是    | 过敏史否认;0-未询问;1-患者否认;2-患者承认 |             |
| past_allergic_list     | ObjectList |      | 是    | 患者过敏史列表                   |             |
| emr_operation_negation | Integer    |      | 是    | 手术史否认;0-未询问;1-患者否认;2-患者承认 |             |
| past_operation_list    | ObjectList |      | 是    | 患者手术史列表                   |             |
| emr_family_negation    | Integer    |      | 是    | 家族史否认;0-未询问;1-患者否认;2-患者承认 |             |
| past_family_list       | ObjectList |      | 是    | 患者家族史列表                   |             |
| personal_list          | ObjectList |      | 是    | 其他个人史列表                   |             |
| diag_list              | ObjectList |      | 是    | 诊断列表 本次就诊的诊断列表            |             |
| emr_followup_type      | Integer    |      | 是    | 随访时间类型；0:定期;1:不定期         | WEBV1.2.3.2 |
| emr_followup_number    | Integer    |      | 是    | 随访时间值                     |             |
| emr_followup_unit      | Integer    |      | 否    | 随访时间单位；1-天;2-周;3-月;4-年    |             |
| emr_followup_notfixed  | String     | 24   | 否    | 不定期随访时间                   | WEBV1.2.3.2 |

患者疾病史列表说明

| 参数名                 | 类型      | 必填   | 说明              |
| ------------------- | ------- | ---- | --------------- |
| diag_id             | String  | 是    | 对应诊断记录的ID       |
| diag_name           | String  | 是    | 诊断名称            |
| diag_icd            | String  | 是    | 诊断ICD编码，剑形编码，病因 |
| diag_attach         | String  | 是    | 附加码，星形编码，临床表现   |
| reco_persistence    | Integer | 否    | 疾病持续时间          |
| reco_pers_unit_name | String  | 否    | 疾病持续时间单位        |
| reco_pers_unit_code | String  | 否    | 疾病持续时间单位代码      |
| reco_describe       | String  | 是    | 描述信息，扩展描述       |

患者过敏史列表说明

| 参数名           | 类型      | 必填   | 说明        |
| ------------- | ------- | ---- | --------- |
| alle_id       | String  | 否    | 过敏原主键     |
| alle_code     | String  | 否    | 过敏原编码     |
| alle_name     | String  | 是    | 过敏原名称     |
| alle_type     | Integer | 是    | 过敏类别      |
| reco_describe | String  | 否    | 描述信息，扩展描述 |

患者手术史列表说明

| 参数名           | 类型     | 必填   | 说明            |
| ------------- | ------ | ---- | ------------- |
| reco_id       | String | 否    | 记录ID   没有表示新增 |
| oper_id       | String | 否    | 术式主键          |
| oper_name     | String | 是    | 术式名称          |
| oper_code     | String | 否    | 术式编码          |
| oper_date     | Date   | 否    | 手术日期          |
| reco_describe | String | 否    | 描述信息，扩展描述     |

患者家族史列表说明

| 参数名          | 类型     | 必填   | 说明    |
| ------------ | ------ | ---- | ----- |
| reco_content | String | 否    | 家族史内容 |

其他个人史列表说明


| 参数名          | 类型     | 必填   | 说明    |
| ------------ | ------ | ---- | ----- |
| reco_content | String | 否    | 个人史内容 |

诊断列表说明

| 参数名            | 类型     | 必填   | 说明              |
| -------------- | ------ | ---- | --------------- |
| diag_pre_id    | String | 否    | 前缀ID            |
| diag_pre_name  | String | 是    | 前缀内容            |
| diag_id        | String | 是    | 诊断id            |
| diag_name      | String | 是    | 诊断名称            |
| diag_icd       | String | 是    | 诊断ICD编码，剑形编码，病因 |
| diag_attach    | String | 否    | 附加码             |
| diag_sufx_id   | String | 否    | 后缀ID            |
| diag_sufx_name | String | 是    | 后缀内容            |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 处理意见模板保存

```url
[POST]/emr/template/suggestion
```

#### 修改更新记录

| 对应业务        | 说明   |
| ----------- | ---- |
| WEBV1.2.3.1 | 新增   |

#### 请求报文参数
| 参数名          | 类型      | 长度   | 必填   | 说明              |
| ------------ | ------- | ---- | ---- | --------------- |
| sugg_content | String  | 256  | 是    | 处理意见内容          |
| sugg_type    | Integer |      | 是    | 所属类型;1:个人;0: 科室 |
| sugg_userid  | Long    |      | 否    | 用户ID            |
| sugg_depa_id | Long    |      | 否    | 科室ID，类型科室时有效    |

#### 回复报文参数

| 参数名     | 类型   | 必填   | 说明       |
| ------- | ---- | ---- | -------- |
| sugg_id | Long | 否    | 处理意见模板ID |

### 处理意见模板修改

```url
[POST]/emr/template/suggestion/update
```

#### 修改更新记录

| 对应业务        | 说明   |
| ----------- | ---- |
| WEBV1.2.3.1 | 新增   |

#### 请求报文参数
| 参数名          | 类型      | 长度   | 必填   | 说明              |
| ------------ | ------- | ---- | ---- | --------------- |
| sugg_id      | String  |      | 否    | 处理意见模板ID        |
| sugg_content | String  | 256  | 是    | 处理意见内容          |
| sugg_type    | Integer |      | 是    | 所属类型;1:个人;0: 科室 |
| sugg_userid  | Long    |      | 否    | 用户ID            |
| sugg_depa_id | Long    |      | 否    | 科室ID，类型科室时有效    |

#### 回复报文参数

| 参数名  | 类型 | 必填 |      说明      |
|---------|------|------|----------------|

### 处理意见模板删除

```url
[GET]/emr/template/suggestion/delete
```

#### 修改更新记录

| 对应业务        | 说明   |
| ----------- | ---- |
| WEBV1.2.3.1 | 新增   |

#### 请求报文参数
| 参数名     | 类型   | 必填   | 说明       |
| ------- | ---- | ---- | -------- |
| sugg_id | Long | 是    | 处理意见模板ID |

#### 回复报文参数

| 参数名  | 类型 | 必填 |      说明      |
|---------|------|------|----------------|


### 处理意见模板获取

```url
[GET]/emr/template/suggestion
```

#### 修改更新记录

| 对应业务        | 说明   |
| ----------- | ---- |
| WEBV1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明                    |
| ------- | ---- | ---- | --------------------- |
| sugg_id | Long | 是    | 处理意见模板ID,没有时为新建，有时为更新 |

#### 回复报文参数

| 参数名            | 类型      | 必填   | 说明                    |
| -------------- | ------- | ---- | --------------------- |
| sugg_id        | Long    | 是    | 处理意见模板ID,没有时为新建，有时为更新 |
| sugg_content   | String  | 是    | 处理意见内容                |
| sugg_type      | Integer | 是    | 所属类型;1:个人;0: 科室       |
| sugg_userid    | String  | 是    | 用户ID                  |
| sugg_username  | String  | 是    | 用户名称                  |
| sugg_depa_id   | String  | 否    | 科室ID，类型科室时有效          |
| sugg_depa_name | String  | 否    | 科室名称，类型科室时有效          |


### 处理意见模板获取列表

```url
[GET]/emr/template/suggestion/list
```

#### 修改更新记录

| 对应业务        | 说明   |
| ----------- | ---- |
| WEBV1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                            |
| ------------ | ------- | ---- | ----------------------------- |
| sugg_content | String  | 否    | 处理意见内容                        |
| sugg_type    | Integer | 是    | 所属类型;1:个人;0: 科室               |
| sugg_depa_id | String  | 否    | 科室ID，类型科室时有效 ,默认取header中的科室ID |
| page_size    | Integer | 否    | 每页条数 空表示10条                   |
| page_num     | Integer | 否    | 第几页 空表示第1页                    |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明       |
| --------- | ---------- | ---- | -------- |
| page_num  | Integer    | 是    | 当前页      |
| page_size | Integer    | 是    | 每页的数量    |
| total     | Integer    | 是    | 总记录数     |
| pages     | Integer    | 是    | 总页数      |
| list      | ObjectList | 否    | 处理意见内容列表 |

| 参数名            | 类型      | 必填   | 说明                    |
| -------------- | ------- | ---- | --------------------- |
| sugg_id        | Long    | 是    | 处理意见模板ID,没有时为新建，有时为更新 |
| sugg_content   | String  | 是    | 处理意见内容                |
| sugg_type      | Integer | 是    | 所属类型;1:个人;0: 科室       |
| sugg_userid    | String  | 是    | 用户ID                  |
| sugg_username  | String  | 是    | 用户名称                  |
| sugg_depa_id   | String  | 是    | 科室ID，类型科室时有效          |
| sugg_depa_name | String  | 是    | 科室名称，类型科室时有效          |


### 处理意见模板获取列表

```url
[GET]/emr/template/suggestions
```

#### 修改更新记录

| 对应业务        | 说明   |
| ----------- | ---- |
| WEBV1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名          | 类型     | 必填   | 说明     |
| ------------ | ------ | ---- | ------ |
| sugg_content | String | 否    | 处理意见内容 |

#### 回复报文参数 Objectlist列表


| 参数名          | 类型     | 必填   | 说明       |
| ------------ | ------ | ---- | -------- |
| sugg_id      | String | 是    | 处理意见模板ID |
| sugg_content | String | 是    | 处理意见内容   |



## 专科检查-基础检查


### 基础检查获取

```http
[GET]/treat_service/speciality_check/baselineexam
```

#### 修改更新记录

| 对应业务        | 说明                                       |
| ----------- | ---------------------------------------- |
| V1.2.3      | 新增                                       |
| V1.2.3.1    | 视力数据新增四个备注字段、遮盖试验原来的ortho拆分为远距离与近距离各一个、集合近点添加TTN选项 |
| WEBV1.2.3.2 | 新加眼球震颤数据、角膜映光点备注、眼轴数据                    |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数


| 参数名                                   | 类型      | 必填   | 说明                                       | 变更          |
| ------------------------------------- | ------- | ---- | ---------------------------------------- | ----------- |
| trea_id                               | String  | 是    | 就诊ID                                     |             |
| ----基础检查通用数据（baselineexam）--          |         |      |                                          |             |
| base_ht_otrho                         | Integer | 否    | 角膜映光点-otrho; 0-未选中;1-选中                  |             |
| base_ht_horizontal                    | String  | 否    | 角膜映光点-水平，otrho否时有效                       |             |
| base_ht_vertical_type                 | String  | 否    | 角膜映光点-垂直方向，otrho否时有效；1-R/L；2-L/R         |             |
| base_ht_vertical                      | String  | 否    | 角膜映光点-垂直                                 |             |
| base_ht_rem                           | String  | 否    | 角膜映光点-备注                                 | WEBV1.2.3.2 |
| base_npc_ttn                          | Integer | 否    | 集合近点-TTN;to the nose;0:未选中（破裂点、恢复点可编辑）；1:选中; |             |
| base_npc_break                        | String  | 否    | 集合近点-破裂点                                 |             |
| base_npc_restore                      | String  | 否    | 集合近点-恢复点                                 |             |
| base_amp_type                         | String  | 否    | 调节幅度-方法,1-移近法; 2-负镜片法;3-移近/移远法           |             |
| base_amp_od_cm                        | String  | 否    | 调节幅度-OD                                  |             |
| base_amp_od                           | String  | 否    | 调节幅度-OD                                  |             |
| base_amp_os_cm                        | String  | 否    | 调节幅度-OS                                  |             |
| base_amp_os                           | String  | 否    | 调节幅度-OS                                  |             |
| base_amp_ou_cm                        | String  | 否    | 调节幅度-OU                                  |             |
| base_amp_ou                           | String  | 否    | 调节幅度-OU                                  |             |
| --其它模板数据（template_data)---            |         |      |                                          |             |
| 瞳孔对光反射                                |         |      |                                          |             |
| pupil_light_reflection_status         | String  | 否    | 异常/正常;1-正常;2-异常                          |             |
| pupil_light_reflection_abnormal_value | String  | 否    | 异常值                                      |             |
| 遮盖试验（CT）                              |         |      |                                          |             |
| distance_ortho                        | Integer | 否    | ortho;0-未选中;1-选中                         |             |
| distance_type                         | String  | 否    | 远距离类型:<br/>1-内隐斜;<br/>2-外隐斜;<br/>3-垂直隐斜;<br/>4-内斜;<br/>5-外斜;<br/>6-间歇性外斜视;<br/>7-垂直性斜视;<br />8-正位; |             |
| distance_value                        | String  | 否    | 远距离说明                                    |             |
| near_ortho                            | Integer | 否    | ortho;0-未选中;1-选中                         |             |
| near_type                             | String  | 否    | 近距离类型:<br/>1-内隐斜;<br/>2-外隐斜;<br/>3-垂直隐斜;<br/>4-内斜;<br/>5-外斜;<br/>6-间歇性外斜视;<br/>7-垂直性斜视;<br />8-正位; |             |
| near_value                            | String  | 否    | 近距离说明                                    |             |
| 眼球运动（EOM）                             |         |      |                                          |             |
| eyeball_movement_status               | String  | 否    | safe/异常;1-SAFE;2-异常                      |             |
| eyeball_movement_abnormal_value       | String  | 否    | 异常值                                      |             |
| 原镜度数                                  |         |      |                                          |             |
| data_od_sphere                        | String  | 否    | OD-球镜                                    |             |
| data_od_cylinder                      | String  | 否    | OD-柱镜                                    |             |
| data_od_axis                          | String  | 否    | OD-轴向                                    |             |
| data_od_rem                           | String  | 否    | OD-备注                                    |             |
| data_os_sphere                        | String  | 否    | OS-球镜                                    |             |
| data_os_cylinder                      | String  | 否    | OS-柱镜                                    |             |
| data_os_axis                          | String  | 否    | OS-轴向                                    |             |
| data_os_rem                           | String  | 否    | 远用OS-备注                                  |             |
| 远视力近视力                                |         |      |                                          |             |
| data_od_distance_vision               | String  | 否    | 裸眼远用OD-视力                                |             |
| data_os_distance_vision               | String  | 否    | 裸眼远用OS-视力                                |             |
| data_ou_distance_vision               | String  | 否    | 裸眼远用OU-视力                                |             |
| data_distance_vision_rem              | String  | 否    | 裸眼远用视力备注                                 |             |
| data_od_near_vision                   | String  | 否    | 裸眼近用OD-视力                                |             |
| data_os_near_vision                   | String  | 否    | 裸眼近用OS-视力                                |             |
| data_ou_near_vision                   | String  | 否    | 裸眼近用OU-视力                                |             |
| data_near_vision_rem                  | String  | 否    | 裸眼近用视力备注                                 |             |
| data_od_distance_original             | String  | 否    | 原镜远用OD-视力                                |             |
| data_os_distance_original             | String  | 否    | 原镜远用OS-视力                                |             |
| data_ou_distance_original             | String  | 否    | 原镜远用OU-视力                                |             |
| data_distance_original_rem            | String  | 否    | 原镜远用视力备注                                 |             |
| data_od_near_original                 | String  | 否    | 原镜近用OD-视力                                |             |
| data_os_near_original                 | String  | 否    | 原镜近用OS-视力                                |             |
| data_ou_near_original                 | String  | 否    | 原镜近用OU-视力                                |             |
| data_near_original_rem                | String  | 否    | 原镜近用视力备注                                 |             |
| 眼压眼轴数据                                |         |      |                                          |             |
| data_od_iop                           | String  | 否    | OD-眼压,mmgh                               | V1.2.3.2    |
| data_os_iop                           | String  | 否    | OS-眼压,mmgh                               | V1.2.3.2    |
| data_od_iop_axis                      | String  | 否    | OD-眼轴,mm                                 | V1.2.3.2    |
| data_os_iop_axis                      | String  | 否    | OD-眼轴,mm                                 | V1.2.3.2    |
| 眼球震颤                                  |         |      |                                          | V1.2.3.2    |
| nystagmus_status                      | Integer | 否    | 眼球震颤状态:<br/>1-否;<br/>2-是                 | V1.2.3.2    |
| nystagmus_middle_status               | Integer | 否    | 眼球震颤中间带状态:<br/>1-不存在;<br/>2-存在           | V1.2.3.2    |
| nystagmus_middle_face                 | Integer | 否    | 眼球震颤中间带面部朝向:<br/>1-面向正前方;<br/>2-面向左前方;<br/>3-面向右前方; | V1.2.3.2    |
| nystagmus_middle_head                 | Integer | 否    | 眼球震颤中间带头部位置:<br/>1-头部正位;<br/>2-头部向右肩倾斜;<br/>3-头部向左肩倾斜; | V1.2.3.2    |
| nystagmus_middle_jaw                  | Integer | 否    | 眼球震颤中间带下巴位置:<br/>1-下巴正位;<br/>2-下巴上抬;<br/>3-下巴内收; | V1.2.3.2    |
| nystagmus_value                       | String  | 否    | 眼震值                                      | V1.2.3.2    |
| nystagmus_nature                      | Integer | 否    | 震颤性质:<br/>1-冲动型;<br/>2-钟摆型;              | V1.2.3.2    |
| nystagmus_direction                   | Integer | 否    | 震颤方向:<br/>1-水平;<br/>2-垂直;<br/>3-旋转;<br/>3-混合; | V1.2.3.2    |
| 近附加                                   |         |      |                                          |             |
| data_add                              | String  | 否    | 近附加数据                                    |             |



### 基础检查保存

```http
[POST]/treat_service/speciality_check/baselineexam
```

#### 修改更新记录

| 对应业务        | 说明                    |
| ----------- | --------------------- |
| V1.2.3      | 新增                    |
| WEBV1.2.3.2 | 新加眼球震颤数据、角膜映光点备注、眼轴数据 |

#### 请求报文参数

|          参数名          	|   类型  	| 长度 	| 必填 	|                           说明                          	|  变更         	|
|--------------------------	|---------	|------	|------	|---------------------------------------------------------	|-------------	|
| trea_id       			| String 	|		| 是   	| 就诊ID           											|				|
| ----基础检查通用数据（baselineexam）--  	|  |	|    	|  															|				|
| base_ht_otrho         	| Integer 	|		| 否   	| 角膜映光点-otrho; 0-未选中;1-选中                         	|				|
| base_ht_horizontal    	| String  	|		| 否   	| 角膜映光点-水平，otrho否时有效                              	|				|
| base_ht_vertical_type 	| String  	|		| 否   	| 角膜映光点-垂直方向，otrho否时有效；1-R/L；2-L/R              	|				|
| base_ht_vertical      	| String  	|		| 否   	| 角膜映光点-垂直                                             |				|
| base_ht_rem           	| String  	|   50 	| 否   	| 角膜映光点-备注                                             | WEBV1.2.3.2 	|
| base_npc_ttn          	| Integer 	|		| 否   	| 集合近点-TTN;to the nose;0:未选中（破裂点、恢复点可编辑）；1:选中;|				|
| base_npc_break        	| String  	|		| 否   	| 集合近点-破裂点                                             |				|
| base_npc_restore      	| String  	|		| 否   	| 集合近点-恢复点                                             |				|
| base_amp_type         	| String  	|		| 否   	| 调节幅度-方法,1-移近法; 2-负镜片法;3-移近/移远法             	|				|
| base_amp_od_cm        	| String  	|		| 否   	| 调节幅度-OD                                               	|				|
| base_amp_od           	| String  	|		| 否   	| 调节幅度-OD                                               	|				|
| base_amp_os_cm        	| String  	|		| 否   	| 调节幅度-OS                                              	|				|
| base_amp_os           	| String  	|		| 否   	| 调节幅度-OS                                               	|				|
| base_amp_ou_cm        	| String  	|		| 否   	| 调节幅度-OU                                              	|				|
| base_amp_ou           	| String  	|		| 否   	| 调节幅度-OU                                             	|				|
| --其它模板数据（template_data)--- |  	|    	|      	|															|				|
| 瞳孔对光反射                |         	|		|      	|                                                        	|				|
| pupil_light_reflection_status | Integer|		| 否   	| 异常/正常;1-正常;2-异常                                    	|				|
| pupil_light_reflection_abnormal_value | String|| 否   	| 异常值                                                    	|				|
| 遮盖试验（CT）            	|         	|		|      	|                                                         	|				|
| option                   	| Integer 	|		| 否  	| ortho;0-未选中;1-选中                                     	|				|
| distance_type            	| Integer 	|		| 否 	| 远距离类型:<br/>1-内隐斜;<br/>2-外隐斜;<br/>3-垂直隐斜;<br/>4-内斜;<br/>5-外斜;<br/>6-间歇性外斜视;<br/>7-垂直性斜视;<br />8-正位; ||
| distance_value           	| String  	|		| 否  	| 远距离说明                                                	|				|
| near_type               	| Integer 	|		| 否 	| 近距离类型:<br/>1-内隐斜;<br/>2-外隐斜;<br/>3-垂直隐斜;<br/>4-内斜;<br/>5-外斜;<br/>6-间歇性外斜视;<br/>7-垂直性斜视;<br />8-正位; ||
| near_value              	| String  	|		| 否 	| 近距离说明                                              	|				|
| 眼球运动（EOM）            	|         	|		|      	|                                                       	|				|
| eyeball_movement_status  	| Integer 	|		| 否   	| safe/异常;1-SAFE;2-异常                                 	|				|
| eyeball_movement_abnormal_value| String|		| 否   	| 异常值                  									|				|
| 原镜度数                 	|         	|		|		|      														|				|
| data_od_sphere   			| String  	|		| 否   	| OD-球镜    												|				|
| data_od_cylinder 			| String  	|		| 否   	| OD-柱镜    												|				|
| data_od_axis     			| String  	|		| 否   	| OD-轴向    												|				|
| data_od_rem      			| String  	|		| 否   	| OD-备注    												|				|
| data_os_sphere   			| String  	|		| 否   	| OS-球镜    												|				|
| data_os_cylinder 			| String  	|		| 否   	| OS-柱镜    												|				|
| data_os_axis     			| String  	|		| 否   	| OS-轴向    												|				|
| data_os_rem      			| String  	|		| 否   	| 远用OS-备注 												|				|
| 远视力近视力                |         	|      	|       |              												|				|
| data_od_distance_vision   | String  	|		| 否   	| 裸眼远用OD-视力												|				|
| data_os_distance_vision   | String  	|		| 否   	| 裸眼远用OS-视力												|				|
| data_ou_distance_vision   | String  	|		| 否   	| 裸眼远用OU-视力												|				|
| data_od_near_vision       | String  	|		| 否   	| 裸眼近用OD-视力												|				|
| data_os_near_vision       | String  	|		| 否   	| 裸眼近用OS-视力												|				|
| data_ou_near_vision       | String  	|		| 否   	| 裸眼近用OU-视力												|				|
| data_od_distance_original | String  	|		| 否   	| 原镜远用OD-视力												|				|
| data_os_distance_original | String  	|		| 否   	| 原镜远用OS-视力												|				|
| data_ou_distance_original | String  	|		| 否   	| 原镜远用OU-视力												|				|
| data_od_near_original     | String  	|		| 否   	| 原镜近用OD-视力												|				|
| data_os_near_original     | String  	|		| 否   	| 原镜近用OS-视力												|				|
| data_ou_near_original     | String  	|		| 否   	| 原镜近用OU-视力												|				|
| 眼压眼轴数据              	|       	|       |      	|                                                           |				|
| data_od_iop  				| String 	|   12 	| 否   	| OD-眼压,mmgh												| WEBV1.2.3.2 	|
| data_os_iop  				| String 	|   12 	| 否   	| OS-眼压,mmgh 												| WEBV1.2.3.2 	|
| data_od_iop_axis 				| String 	|   12 	| 否   	| OD-眼轴,mm   												| WEBV1.2.3.2 	|
| data_os_iop_axis 				| String 	|   12 	| 否   	| OD-眼轴,mm   												| WEBV1.2.3.2 	|
| 眼球震颤                   |         	|      	|       |                                                           | WEBV1.2.3.2 	|
| nystagmus_status        	| Integer 	|      	| 否   	| 眼球震颤状态:<br/>1-否;<br/>2-是                            	| WEBV1.2.3.2 	|
| nystagmus_middle_status 	| Integer 	|      	| 否   	| 眼球震颤中间带状态:<br/>1-不存在;<br/>2-存在                	| WEBV1.2.3.2 	|
| nystagmus_middle_face   	| Integer 	|      	| 否   	| 眼球震颤中间带面部朝向:<br/>1-面向正前方;<br/>2-面向左前方;<br/>3-面向右前方;| WEBV1.2.3.2 	|
| nystagmus_middle_head   	| Integer 	|      	| 否   	| 眼球震颤中间带头部位置:<br/>1-头部正位;<br/>2-头部向右肩倾斜;<br/>3-头部向左肩倾斜;| WEBV1.2.3.2 	|
| nystagmus_middle_jaw    	| Integer 	|      	| 否   	| 眼球震颤中间带下巴位置:<br/>1-下巴正位;<br/>2-下巴上抬;<br/>3-下巴内收; | WEBV1.2.3.2 	|
| nystagmus_value         	| String  	|   12 	| 否   	| 眼震值                                                    	| WEBV1.2.3.2 	|
| nystagmus_nature        	| Integer 	|      	| 否   	| 震颤性质:<br/>1-冲动型;<br/>2-钟摆型;                       	| WEBV1.2.3.2 	|
| nystagmus_direction     	| Integer 	|      	| 否   	| 震颤方向:<br/>1-水平;<br/>2-垂直;<br/>3-旋转;<br/>3-混合; 	| WEBV1.2.3.2 	|
| 近附加                     |         	|      	|       |                                                          	|				|
| data_add 					| String 	|		| 否   	| 近附加数据 													|				|

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |




##专科检查-屈光检查


### 获取屈光检查数据

> [GET]/treat_service/speciality_check/refraction 

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊号  |

#### 回复报文参数

| 参数名                                 | 类型         | 必填   | 说明           |
| ----------------------------------- | ---------- | ---- | ------------ |
| trea_id                             | String     | 是    | 就诊号          |
| --- 电脑验光-----                       |            |      |              |
| data_od_sphere                      | String     | 否    | 电脑验光球镜od     |
| data_od_cylinder                    | String     | 否    | 电脑验光柱镜od     |
| data_od_axis                        | String     | 否    | 电脑验光轴向od     |
| data_od_rem                         | String     | 否    | 电脑验光OD备注     |
| data_os_sphere                      | String     | 否    | 电脑验光球镜os     |
| data_os_cylinder                    | String     | 否    | 电脑验光柱镜os     |
| data_os_axis                        | String     | 否    | 电脑验光轴向os     |
| data_os_rem                         | String     | 否    | 电脑验光OS备注     |
| --- 睫麻后电脑验光-----                    |            |      |              |
| cycloplegic_data_od_sphere          | String     | 否    | 电脑验光球镜od     |
| cycloplegic_data_od_cylinder        | String     | 否    | 电脑验光柱镜od     |
| cycloplegic_data_od_axis            | String     | 否    | 电脑验光轴向od     |
| cycloplegic_data_od_rem             | String     | 否    | 电脑验光OD备注     |
| cycloplegic_data_os_sphere          | String     | 否    | 电脑验光球镜os     |
| cycloplegic_data_os_cylinder        | String     | 否    | 电脑验光柱镜os     |
| cycloplegic_data_os_axis            | String     | 否    | 电脑验光轴向os     |
| cycloplegic_data_os_rem             | String     | 否    | 电脑验光OS备注     |
| --- 主觉检影验光-----                     |            |      |              |
| retinoscopy_od_sphere               | Double     | 否    | 检影验光OD-球镜    |
| retinoscopy_od_cylinder             | Double     | 否    | 检影验光OD-柱镜    |
| retinoscopy_od_axis                 | Double     | 否    | 检影验光OD-轴向    |
| retinoscopy_od_vision               | Double     | 否    | 检影验光OD-视力    |
| retinoscopy_od_memo                 | String     | 否    | 检影验光OD-备注    |
| retinoscopy_os_sphere               | Double     | 否    | 检影验光OS-球镜    |
| retinoscopy_os_cylinder             | Double     | 否    | 检影验光OS-柱镜    |
| retinoscopy_os_axis                 | Double     | 否    | 检影验光OS-轴向    |
| retinoscopy_os_vision               | Double     | 否    | 检影验光OS-视力    |
| retinoscopy_os_memo                 | String     | 否    | 检影验光OS-备注    |
| cycloplegic_retinoscopy_od_sphere   | Double     | 否    | 睫麻后检影验光OD-球镜 |
| cycloplegic_retinoscopy_od_cylinder | Double     | 否    | 睫麻后检影验光OD-柱镜 |
| cycloplegic_retinoscopy_od_axis     | Double     | 否    | 睫麻后检影验光OD-轴向 |
| cycloplegic_retinoscopy_od_vision   | Double     | 否    | 睫麻后检影验光OD-视力 |
| cycloplegic_retinoscopy_od_memo     | String     | 否    | 睫麻后检影验光OD-备注 |
| cycloplegic_retinoscopy_os_sphere   | Double     | 否    | 睫麻后检影验光OS-球镜 |
| cycloplegic_retinoscopy_os_cylinder | Double     | 否    | 睫麻后检影验光OS-柱镜 |
| cycloplegic_retinoscopy_os_axis     | Double     | 否    | 睫麻后检影验光OS-轴向 |
| cycloplegic_retinoscopy_os_vision   | Double     | 否    | 睫麻后检影验光OS-视力 |
| cycloplegic_retinoscopy_os_memo     | String     | 否    | 睫麻后检影验光OS-备注 |
| subjective_od_sphere                | Double     | 否    | 主觉验光OD-球镜    |
| subjective_od_cylinder              | Double     | 否    | 主觉验光OD-柱镜    |
| subjective_od_axis                  | Double     | 否    | 主觉验光OD-轴向    |
| subjective_od_prism                 | Double     | 否    | 主觉验光OD-棱镜    |
| subjective_od_vision                | Double     | 否    | 主觉验光OD-视力    |
| subjective_od_memo                  | String     | 否    | 主觉验光OD-备注    |
| subjective_os_sphere                | Double     | 否    | 主觉验光OS-球镜    |
| subjective_os_cylinder              | Double     | 否    | 主觉验光OS-柱镜    |
| subjective_os_axis                  | Double     | 否    | 主觉验光OS-轴向    |
| subjective_od_prism                 | Double     | 否    | 主觉验光OS-棱镜    |
| subjective_os_vision                | Double     | 否    | 主觉验光OS-视力    |
| subjective_os_memo                  | String     | 否    | 主觉验光OS-备注    |
| cycloplegic_subjective_od_sphere    | Double     | 否    | 睫麻后主觉验光OD-球镜 |
| cycloplegic_subjective_od_cylinder  | Double     | 否    | 睫麻后主觉验光OD-柱镜 |
| cycloplegic_subjective_od_axis      | Double     | 否    | 睫麻后主觉验光OD-轴向 |
| cycloplegic_subjective_od_prism     | Double     | 否    | 睫麻后主觉验光OD-棱镜 |
| cycloplegic_subjective_od_vision    | Double     | 否    | 睫麻后主觉验光OD-视力 |
| cycloplegic_subjective_od_memo      | String     | 否    | 睫麻后主觉验光OD-备注 |
| cycloplegic_subjective_os_sphere    | Double     | 否    | 睫麻后主觉验光OS-球镜 |
| cycloplegic_subjective_os_cylinder  | Double     | 否    | 睫麻后主觉验光OS-柱镜 |
| cycloplegic_subjective_os_axis      | Double     | 否    | 睫麻后主觉验光OS-轴向 |
| cycloplegic_subjective_os_vision    | Double     | 否    | 睫麻后主觉验光OS-棱镜 |
| cycloplegic_subjective_os_prism     | Double     | 否    | 睫麻后主觉验光OS-视力 |
| cycloplegic_subjective_os_memo      | String     | 否    | 睫麻后主觉验光OS-备注 |
| presbyopicadd                       | Double     | 否    | 附近加          |
| --- 配镜处方数据-----                     |            |      |              |
| opto_id                             | String     | 是    | 视光处方ID       |
| opto_far_pd                         | Integer    | 否    | 瞳距-远用        |
| opto_near_pd                        | Integer    | 否    | 瞳距-近用        |
| opto_od_pd                          | Integer    | 否    | 瞳距-单眼OD      |
| opto_os_pd                          | Integer    | 否    | 瞳距-单眼OS      |
| opto_od_ph                          | Integer    | 否    | 瞳高-OD        |
| opto_os_ph                          | Integer    | 否    | 瞳高-OS        |
| opto_far_od_sphere                  | Double     | 否    | 远用OD-球镜      |
| opto_far_od_cylinder                | Double     | 否    | 远用OD-柱镜      |
| opto_far_od_axis                    | Double     | 否    | 远用OD-轴向      |
| opto_far_od_prism                   | Double     | 否    | 远用OD-棱镜      |
| opto_far_od_vision                  | Double     | 否    | 远用OD-视力      |
| opto_far_od_memo                    | String     | 否    | 远用OD-备注      |
| opto_far_os_sphere                  | Double     | 否    | 远用OS-球镜      |
| opto_far_os_cylinder                | Double     | 否    | 远用OS-柱镜      |
| opto_far_os_axis                    | Double     | 否    | 远用OS-轴向      |
| opto_far_os_prism                   | Double     | 否    | 远用OS-棱镜      |
| opto_far_os_vision                  | Double     | 否    | 远用OS-视力      |
| opto_far_os_memo                    | String     | 否    | 远用OS-备注      |
| opto_near_od_sphere                 | Double     | 否    | 近用OD-球镜      |
| opto_near_od_cylinder               | Double     | 否    | 近用OD-柱镜      |
| opto_near_od_axis                   | Double     | 否    | 近用OD-轴向      |
| opto_near_od_prism                  | Double     | 否    | 近用OD-棱镜      |
| opto_near_od_vision                 | Double     | 否    | 近用OD-视力      |
| opto_near_od_memo                   | String     | 否    | 近用OD-备注      |
| opto_near_os_sphere                 | Double     | 否    | 近用OS-球镜      |
| opto_near_os_cylinder               | Double     | 否    | 近用OS-柱镜      |
| opto_near_os_axis                   | Double     | 否    | 近用OS-轴向      |
| opto_near_os_prism                  | Double     | 否    | 近用OS-棱镜      |
| opto_near_os_vision                 | Double     | 否    | 近用OS-视力      |
| opto_near_os_memo                   | String     | 否    | 近用OS-备注      |
| opto_lens_od_sphere                 | Double     | 否    | 隐形眼镜OD-球镜    |
| opto_lens_od_cylinder               | Double     | 否    | 隐形眼镜OD-柱镜    |
| opto_lens_od_axis                   | Double     | 否    | 隐形眼镜OD-轴向    |
| opto_lens_od_memo                   | String     | 否    | 隐形眼镜OD-备注    |
| opto_lens_os_sphere                 | Double     | 否    | 隐形眼镜OS-球镜    |
| opto_lens_os_cylinder               | Double     | 否    | 隐形眼镜OS-柱镜    |
| opto_lens_os_axis                   | Double     | 否    | 隐形眼镜OS-轴向    |
| opto_lens_os_memo                   | String     | 否    | 隐形眼镜OS-备注    |
| --- 角膜曲率数据-----                     |            |      |              |
| corneal_od_cliffy                   | String     | 否    | 右眼陡峭         |
| corneal_od_flat                     | String     | 否    | 右眼平坦         |
| corneal_od_axis                     | String     | 否    | 右眼轴向         |
| corneal_os_cliffy                   | String     | 否    | 左眼陡峭         |
| corneal_os_flat                     | String     | 否    | 左眼平坦         |
| corneal_os_axis                     | String     | 否    | 左眼轴向         |
| --- 其他处方-----                       |            |      |              |
| other_prescription_list             | ObjectList | 否    | 其他处方列表       |

其他处方列表说明

| 参数名             | 类型     | 必填   | 说明              |
| --------------- | ------ | ---- | --------------- |
| othe_id         | String | 否    | 其他处方处方id（无代表新增） |
| othe_clas_id    | String | 是    | 类别id            |
| othe_clas_code  | String | 是    | 商品类别代码          |
| othe_goods_id   | String | 是    | 商品id            |
| othe_count      | String | 是    | 数量              |
| othe_goods_unit | String | 否    | 单位              |
| othe_rem        | String | 否    | 备注              |


### 保存屈光检查数据

>  [POST]/treat_service/speciality_check/refraction

#### 请求报文参数

| 参数名                                 | 类型         | 必填   | 说明           |
| ----------------------------------- | ---------- | ---- | ------------ |
| trea_id                             | String     | 是    | 就诊号          |
| --- 电脑验光-----                       |            |      |              |
| data_od_sphere                      | String     | 否    | 电脑验光球镜od     |
| data_od_cylinder                    | String     | 否    | 电脑验光柱镜od     |
| data_od_axis                        | String     | 否    | 电脑验光轴向od     |
| data_od_rem                         | String     | 否    | 电脑验光OD备注     |
| data_os_sphere                      | String     | 否    | 电脑验光球镜os     |
| data_os_cylinder                    | String     | 否    | 电脑验光柱镜os     |
| data_os_axis                        | String     | 否    | 电脑验光轴向os     |
| data_os_rem                         | String     | 否    | 电脑验光OS备注     |
| --- 睫麻后电脑验光-----                    |            |      |              |
| cycloplegic_data_od_sphere          | String     | 否    | 电脑验光球镜od     |
| cycloplegic_data_od_cylinder        | String     | 否    | 电脑验光柱镜od     |
| cycloplegic_data_od_axis            | String     | 否    | 电脑验光轴向od     |
| cycloplegic_data_od_rem             | String     | 否    | 电脑验光OD备注     |
| cycloplegic_data_os_sphere          | String     | 否    | 电脑验光球镜os     |
| cycloplegic_data_os_cylinder        | String     | 否    | 电脑验光柱镜os     |
| cycloplegic_data_os_axis            | String     | 否    | 电脑验光轴向os     |
| cycloplegic_data_os_rem             | String     | 否    | 电脑验光OS备注     |
| --- 主觉检影验光-----                     |            |      |              |
| retinoscopy_od_sphere               | Double     | 否    | 检影验光OD-球镜    |
| retinoscopy_od_cylinder             | Double     | 否    | 检影验光OD-柱镜    |
| retinoscopy_od_axis                 | Double     | 否    | 检影验光OD-轴向    |
| retinoscopy_od_vision               | Double     | 否    | 检影验光OD-视力    |
| retinoscopy_od_memo                 | String     | 否    | 检影验光OD-备注    |
| retinoscopy_os_sphere               | Double     | 否    | 检影验光OS-球镜    |
| retinoscopy_os_cylinder             | Double     | 否    | 检影验光OS-柱镜    |
| retinoscopy_os_axis                 | Double     | 否    | 检影验光OS-轴向    |
| retinoscopy_os_vision               | Double     | 否    | 检影验光OS-视力    |
| retinoscopy_os_memo                 | String     | 否    | 检影验光OS-备注    |
| cycloplegic_retinoscopy_od_sphere   | Double     | 否    | 睫麻后检影验光OD-球镜 |
| cycloplegic_retinoscopy_od_cylinder | Double     | 否    | 睫麻后检影验光OD-柱镜 |
| cycloplegic_retinoscopy_od_axis     | Double     | 否    | 睫麻后检影验光OD-轴向 |
| cycloplegic_retinoscopy_od_vision   | Double     | 否    | 睫麻后检影验光OD-视力 |
| cycloplegic_retinoscopy_od_memo     | String     | 否    | 睫麻后检影验光OD-备注 |
| cycloplegic_retinoscopy_os_sphere   | Double     | 否    | 睫麻后检影验光OS-球镜 |
| cycloplegic_retinoscopy_os_cylinder | Double     | 否    | 睫麻后检影验光OS-柱镜 |
| cycloplegic_retinoscopy_os_axis     | Double     | 否    | 睫麻后检影验光OS-轴向 |
| cycloplegic_retinoscopy_os_vision   | Double     | 否    | 睫麻后检影验光OS-视力 |
| cycloplegic_retinoscopy_os_memo     | String     | 否    | 睫麻后检影验光OS-备注 |
| subjective_od_sphere                | Double     | 否    | 主觉验光OD-球镜    |
| subjective_od_cylinder              | Double     | 否    | 主觉验光OD-柱镜    |
| subjective_od_axis                  | Double     | 否    | 主觉验光OD-轴向    |
| subjective_od_prism                 | Double     | 否    | 主觉验光OD-棱镜    |
| subjective_od_vision                | Double     | 否    | 主觉验光OD-视力    |
| subjective_od_memo                  | String     | 否    | 主觉验光OD-备注    |
| subjective_os_sphere                | Double     | 否    | 主觉验光OS-球镜    |
| subjective_os_cylinder              | Double     | 否    | 主觉验光OS-柱镜    |
| subjective_os_axis                  | Double     | 否    | 主觉验光OS-轴向    |
| subjective_od_prism                 | Double     | 否    | 主觉验光OS-棱镜    |
| subjective_os_vision                | Double     | 否    | 主觉验光OS-视力    |
| subjective_os_memo                  | String     | 否    | 主觉验光OS-备注    |
| cycloplegic_subjective_od_sphere    | Double     | 否    | 睫麻后主觉验光OD-球镜 |
| cycloplegic_subjective_od_cylinder  | Double     | 否    | 睫麻后主觉验光OD-柱镜 |
| cycloplegic_subjective_od_axis      | Double     | 否    | 睫麻后主觉验光OD-轴向 |
| cycloplegic_subjective_od_prism     | Double     | 否    | 睫麻后主觉验光OD-棱镜 |
| cycloplegic_subjective_od_vision    | Double     | 否    | 睫麻后主觉验光OD-视力 |
| cycloplegic_subjective_od_memo      | String     | 否    | 睫麻后主觉验光OD-备注 |
| cycloplegic_subjective_os_sphere    | Double     | 否    | 睫麻后主觉验光OS-球镜 |
| cycloplegic_subjective_os_cylinder  | Double     | 否    | 睫麻后主觉验光OS-柱镜 |
| cycloplegic_subjective_os_axis      | Double     | 否    | 睫麻后主觉验光OS-轴向 |
| cycloplegic_subjective_os_vision    | Double     | 否    | 睫麻后主觉验光OS-棱镜 |
| cycloplegic_subjective_os_prism     | Double     | 否    | 睫麻后主觉验光OS-视力 |
| cycloplegic_subjective_os_memo      | String     | 否    | 睫麻后主觉验光OS-备注 |
| presbyopicadd                       | Double     | 否    | 附近加          |
| --- 配镜处方数据-----                     |            |      |              |
| opto_id                             | String     | 是    | 视光处方ID       |
| opto_far_pd                         | Integer    | 否    | 瞳距-远用        |
| opto_near_pd                        | Integer    | 否    | 瞳距-近用        |
| opto_od_pd                          | Integer    | 否    | 瞳距-单眼OD      |
| opto_os_pd                          | Integer    | 否    | 瞳距-单眼OS      |
| opto_od_ph                          | Integer    | 否    | 瞳高-OD        |
| opto_os_ph                          | Integer    | 否    | 瞳高-OS        |
| opto_far_od_sphere                  | Double     | 否    | 远用OD-球镜      |
| opto_far_od_cylinder                | Double     | 否    | 远用OD-柱镜      |
| opto_far_od_axis                    | Double     | 否    | 远用OD-轴向      |
| opto_far_od_prism                   | Double     | 否    | 远用OD-棱镜      |
| opto_far_od_vision                  | Double     | 否    | 远用OD-视力      |
| opto_far_od_memo                    | String     | 否    | 远用OD-备注      |
| opto_far_os_sphere                  | Double     | 否    | 远用OS-球镜      |
| opto_far_os_cylinder                | Double     | 否    | 远用OS-柱镜      |
| opto_far_os_axis                    | Double     | 否    | 远用OS-轴向      |
| opto_far_os_prism                   | Double     | 否    | 远用OS-棱镜      |
| opto_far_os_vision                  | Double     | 否    | 远用OS-视力      |
| opto_far_os_memo                    | String     | 否    | 远用OS-备注      |
| opto_near_od_sphere                 | Double     | 否    | 近用OD-球镜      |
| opto_near_od_cylinder               | Double     | 否    | 近用OD-柱镜      |
| opto_near_od_axis                   | Double     | 否    | 近用OD-轴向      |
| opto_near_od_prism                  | Double     | 否    | 近用OD-棱镜      |
| opto_near_od_vision                 | Double     | 否    | 近用OD-视力      |
| opto_near_od_memo                   | String     | 否    | 近用OD-备注      |
| opto_near_os_sphere                 | Double     | 否    | 近用OS-球镜      |
| opto_near_os_cylinder               | Double     | 否    | 近用OS-柱镜      |
| opto_near_os_axis                   | Double     | 否    | 近用OS-轴向      |
| opto_near_os_prism                  | Double     | 否    | 近用OS-棱镜      |
| opto_near_os_vision                 | Double     | 否    | 近用OS-视力      |
| opto_near_os_memo                   | String     | 否    | 近用OS-备注      |
| opto_lens_od_sphere                 | Double     | 否    | 隐形眼镜OD-球镜    |
| opto_lens_od_cylinder               | Double     | 否    | 隐形眼镜OD-柱镜    |
| opto_lens_od_axis                   | Double     | 否    | 隐形眼镜OD-轴向    |
| opto_lens_od_memo                   | String     | 否    | 隐形眼镜OD-备注    |
| opto_lens_os_sphere                 | Double     | 否    | 隐形眼镜OS-球镜    |
| opto_lens_os_cylinder               | Double     | 否    | 隐形眼镜OS-柱镜    |
| opto_lens_os_axis                   | Double     | 否    | 隐形眼镜OS-轴向    |
| opto_lens_os_memo                   | String     | 否    | 隐形眼镜OS-备注    |
| --- 角膜曲率数据-----                     |            |      |              |
| corneal_od_cliffy                   | String     | 否    | 右眼陡峭         |
| corneal_od_flat                     | String     | 否    | 右眼平坦         |
| corneal_od_axis                     | String     | 否    | 右眼轴向         |
| corneal_os_cliffy                   | String     | 否    | 左眼陡峭         |
| corneal_os_flat                     | String     | 否    | 左眼平坦         |
| corneal_os_axis                     | String     | 否    | 左眼轴向         |
| --- 其他处方-----                       |            |      |              |
| other_prescription_list             | ObjectList | 否    | 其他处方列表       |

其他处方列表说明

| 参数名             | 类型     | 必填   | 说明              |
| --------------- | ------ | ---- | --------------- |
| othe_id         | String | 否    | 其他处方处方id（无代表新增） |
| othe_clas_id    | String | 是    | 类别id            |
| othe_clas_code  | String | 是    | 商品类别代码          |
| othe_goods_id   | String | 是    | 商品id            |
| othe_count      | String | 是    | 数量              |
| othe_goods_unit | String | 否    | 单位              |
| othe_rem        | String | 否    | 备注              |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



##专科检查-眼健康检查


### 专科检查-眼健康检查获取

```http
[GET]/treat_service/speciality_check/eyehealth
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊号  |

#### 回复报文参数

| 参数名                     | 类型     | 必填   | 说明                    |
| ----------------------- | ------ | ---- | --------------------- |
| --模板数据(template_data)-- | Object |      |                       |
| 裂隙灯检查                   |        |      |                       |
| od_eyelid               | String | 否    | 眼睑od:常规时默认:无倒睫，眼睑闭合完全 |
| os_eyelid               | String | 否    | 眼睑os:常规时默认:无倒睫，眼睑闭合完全 |
| od_tears                | String | 否    | 泪器od:常规时默认:泪点位正       |
| os_tears                | String | 否    | 泪器os:常规时默认:泪点位正       |
| od_conjunctiva          | String | 否    | 结膜od:常规时默认:无充血、水肿     |
| os_conjunctiva          | String | 否    | 结膜os:常规时默认:无充血、水肿     |
| od_cornea               | String | 否    | 角膜od:常规时默认:透明         |
| os_cornea               | String | 否    | 角膜os:常规时默认:透明         |
| od_chamber              | String | 否    | 前房od:常规时默认:清、深        |
| os_chamber              | String | 否    | 前房os:常规时默认:清、深        |
| od_lris                 | String | 否    | 虹膜od:常规时默认:纹理清        |
| os_lris                 | String | 否    | 虹膜os:常规时默认:纹理清        |
| od_pupil                | String | 否    | 瞳孔od:常规时默认:PERRL      |
| os_pupil                | String | 否    | 瞳孔os:常规时默认:PERRL      |
| od_crystal              | String | 否    | 晶体od:常规时默认:透明         |
| os_crystal              | String | 否    | 晶体os:常规时默认:透明         |
| od_vitreous             | String | 否    | 玻璃体od:常规时默认:无混浊       |
| os_vitreous             | String | 否    | 玻璃体os:常规时默认:无混浊       |
| slit_lamp_od_other      | String | 否    | 其它od                  |
| slit_lamp_os_other      | String | 否    | 其它os                  |
| 眼底镜检查                   |        |      |                       |
| od_disk                 | String | 否    | 视盘OD:常规时默认:色红界清       |
| os_disk                 | String | 否    | 视盘OS:常规时默认:色红界清       |
| od_cd                   | String | 否    | C/D OD:常规时默认:约0.3     |
| os_cd                   | String | 否    | C/D OS:常规时默认:约0.3     |
| od_macular              | String | 否    | 黄斑OD:常规时默认:中心凹反光可见    |
| os_macular              | String | 否    | 黄斑OS:常规时默认:中心凹反光可见    |
| eye_mirror_od_other     | String | 否    | 其它OD                  |
| eye_mirror_os_other     | String | 否    | 其它OS                  |



### 专科检查-眼健康检查保存

```http
[POST]/treat_service/speciality_check/eyehealth
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                     | 类型     | 必填   | 说明                    |
| ----------------------- | ------ | ---- | --------------------- |
| trea_id                 | String | 是    | 就诊ID                  |
| --模板数据(template_data)-- | Object |      |                       |
| 裂隙灯检查                   |        |      |                       |
| od_eyelid               | String | 否    | 眼睑od:常规时默认:无倒睫，眼睑闭合完全 |
| os_eyelid               | String | 否    | 眼睑os:常规时默认:无倒睫，眼睑闭合完全 |
| od_tears                | String | 否    | 泪器od:常规时默认:泪点位正       |
| os_tears                | String | 否    | 泪器os:常规时默认:泪点位正       |
| od_conjunctiva          | String | 否    | 结膜od:常规时默认:无充血、水肿     |
| os_conjunctiva          | String | 否    | 结膜os:常规时默认:无充血、水肿     |
| od_cornea               | String | 否    | 角膜od:常规时默认:透明         |
| os_cornea               | String | 否    | 角膜os:常规时默认:透明         |
| od_chamber              | String | 否    | 前房od:常规时默认:清、深        |
| os_chamber              | String | 否    | 前房os:常规时默认:清、深        |
| od_lris                 | String | 否    | 虹膜od:常规时默认:纹理清        |
| os_lris                 | String | 否    | 虹膜os:常规时默认:纹理清        |
| od_pupil                | String | 否    | 瞳孔od:常规时默认:PERRL      |
| os_pupil                | String | 否    | 瞳孔os:常规时默认:PERRL      |
| od_crystal              | String | 否    | 晶体od:常规时默认:透明         |
| os_crystal              | String | 否    | 晶体os:常规时默认:透明         |
| od_vitreous             | String | 否    | 玻璃体od:常规时默认:无混浊       |
| os_vitreous             | String | 否    | 玻璃体os:常规时默认:无混浊       |
| slit_lamp_od_other      | String | 否    | 其它od                  |
| slit_lamp_os_other      | String | 否    | 其它os                  |
| 眼底镜检查                   |        |      |                       |
| od_disk                 | String | 否    | 视盘OD:常规时默认:色红界清       |
| os_disk                 | String | 否    | 视盘OS:常规时默认:色红界清       |
| od_cd                   | String | 否    | C/D OD:常规时默认:约0.3     |
| os_cd                   | String | 否    | C/D OS:常规时默认:约0.3     |
| od_macular              | String | 否    | 黄斑OD:常规时默认:中心凹反光可见    |
| os_macular              | String | 否    | 黄斑OS:常规时默认:中心凹反光可见    |
| eye_mirror_od_other     | String | 否    | 其它OD                  |
| eye_mirror_os_other     | String | 否    | 其它OS                  |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |




### 专科检查-眼健康裂隙灯检查模板保存

```http
[POST]/emr/template/eyehealth/slitlamp
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                 | 类型      | 必填   | 说明   |
| ------------------- | ------- | ---- | ---- |
| slit_name           | String  | 64   | 是    |
| slit_od_eyelid      | String  |      | 否    |
| slit_os_eyelid      | String  |      | 否    |
| slit_od_tears       | String  |      | 否    |
| slit_os_tears       | String  |      | 否    |
| slit_od_conjunctiva | String  |      | 否    |
| slit_os_conjunctiva | String  |      | 否    |
| slit_od_cornea      | String  |      | 否    |
| slit_os_cornea      | String  |      | 否    |
| slit_od_chamber     | String  |      | 否    |
| slit_os_chamber     | String  |      | 否    |
| slit_od_lris        | String  |      | 否    |
| slit_os_lris        | String  |      | 否    |
| slit_od_pupil       | String  |      | 否    |
| slit_os_pupil       | String  |      | 否    |
| slit_od_crystal     | String  |      | 否    |
| slit_os_crystal     | String  |      | 否    |
| slit_od_vitreous    | String  |      | 否    |
| slit_os_vitreous    | String  |      | 否    |
| slit_od_other       | String  |      | 否    |
| slit_os_other       | String  |      | 否    |
| slit_type           | Integer |      | 是    |
| slit_userid         | Long    |      | 否    |
| slit_depa_id        | Long    |      | 否    |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

### 专科检查-眼健康裂隙灯检查模板修改

```http
[POST]/emr/template/eyehealth/slitlamp/update
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                 | 类型      | 必填   | 说明   |
| ------------------- | ------- | ---- | ---- |
| slit_name           | String  | 64   | 是    |
| slit_od_eyelid      | String  |      | 否    |
| slit_os_eyelid      | String  |      | 否    |
| slit_od_tears       | String  |      | 否    |
| slit_os_tears       | String  |      | 否    |
| slit_od_conjunctiva | String  |      | 否    |
| slit_os_conjunctiva | String  |      | 否    |
| slit_od_cornea      | String  |      | 否    |
| slit_os_cornea      | String  |      | 否    |
| slit_od_chamber     | String  |      | 否    |
| slit_os_chamber     | String  |      | 否    |
| slit_od_lris        | String  |      | 否    |
| slit_os_lris        | String  |      | 否    |
| slit_od_pupil       | String  |      | 否    |
| slit_os_pupil       | String  |      | 否    |
| slit_od_crystal     | String  |      | 否    |
| slit_os_crystal     | String  |      | 否    |
| slit_od_vitreous    | String  |      | 否    |
| slit_os_vitreous    | String  |      | 否    |
| slit_od_other       | String  |      | 否    |
| slit_os_other       | String  |      | 否    |
| slit_type           | Integer |      | 是    |
| slit_userid         | Long    |      | 否    |
| slit_depa_id        | Long    |      | 否    |


### 专科检查-眼健康裂隙灯检查模板获取

```http
[GET]/emr/template/eyehealth/slitlamp
```

#### 修改更新记录

| 对应业务     | 说明   |
| -------- | ---- |
| V1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明      |
| ------- | ---- | ---- | ------- |
| slit_id | Long | 是    | 裂隙灯模板ID |

#### 回复报文参数

| 参数名                 | 类型      | 长度   | 必填   | 说明              |
| ------------------- | ------- | ---- | ---- | --------------- |
| slit_id             | String  |      | 是    | 裂隙灯模板ID         |
| slit_name           | String  | 64   | 是    | 模板名称            |
| slit_od_eyelid      | String  |      | 否    | 眼睑od            |
| slit_os_eyelid      | String  |      | 否    | 眼睑os            |
| slit_od_tears       | String  |      | 否    | 泪器od            |
| slit_os_tears       | String  |      | 否    | 泪器os            |
| slit_od_conjunctiva | String  |      | 否    | 结膜od            |
| slit_os_conjunctiva | String  |      | 否    | 结膜os            |
| slit_od_cornea      | String  |      | 否    | 角膜od            |
| slit_os_cornea      | String  |      | 否    | 角膜os            |
| slit_od_chamber     | String  |      | 否    | 前房od            |
| slit_os_chamber     | String  |      | 否    | 前房os            |
| slit_od_lris        | String  |      | 否    | 虹膜od            |
| slit_os_lris        | String  |      | 否    | 虹膜os            |
| slit_od_pupil       | String  |      | 否    | 瞳孔od            |
| slit_os_pupil       | String  |      | 否    | 瞳孔os            |
| slit_od_crystal     | String  |      | 否    | 晶体od            |
| slit_os_crystal     | String  |      | 否    | 晶体os            |
| slit_od_vitreous    | String  |      | 否    | 玻璃体od           |
| slit_os_vitreous    | String  |      | 否    | 玻璃体os           |
| slit_od_other       | String  |      | 否    | 其它od            |
| slit_os_other       | String  |      | 否    | 其它os            |
| slit_type           | Integer |      | 是    | 所属类型;1:个人;0: 科室 |
| slit_userid         | String  |      | 是    | 用户ID            |
| slit_username       | String  |      | 是    | 用户名称            |
| slit_depa_id        | String  |      | 否    | 科室ID，类型科室时有效    |
| slit_depa_name      | String  |      | 否    | 科室名称，类型科室时有效    |

### 专科检查-眼健康裂隙灯检查模板列表获取

```http
[GET]/emr/template/eyehealth/slitlamp/list
```

#### 修改更新记录

| 对应业务     | 说明   |
| -------- | ---- |
| V1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                           |
| ------------ | ------- | ---- | ---------------------------- |
| slit_name    | Long    | 否    | 裂隙灯模板名称                      |
| slit_type    | Integer | 是    | 所属类型;1:个人;0: 科室              |
| slit_depa_id | String  | 否    | 科室ID，类型科室时有效,默认取header中的科室ID |
| page_size    | Integer | 否    | 每页条数 空表示10条                  |
| page_num     | Integer | 否    | 第几页 空表示第1页                   |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明           |
| --------- | ---------- | ---- | ------------ |
| page_num  | Integer    | 是    | 当前页          |
| page_size | Integer    | 是    | 每页的数量        |
| total     | Integer    | 是    | 总记录数         |
| pages     | Integer    | 是    | 总页数          |
| list      | ObjectList | 否    | 眼健康裂隙灯检查模板列表 |

##### 眼健康裂隙灯检查模板列表

| 参数名            | 类型      | 长度   | 必填   | 说明              |
| -------------- | ------- | ---- | ---- | --------------- |
| slit_id        | String  |      | 是    | 裂隙灯模板ID         |
| slit_name      | String  | 64   | 是    | 模板名称            |
| slit_type      | Integer |      | 是    | 所属类型;1:个人;0: 科室 |
| slit_userid    | String  |      | 是    | 用户ID            |
| slit_username  | String  |      | 否    | 用户名称            |
| slit_depa_id   | String  |      | 否    | 科室ID，类型科室时有效    |
| slit_depa_name | String  |      | 否    | 科室名称，类型科室时有效    |

### 专科检查-眼健康裂隙灯检查模板列表获取

```http
[GET]/emr/template/eyehealth/slitlamps
```

#### 修改更新记录

| 对应业务     | 说明   |
| -------- | ---- |
| V1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明      |
| --------- | ------ | ---- | ------- |
| slit_name | String | 否    | 裂隙灯模板名称 |

#### 回复报文参数objectList

>最多返回前50条数据

| 参数名       | 类型     | 长度   | 必填   | 说明      |
| --------- | ------ | ---- | ---- | ------- |
| slit_id   | String |      | 是    | 裂隙灯模板ID |
| slit_name | String | 64   | 是    | 模板名称    |


### 专科检查-眼健康裂隙灯检查模板删除

```http
[GET]/emr/template/eyehealth/slitlamp/delete
```

#### 修改更新记录

| 对应业务     | 说明   |
| -------- | ---- |
| V1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明      |
| ------- | ---- | ---- | ------- |
| slit_id | Long | 是    | 裂隙灯模板ID |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 专科检查-眼健康眼底镜检查模板保存

```http
[POST]/emr/template/eyehealth/ophthalmoscope
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名             | 类型      | 必填   | 说明   |
| --------------- | ------- | ---- | ---- |
| opht_name       | String  | 64   | 是    |
| opht_od_disk    | String  |      | 否    |
| opht_os_disk    | String  |      | 否    |
| opht_od_cd      | String  |      | 否    |
| opht_os_cd      | String  |      | 否    |
| opht_od_macular | String  |      | 否    |
| opht_os_macular | String  |      | 否    |
| opht_od_other   | String  |      | 否    |
| opht_os_other   | String  |      | 否    |
| opht_type       | Integer |      | 是    |
| opht_userid     | Long    |      | 否    |
| opht_depa_id    | Long    |      | 否    |


#### 回复报文参数

| 参数名     | 类型   | 必填   | 说明      |
| ------- | ---- | ---- | ------- |
| opht_id | Long | 是    | 眼底镜模板ID |

### 专科检查-眼健康眼底镜检查模板修改

```http
[POST]/emr/template/eyehealth/ophthalmoscope/update
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名             | 类型      | 长度   | 必填   | 说明              |
| --------------- | ------- | ---- | ---- | --------------- |
| opht_id         | Long    |      | 是    | 眼底镜模板ID         |
| opht_name       | String  | 64   | 是    | 模板名称            |
| opht_od_disk    | String  |      | 否    | 视盘OD            |
| opht_os_disk    | String  |      | 否    | 视盘OS            |
| opht_od_cd      | String  |      | 否    | C/D OD          |
| opht_os_cd      | String  |      | 否    | C/D OS          |
| opht_od_macular | String  |      | 否    | 黄斑OD            |
| opht_os_macular | String  |      | 否    | 黄斑OS            |
| opht_od_other   | String  |      | 否    | 其它OD            |
| opht_os_other   | String  |      | 否    | 其它OS            |
| opht_type       | Integer |      | 是    | 所属类型;1:个人;0: 科室 |
| opht_userid     | Long    |      | 否    | 用户ID            |
| opht_depa_id    | Long    |      | 否    | 科室ID，类型科室时有效    |


### 专科检查-眼健康眼底镜检查模板获取

```http
[GET]/emr/template/eyehealth/ophthalmoscope
```

#### 修改更新记录

| 对应业务     | 说明   |
| -------- | ---- |
| V1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明      |
| ------- | ---- | ---- | ------- |
| opht_id | Long | 是    | 眼底镜模板ID |

#### 回复报文参数

| 参数名             | 类型      | 长度   | 必填   | 说明              |
| --------------- | ------- | ---- | ---- | --------------- |
| opht_name       | String  | 64   | 是    | 模板名称            |
| opht_od_disk    | String  |      | 否    | 视盘OD            |
| opht_os_disk    | String  |      | 否    | 视盘OS            |
| opht_od_cd      | String  |      | 否    | C/D OD          |
| opht_os_cd      | String  |      | 否    | C/D OS          |
| opht_od_macular | String  |      | 否    | 黄斑OD            |
| opht_os_macular | String  |      | 否    | 黄斑OS            |
| opht_od_other   | String  |      | 否    | 其它OD            |
| opht_os_other   | String  |      | 否    | 其它OS            |
| opht_type       | Integer |      | 是    | 所属类型;1:个人;0: 科室 |
| opht_userid     | Long    |      | 是    | 用户ID            |
| opht_username   | String  |      | 是    | 用户名称            |
| opht_depa_id    | Long    |      | 否    | 科室ID，类型科室时有效    |
| opht_depa_name  | String  |      | 否    | 科室名称，类型科室时有效    |

### 专科检查-眼健康眼底镜检查模板列表获取

```http
[GET]/emr/template/eyehealth/ophthalmoscope/list
```

#### 修改更新记录

| 对应业务     | 说明   |
| -------- | ---- |
| V1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                            |
| ------------ | ------- | ---- | ----------------------------- |
| opht_name    | String  | 否    | 模板名称                          |
| opht_type    | Integer | 是    | 所属类型;1:个人;0: 科室               |
| opht_depa_id | Long    | 否    | 科室ID，类型科室时有效 ,默认取header中的科室ID |
| page_size    | Integer | 否    | 每页条数 空表示10条                   |
| page_num     | Integer | 否    | 第几页 空表示第1页                    |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明           |
| --------- | ---------- | ---- | ------------ |
| page_num  | Integer    | 是    | 当前页          |
| page_size | Integer    | 是    | 每页的数量        |
| total     | Integer    | 是    | 总记录数         |
| pages     | Integer    | 是    | 总页数          |
| list      | ObjectList | 否    | 眼健康眼底镜检查模板列表 |

##### 眼健康眼底镜检查模板列表

| 参数名            | 类型      | 长度   | 必填   | 说明              |
| -------------- | ------- | ---- | ---- | --------------- |
| opht_id        | Long    |      | 是    | 眼底镜模板ID         |
| opht_name      | String  | 64   | 是    | 模板名称            |
| opht_type      | Integer |      | 是    | 所属类型;1:个人;0: 科室 |
| opht_userid    | Long    |      | 是    | 用户ID            |
| opht_username  | String  |      | 是    | 用户名称            |
| opht_depa_id   | Long    |      | 否    | 科室ID，类型科室时有效    |
| opht_depa_name | String  |      | 否    | 科室名称，类型科室时有效    |


### 专科检查-眼健康眼底镜检查模板列表获取

```http
[GET]/emr/template/eyehealth/ophthalmoscopes
```

#### 修改更新记录

| 对应业务     | 说明   |
| -------- | ---- |
| V1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名       | 类型     | 必填   | 说明   |
| --------- | ------ | ---- | ---- |
| opht_name | String | 否    | 模板名称 |

#### 回复报文参数ObjectList

>最多返回前50条数据

| 参数名       | 类型     | 长度   | 必填   | 说明      |
| --------- | ------ | ---- | ---- | ------- |
| opht_id   | Long   |      | 是    | 眼底镜模板ID |
| opht_name | String | 64   | 是    | 模板名称    |

### 专科检查-眼健康眼底镜检查模板删除

```http
[GET]/emr/template/eyehealth/ophthalmoscope/delete
```

#### 修改更新记录

| 对应业务     | 说明   |
| -------- | ---- |
| V1.2.3.1 | 新增   |

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明      |
| ------- | ---- | ---- | ------- |
| opht_id | Long | 是    | 眼底镜模板ID |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


##专科检查-RGP


### 专科检查-RGP初检获取

```http
[GET]/treat_service/speciality_check/rgp/initial
```

#### 修改更新记录

| 对应业务        | 说明                          |
| ----------- | --------------------------- |
| V1.2.3      | 新增                          |
| WEBV1.2.3.2 | 眼压眼轴修改为独立存储,裂隙灯检查下新增一行备注输入框 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数

| 参数名                              | 类型       | 必填     | 说明                                       |
| -------------------------------- | -------- | ------ | ---------------------------------------- |
| trea_id                          | String   | 是      | 就诊ID                                     |
| 主觉验光subjective                   | Object   | 是      | 主觉验光                                     |
| data_od_sphere                   | String   | 否      | 主觉验光OD-球镜                                |
| data_od_cylinder                 | String   | 否      | 主觉验光OD-柱镜                                |
| data_od_axis                     | String   | 否      | 主觉验光OD-轴向                                |
| data_od_prism                    | String   | 否      | 主觉验光OD-棱镜                                |
| data_od_vision                   | String   | 否      | 主觉验光OD-视力                                |
| data_od_memo                     | String   | 否      | 主觉验光OD-备注                                |
| data_os_sphere                   | String   | 否      | 主觉验光OS-球镜                                |
| data_os_cylinder                 | String   | 否      | 主觉验光OS-柱镜                                |
| data_os_axis                     | String   | 否      | 主觉验光OS-轴向                                |
| data_os_prism                    | String   | 否      | 主觉验光OS-棱镜                                |
| data_os_vision                   | String   | 否      | 主觉验光OS-视力                                |
| data_os_memo                     | String   | 否      | 主觉验光OS-备注                                |
| 角膜曲率corneal_curvature            |          |        | 角膜曲率                                     |
| ----------------                 | -------- | ------ | ----------                               |
| corneal_od_cliffy                | String   | 否      | 右眼陡峭                                     |
| corneal_od_flat                  | String   | 否      | 右眼平坦                                     |
| corneal_od_axis                  | String   | 否      | 右眼轴向                                     |
| corneal_os_cliffy                | String   | 否      | 左眼陡峭                                     |
| corneal_os_flat                  | String   | 否      | 左眼平坦                                     |
| corneal_os_axis                  | String   | 否      | 左眼轴向                                     |
| 其它模板数据template_data              |          |        | 其它模板数据                                   |
| glasses_need                     | String   | 否      | 戴镜需求:<br/>1-化妆品;<br/>2-框架眼镜配戴不方便;<br/>3-运动及娱乐;<br/>4-职业;<br/>5-高度屈光不正;<br/>6-度数增加;<br/>7-散光;<br/>8-屈光参差;<br/>9-无晶体眼;<br/>10-圆锥角膜;多选使用逗号分隔。 |
| 病史                               |          |        |                                          |
| medical_history_normal           | Integer  | 否      | 病史无殊:<br/>0-没选中无殊;<br/>1-选中无殊;           |
| medical_history_detail           | String   | 否      | 病史详情:<br/>1-过敏体质;<br/>2-鼻窦炎;<br/>3-枯草热;<br/>4-干涩或干涩综合症;<br/>5-抽搐或癫痫;<br/>6-眩晕;<br/>7-糖尿病;<br/>8-怀孕;<br/>9-甲状腺功能失调;<br/>1-精神治疗史;多选使用逗号分隔。 |
| is_wear                          | String   | 否      | 是否曾配戴过角膜接触镜                              |
| is_glass_type                    | String   | 否      | 配戴过的角膜接触镜:<br/>1-OK镜;<br/>2-RGP;<br/>3-软镜;多选使用逗号分隔。 |
| detial_history                   | String   | 否      | 配镜详细病史                                   |
| 戴镜前眼部检查                          |          |        |                                          |
| bare_vision_od                   | String   | 否      | 裸眼视力OD                                   |
| bare_vision_os                   | String   | 否      | 裸眼视力OS                                   |
| con_pres_od_ball                 | String   | 否      | 惯用处方OD球镜                                 |
| con_pres_od_column               | String   | 否      | 惯用处方OD柱镜                                 |
| con_pres_od_axis                 | String   | 否      | 惯用处方OD轴向                                 |
| con_pres_os_ball                 | String   | 否      | 惯用处方OS球镜                                 |
| con_pres_os_column               | String   | 否      | 惯用处方OS柱镜                                 |
| con_pres_os_axis                 | String   | 否      | 惯用处方OS轴向                                 |
| srmer_od                         | String   | 否      | Schirmer试验OD                             |
| schirmer_os                      | String   | 否      | Schirmer试验OS                             |
| intraocular_pressure_od          | String   | 否      | 眼压OD                                     |
| intraocular_pressure_os          | String   | 否      | 眼压OS                                     |
| eyelid_tension                   | Integer  | 否      | 眼睑张力:<br>1-强;<br/>2-中等;<br/>3-弱;         |
| ct_od                            | String   | 否      | 角膜厚度OD                                   |
| ct_os                            | String   | 否      | 角膜厚度OS                                   |
| corneal_sensitivity_od           | String   | 否      | 角膜敏感度OD                                  |
| corneal_sensitivity_os           | String   | 否      | 角膜敏感度OS                                  |
| break_up_time_od                 | String   | 否      | 泪膜破裂时间OD                                 |
| break_up_time_os                 | String   | 否      | 泪膜破裂时间OS                                 |
| pupil_od                         | String   | 否      | 瞳孔OD                                     |
| pupil_os                         | String   | 否      | 瞳孔OS                                     |
| eye_axis_od                      | String   | 否      | 眼轴OD                                     |
| eye_axis_os                      | String   | 否      | 眼轴OS                                     |
| iris_diameter_od                 | String   | 否      | 水平可见虹膜直径OD                               |
| iris_diameter_os                 | String   | 否      | 水平可见虹膜直径OS                               |
| mirror_drive                     | Integer  | 否      | 戴镜动机:<br>1-强;<br/>2-中等;<br/>3-弱;         |
| 眼部裂隙灯检查                          |          |        |                                          |
| epithelial_edema_od              | Integer  | 否      | 眼部裂隙灯检查-上皮水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_od                 | Integer  | 否      | 眼部裂隙灯检查-微囊od;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_od                   | Integer  | 否      | 眼部裂隙灯检查-角膜点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_od             | Integer  | 否      | 眼部裂隙灯检查-3、9点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_od                | Integer  | 否      | 眼部裂隙灯检查-角膜基质od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_od    | Integer  | 否      | 眼部裂隙灯检查-角膜新生血管od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_od             | Integer  | 否      | 眼部裂隙灯检查-角膜缘充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_od | Integer  | 否      | 眼部裂隙灯检查-球结膜充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_od     | Integer  | 否      | 眼部裂隙灯检查-球结膜水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_od          | Integer  | 否      | 眼部裂隙灯检查-脸板结膜异常od;<br/>0;<br/>1;<br/>2;<br/>3; |
| epithelial_edema_os              | Integer  | 否      | 眼部裂隙灯检查-上皮水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_os                 | Integer  | 否      | 眼部裂隙灯检查-微囊os;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_os                   | Integer  | 否      | 眼部裂隙灯检查-角膜点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_os             | Integer  | 否      | 眼部裂隙灯检查-3、9点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_os                | Integer  | 否      | 眼部裂隙灯检查-角膜基质os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_os    | Integer  | 否      | 眼部裂隙灯检查-角膜新生血管os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_os             | Integer  | 否      | 眼部裂隙灯检查-角膜缘充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_os | Integer  | 否      | 眼部裂隙灯检查-球结膜充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_os     | Integer  | 否      | 眼部裂隙灯检查-球结膜水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_os          | Integer  | 否      | 眼部裂隙灯检查-脸板结膜异常os;<br/>0;<br/>1;<br/>2;<br/>3; |
| slit_lamp_rem                    | string   | 否      | 眼部裂隙灯检查-备注                               |
| 眼底检查                             |          |        |                                          |
| disk_od                          | String   | 否      | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_od                            | String   | 否      | 眼底检查-C/D od;常规时默认为：0.3                   |
| rim_od                           | String   | 否      | 眼底检查-盘沿od;常规时默认为：粉红色、清                   |
| peripheral_od                    | String   | 否      | 眼底检查-外周od;常规时默认为：清晰                      |
| av_od                            | String   | 否      | 眼底检查-A/V od;常规时默认为：2:3                   |
| macular_od                       | String   | 否      | 眼底检查-黄斑od;常规时默认为：中心凹反光可见                 |
| disk_os                          | String   | 否      | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_os                            | String   | 否      | 眼底检查-C/D os;常规时默认为：0.3                   |
| rim_os                           | String   | 否      | 眼底检查-盘沿os;常规时默认为：粉红色、清                   |
| peripheral_os                    | String   | 否      | 眼底检查-外周os;常规时默认为：清晰                      |
| av_os                            | String   | 否      | 眼底检查-A/V os;常规时默认为：2:3                   |
| macular_os                       | String   | 否      | 眼底检查-黄斑os;常规时默认为：中心凹反光可见                 |
| 眼压眼轴数据                           |          |        |                                          |
| data_od_iop                      | String   | 12     | 否                                        |
| data_os_iop                      | String   | 12     | 否                                        |
| data_od_iop_axis                 | String   | 12     | 否                                        |
| data_os_iop_axis                 | String   | 12     | 否                                        |



### 专科检查-RGP初检保存

```http
[POST]/treat_service/speciality_check/rgp/initial
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                              | 类型       | 必填     | 说明                                       |
| -------------------------------- | -------- | ------ | ---------------------------------------- |
| trea_id                          | String   | 是      | 就诊ID                                     |
| 主觉验光subjective                   | Object   | 是      | 主觉验光                                     |
| data_od_sphere                   | String   | 否      | 主觉验光OD-球镜                                |
| data_od_cylinder                 | String   | 否      | 主觉验光OD-柱镜                                |
| data_od_axis                     | String   | 否      | 主觉验光OD-轴向                                |
| data_od_prism                    | String   | 否      | 主觉验光OD-棱镜                                |
| data_od_vision                   | String   | 否      | 主觉验光OD-视力                                |
| data_od_memo                     | String   | 否      | 主觉验光OD-备注                                |
| data_os_sphere                   | String   | 否      | 主觉验光OS-球镜                                |
| data_os_cylinder                 | String   | 否      | 主觉验光OS-柱镜                                |
| data_os_axis                     | String   | 否      | 主觉验光OS-轴向                                |
| data_os_prism                    | String   | 否      | 主觉验光OS-棱镜                                |
| data_os_vision                   | String   | 否      | 主觉验光OS-视力                                |
| data_os_memo                     | String   | 否      | 主觉验光OS-备注                                |
| 角膜曲率corneal_curvature            | Object   | 否      | 角膜曲率                                     |
| ----------------                 | -------- | ------ | ----------                               |
| corneal_od_cliffy                | String   | 否      | 右眼陡峭                                     |
| corneal_od_flat                  | String   | 否      | 右眼平坦                                     |
| corneal_od_axis                  | String   | 否      | 右眼轴向                                     |
| corneal_os_cliffy                | String   | 否      | 左眼陡峭                                     |
| corneal_os_flat                  | String   | 否      | 左眼平坦                                     |
| corneal_os_axis                  | String   | 否      | 左眼轴向                                     |
| 其它模板数据template_data              | Object   | 是      | 其它模板数据                                   |
| glasses_need                     | String   | 否      | 戴镜需求:<br/>1-化妆品;<br/>2-框架眼镜配戴不方便;<br/>3-运动及娱乐;<br/>4-职业;<br/>5-高度屈光不正;<br/>6-度数增加;<br/>7-散光;<br/>8-屈光参差;<br/>9-无晶体眼;<br/>10-圆锥角膜;多选使用逗号分隔。 |
| 病史                               |          |        |                                          |
| medical_history_normal           | Integer  | 否      | 病史无殊:<br/>0-没选中无殊;<br/>1-选中无殊;           |
| medical_history_detail           | String   | 否      | 病史详情:<br/>1-过敏体质;<br/>2-鼻窦炎;<br/>3-枯草热;<br/>4-干涩或干涩综合症;<br/>5-抽搐或癫痫;<br/>6-眩晕;<br/>7-糖尿病;<br/>8-怀孕;<br/>9-甲状腺功能失调;<br/>1-精神治疗史;多选使用逗号分隔。 |
| is_wear                          | String   | 否      | 是否曾配戴过角膜接触镜                              |
| is_glass_type                    | String   | 否      | 配戴过的角膜接触镜:<br/>1-OK镜;<br/>2-RGP;<br/>3-软镜;多选使用逗号分隔。 |
| detial_history                   | String   | 否      | 配镜详细病史                                   |
| 戴镜前眼部检查                          |          |        |                                          |
| bare_vision_od                   | String   | 否      | 裸眼视力OD                                   |
| bare_vision_os                   | String   | 否      | 裸眼视力OS                                   |
| con_pres_od_ball                 | String   | 否      | 惯用处方OD球镜                                 |
| con_pres_od_column               | String   | 否      | 惯用处方OD柱镜                                 |
| con_pres_od_axis                 | String   | 否      | 惯用处方OD轴向                                 |
| con_pres_os_ball                 | String   | 否      | 惯用处方OS球镜                                 |
| con_pres_os_column               | String   | 否      | 惯用处方OS柱镜                                 |
| con_pres_os_axis                 | String   | 否      | 惯用处方OS轴向                                 |
| schirmer_od                      | String   | 否      | Schirmer试验OD                             |
| schirmer_os                      | String   | 否      | Schirmer试验OS                             |
| intraocular_pressure_od          | String   | 否      | 眼压OD                                     |
| intraocular_pressure_os          | String   | 否      | 眼压OS                                     |
| eyelid_tension                   | Integer  | 否      | 眼睑张力:<br>1-强;<br/>2-中等;<br/>3-弱;         |
| ct_od                            | String   | 否      | 角膜厚度OD                                   |
| ct_os                            | String   | 否      | 角膜厚度OS                                   |
| corneal_sensitivity_od           | String   | 否      | 角膜敏感度OD                                  |
| corneal_sensitivity_os           | String   | 否      | 角膜敏感度OS                                  |
| break_up_time_od                 | String   | 否      | 泪膜破裂时间OD                                 |
| break_up_time_os                 | String   | 否      | 泪膜破裂时间OS                                 |
| pupil_od                         | String   | 否      | 瞳孔OD                                     |
| pupil_os                         | String   | 否      | 瞳孔OS                                     |
| eye_axis_od                      | String   | 否      | 眼轴OD                                     |
| eye_axis_os                      | String   | 否      | 眼轴OS                                     |
| iris_diameter_od                 | String   | 否      | 水平可见虹膜直径OD                               |
| iris_diameter_os                 | String   | 否      | 水平可见虹膜直径OS                               |
| mirror_drive                     | Integer  | 否      | 戴镜动机:<br>1-强;<br/>2-中等;<br/>3-弱;         |
| 眼部裂隙灯检查                          |          |        |                                          |
| epithelial_edema_od              | Integer  | 否      | 眼部裂隙灯检查-上皮水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_od                 | Integer  | 否      | 眼部裂隙灯检查-微囊od;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_od                   | Integer  | 否      | 眼部裂隙灯检查-角膜点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_od             | Integer  | 否      | 眼部裂隙灯检查-3、9点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_od                | Integer  | 否      | 眼部裂隙灯检查-角膜基质od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_od    | Integer  | 否      | 眼部裂隙灯检查-角膜新生血管od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_od             | Integer  | 否      | 眼部裂隙灯检查-角膜缘充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_od | Integer  | 否      | 眼部裂隙灯检查-球结膜充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_od     | Integer  | 否      | 眼部裂隙灯检查-球结膜水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_od          | Integer  | 否      | 眼部裂隙灯检查-脸板结膜异常od;<br/>0;<br/>1;<br/>2;<br/>3; |
| epithelial_edema_os              | Integer  | 否      | 眼部裂隙灯检查-上皮水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_os                 | Integer  | 否      | 眼部裂隙灯检查-微囊os;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_os                   | Integer  | 否      | 眼部裂隙灯检查-角膜点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_os             | Integer  | 否      | 眼部裂隙灯检查-3、9点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_os                | Integer  | 否      | 眼部裂隙灯检查-角膜基质os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_os    | Integer  | 否      | 眼部裂隙灯检查-角膜新生血管os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_os             | Integer  | 否      | 眼部裂隙灯检查-角膜缘充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_os | Integer  | 否      | 眼部裂隙灯检查-球结膜充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_os     | Integer  | 否      | 眼部裂隙灯检查-球结膜水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_os          | Integer  | 否      | 眼部裂隙灯检查-脸板结膜异常os;<br/>0;<br/>1;<br/>2;<br/>3; |
| slit_lamp_rem                    | string   | 否      | 眼部裂隙灯检查-备注                               |
| 眼底检查                             |          |        |                                          |
| disk_od                          | String   | 否      | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_od                            | String   | 否      | 眼底检查-C/D od;常规时默认为：0.3                   |
| rim_od                           | String   | 否      | 眼底检查-盘沿od;常规时默认为：粉红色、清                   |
| peripheral_od                    | String   | 否      | 眼底检查-外周od;常规时默认为：清晰                      |
| av_od                            | String   | 否      | 眼底检查-A/V od;常规时默认为：2:3                   |
| macular_od                       | String   | 否      | 眼底检查-黄斑od;常规时默认为：中心凹反光可见                 |
| disk_os                          | String   | 否      | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_os                            | String   | 否      | 眼底检查-C/D os;常规时默认为：0.3                   |
| rim_os                           | String   | 否      | 眼底检查-盘沿os;常规时默认为：粉红色、清                   |
| peripheral_os                    | String   | 否      | 眼底检查-外周os;常规时默认为：清晰                      |
| av_os                            | String   | 否      | 眼底检查-A/V os;常规时默认为：2:3                   |
| macular_os                       | String   | 否      | 眼底检查-黄斑os;常规时默认为：中心凹反光可见                 |
| 眼压眼轴数据                           |          |        |                                          |
| data_od_iop                      | String   | 否      | OD-眼压,mmgh                               |
| data_os_iop                      | String   | 否      | OS-眼压,mmgh                               |
| data_od_iop_axis                 | String   | 否      | OD-眼轴,mm                                 |
| data_os_iop_axis                 | String   | 否      | OD-眼轴,mm                                 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 专科检查-RGP试戴获取

```http
[GET]/treat_service/speciality_check/rgp/try
```

#### 修改更新记录

| 对应业务        | 说明        |
| ----------- | --------- |
| V1.2.3      | 新增        |
| WEBV1.2.3.3 | 基弧、度数拆为二个 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数

| 参数名                     | 类型         | 必填   | 说明            |
| ----------------------- | ---------- | ---- | ------------- |
| trea_id                 | String     | 是    | 就诊ID          |
| rgp_trys                | ObjectList | 是    | 试戴片列表         |
| 其他模板数据template_data     |            |      |               |
| 最终镜片                    |            |      |               |
| glass_times             | Integer    | 否    | 次数-从第1开始记     |
| glass_times_os          | Integer    | 否    | OS次数-从第1开始记   |
| glass_brand_od          | Long       | 否    | od品牌ID        |
| glass_material_od       | Long       | 否    | od材质ID        |
| glass_base_curve_od     | String     | 否    | od基弧1         |
| glass_base_curve_od2    | String     | 否    | od基弧2         |
| glass_diameter_od       | String     | 否    | od直径          |
| glass_degree_od         | String     | 否    | od度数1         |
| glass_degree_od2        | String     | 否    | od度数2         |
| glass_memo_od           | String     | 否    | 最终镜片-OD备注     |
| glass_brand_os          | Long       | 否    | os品牌ID        |
| glass_material_os       | Long       | 否    | os材质ID        |
| glass_base_curve_os     | String     | 否    | os基弧1         |
| glass_base_curve_os2    | String     | 否    | os基弧2         |
| glass_diameter_os       | String     | 否    | os直径          |
| glass_degree_os         | String     | 否    | os度数1         |
| glass_degree_os2        | String     | 否    | os度数2         |
| glass_memo_os           | String     | 否    | 最终镜片-OS备注     |
| 试戴验光                    |            |      |               |
| try_optometry_ball_od   | String     | 否    | od球镜          |
| try_optometry_column_od | String     | 否    | od柱镜          |
| try_optometry_axis_od   | String     | 否    | od轴向          |
| try_optometry_vision_od | String     | 否    | od视力          |
| try_optometry_ball_os   | String     | 否    | os球镜          |
| try_optometry_column_os | String     | 否    | os柱镜          |
| try_optometry_axis_os   | String     | 否    | os轴向          |
| try_optometry_vision_os | String     | 否    | os视力          |
| RGP处方rgp_prescription   |            |      |               |
| rgp_times               | Integer    | 否    | 哪次试戴,从1记      |
| rgp_times_os            | Integer    | 否    | OS试戴次数-从第1开始记 |
| rgp_od_brand_id         | Long       | 否    | OD-品牌id       |
| rgp_od_brand            | String     | 否    | OD-品牌         |
| rgp_od_material_id      | Long       | 否    | OD-材质id       |
| rgp_od_material         | String     | 否    | OD-材质         |
| rgp_od_curve            | String     | 否    | OD-基弧1        |
| rgp_od_curve2           | String     | 否    | OD-基弧2        |
| rgp_od_diameter         | String     | 否    | OD-直径         |
| rgp_od_degree           | String     | 否    | OD-度数1        |
| rgp_od_degree2          | String     | 否    | OD-度数2        |
| rgp_od_rem              | String     | 否    | OD-备注         |
| rgp_os_brand_id         | Long       | 否    | OS-品牌id       |
| rgp_os_brand            | String     | 否    | OS-品牌         |
| rgp_os_material_id      | Long       | 否    | OS-材质id       |
| rgp_os_material         | String     | 否    | OS-材质         |
| rgp_os_curve            | String     | 否    | OS-基弧1        |
| rgp_os_curve2           | String     | 否    | OS-基弧2        |
| rgp_os_diameter         | String     | 否    | OS-直径         |
| rgp_os_degree           | String     | 否    | OS-度数1        |
| rgp_os_degree2          | String     | 否    | OS-度数2        |
| rgp_os_rem              | String     | 否    | OD-备注         |

##### 试戴片列表

说明
1. 数据为ObjectList结构
2. 其它模板本来的参数KEY生成规则为${原KEY}_${一位的试戴片顺序(从1开始)};ID生成规则为:5${二位的试戴片顺序(从1开始)}${原定义的二位数}

| 参数名                             | 类型      | 必填   | 说明                                       |
| ------------------------------- | ------- | ---- | ---------------------------------------- |
| index                           | Integer | 是    | 第几次试戴，从0开始计                              |
| base_curve_od                   | String  | 否    | OD-基弧1                                   |
| base_curve_od2                  | String  | 否    | OD-基弧2                                   |
| diameter_od                     | String  | 否    | 直径                                       |
| degree_od                       | String  | 否    | 度数1                                      |
| degree_od2                      | String  | 否    | 度数2                                      |
| level_central_od                | Integer | 否    | 中心定位:<br/>1-中心;<br/>2-颞侧;<br/>3-鼻侧;<br/>4-上方;<br/>5-下方; |
| central_value_od                | String  | 否    | 中心定位值:<br/>↑<br/>↓                       |
| activity_od                     | Integer | 否    | 活动类型:<br/>1-平滑;<br/>2-快速下滑;<br/>3-顶端旋转;  |
| activity_type_od                | String  | 否    | 活动类型值:<br/>↑<br/>↓                       |
| move_degree_od                  | Integer | 否    | 移动度:<br/>1-快;<br/>2-适中;<br/>3-慢;         |
| move_od                         | String  | 否    | 移动度值:<br/>↑<br/>↓                        |
| stable_degree_od                | Integer | 否    | 稳定度:<br/>1-是;<br/>2-否;                   |
| stability_od                    | String  | 否    | 稳定度值:<br/>↑<br/>↓                        |
| fulores_imaging_od              | Integer | 否    | 中央荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| central_fluorescence_imaging_od | String  | 否    | 中央荧光显像值:<br/>↑<br/>↓                     |
| discri_imaging_od               | Integer | 否    | 中周荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| discri_imaging_value_od         | String  | 否    | 中周荧光显像值:<br/>↑<br/>↓                     |
| side_arc_width_od               | Integer | 否    | 边弧宽度:<br/>1-宽;<br/>2-适中;<br/>3-窄;        |
| curve_with_od                   | String  | 否    | 边弧宽度值:<br/>↑<br/>↓                       |
| side_arc_tilted_od              | Integer | 否    | 边弧翘起:<br/>1-低;<br/>2-中;<br/>3-高;         |
| curve_raise_od                  | String  | 否    | 边弧翘起值:<br/>↑<br/>↓                       |
| coverage_degree_od              | Integer | 否    | 覆盖度:<br/>1-好;<br/>2-差;                   |
| coverage_od                     | String  | 否    | 覆盖度值:<br/>↑<br/>↓                        |
| base_curve_os                   | String  | 否    | OS-基弧1                                   |
| base_curve_os2                  | String  | 否    | OS-基弧2                                   |
| diameter_os                     | String  | 否    | 直径                                       |
| degree_os                       | String  | 否    | 度数1                                      |
| degree_os2                      | String  | 否    | 度数2                                      |
| level_central_os                | Integer | 否    | 中心定位:<br/>1-中心;<br/>2-颞侧;<br/>3-鼻侧;<br/>4-上方;<br/>5-下方; |
| central_value_os                | String  | 否    | 中心定位值:<br/>↑<br/>↓                       |
| activity_os                     | Integer | 否    | 活动类型:<br/>1-平滑;<br/>2-快速下滑;<br/>3-顶端旋转;  |
| activity_type_os                | String  | 否    | 活动类型值:<br/>↑<br/>↓                       |
| move_degree_os                  | Integer | 否    | 移动度:<br/>1-快;<br/>2-适中;<br/>3-慢;         |
| move_os                         | String  | 否    | 移动度值:<br/>↑<br/>↓                        |
| stable_degree_os                | Integer | 否    | 稳定度:<br/>1-是;<br/>2-否;                   |
| stability_os                    | String  | 否    | 稳定度值:<br/>↑<br/>↓                        |
| fulores_imaging_os              | Integer | 否    | 中央荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| central_fluorescence_imaging_os | String  | 否    | 中央荧光显像值:<br/>↑<br/>↓                     |
| discri_imaging_os               | Integer | 否    | 中周荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| discri_imaging_value_os         | String  | 否    | 中周荧光显像值:<br/>↑<br/>↓                     |
| side_arc_width_os               | Integer | 否    | 边弧宽度:<br/>1-宽;<br/>2-适中;<br/>3-窄;        |
| curve_with_os                   | String  | 否    | 边弧宽度值:<br/>↑<br/>↓                       |
| side_arc_tilted_os              | Integer | 否    | 边弧翘起:<br/>1-低;<br/>2-中;<br/>3-高;         |
| curve_raise_os                  | String  | 否    | 边弧翘起值:<br/>↑<br/>↓                       |
| coverage_degree_os              | Integer | 否    | 覆盖度:<br/>1-好;<br/>2-差;                   |
| coverage_os                     | String  | 否    | 覆盖度值:<br/>↑<br/>↓                        |

RGP处方说明：
1. 处方来源设置为：2-试戴
2. 哪次试戴状态设置为:null






### 专科检查-RGP试戴保存

```http
[POST]/treat_service/speciality_check/rgp/try
```

#### 修改更新记录

| 对应业务        | 说明        |
| ----------- | --------- |
| V1.2.3      | 新增        |
| WEBV1.2.3.3 | 基弧、度数拆为二个 |

#### 请求报文参数

| 参数名                     | 类型         | 必填   | 说明          |
| ----------------------- | ---------- | ---- | ----------- |
| trea_id                 | String     | 是    | 就诊ID        |
| rgp_trys                | ObjectList | 是    | 试戴片列表       |
| 其他模板数据template_data     |            |      |             |
| 最终镜片                    |            |      |             |
| glass_times             | Integer    | 否    | 次数-从第1开始记   |
| glass_times_os          | Integer    | 否    | OS次数-从第1开始记 |
| glass_brand_od          | Long       | 否    | od品牌ID      |
| glass_material_od       | Long       | 否    | od材质ID      |
| glass_base_curve_od     | String     | 否    | od基弧1       |
| glass_base_curve_od2    | String     | 否    | od基弧2       |
| glass_diameter_od       | String     | 否    | od直径        |
| glass_degree_od         | String     | 否    | od度数1       |
| glass_degree_od2        | String     | 否    | od度数2       |
| glass_memo_od           | String     | 否    | 最终镜片-OD备注   |
| glass_brand_os          | Long       | 否    | os品牌ID      |
| glass_material_os       | Long       | 否    | os材质ID      |
| glass_base_curve_os     | String     | 否    | os基弧1       |
| glass_base_curve_os2    | String     | 否    | os基弧2       |
| glass_diameter_os       | String     | 否    | os直径        |
| glass_degrees_os        | String     | 否    | os度数1       |
| glass_degree_os2        | String     | 否    | os度数2       |
| glass_memo_os           | String     | 否    | 最终镜片-OS备注   |
| 试戴验光                    |            |      |             |
| try_optometry_ball_od   | String     | 否    | od球镜        |
| try_optometry_column_od | String     | 否    | od柱镜        |
| try_optometry_axis_od   | String     | 否    | od轴向        |
| try_optometry_vision_od | String     | 否    | od视力        |
| try_optometry_ball_os   | String     | 否    | os球镜        |
| try_optometry_column_os | String     | 否    | os柱镜        |
| try_optometry_axis_os   | String     | 否    | os轴向        |
| try_optometry_vision_os | String     | 否    | os视力        |
| RGP处方rgp_prescription   |            |      |             |
| rgp_times               | Integer    | 否    | 哪次试戴,从1记    |
| rgp_times_os            | Integer    | 否    | OS哪次试戴,从1记  |
| rgp_od_brand_id         | Long       | 否    | OD-品牌id     |
| rgp_od_brand            | String     | 否    | OD-品牌       |
| rgp_od_material_id      | Long       | 否    | OD-材质id     |
| rgp_od_material         | String     | 否    | OD-材质       |
| rgp_od_curve            | String     | 否    | OD-基弧1      |
| rgp_od_curve2           | String     | 否    | OD-基弧2      |
| rgp_od_diameter         | String     | 否    | OD-直径       |
| rgp_od_degree           | String     | 否    | OD-度数1      |
| rgp_od_degree2          | String     | 否    | OD-度数2      |
| rgp_od_rem              | String     | 否    | OD-备注       |
| rgp_os_brand_id         | Long       | 否    | OS-品牌id     |
| rgp_os_brand            | String     | 否    | OS-品牌       |
| rgp_os_material_id      | Long       | 否    | OS-材质id     |
| rgp_os_material         | String     | 否    | OS-材质       |
| rgp_os_curve            | String     | 否    | OS-基弧1      |
| rgp_os_curve2           | String     | 否    | OS-基弧2      |
| rgp_os_diameter         | String     | 否    | OS-直径       |
| rgp_os_degree           | String     | 否    | OS-度数1      |
| rgp_os_degree2          | String     | 否    | OS-度数2      |
| rgp_os_rem              | String     | 否    | OD-备注       |

##### 试戴片列表

说明
1. 数据为ObjectList结构
2. 其它模板本来的参数KEY生成规则为${原KEY}_${一位的试戴片顺序(从1开始)};ID生成规则为:5${二位的试戴片顺序(从1开始)}${原定义的二位数}

| 参数名                             | 类型      | 必填   | 说明                                       |
| ------------------------------- | ------- | ---- | ---------------------------------------- |
| index                           | Integer | 是    | 第几次试戴，从0开始计                              |
| diameter_od                     | String  | 否    | 直径                                       |
| base_curve_od                   | String  | 否    | OD-基弧1                                   |
| base_curve_od2                  | String  | 否    | OD-基弧2                                   |
| degree_od                       | String  | 否    | 度数1                                      |
| degree_od2                      | String  | 否    | 度数2                                      |
| level_central_od                | Integer | 否    | 中心定位:<br/>1-中心;<br/>2-颞侧;<br/>3-鼻侧;<br/>4-上方;<br/>5-下方; |
| central_value_od                | String  | 否    | 中心定位值:<br/>↑<br/>↓                       |
| activity_od                     | Integer | 否    | 活动类型:<br/>1-平滑;<br/>2-快速下滑;<br/>3-顶端旋转;  |
| activity_type_od                | String  | 否    | 活动类型值:<br/>↑<br/>↓                       |
| move_degree_od                  | Integer | 否    | 移动度:<br/>1-快;<br/>2-适中;<br/>3-慢;         |
| move_od                         | String  | 否    | 移动度值:<br/>↑<br/>↓                        |
| stable_degree_od                | Integer | 否    | 稳定度:<br/>1-是;<br/>2-否;                   |
| stability_od                    | String  | 否    | 稳定度值:<br/>↑<br/>↓                        |
| fulores_imaging_od              | Integer | 否    | 中央荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| central_fluorescence_imaging_od | String  | 否    | 中央荧光显像值:<br/>↑<br/>↓                     |
| discri_imaging_od               | Integer | 否    | 中周荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| discri_imaging_value_od         | String  | 否    | 中周荧光显像值:<br/>↑<br/>↓                     |
| side_arc_width_od               | Integer | 否    | 边弧宽度:<br/>1-宽;<br/>2-适中;<br/>3-窄;        |
| curve_with_od                   | String  | 否    | 边弧宽度值:<br/>↑<br/>↓                       |
| side_arc_tilted_od              | Integer | 否    | 边弧翘起:<br/>1-低;<br/>2-中;<br/>3-高;         |
| curve_raise_od                  | String  | 否    | 边弧翘起值:<br/>↑<br/>↓                       |
| coverage_degree_od              | Integer | 否    | 覆盖度:<br/>1-好;<br/>2-差;                   |
| coverage_od                     | String  | 否    | 覆盖度值:<br/>↑<br/>↓                        |
| base_curve_os                   | String  | 否    | OS-基弧1                                   |
| base_curve_os2                  | String  | 否    | OS-基弧2                                   |
| diameter_os                     | String  | 否    | 直径                                       |
| degree_os                       | String  | 否    | 度数1                                      |
| degree_os2                      | String  | 否    | 度数2                                      |
| level_central_os                | Integer | 否    | 中心定位:<br/>1-中心;<br/>2-颞侧;<br/>3-鼻侧;<br/>4-上方;<br/>5-下方; |
| central_value_os                | String  | 否    | 中心定位值:<br/>↑<br/>↓                       |
| activity_os                     | Integer | 否    | 活动类型:<br/>1-平滑;<br/>2-快速下滑;<br/>3-顶端旋转;  |
| activity_type_os                | String  | 否    | 活动类型值:<br/>↑<br/>↓                       |
| move_degree_os                  | Integer | 否    | 移动度:<br/>1-快;<br/>2-适中;<br/>3-慢;         |
| move_os                         | String  | 否    | 移动度值:<br/>↑<br/>↓                        |
| stable_degree_os                | Integer | 否    | 稳定度:<br/>1-是;<br/>2-否;                   |
| stability_os                    | String  | 否    | 稳定度值:<br/>↑<br/>↓                        |
| fulores_imaging_os              | Integer | 否    | 中央荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| central_fluorescence_imaging_os | String  | 否    | 中央荧光显像值:<br/>↑<br/>↓                     |
| discri_imaging_os               | Integer | 否    | 中周荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| discri_imaging_value_os         | String  | 否    | 中周荧光显像值:<br/>↑<br/>↓                     |
| side_arc_width_os               | Integer | 否    | 边弧宽度:<br/>1-宽;<br/>2-适中;<br/>3-窄;        |
| curve_with_os                   | String  | 否    | 边弧宽度值:<br/>↑<br/>↓                       |
| side_arc_tilted_os              | Integer | 否    | 边弧翘起:<br/>1-低;<br/>2-中;<br/>3-高;         |
| curve_raise_os                  | String  | 否    | 边弧翘起值:<br/>↑<br/>↓                       |
| coverage_degree_os              | Integer | 否    | 覆盖度:<br/>1-好;<br/>2-差;                   |
| coverage_os                     | String  | 否    | 覆盖度值:<br/>↑<br/>↓                        |

RGP处方说明：
1. 处方来源设置为：2-试戴
2. 哪次试戴状态设置为:null



#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 专科检查-RGP分发获取

```http
[GET]/treat_service/speciality_check/rgp/distribute
```

#### 修改更新记录

|  对应业务 	| 说明 					|
|-----------|---------------------	|
| V1.2.3 	| 新增 			|
| V1.2.3.2 	| 新增不定期随访时间,中心定位支持多选；覆盖度增加“可接受”选项 	|

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数

| 参数名                             | 类型      | 必填   | 说明                                       | 变更          |
| ------------------------------- | ------- | ---- | ---------------------------------------- | ----------- |
| trea_id                         | String  | 是    | 就诊ID                                     |             |
| 下次随访时间next_follow_up_time       |         |      |                                          |             |
| next_follow_up_time             | Integer | 是    | 下次随访时间                                   |             |
| next_follow_up_time_unit        | Integer | 是    | 下次随访时间单位<br/>1-天;<br/>2-周;<br/>3-月;<br/>4-年 |             |
| emr_followup_type               | Integer | 是    | 随访时间类型；0:定期;1:不定期                        | WEBV1.2.3.2 |
| emr_followup_notfixed           | String  | 否    | 不定期随访时间                                  | WEBV1.2.3.2 |
| RGP处方rgp_prescription           |         |      |                                          |             |
| rgp_od_brand_id                 | Long    | 否    | OD-品牌id                                  |             |
| rgp_od_brand                    | String  | 否    | OD-品牌                                    |             |
| rgp_od_material_id              | Long    | 否    | OD-材质id                                  |             |
| rgp_od_material                 | String  | 否    | OD-材质                                    |             |
| rgp_od_curve                    | String  | 否    | OD-基弧                                    |             |
| rgp_od_diameter                 | String  | 否    | OD-直径                                    |             |
| rgp_od_degree                   | String  | 否    | OD-度数                                    |             |
| rgp_od_rem                      | String  | 否    | OD-备注                                    |             |
| rgp_os_brand_id                 | Long    | 否    | OS-品牌id                                  |             |
| rgp_os_brand                    | String  | 否    | OS-品牌                                    |             |
| rgp_os_material_id              | Long    | 否    | OS-材质id                                  |             |
| rgp_os_material                 | String  | 否    | OS-材质                                    |             |
| rgp_os_curve                    | String  | 否    | OS-基弧                                    |             |
| rgp_os_diameter                 | String  | 否    | OS-直径                                    |             |
| rgp_os_degree                   | String  | 否    | OS-度数                                    |             |
| rgp_os_rem                      | String  | 否    | OD-备注                                    |             |
| 模板数据template_data               |         |      |                                          |             |
| 矫正视力                            |         |      |                                          |             |
| corrected_vision_od_vision      | 70501   | 是    | od视力                                     |             |
| corrected_vision_os_vision      | 70502   | 是    | os视力                                     |             |
| 戴镜验光                            |         |      |                                          |             |
| optometry_od_ball               | String  | 否    | od球镜                                     |             |
| optometry_od_column             | String  | 否    | od柱镜                                     |             |
| optometry_od_axis               | String  | 否    | od轴向                                     |             |
| optometry_od_vision             | String  | 否    | od视力                                     |             |
| optometry_os_ball               | String  | 否    | os球镜                                     |             |
| optometry_os_column             | String  | 否    | os柱镜                                     |             |
| optometry_os_axis               | String  | 否    | os轴向                                     |             |
| optometry_os_vision             | String  | 否    | os视力                                     |             |
| 荧光素图像评估                         |         |      |                                          |             |
| level_central_od                | Integer | 否    | 中心定位od:<br/>2-中心;<br/>1-颞侧;<br/>3-鼻侧;<br/>4-上方;<br/>5-下方; |             |
| central_value_od                | Integer | 否    | 中心定位值:<br/>1-↑;<br/>2-↓;<br/>3-←(选中心时有);<br/>4-→(选中心时有); |             |
| level_central_os                | Integer | 否    | 中心定位os:<br/>1-中心;<br/>2-颞侧;<br/>3-鼻侧;<br/>4-上方;<br/>5-下方; |             |
| central_value_os                | Integer | 否    | 中心定位值:<br/>1-↑;<br/>2-↓;<br/>3-←(选中心时有);<br/>4-→(选中心时有); |             |
| activity_od                     | Integer | 否    | 活动类型od:<br/>1-平滑;<br/>2-快速下滑;<br/>3-顶端旋转; |             |
| activity_type_od                | Integer | 否    | 活动类型值:<br/>1-↑;<br/>2-↓;                 |             |
| activity_os                     | Integer | 否    | 活动类型os:<br/>1-平滑;<br/>2-快速下滑;<br/>3-顶端旋转; |             |
| activity_type_os                | Integer | 否    | 活动类型值:<br/>1-↑;<br/>2-↓;                 |             |
| move_degree_od                  | Integer | 否    | 移动度:<br/>1-快;<br/>2-适中;<br/>3-慢;         |             |
| move_od                         | Integer | 否    | 移动度值:<br/>1-↑;<br/>2-↓;                  |             |
| move_degree_os                  | Integer | 否    | 移动度:<br/>1-快;<br/>2-适中;<br/>3-慢;         |             |
| move_os                         | Integer | 否    | 移动度值:<br/>1-↑;<br/>2-↓;                  |             |
| stable_degree_od                | Integer | 否    | 稳定度:<br/>1-是;<br/>2-否;                   |             |
| stability_od                    | Integer | 否    | 稳定度值:<br/>1-↑;<br/>2-↓;                  |             |
| stable_degree_os                | Integer | 否    | 稳定度:<br/>1-是;<br/>2-否;                   |             |
| stability_os                    | Integer | 否    | 稳定度值:<br/>1-↑;<br/>2-↓;                  |             |
| fulores_imaging_od              | Integer | 否    | 中央荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |             |
| central_fluorescence_imaging_od | Integer | 否    | 中央荧光显像值:<br/>1-↑;<br/>2-↓;               |             |
| fulores_imaging_os              | Integer | 否    | 中央荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |             |
| central_fluorescence_imaging_os | Integer | 否    | 中央荧光显像值:<br/>1-↑;<br/>2-↓;               |             |
| discri_imaging_od               | Integer | 否    | 中周荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |             |
| discri_imaging_value_od         | Integer | 否    | 中周荧光显像值:<br/>1-↑;<br/>2-↓;               |             |
| discri_imaging_os               | Integer | 否    | 中周荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |             |
| discri_imaging_value_os         | Integer | 否    | 中周荧光显像值:<br/>1-↑;<br/>2-↓;               |             |
| side_arc_width_od               | Integer | 否    | 边弧宽度:<br/>1-宽;<br/>2-适中;<br/>3-窄;        |             |
| curve_with_od                   | Integer | 否    | 边弧宽度值:<br/>1-↑;<br/>2-↓;                 |             |
| side_arc_width_os               | Integer | 否    | 边弧宽度:<br/>1-宽;<br/>2-适中;<br/>3-窄;        |             |
| curve_with_os                   | Integer | 否    | 边弧宽度值:<br/>1-↑;<br/>2-↓;                 |             |
| side_arc_tilted_od              | Integer | 否    | 边缘翘起:<br/>1-低;<br/>2-中;<br/>3-高;         |             |
| curve_raise_od                  | Integer | 否    | 边缘翘起值:<br/>1-↑;<br/>2-↓;                 |             |
| side_arc_tilted_os              | Integer | 否    | 边弧翘起:<br/>1-低;<br/>2-中;<br/>3-高;         |             |
| curve_raise_os                  | Integer | 否    | 边弧翘起值:<br/>1-↑;<br/>2-↓;                 |             |
| coverage_degree_od              | Integer | 否    | 覆盖度:<br/>1-好;<br/>2-差;<br/>3-可接受;        |             |
| coverage_od                     | Integer | 否    | 覆盖度值:<br/>1-↑;<br/>2-↓;                  |             |
| coverage_degree_os              | Integer | 否    | 覆盖度:<br/>1-好;<br/>2-差;<br/>3-可接受;        |             |
| coverage_os                     | Integer | 否    | 覆盖度值:<br/>1-↑;<br/>2-↓;                  |             |
| fit_type_od                     | Integer | 否    | 配适类型od:<br/>1-平坦;<br/>2-匹配;<br/>3-陡峭;    |             |
| fit_type_value_od               | Integer | 否    | 配适类型od值:<br/>1-↑;<br/>2-↓;               |             |
| fit_type_os                     | Integer | 否    | 配适类型os:<br/>1-平坦;<br/>2-匹配;<br/>3-陡峭;    |             |
| fit_type_value_os               | Integer | 否    | 配适类型os值:<br/>1-↑;<br/>2-↓;               |             |
| 新处方                             |         |      |                                          |             |
| is_need_new_prescription        | Integer | 否    | 是否需要新处方L:<br/>1-否;<br/>2-是               |             |
| patient_guide                   | Integer | 否    | 患者戴镜指南:<br/>1-戴镜、摘镜操作;<br/>2-镜片护理方法;     |             |



### 专科检查-RGP分发保存

```http
[POST]/treat_service/speciality_check/rgp/distribute
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                             | 类型      | 必填   | 说明                                       |
| ------------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                         | String  | 是    | 就诊ID                                     |
| 下次随访时间next_follow_up_time       |         |      |                                          |
| next_follow_up_time             | Integer | 是    | 下次随访时间                                   |
| next_follow_up_time_unit        | Integer | 是    | 下次随访时间单位<br/>1-天;<br/>2-周;<br/>3-月;<br/>4-年 |
| RGP处方rgp_prescription           |         |      |                                          |
| rgp_od_brand_id                 | Long    | 否    | OD-品牌id                                  |
| rgp_od_brand                    | String  | 否    | OD-品牌                                    |
| rgp_od_material_id              | Long    | 否    | OD-材质id                                  |
| rgp_od_material                 | String  | 否    | OD-材质                                    |
| rgp_od_curve                    | String  | 否    | OD-基弧                                    |
| rgp_od_diameter                 | String  | 否    | OD-直径                                    |
| rgp_od_degree                   | String  | 否    | OD-度数                                    |
| rgp_od_rem                      | String  | 否    | OD-备注                                    |
| rgp_os_brand_id                 | Long    | 否    | OS-品牌id                                  |
| rgp_os_brand                    | String  | 否    | OS-品牌                                    |
| rgp_os_material_id              | Long    | 否    | OS-材质id                                  |
| rgp_os_material                 | String  | 否    | OS-材质                                    |
| rgp_os_curve                    | String  | 否    | OS-基弧                                    |
| rgp_os_diameter                 | String  | 否    | OS-直径                                    |
| rgp_os_degree                   | String  | 否    | OS-度数                                    |
| rgp_os_rem                      | String  | 否    | OD-备注                                    |
| 模板数据template_data               |         |      |                                          |
| 矫正视力                            |         |      |                                          |
| corrected_vision_od_vision      | 70501   | 是    | od视力                                     |
| corrected_vision_os_vision      | 70502   | 是    | os视力                                     |
| 戴镜验光                            |         |      |                                          |
| optometry_od_ball               | String  | 否    | od球镜                                     |
| optometry_od_column             | String  | 否    | od柱镜                                     |
| optometry_od_axis               | String  | 否    | od轴向                                     |
| optometry_od_vision             | String  | 否    | od视力                                     |
| optometry_os_ball               | String  | 否    | os球镜                                     |
| optometry_os_column             | String  | 否    | os柱镜                                     |
| optometry_os_axis               | String  | 否    | os轴向                                     |
| optometry_os_vision             | String  | 否    | os视力                                     |
| 荧光素图像评估                         |         |      |                                          |
| level_central_od                | Integer | 否    | 中心定位od:<br/>1-中心;<br/>2-颞侧;<br/>3-鼻侧;<br/>4-上方;<br/>5-下方; |
| central_value_od                | Integer | 否    | 中心定位值:<br/>1-↑;<br/>2-↓;<br/>3-←(选中心时有);<br/>4-→(选中心时有); |
| level_central_os                | Integer | 否    | 中心定位os:<br/>1-中心;<br/>2-颞侧;<br/>3-鼻侧;<br/>4-上方;<br/>5-下方; |
| central_value_os                | Integer | 否    | 中心定位值:<br/>1-↑;<br/>2-↓;<br/>3-←(选中心时有);<br/>4-→(选中心时有); |
| activity_od                     | Integer | 否    | 活动类型od:<br/>1-平滑;<br/>2-快速下滑;<br/>3-顶端旋转; |
| activity_type_od                | Integer | 否    | 活动类型值:<br/>1-↑;<br/>2-↓;                 |
| activity_os                     | Integer | 否    | 活动类型os:<br/>1-平滑;<br/>2-快速下滑;<br/>3-顶端旋转; |
| activity_type_os                | Integer | 否    | 活动类型值:<br/>1-↑;<br/>2-↓;                 |
| move_degree_od                  | Integer | 否    | 移动度:<br/>1-快;<br/>2-适中;<br/>3-慢;         |
| move_od                         | Integer | 否    | 移动度值:<br/>1-↑;<br/>2-↓;                  |
| move_degree_os                  | Integer | 否    | 移动度:<br/>1-快;<br/>2-适中;<br/>3-慢;         |
| move_os                         | Integer | 否    | 移动度值:<br/>1-↑;<br/>2-↓;                  |
| stable_degree_od                | Integer | 否    | 稳定度:<br/>1-是;<br/>2-否;                   |
| stability_od                    | Integer | 否    | 稳定度值:<br/>1-↑;<br/>2-↓;                  |
| stable_degree_os                | Integer | 否    | 稳定度:<br/>1-是;<br/>2-否;                   |
| stability_os                    | Integer | 否    | 稳定度值:<br/>1-↑;<br/>2-↓;                  |
| fulores_imaging_od              | Integer | 否    | 中央荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| central_fluorescence_imaging_od | Integer | 否    | 中央荧光显像值:<br/>1-↑;<br/>2-↓;               |
| fulores_imaging_os              | Integer | 否    | 中央荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| central_fluorescence_imaging_os | Integer | 否    | 中央荧光显像值:<br/>1-↑;<br/>2-↓;               |
| discri_imaging_od               | Integer | 否    | 中周荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| discri_imaging_value_od         | Integer | 否    | 中周荧光显像值:<br/>1-↑;<br/>2-↓;               |
| discri_imaging_os               | Integer | 否    | 中周荧光显像:<br/>1-充盈;<br/>2-均匀;<br/>3-接触;    |
| discri_imaging_value_os         | Integer | 否    | 中周荧光显像值:<br/>1-↑;<br/>2-↓;               |
| side_arc_width_od               | Integer | 否    | 边弧宽度:<br/>1-宽;<br/>2-适中;<br/>3-窄;        |
| curve_with_od                   | Integer | 否    | 边弧宽度值:<br/>1-↑;<br/>2-↓;                 |
| side_arc_width_os               | Integer | 否    | 边弧宽度:<br/>1-宽;<br/>2-适中;<br/>3-窄;        |
| curve_with_os                   | Integer | 否    | 边弧宽度值:<br/>1-↑;<br/>2-↓;                 |
| side_arc_tilted_od              | Integer | 否    | 边缘翘起:<br/>1-低;<br/>2-中;<br/>3-高;         |
| curve_raise_od                  | Integer | 否    | 边缘翘起值:<br/>1-↑;<br/>2-↓;                 |
| side_arc_tilted_os              | Integer | 否    | 边弧翘起:<br/>1-低;<br/>2-中;<br/>3-高;         |
| curve_raise_os                  | Integer | 否    | 边弧翘起值:<br/>1-↑;<br/>2-↓;                 |
| coverage_degree_od              | Integer | 否    | 覆盖度:<br/>1-好;<br/>2-差;<br/>3-可接受;        |
| coverage_od                     | Integer | 否    | 覆盖度值:<br/>1-↑;<br/>2-↓;                  |
| coverage_degree_os              | Integer | 否    | 覆盖度:<br/>1-好;<br/>2-差;<br/>3-可接受;        |
| coverage_os                     | Integer | 否    | 覆盖度值:<br/>1-↑;<br/>2-↓;                  |
| fit_type_od                     | Integer | 否    | 配适类型od:<br/>1-平坦;<br/>2-匹配;<br/>3-陡峭;    |
| fit_type_value_od               | Integer | 否    | 配适类型od值:<br/>1-↑;<br/>2-↓;               |
| fit_type_os                     | Integer | 否    | 配适类型os:<br/>1-平坦;<br/>2-匹配;<br/>3-陡峭;    |
| fit_type_value_os               | Integer | 否    | 配适类型os值:<br/>1-↑;<br/>2-↓;               |
| 新处方                             |         |      |                                          |
| is_need_new_prescription        | Integer | 否    | 是否需要新处方L:<br/>1-否;<br/>2-是               |
| patient_guide                   | Integer | 否    | 患者戴镜指南:<br/>1-戴镜、摘镜操作;<br/>2-镜片护理方法;     |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 专科检查-RGP复查获取

```http
[GET]/treat_service/speciality_check/rgp/recheck
```

#### 修改更新记录

| 对应业务        | 说明     |
| ----------- | ------ |
| V1.2.3      | 新增     |
| WEBV1.2.3.1 | 新增随访次数 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数



| 参数名                              | 类型      | 必填   | 说明                                       |
| -------------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                          | String  | 是    | 就诊ID                                     |
| 下次随访时间next_follow_up_time        |         |      |                                          |
| next_follow_up_time              | Integer | 是    | 下次随访时间                                   |
| next_follow_up_time_unit         | Integer | 是    | 下次随访时间单位<br/>1-天;<br/>2-周;<br/>3-月;<br/>4-年 |
| RGP处方rgp_prescription            |         |      |                                          |
| rgp_od_brand_id                  | Long    | 否    | OD-品牌id                                  |
| rgp_od_brand                     | String  | 否    | OD-品牌                                    |
| rgp_od_material_id               | Long    | 否    | OD-材质id                                  |
| rgp_od_material                  | String  | 否    | OD-材质                                    |
| rgp_od_curve                     | String  | 否    | OD-基弧                                    |
| rgp_od_diameter                  | String  | 否    | OD-直径                                    |
| rgp_od_degree                    | String  | 否    | OD-度数                                    |
| rgp_od_rem                       | String  | 否    | OD-备注                                    |
| rgp_os_brand_id                  | Long    | 否    | OS-品牌id                                  |
| rgp_os_brand                     | String  | 否    | OS-品牌                                    |
| rgp_os_material_id               | Long    | 否    | OS-材质id                                  |
| rgp_os_material                  | String  | 否    | OS-材质                                    |
| rgp_os_curve                     | String  | 否    | OS-基弧                                    |
| rgp_os_diameter                  | String  | 否    | OS-直径                                    |
| rgp_os_degree                    | String  | 否    | OS-度数                                    |
| rgp_os_rem                       | String  | 否    | OD-备注                                    |
| 模板数据template_data                |         |      |                                          |
| follow_up_time                   | Integer | 是    | 随访时间:<br/>1-一周;<br/>2-1月;<br/>3-3月;<br/>4-6月;<br/>5-12月;<br/>6-不定期; |
| follow_up_time_custom            | String  | 否    | 随访时间自定义                                  |
| recheck_times                    | Integer | 否    | 第几次复查                                    |
| daily_glasses_time               | Integer | 是    | 每日戴镜时间                                   |
| weekly_glasses_time              | Integer | 是    | 每周戴镜天数                                   |
| 矫正视力                             |         |      |                                          |
| corrected_vision_od_vision       | String  | 是    | od视力                                     |
| corrected_vision_os_vision       | String  | 是    | os视力                                     |
| 戴镜验光                             |         |      |                                          |
| optometry_od_ball                | String  | 否    | od球镜                                     |
| optometry_od_column              | String  | 否    | od柱镜                                     |
| optometry_od_axis                | String  | 否    | od轴向                                     |
| optometry_od_vision              | String  | 否    | od视力                                     |
| optometry_os_ball                | String  | 否    | os球镜                                     |
| optometry_os_column              | String  | 否    | os柱镜                                     |
| optometry_os_axis                | String  | 否    | os轴向                                     |
| optometry_os_vision              | String  | 否    | os视力                                     |
| 荧光素图像评估                          |         |      |                                          |
| level_central_od                 | 70701   | 707  | 水平中心od                                   |
| level_central_os                 | 70703   | 707  | 水平中心os                                   |
| activity_od                      | 70705   | 707  | 活动类型od                                   |
| activity_os                      | 70707   | 707  | 活动类型os                                   |
| move_degree_od                   | 70709   | 707  | 移动od                                     |
| move_degree_os                   | 70711   | 707  | 移动os                                     |
| stable_degree_od                 | 70713   | 707  | 稳定od                                     |
| stable_degree_os                 | 70715   | 707  | 稳定os                                     |
| fulores_imaging_od               | 70717   | 707  | 中央荧光od                                   |
| fulores_imaging_os               | 70719   | 707  | 中央荧光os                                   |
| discri_imaging_od                | 70721   | 707  | 中周荧光od                                   |
| discri_imaging_os                | 70723   | 707  | 中周荧光os                                   |
| side_arc_width_od                | 70725   | 707  | 边弧od                                     |
| side_arc_width_os                | 70727   | 707  | 边弧os                                     |
| side_arc_tilted_od               | 70729   | 707  | 边缘od                                     |
| side_arc_tilted_os               | 70731   | 707  | 边缘os                                     |
| coverage_degree_od               | 70733   | 707  | 覆盖od                                     |
| coverage_degree_os               | 70735   | 707  | 覆盖os                                     |
| fit_type_od                      | 70737   | 707  | 配适od                                     |
| fit_type_os                      | 70739   | 707  | 配适os                                     |
| 眼部裂隙灯检查                          |         |      |                                          |
| epithelial_edema_od              | Integer | 否    | 眼部裂隙灯检查-上皮水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_od                 | Integer | 否    | 眼部裂隙灯检查-微囊od;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_od                   | Integer | 否    | 眼部裂隙灯检查-角膜点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_od             | Integer | 否    | 眼部裂隙灯检查-3、9点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_od                | Integer | 否    | 眼部裂隙灯检查-角膜基质od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_od    | Integer | 否    | 眼部裂隙灯检查-角膜新生血管od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_od             | Integer | 否    | 眼部裂隙灯检查-角膜缘充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_od | Integer | 否    | 眼部裂隙灯检查-球结膜充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_od     | Integer | 否    | 眼部裂隙灯检查-球结膜水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_od          | Integer | 否    | 眼部裂隙灯检查-脸板结膜异常od;<br/>0;<br/>1;<br/>2;<br/>3; |
| epithelial_edema_os              | Integer | 否    | 眼部裂隙灯检查-上皮水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_os                 | Integer | 否    | 眼部裂隙灯检查-微囊os;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_os                   | Integer | 否    | 眼部裂隙灯检查-角膜点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_os             | Integer | 否    | 眼部裂隙灯检查-3、9点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_os                | Integer | 否    | 眼部裂隙灯检查-角膜基质os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_os    | Integer | 否    | 眼部裂隙灯检查-角膜新生血管os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_os             | Integer | 否    | 眼部裂隙灯检查-角膜缘充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_os | Integer | 否    | 眼部裂隙灯检查-球结膜充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_os     | Integer | 否    | 眼部裂隙灯检查-球结膜水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_os          | Integer | 否    | 眼部裂隙灯检查-脸板结膜异常os;<br/>0;<br/>1;<br/>2;<br/>3; |
| 眼底检查                             |         |      |                                          |
| disk_od                          | String  | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_od                            | String  | 否    | 眼底检查-C/D od;常规时默认为：0.3                   |
| rim_od                           | String  | 否    | 眼底检查-盘沿od;常规时默认为：粉红色、清                   |
| peripheral_od                    | String  | 否    | 眼底检查-外周od;常规时默认为：清晰                      |
| av_od                            | String  | 否    | 眼底检查-A/V od;常规时默认为：2:3                   |
| macular_od                       | String  | 否    | 眼底检查-黄斑od;常规时默认为：中心凹反光可见                 |
| disk_os                          | String  | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_os                            | String  | 否    | 眼底检查-C/D os;常规时默认为：0.3                   |
| rim_os                           | String  | 否    | 眼底检查-盘沿os;常规时默认为：粉红色、清                   |
| peripheral_os                    | String  | 否    | 眼底检查-外周os;常规时默认为：清晰                      |
| av_os                            | String  | 否    | 眼底检查-A/V os;常规时默认为：2:3                   |
| macular_os                       | String  | 否    | 眼底检查-黄斑os;常规时默认为：中心凹反光可见                 |
| handle                           | String  | 否    | 处理                                       |
| 新处方                              |         |      |                                          |
| is_need_new_prescription         | Integer | 否    | 是否需要新处方L:<br/>1-否;<br/>2-是               |


RGP处方说明：
1. 处方来源设置为：3-复查




### 专科检查-RGP复查保存

```http
[POST]/treat_service/speciality_check/rgp/recheck
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                              | 类型      | 必填   | 说明                                       |
| -------------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                          | String  | 是    | 就诊ID                                     |
| 下次随访时间next_follow_up_time        |         |      |                                          |
| next_follow_up_time              | Integer | 是    | 下次随访时间                                   |
| next_follow_up_time_unit         | Integer | 是    | 下次随访时间单位<br/>1-天;<br/>2-周;<br/>3-月;<br/>4-年 |
| RGP处方rgp_prescription            |         |      |                                          |
| rgp_od_brand_id                  | Long    | 否    | OD-品牌id                                  |
| rgp_od_brand                     | String  | 否    | OD-品牌                                    |
| rgp_od_material_id               | Long    | 否    | OD-材质id                                  |
| rgp_od_material                  | String  | 否    | OD-材质                                    |
| rgp_od_curve                     | String  | 否    | OD-基弧                                    |
| rgp_od_diameter                  | String  | 否    | OD-直径                                    |
| rgp_od_degree                    | String  | 否    | OD-度数                                    |
| rgp_od_rem                       | String  | 否    | OD-备注                                    |
| rgp_os_brand_id                  | Long    | 否    | OS-品牌id                                  |
| rgp_os_brand                     | String  | 否    | OS-品牌                                    |
| rgp_os_material_id               | Long    | 否    | OS-材质id                                  |
| rgp_os_material                  | String  | 否    | OS-材质                                    |
| rgp_os_curve                     | String  | 否    | OS-基弧                                    |
| rgp_os_diameter                  | String  | 否    | OS-直径                                    |
| rgp_os_degree                    | String  | 否    | OS-度数                                    |
| rgp_os_rem                       | String  | 否    | OD-备注                                    |
| 模板数据template_data                |         |      |                                          |
| follow_up_time                   | Integer | 是    | 随访时间:<br/>1-一周;<br/>2-1月;<br/>3-3月;<br/>4-6月;<br/>5-12月;<br/>6-不定期; |
| follow_up_time_custom            | String  | 否    | 随访时间自定义                                  |
| recheck_times                    | Integer | 否    | 第几次复查                                    |
| daily_glasses_time               | Integer | 是    | 每日戴镜时间                                   |
| weekly_glasses_time              | Integer | 是    | 每周戴镜天数                                   |
| 矫正视力                             |         |      |                                          |
| corrected_vision_od_vision       | String  | 是    | od视力                                     |
| corrected_vision_os_vision       | String  | 是    | os视力                                     |
| 戴镜验光                             |         |      |                                          |
| optometry_od_ball                | String  | 否    | od球镜                                     |
| optometry_od_column              | String  | 否    | od柱镜                                     |
| optometry_od_axis                | String  | 否    | od轴向                                     |
| optometry_od_vision              | String  | 否    | od视力                                     |
| optometry_os_ball                | String  | 否    | os球镜                                     |
| optometry_os_column              | String  | 否    | os柱镜                                     |
| optometry_os_axis                | String  | 否    | os轴向                                     |
| optometry_os_vision              | String  | 否    | os视力                                     |
| 荧光素图像评估                          |         |      |                                          |
| level_central_od                 | 70701   | 707  | 水平中心od                                   |
| level_central_os                 | 70703   | 707  | 水平中心os                                   |
| activity_od                      | 70705   | 707  | 活动类型od                                   |
| activity_os                      | 70707   | 707  | 活动类型os                                   |
| move_degree_od                   | 70709   | 707  | 移动od                                     |
| move_degree_os                   | 70711   | 707  | 移动os                                     |
| stable_degree_od                 | 70713   | 707  | 稳定od                                     |
| stable_degree_os                 | 70715   | 707  | 稳定os                                     |
| fulores_imaging_od               | 70717   | 707  | 中央荧光od                                   |
| fulores_imaging_os               | 70719   | 707  | 中央荧光os                                   |
| discri_imaging_od                | 70721   | 707  | 中周荧光od                                   |
| discri_imaging_os                | 70723   | 707  | 中周荧光os                                   |
| side_arc_width_od                | 70725   | 707  | 边弧od                                     |
| side_arc_width_os                | 70727   | 707  | 边弧os                                     |
| side_arc_tilted_od               | 70729   | 707  | 边缘od                                     |
| side_arc_tilted_os               | 70731   | 707  | 边缘os                                     |
| coverage_degree_od               | 70733   | 707  | 覆盖od                                     |
| coverage_degree_os               | 70735   | 707  | 覆盖os                                     |
| fit_type_od                      | 70737   | 707  | 配适od                                     |
| fit_type_os                      | 70739   | 707  | 配适os                                     |
| 眼部裂隙灯检查                          |         |      |                                          |
| epithelial_edema_od              | Integer | 否    | 眼部裂隙灯检查-上皮水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_od                 | Integer | 否    | 眼部裂隙灯检查-微囊od;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_od                   | Integer | 否    | 眼部裂隙灯检查-角膜点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_od             | Integer | 否    | 眼部裂隙灯检查-3、9点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_od                | Integer | 否    | 眼部裂隙灯检查-角膜基质od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_od    | Integer | 否    | 眼部裂隙灯检查-角膜新生血管od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_od             | Integer | 否    | 眼部裂隙灯检查-角膜缘充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_od | Integer | 否    | 眼部裂隙灯检查-球结膜充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_od     | Integer | 否    | 眼部裂隙灯检查-球结膜水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_od          | Integer | 否    | 眼部裂隙灯检查-脸板结膜异常od;<br/>0;<br/>1;<br/>2;<br/>3; |
| epithelial_edema_os              | Integer | 否    | 眼部裂隙灯检查-上皮水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_os                 | Integer | 否    | 眼部裂隙灯检查-微囊os;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_os                   | Integer | 否    | 眼部裂隙灯检查-角膜点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_os             | Integer | 否    | 眼部裂隙灯检查-3、9点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_os                | Integer | 否    | 眼部裂隙灯检查-角膜基质os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_os    | Integer | 否    | 眼部裂隙灯检查-角膜新生血管os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_os             | Integer | 否    | 眼部裂隙灯检查-角膜缘充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_os | Integer | 否    | 眼部裂隙灯检查-球结膜充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_os     | Integer | 否    | 眼部裂隙灯检查-球结膜水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_os          | Integer | 否    | 眼部裂隙灯检查-脸板结膜异常os;<br/>0;<br/>1;<br/>2;<br/>3; |
| 眼底检查                             |         |      |                                          |
| disk_od                          | String  | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_od                            | String  | 否    | 眼底检查-C/D od;常规时默认为：0.3                   |
| rim_od                           | String  | 否    | 眼底检查-盘沿od;常规时默认为：粉红色、清                   |
| peripheral_od                    | String  | 否    | 眼底检查-外周od;常规时默认为：清晰                      |
| av_od                            | String  | 否    | 眼底检查-A/V od;常规时默认为：2:3                   |
| macular_od                       | String  | 否    | 眼底检查-黄斑od;常规时默认为：中心凹反光可见                 |
| disk_os                          | String  | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_os                            | String  | 否    | 眼底检查-C/D os;常规时默认为：0.3                   |
| rim_os                           | String  | 否    | 眼底检查-盘沿os;常规时默认为：粉红色、清                   |
| peripheral_os                    | String  | 否    | 眼底检查-外周os;常规时默认为：清晰                      |
| av_os                            | String  | 否    | 眼底检查-A/V os;常规时默认为：2:3                   |
| macular_os                       | String  | 否    | 眼底检查-黄斑os;常规时默认为：中心凹反光可见                 |
| handle                           | String  | 否    | 处理                                       |
| 新处方                              |         |      |                                          |
| is_need_new_prescription         | Integer | 否    | 是否需要新处方L:<br/>1-否;<br/>2-是               |


RGP处方说明：
1. 处方来源设置为：3-复查

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


##专科检查-OK镜


### 专科检查-OK镜初检获取

```http
[GET]/treat_service/speciality_check/rtho_k_lenses/initial
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数

| 参数名                              | 类型      | 必填   | 说明                                       |
| -------------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                          | String  | 是    | 就诊ID                                     |
| 主觉验光subjective                   |         |      | 主觉验光表                                    |
| data_od_sphere                   | String  | 否    | 主觉验光OD-球镜                                |
| data_od_cylinder                 | String  | 否    | 主觉验光OD-柱镜                                |
| data_od_axis                     | String  | 否    | 主觉验光OD-轴向                                |
| data_od_prism                    | String  | 否    | 主觉验光OD-棱镜                                |
| data_od_vision                   | String  | 否    | 主觉验光OD-视力                                |
| data_od_memo                     | String  | 否    | 主觉验光OD-备注                                |
| data_os_sphere                   | String  | 否    | 主觉验光OS-球镜                                |
| data_os_cylinder                 | String  | 否    | 主觉验光OS-柱镜                                |
| data_os_axis                     | String  | 否    | 主觉验光OS-轴向                                |
| data_os_prism                    | String  | 否    | 主觉验光OS-棱镜                                |
| data_os_vision                   | String  | 否    | 主觉验光OS-视力                                |
| data_os_memo                     | String  | 否    | 主觉验光OS-备注                                |
| 角膜曲率corneal_curvature            | Object  | 否    | 角膜曲率表                                    |
| corneal_od_cliffy                | String  | 否    | 右眼陡峭                                     |
| corneal_od_flat                  | String  | 否    | 右眼平坦                                     |
| corneal_od_axis                  | String  | 否    | 右眼轴向                                     |
| corneal_os_cliffy                | String  | 否    | 左眼陡峭                                     |
| corneal_os_flat                  | String  | 否    | 左眼平坦                                     |
| corneal_os_axis                  | String  | 否    | 左眼轴向                                     |
| 其它模板数据template_data              | Object  | 是    | 其它模板数据                                   |
| bare_vision_od                   | String  | 否    | 裸眼视力OD                                   |
| bare_vision_os                   | String  | 否    | 裸眼视力OS                                   |
| corneal_topography_steep_od      | String  | 否    | 角膜地形图陡峭OD                                |
| corneal_topography_flat_od       | String  | 否    | 角膜地形图平坦OD                                |
| corneal_topography_axis_od       | String  | 否    | 角膜地形图轴向OD                                |
| corneal_topography_steep_os      | String  | 否    | 角膜地形图陡峭OS                                |
| corneal_topography_flat_os       | String  | 否    | 角膜地形图平坦OS                                |
| corneal_topography_axis_os       | String  | 否    | 角膜地形图轴向OS                                |
| iop_od                           | String  | 否    | 眼压OD                                     |
| iop_os                           | String  | 否    | 眼压OS                                     |
| eye_axis_od                      | String  | 否    | 眼轴OD                                     |
| eye_axis_os                      | String  | 否    | 眼轴OS                                     |
| corneal_endothelium_od           | String  | 否    | 角膜内皮OD                                   |
| corneal endothelium_os           | String  | 否    | 角膜内皮OS                                   |
| pupil_diameter_od                | String  | 否    | HVID/瞳孔直径OD                              |
| pupil_diameter_os                | String  | 否    | HVID/瞳孔直径OS                              |
| corneal_thickness_od             | String  | 否    | 角膜厚度OD                                   |
| corneal_thickness_os             | String  | 否    | 角膜厚度OS                                   |
| remark                           | String  | 否    | 备注                                       |
| epithelial_edema_od              | Integer | 否    | 眼部裂隙灯检查-上皮水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_od                 | Integer | 否    | 眼部裂隙灯检查-微囊od;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_od                   | Integer | 否    | 眼部裂隙灯检查-角膜点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_od             | Integer | 否    | 眼部裂隙灯检查-3、9点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_od                | Integer | 否    | 眼部裂隙灯检查-角膜基质od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_od    | Integer | 否    | 眼部裂隙灯检查-角膜新生血管od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_od             | Integer | 否    | 眼部裂隙灯检查-角膜缘充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_od | Integer | 否    | 眼部裂隙灯检查-球结膜充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_od     | Integer | 否    | 眼部裂隙灯检查-球结膜水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_od          | Integer | 否    | 眼部裂隙灯检查-脸板结膜异常od;<br/>0;<br/>1;<br/>2;<br/>3; |
| epithelial_edema_os              | Integer | 否    | 眼部裂隙灯检查-上皮水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_os                 | Integer | 否    | 眼部裂隙灯检查-微囊os;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_os                   | Integer | 否    | 眼部裂隙灯检查-角膜点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_os             | Integer | 否    | 眼部裂隙灯检查-3、9点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_os                | Integer | 否    | 眼部裂隙灯检查-角膜基质os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_os    | Integer | 否    | 眼部裂隙灯检查-角膜新生血管os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_os             | Integer | 否    | 眼部裂隙灯检查-角膜缘充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_os | Integer | 否    | 眼部裂隙灯检查-球结膜充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_os     | Integer | 否    | 眼部裂隙灯检查-球结膜水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_os          | Integer | 否    | 眼部裂隙灯检查-脸板结膜异常os;<br/>0;<br/>1;<br/>2;<br/>3; |
| slit_lamp_rem                    | String  | 否    | 眼部裂隙灯检查-备注                               |
| disk_od                          | String  | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_od                            | String  | 否    | 眼底检查-C/D od;常规时默认为：0.3                   |
| rim_od                           | String  | 否    | 眼底检查-盘沿od;常规时默认为：粉红色、清                   |
| peripheral_od                    | String  | 否    | 眼底检查-外周od;常规时默认为：清晰                      |
| av_od                            | String  | 否    | 眼底检查-A/V od;常规时默认为：2:3                   |
| macular_od                       | String  | 否    | 眼底检查-黄斑od;常规时默认为：中心凹反光可见                 |
| disk_os                          | String  | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_os                            | String  | 否    | 眼底检查-C/D os;常规时默认为：0.3                   |
| rim_os                           | String  | 否    | 眼底检查-盘沿os;常规时默认为：粉红色、清                   |
| peripheral_os                    | String  | 否    | 眼底检查-外周os;常规时默认为：清晰                      |
| av_os                            | String  | 否    | 眼底检查-A/V os;常规时默认为：2:3                   |
| macular_os                       | String  | 否    | 眼底检查-黄斑os;常规时默认为：中心凹反光可见                 |
| 眼压眼轴数据                           |         |      |                                          |
| data_od_iop                      | String  | 否    | OD-眼压,mmgh                               |
| data_os_iop                      | String  | 否    | OS-眼压,mmgh                               |
| data_od_iop_axis                 | String  | 否    | OD-眼轴,mm                                 |
| data_os_iop_axis                 | String  | 否    | OD-眼轴,mm                                 |



### 专科检查-OK镜初检保存

```http
[POST]/treat_service/speciality_check/rtho_k_lenses/initial
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                              | 类型      | 必填   | 说明                                       |
| -------------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                          | String  | 是    | 就诊ID                                     |
| 主觉验光subjective                   |         |      | 主觉验光表                                    |
| data_od_sphere                   | String  | 否    | 主觉验光OD-球镜                                |
| data_od_cylinder                 | String  | 否    | 主觉验光OD-柱镜                                |
| data_od_axis                     | String  | 否    | 主觉验光OD-轴向                                |
| data_od_prism                    | String  | 否    | 主觉验光OD-棱镜                                |
| data_od_vision                   | String  | 否    | 主觉验光OD-视力                                |
| data_od_memo                     | String  | 否    | 主觉验光OD-备注                                |
| data_os_sphere                   | String  | 否    | 主觉验光OS-球镜                                |
| data_os_cylinder                 | String  | 否    | 主觉验光OS-柱镜                                |
| data_os_axis                     | String  | 否    | 主觉验光OS-轴向                                |
| data_os_prism                    | String  | 否    | 主觉验光OS-棱镜                                |
| data_os_vision                   | String  | 否    | 主觉验光OS-视力                                |
| data_os_memo                     | String  | 否    | 主觉验光OS-备注                                |
| 角膜曲率corneal_curvature            | Object  | 否    | 角膜曲率表                                    |
| corneal_od_cliffy                | String  | 否    | 右眼陡峭                                     |
| corneal_od_flat                  | String  | 否    | 右眼平坦                                     |
| corneal_od_axis                  | String  | 否    | 右眼轴向                                     |
| corneal_os_cliffy                | String  | 否    | 左眼陡峭                                     |
| corneal_os_flat                  | String  | 否    | 左眼平坦                                     |
| corneal_os_axis                  | String  | 否    | 左眼轴向                                     |
| 其它模板数据template_data              | Object  | 是    | 其它模板数据                                   |
| bare_vision_od                   | String  | 否    | 裸眼视力OD                                   |
| bare_vision_os                   | String  | 否    | 裸眼视力OS                                   |
| corneal_topography_steep_od      | String  | 否    | 角膜地形图陡峭OD                                |
| corneal_topography_flat_od       | String  | 否    | 角膜地形图平坦OD                                |
| corneal_topography_axis_od       | String  | 否    | 角膜地形图轴向OD                                |
| corneal_topography_steep_os      | String  | 否    | 角膜地形图陡峭OS                                |
| corneal_topography_flat_os       | String  | 否    | 角膜地形图平坦OS                                |
| corneal_topography_axis_os       | String  | 否    | 角膜地形图轴向OS                                |
| iop_od                           | String  | 否    | 眼压OD                                     |
| iop_os                           | String  | 否    | 眼压OS                                     |
| eye_axis_od                      | String  | 否    | 眼轴OD                                     |
| eye_axis_os                      | String  | 否    | 眼轴OS                                     |
| corneal_endothelium_od           | String  | 否    | 角膜内皮OD                                   |
| corneal endothelium_os           | String  | 否    | 角膜内皮OS                                   |
| pupil_diameter_od                | String  | 否    | HVID/瞳孔直径OD                              |
| pupil_diameter_os                | String  | 否    | HVID/瞳孔直径OS                              |
| corneal_thickness_od             | String  | 否    | 角膜厚度OD                                   |
| corneal_thickness_os             | String  | 否    | 角膜厚度OS                                   |
| remark                           | String  | 否    | 备注                                       |
| epithelial_edema_od              | Integer | 否    | 眼部裂隙灯检查-上皮水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_od                 | Integer | 否    | 眼部裂隙灯检查-微囊od;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_od                   | Integer | 否    | 眼部裂隙灯检查-角膜点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_od             | Integer | 否    | 眼部裂隙灯检查-3、9点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_od                | Integer | 否    | 眼部裂隙灯检查-角膜基质od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_od    | Integer | 否    | 眼部裂隙灯检查-角膜新生血管od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_od             | Integer | 否    | 眼部裂隙灯检查-角膜缘充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_od | Integer | 否    | 眼部裂隙灯检查-球结膜充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_od     | Integer | 否    | 眼部裂隙灯检查-球结膜水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_od          | Integer | 否    | 眼部裂隙灯检查-脸板结膜异常od;<br/>0;<br/>1;<br/>2;<br/>3; |
| epithelial_edema_os              | Integer | 否    | 眼部裂隙灯检查-上皮水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_os                 | Integer | 否    | 眼部裂隙灯检查-微囊os;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_os                   | Integer | 否    | 眼部裂隙灯检查-角膜点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_os             | Integer | 否    | 眼部裂隙灯检查-3、9点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_os                | Integer | 否    | 眼部裂隙灯检查-角膜基质os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_os    | Integer | 否    | 眼部裂隙灯检查-角膜新生血管os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_os             | Integer | 否    | 眼部裂隙灯检查-角膜缘充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_os | Integer | 否    | 眼部裂隙灯检查-球结膜充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_os     | Integer | 否    | 眼部裂隙灯检查-球结膜水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_os          | Integer | 否    | 眼部裂隙灯检查-脸板结膜异常os;<br/>0;<br/>1;<br/>2;<br/>3; |
| slit_lamp_rem                    | String  | 否    | 眼部裂隙灯检查-备注                               |
| disk_od                          | String  | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_od                            | String  | 否    | 眼底检查-C/D od;常规时默认为：0.3                   |
| rim_od                           | String  | 否    | 眼底检查-盘沿od;常规时默认为：粉红色、清                   |
| peripheral_od                    | String  | 否    | 眼底检查-外周od;常规时默认为：清晰                      |
| av_od                            | String  | 否    | 眼底检查-A/V od;常规时默认为：2:3                   |
| macular_od                       | String  | 否    | 眼底检查-黄斑od;常规时默认为：中心凹反光可见                 |
| disk_os                          | String  | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_os                            | String  | 否    | 眼底检查-C/D os;常规时默认为：0.3                   |
| rim_os                           | String  | 否    | 眼底检查-盘沿os;常规时默认为：粉红色、清                   |
| peripheral_os                    | String  | 否    | 眼底检查-外周os;常规时默认为：清晰                      |
| av_os                            | String  | 否    | 眼底检查-A/V os;常规时默认为：2:3                   |
| macular_os                       | String  | 否    | 眼底检查-黄斑os;常规时默认为：中心凹反光可见                 |
| 眼压眼轴数据                           |         |      |                                          |
| data_od_iop                      | String  | 否    | OD-眼压,mmgh                               |
| data_os_iop                      | String  | 否    | OS-眼压,mmgh                               |
| data_od_iop_axis                 | String  | 否    | OD-眼轴,mm                                 |
| data_os_iop_axis                 | String  | 否    | OD-眼轴,mm                                 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 专科检查-OK镜试戴获取

```http
[GET]/treat_service/speciality_check/rtho_k_lenses/try
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数


| 参数名                 | 类型         | 必填   | 说明                   |
| ------------------- | ---------- | ---- | -------------------- |
| trea_id             | String     | 是    | 就诊ID                 |
| rtho_k_trys         | ObjectList | 是    | 试戴片列表                |
| 试戴验光increase_degree | Object     | 否    | 模板                   |
| optometry_od_ball   | String     | 否    | od球镜                 |
| optometry_od_column | String     | 否    | od柱镜                 |
| optometry_od_axis   | String     | 否    | od轴向                 |
| optometry_od_vision | String     | 否    | od视力                 |
| optometry_os_ball   | String     | 否    | os球镜                 |
| optometry_os_column | String     | 否    | os柱镜                 |
| optometry_os_axis   | String     | 否    | os轴向                 |
| optometry_os_vision | String     | 否    | os视力                 |
| 最终处方prescription    |            |      | OK镜处方                |
| orth_times          | Integer    | 是    | 哪次试戴，第几次试镜得结果，从1开始记的 |
| orth_times_os       | Integer    | 是    | OS-哪次试戴，第几次试镜得结果     |
| orth_od_brand_id    | String     | 否    | OD-品牌id，右眼镜片品牌id     |
| orth_od_brand       | String     | 否    | OD-品牌，右眼镜片品牌名称       |
| orth_od_rem         | String     | 否    | OD-备注                |
| orth_od_paras       | ObjectList | 否    | OD-属性列表              |
| orth_os_brand_id    | String     | 否    | OS-品牌id，左眼镜片品牌id     |
| orth_os_brand       | String     | 否    | OS-品牌，左眼镜片品牌名称       |
| orth_os_rem         | String     | 否    | OS-备注                |
| orth_os_paras       | ObjectList | 否    | OS-属性列表              |


 #####试戴片列表

1. 数据为ObjectList结构
2. 品牌参数属性在存入专科检查项表中时,key的结成结构如下：[od|os]_${属性ID}_${试戴片顺序数(从1开始)}_${属性顺序数(从0开始)}，如"od_2000004_1_2"就是右眼第一个试戴处，属性ID是2000004且在属性列表是第3个顺序的属性。ID的生成规则为从原ID15以后开始加，如原来这列最后一个模板的值是90517，那么最后值就是90120。
3. 其它模板本来的参数KEY生成规则为${原KEY}_${一位的试戴片顺序(从1开始)};ID生成规则为:9${二位的试戴片顺序(从1开始)}${原定义的二位数}

| 参数名                        | 类型         | 必填   | 说明                                       |
| -------------------------- | ---------- | ---- | ---------------------------------------- |
| index                      | Integer    | 是    | 第几次试戴，从0开始计                              |
| brand_od                   | String     | 是    | OD品牌，品牌ID                                |
| brand_args_od              | ObjectList | 是    | OD品牌参数列表                                 |
| base_arc_od                | Integer    | 否    | 基弧区:<br/>1-小;<br/>2-适中;<br/>3-大;         |
| base_arc_value_od          | String     | 否    | 基弧区值:<br/>↑<br/>↓                        |
| center_contact_od          | Integer    | 否    | 中心接触:<br/>1-淡;<br/>2-适中;<br/>3-深;        |
| center_contact_value_od    | String     | 否    | 中心接触值:<br/>↑<br/>↓                       |
| reverse_arc_od             | Integer    | 否    | 反转弧:<br/>1-陡;<br/>2-好;<br/>3-平;          |
| reverse_arc_value_od       | String     | 否    | 反转弧值:<br/>↑<br/>↓                        |
| fixed_arc_od               | Integer    | 否    | 定点弧:<br/>1-陡;<br/>2-好;<br/>3-平;          |
| fixed_arc_value_od         | String     | 否    | 定点弧值:<br/>↑<br/>↓                        |
| blinking_position_od       | Integer    | 否    | 眨眼时镜片位置:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; |
| blinking_position_value_od | String     | 否    | 眨眼时镜片位置值:<br/>↑<br/>↓                    |
| blinked_position_od        | Integer    | 否    | 眨眼后镜片位置:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; |
| blinked_position_value_od  | String     | 否    | 眨眼后镜片位置值:<br/>↑<br/>↓                    |
| peripheral_arcs_od         | Integer    | 否    | 周边弧:<br/>1-窄;<br/>2-好;<br/>3-宽;          |
| peripheral_arcs_value_od   | String     | 否    | 周边弧值:<br/>↑<br/>↓                        |
| activity_od                | Integer    | 否    | 活动度:<br/>1-偏大;<br/>2-正常;<br/>3-偏小        |
| activity_value_od          | String     | 否    | 活动度值:<br/>↑<br/>↓                        |
| brand_os                   | String     | 是    | OS品牌，品牌ID                                |
| brand_args_os              | ObjectList | 是    | OS品牌参数列表                                 |
| base_arc_os                | Integer    | 否    | 基弧区:<br/>1-小;<br/>2-适中;<br/>3-大;         |
| base_arc_value_os          | String     | 否    | 基弧区值:<br/>↑<br/>↓                        |
| center_contact_os          | Integer    | 否    | 中心接触:<br/>1-淡;<br/>2-适中;<br/>3-深;        |
| center_contact_value_os    | String     | 否    | 中心接触值:<br/>↑<br/>↓                       |
| reverse_arc_os             | Integer    | 否    | 反转弧:<br/>1-陡;<br/>2-好;<br/>3-平;          |
| reverse_arc_value_os       | String     | 否    | 反转弧值:<br/>↑<br/>↓                        |
| fixed_arc_os               | Integer    | 否    | 定点弧:<br/>1-陡;<br/>2-好;<br/>3-平;          |
| fixed_arc_value_os         | String     | 否    | 定点弧值:<br/>↑<br/>↓                        |
| blinking_position_os       | Integer    | 否    | 眨眼时镜片位置:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; |
| blinking_position_value_os | String     | 否    | 眨眼时镜片位置值:<br/>↑<br/>↓                    |
| blinked_position_os        | Integer    | 否    | 眨眼后镜片位置:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; |
| blinked_position_value_os  | String     | 否    | 眨眼后镜片位置值:<br/>↑<br/>↓                    |
| peripheral_arcs_os         | Integer    | 否    | 周边弧:<br/>1-窄;<br/>2-好;<br/>3-宽;          |
| peripheral_arcs_value_os   | String     | 否    | 周边弧值:<br/>↑<br/>↓                        |
| activity_os                | Integer    | 否    | 活动度:<br/>1-偏大;<br/>2-正常;<br/>3-偏小        |
| activity_value_os          | String     | 否    | 活动度值:<br/>↑<br/>↓                        |

###### 试戴片列表品牌属性参数

说明：
1. 结构为ObjectList
2. 品牌参数属性在存入专科检查项表中时,key的结成结构如下：[od|os]_${属性ID}_${试戴片顺序数(从1开始)}_${属性顺序数(从0开始)}，如"od_2000004_1_2"就是右眼第一个试戴处，属性ID是2000004且在属性列表是第3个顺序的属性。ID的生成规则为从原ID15以后开始加，如原来这列最后一个模板的值是90517，那么最后值就是90520。

| 参数名             | 类型     | 必填   | 说明   |
| --------------- | ------ | ---- | ---- |
| para_prop_id    | Long   | 是    | 属性ID |
| prop_prop_value | String | 否    | 属性值  |

###### 最终处方品牌属性参数

1. 结构为ObjectList

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| para_prop_id   | Long   | 是    | 属性码ID |
| para_prop_name | String | 是    | 属性名称  |
| para_choi_id   | Long   | 否    | 属性值ID |
| para_choi_code | String | 否    | 属性值代码 |
| para_value     | String | 否    | 属性值   |



### 专科检查-OK镜试戴保存

```http
[POST]/treat_service/speciality_check/rtho_k_lenses/try
```

#### 修改更新记录

| 对应业务        | 说明               |
| ----------- | ---------------- |
| V1.2.3      | 新增               |
| WEBV1.2.3.3 | 最终镜片、处方中，左右眼分开引用 |

#### 请求报文参数

| 参数名                 | 类型         | 必填   | 说明                   |
| ------------------- | ---------- | ---- | -------------------- |
| trea_id             | String     | 是    | 就诊ID                 |
| rtho_k_trys         | ObjectList | 是    | 试戴片列表                |
| 试戴验光increase_degree | Object     | 否    | 模板                   |
| optometry_od_ball   | String     | 否    | od球镜                 |
| optometry_od_column | String     | 否    | od柱镜                 |
| optometry_od_axis   | String     | 否    | od轴向                 |
| optometry_od_vision | String     | 否    | od视力                 |
| optometry_os_ball   | String     | 否    | os球镜                 |
| optometry_os_column | String     | 否    | os柱镜                 |
| optometry_os_axis   | String     | 否    | os轴向                 |
| optometry_os_vision | String     | 否    | os视力                 |
| 最终处方prescription    |            |      | OK镜处方                |
| orth_times          | Integer    | 是    | 哪次试戴，第几次试镜得结果，从1开始记的 |
| orth_times_os       | Integer    | 是    | OS-哪次试戴，第几次试镜得结果     |
| orth_od_brand_id    | String     | 否    | OD-品牌id，右眼镜片品牌id     |
| orth_od_brand       | String     | 否    | OD-品牌，右眼镜片品牌名称       |
| orth_od_rem         | String     | 否    | OD-备注                |
| orth_od_paras       | ObjectList | 否    | OD-属性列表              |
| orth_os_brand_id    | String     | 否    | OS-品牌id，左眼镜片品牌id     |
| orth_os_brand       | String     | 否    | OS-品牌，左眼镜片品牌名称       |
| orth_os_rem         | String     | 否    | OS-备注                |
| orth_os_paras       | ObjectList | 否    | OS-属性列表              |


 #####试戴片列表

1. 数据为ObjectList结构
2. 品牌参数属性在存入专科检查项表中时,key的结成结构如下：[od|os]_${属性ID}_${试戴片顺序数(从1开始)}_${属性顺序数(从0开始)}，如"od_2000004_1_2"就是右眼第一个试戴处，属性ID是2000004且在属性列表是第3个顺序的属性。ID的生成规则为从原ID15以后开始加，如原来这列最后一个模板的值是90517，那么最后值就是90120。
3. 其它模板本来的参数KEY生成规则为${原KEY}_${一位的试戴片顺序(从1开始)};ID生成规则为:9${二位的试戴片顺序(从1开始)}${原定义的二位数}

| 参数名                        | 类型         | 必填   | 说明                                       |
| -------------------------- | ---------- | ---- | ---------------------------------------- |
| index                      | Integer    | 是    | 第几次试戴，从0开始计                              |
| brand_od                   | String     | 是    | OD品牌，品牌ID                                |
| brand_args_od              | ObjectList | 是    | OD品牌参数列表                                 |
| base_arc_od                | Integer    | 否    | 基弧区:<br/>1-小;<br/>2-适中;<br/>3-大;         |
| base_arc_value_od          | String     | 否    | 基弧区值:<br/>↑<br/>↓                        |
| center_contact_od          | Integer    | 否    | 中心接触:<br/>1-淡;<br/>2-适中;<br/>3-深;        |
| center_contact_value_od    | String     | 否    | 中心接触值:<br/>↑<br/>↓                       |
| reverse_arc_od             | Integer    | 否    | 反转弧:<br/>1-陡;<br/>2-好;<br/>3-平;          |
| reverse_arc_value_od       | String     | 否    | 反转弧值:<br/>↑<br/>↓                        |
| fixed_arc_od               | Integer    | 否    | 定点弧:<br/>1-陡;<br/>2-好;<br/>3-平;          |
| fixed_arc_value_od         | String     | 否    | 定点弧值:<br/>↑<br/>↓                        |
| blinking_position_od       | Integer    | 否    | 眨眼时镜片位置:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; |
| blinking_position_value_od | String     | 否    | 眨眼时镜片位置值:<br/>↑<br/>↓                    |
| blinked_position_od        | Integer    | 否    | 眨眼后镜片位置:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; |
| blinked_position_value_od  | String     | 否    | 眨眼后镜片位置值:<br/>↑<br/>↓                    |
| peripheral_arcs_od         | Integer    | 否    | 周边弧:<br/>1-窄;<br/>2-好;<br/>3-宽;          |
| peripheral_arcs_value_od   | String     | 否    | 周边弧值:<br/>↑<br/>↓                        |
| activity_od                | Integer    | 否    | 活动度:<br/>1-偏大;<br/>2-正常;<br/>3-偏小        |
| activity_value_od          | String     | 否    | 活动度值:<br/>↑<br/>↓                        |
| brand_os                   | String     | 是    | OS品牌，品牌ID                                |
| brand_args_os              | ObjectList | 是    | OS品牌参数列表                                 |
| base_arc_os                | Integer    | 否    | 基弧区:<br/>1-小;<br/>2-适中;<br/>3-大;         |
| base_arc_value_os          | String     | 否    | 基弧区值:<br/>↑<br/>↓                        |
| center_contact_os          | Integer    | 否    | 中心接触:<br/>1-淡;<br/>2-适中;<br/>3-深;        |
| center_contact_value_os    | String     | 否    | 中心接触值:<br/>↑<br/>↓                       |
| reverse_arc_os             | Integer    | 否    | 反转弧:<br/>1-陡;<br/>2-好;<br/>3-平;          |
| reverse_arc_value_os       | String     | 否    | 反转弧值:<br/>↑<br/>↓                        |
| fixed_arc_os               | Integer    | 否    | 定点弧:<br/>1-陡;<br/>2-好;<br/>3-平;          |
| fixed_arc_value_os         | String     | 否    | 定点弧值:<br/>↑<br/>↓                        |
| blinking_position_os       | Integer    | 否    | 眨眼时镜片位置:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; |
| blinking_position_value_os | String     | 否    | 眨眼时镜片位置值:<br/>↑<br/>↓                    |
| blinked_position_os        | Integer    | 否    | 眨眼后镜片位置:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; |
| blinked_position_value_os  | String     | 否    | 眨眼后镜片位置值:<br/>↑<br/>↓                    |
| peripheral_arcs_os         | Integer    | 否    | 周边弧:<br/>1-窄;<br/>2-好;<br/>3-宽;          |
| peripheral_arcs_value_os   | String     | 否    | 周边弧值:<br/>↑<br/>↓                        |
| activity_os                | Integer    | 否    | 活动度:<br/>1-偏大;<br/>2-正常;<br/>3-偏小        |
| activity_value_os          | String     | 否    | 活动度值:<br/>↑<br/>↓                        |


###### 试戴片列表品牌属性参数

说明：
1. 结构为ObjectList
2. 品牌参数属性在存入专科检查项表中时,key的结成结构如下：[od|os]_${属性ID}_${试戴片顺序数(从1开始)}_${属性顺序数(从0开始)}，如"od_2000004_1_2"就是右眼第一个试戴处，属性ID是2000004且在属性列表是第3个顺序的属性。ID的生成规则为从原ID15以后开始加，如原来这列最后一个模板的值是90517，那么最后值就是90520。

| 参数名             | 类型     | 必填   | 说明   |
| --------------- | ------ | ---- | ---- |
| para_prop_id    | Long   | 是    | 属性ID |
| prop_prop_value | String | 否    | 属性值  |

###### 最终处方品牌属性参数

1. 结构为ObjectList

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| para_prop_id   | Long   | 是    | 属性码ID |
| para_choi_id   | Long   | 否    | 属性值ID |
| para_choi_code | String | 否    | 属性值代码 |
| para_value     | String | 否    | 属性值   |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 专科检查-OK镜分发获取

```http
[GET]/treat_service/speciality_check/rtho_k_lenses/distribute
```

#### 修改更新记录

|  对应业务 	| 说明 					|
|-----------|---------------------	|
| V1.2.3 	| 新增 		 			|
| V1.2.3.2 	| 新增不定期随访时间 		|

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数

|       参数名        		|  类型  		| 必填 	|   说明   										|     变更 	  			|
|---------------------------|---------------|------	|-------------------------------------------	|----------------------	|
| trea_id             		| String 		| 是   	| 就诊ID   										| 						|
| 新处方prescription        	|  				|    	| OK镜处方   									| 						|
| orth_od_brand_id 			| String     	| 否   	| OD-品牌id，右眼镜片品牌id 						| 						|
| orth_od_brand    			| String     	| 否   	| OD-品牌，右眼镜片品牌名称 						| 						|
| orth_od_rem      			| String     	| 否   	| OD-备注                  						| 						|
| orth_od_paras    			| ObjectList 	| 否   	| OD-属性列表               						| 						|
| orth_os_brand_id 			| String     	| 否   	| OS-品牌id，左眼镜片品牌id 						| 						|
| orth_os_brand    			| String     	| 否   	| OS-品牌，左眼镜片品牌名称 						| 						|
| orth_os_rem      			| String     	| 否   	| OS-备注                   						|	 					|
| orth_os_paras    			| ObjectList 	| 否   	| OS-属性列表               						| 						|
| 随访时间next_follow_up_time|  				|    	| 病历信息表 										| 						|
| next_follow_up_time      	| Integer 		| 是   	| 下次随访时间                                   	| 						|
| next_follow_up_time_unit 	| Integer 		| 是   	| 下次随访时间单位<br/>1-天;<br/>2-周;<br/>3-月;<br/>4-年 	|				|
| emr_followup_type      	| Integer 		| 是   	| 随访时间类型；0:定期;1:不定期                    	| V1.2.3.2新增			|
| emr_followup_notfixed 	| Integer 		| 是   	| 不定期随访时间 									| V1.2.3.2新增			|
| 模板数据template_data      |  				|    	| 模板 											| 						|
| 矫正视力                   |  				|    	| 模板 											| 						|
| corrected_vision_od_vision| String 		| 是   	| od视力											|                       |
| corrected_vision_os_vision| String 		| 是   	| os视力											|                       |
| 戴镜验光                   |  				|    	| 模板 											| 						|
| optometry_od_ball         | String     	| 否   	| od球镜											|                       |
| optometry_od_column       | String     	| 否   	| od柱镜											|                       |
| optometry_od_axis         | String     	| 否   	| od轴向											|                       |
| optometry_od_vision       | String     	| 否   	| od视力											|                       |
| optometry_os_ball         | String     	| 否   	| os球镜											|                       |
| optometry_os_column       | String     	| 否   	| os柱镜											|                       |
| optometry_os_axis         | String     	| 否   	| os轴向											|                       |
| optometry_os_vision       | String     	| 否   	| os视力											|                       |
| 镜片适配                   |  				|    	| 模板 											| 						|
| base_arc_od               | Integer 		| 是   	| 基弧区od:<br/>1-小;<br/>2-适中;<br/>3-大		|						|
| base_arc_os               | Integer 		| 是   	| 基弧区os:<br/>1-小;<br/>2-适中;<br/>3-大 		|						|
| center_contact_od         | Integer 		| 是   	| 中心接触od:<br/>1-淡;<br/>2-适中;<br/>3-深		|						|
| center_contact_os         | Integer 		| 是   	| 中心接触os:<br/>1-淡;<br/>2-适中;<br/>3-深		|						|
| reverse_arc_od            | Integer 		| 是   	| 反转弧od:<br/>1-陡;<br/>2-好;<br/>3-平;			|						|
| reverse_arc_os            | Integer 		| 是   	| 反转弧os:<br/>1-陡;<br/>2-好;<br/>3-平;			|						|
| fixed_arc_od              | Integer 		| 是   	| 定点弧od:<br/>1-陡;<br/>2-好;<br/>3-平;			|						|
| fixed_arc_os              | Integer 		| 是   	| 定点弧os:<br/>1-陡;<br/>2-好;<br/>3-平;			|						|
| blinking_lens_position_ od| Integer 		| 是   	| 眨眼时镜片位置od:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧;| |
| blinking_lens_position_ os| Integer 		| 是   	| 眨眼时镜片位置os:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧;| |
| blinked_lens_position_ od | Integer 		| 是   	| 眨眼后镜片位置od:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧;| |
| blinked_lens_position_ os | Integer 		| 是   	| 眨眼后镜片位置os:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧;| |
| peripheral_arcs_od        | Integer 		| 是   	| 周边弧od:<br/>1-窄;<br/>2-好;<br/>3-宽;			|						|
| peripheral_arcs_os        | Integer 		| 是   	| 周边弧os:<br/>1-窄;<br/>2-好;<br/>3-宽;			|						|
| activity_od               | Integer 		| 是   	| 活动度od:<br/>1-偏大;<br/>2-正常;<br/>3-偏小		|						|
| activity_os               | Integer 		| 是   	| 活动度os:<br/>1-偏大;<br/>2-正常;<br/>3-偏小		|						|
| handle                    | String     	| 否   	| 处理                                  			|						|
| is_need_new_prescription  | Integer 		| 否   	| 是否需要新处方:<br/>1-否;<br/>2-是;    			|						|
| patient_guide             | String  		| 否   	| 患者戴镜指南:<br/>1-戴镜、摘镜操作;<br/>2-镜片护理方法;|					|



###### 最终处方品牌属性参数

说明
1. 结构为ObjectList

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| para_prop_id   | Long   | 是    | 属性码ID |
| para_prop_name | String | 是    | 属性名称  |
| para_choi_id   | Long   | 否    | 属性值ID |
| para_choi_code | String | 否    | 属性值代码 |
| para_value     | String | 否    | 属性值   |





### 专科检查-OK镜分发保存

```http
[POST]/treat_service/speciality_check/rtho_k_lenses/distribute
```

#### 修改更新记录

|  对应业务 	| 说明 					|
|-----------|---------------------	|
| V1.2.3 	| 新增 		 			|
| V1.2.3.2 	| 新增不定期随访时间 		|

#### 请求报文参数

|          参数名          	|   类型  	| 长度 	| 必填 	|                           说明                          	|  变更         	|
|--------------------------	|---------	|------	|------	|---------------------------------------------------------	|-------------	|
| trea_id            		| String 	|      	| 是   	| 就诊ID   													|				|
| 新处方prescription        	|  			|    	| 		|OK镜处方   													|				|
| orth_od_brand_id 			| String    |      	| 否   	| OD-品牌id，右眼镜片品牌id									|				|
| orth_od_brand    			| String    |      	| 否   	| OD-品牌，右眼镜片品牌名称										|				|
| orth_od_rem      			| String    |      	| 否   	| OD-备注                									|				|
| orth_od_paras    			| ObjectList|      	| 否   	| OD-属性列表             									|				|
| orth_os_brand_id 			| String    |      	| 否   	| OS-品牌id，左眼镜片品牌id									|				|
| orth_os_brand    			| String    |      	| 否   	| OS-品牌，左眼镜片品牌名称										|				|
| orth_os_rem      			| String    |      	| 否   	| OS-备注                 									|				|
| orth_os_paras    			| ObjectList|      	| 否   	| OS-属性列表              									|				|
| 随访时间next_follow_up_time|  			|    	| 		| 病历信息表 													|				|
| next_follow_up_time      	| Integer 	|      	| 否   	| 下次随访时间   	  		                               	    |             	|
| next_follow_up_time_unit 	| Integer 	|      	| 否   	| 下次随访时间单位<br/>1-天;<br/>2-周;<br/>3-月;<br/>4-年 		|             	|
| emr_followup_type        	| Integer 	|      	| 是   	| 随访时间类型；0:定期;1:不定期                           		| WEBV1.2.3.2 	|
| emr_followup_notfixed    	| String  	|   24 	| 否   	| 不定期随访时间                                          	| WEBV1.2.3.2 	|
| 模板数据template_data      |  			|    	|		| 模板 														|				|
| 矫正视力                   |         	|      	|       |                                                           |				|
| corrected_vision_od_vision| String  	|      	| 是   	| od视力                                                 	|				|
| corrected_vision_os_vision| String  	|      	| 是   	| os视力                                                  	|				|
| 戴镜验光                   |         	|      	|       |                                                           |				|
| optometry_od_ball         | String  	|      	| 否   	| od球镜                                                  	|				|
| optometry_od_column       | String  	|      	| 否   	| od柱镜                                                    	|				|
| optometry_od_axis         | String  	|      	| 否   	| od轴向                                                		|				|
| optometry_od_vision       | String  	|      	| 否   	| od视力                                                  	|				|
| optometry_os_ball         | String  	|      	| 否   	| os球镜                                                  	|				|
| optometry_os_column       | String  	|      	| 否   	| os柱镜                                                   	|				|
| optometry_os_axis         | String  	|      	| 否   	| os轴向                                                   	|				|
| optometry_os_vision       | String  	|      	| 否   	| os视力                                                  	|				|
| 镜片适配                   |         	|      	|       |                                                          	|				|
| base_arc_od               | Integer 	|      	| 是   	| 基弧区od:<br/>1-小;<br/>2-适中;<br/>3-大                  	|				|
| base_arc_os               | Integer 	|      	| 是   	| 基弧区os:<br/>1-小;<br/>2-适中;<br/>3-大                   	|				|
| center_contact_od         | Integer 	|      	| 是   	| 中心接触od:<br/>1-淡;<br/>2-适中;<br/>3-深                	|				|
| center_contact_os         | Integer 	|      	| 是   	| 中心接触os:<br/>1-淡;<br/>2-适中;<br/>3-深                	|				|
| reverse_arc_od            | Integer 	|      	| 是   	| 反转弧od:<br/>1-陡;<br/>2-好;<br/>3-平;                   	|				|
| reverse_arc_os            | Integer 	|      	| 是   	| 反转弧os:<br/>1-陡;<br/>2-好;<br/>3-平;                   	|				|
| fixed_arc_od              | Integer 	|      	| 是   	| 定点弧od:<br/>1-陡;<br/>2-好;<br/>3-平;                   	|				|
| fixed_arc_os              | Integer 	|      	| 是   	| 定点弧os:<br/>1-陡;<br/>2-好;<br/>3-平;                   	|				|
| blinking_lens_position_ od| Integer 	|      	| 是   	| 眨眼时镜片位置od:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; ||
| blinking_lens_position_ os| Integer 	|      	| 是   	| 眨眼时镜片位置os:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; ||
| blinked_lens_position_ od | Integer 	|      	| 是   	| 眨眼后镜片位置od:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; ||
| blinked_lens_position_ os | Integer 	|      	| 是   	| 眨眼后镜片位置os:<br/>1-中心;<br/>2-上;<br/>3-下;<br/>4-偏鼻侧;<br/>5-偏颞侧; ||
| peripheral_arcs_od        | Integer 	|      	| 是   	| 周边弧od:<br/>1-窄;<br/>2-好;<br/>3-宽;                    	|				|
| peripheral_arcs_os        | Integer 	|      	| 是   	| 周边弧os:<br/>1-窄;<br/>2-好;<br/>3-宽;               		|				|
| activity_od               | Integer 	|      	| 是   	| 活动度od:<br/>1-偏大;<br/>2-正常;<br/>3-偏小             	|				|
| activity_os               | Integer 	|      	| 是   	| 活动度os:<br/>1-偏大;<br/>2-正常;<br/>3-偏小              	|				|
| handle                    | String  	|		| 否   	| 处理                                                 		|				|
| is_need_new_prescription  | Integer 	|		| 否   	| 是否需要新处方:<br/>1-否;<br/>2-是;                        	|				|
| patient_guide             | String  	|		| 否   	| 患者戴镜指南:<br/>1-戴镜、摘镜操作;<br/>2-镜片护理方法;        	|				|



###### 最终处方品牌属性参数

说明
1. 结构为ObjectList

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| para_prop_id   | Long   | 是    | 属性码ID |
| para_prop_name | String | 是    | 属性名称  |
| para_choi_id   | Long   | 否    | 属性值ID |
| para_choi_code | String | 否    | 属性值代码 |
| para_value     | String | 否    | 属性值   |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 专科检查-OK镜复查获取

```http
[GET]/treat_service/speciality_check/rtho_k_lenses/recheck
```

#### 修改更新记录

|  对应业务 	| 说明 						|
|-----------|---------------------		|
| V1.2.3 	| 新增 						|
| V1.2.3.1 	| 新增本次随访时间及随访次数 	|
| V1.2.3.2 	| 新增不定期随访时间 			|

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数

| 参数名                              | 类型         | 必填   | 说明                                       |
| -------------------------------- | ---------- | ---- | ---------------------------------------- |
| trea_id                          | String     | 是    | 就诊ID                                     |
| 主觉验光subjective                   |            |      | 主觉验光表表                                   |
| data_od_sphere                   | String     | 否    | 主觉验光OD-球镜                                |
| data_od_cylinder                 | String     | 否    | 主觉验光OD-柱镜                                |
| data_od_axis                     | String     | 否    | 主觉验光OD-轴向                                |
| data_od_prism                    | String     | 否    | 主觉验光OD-棱镜                                |
| data_od_vision                   | String     | 否    | 主觉验光OD-视力                                |
| data_od_memo                     | String     | 否    | 主觉验光OD-备注                                |
| data_os_sphere                   | String     | 否    | 主觉验光OS-球镜                                |
| data_os_cylinder                 | String     | 否    | 主觉验光OS-柱镜                                |
| data_os_axis                     | String     | 否    | 主觉验光OS-轴向                                |
| data_os_prism                    | String     | 否    | 主觉验光OS-棱镜                                |
| data_os_vision                   | String     | 否    | 主觉验光OS-视力                                |
| data_os_memo                     | String     | 否    | 主觉验光OS-备注                                |
| 角膜曲率corneal_curvature            |            |      | 角膜曲率表                                    |
| corneal_od_cliffy                | String     | 否    | 右眼陡峭                                     |
| corneal_od_flat                  | String     | 否    | 右眼平坦                                     |
| corneal_od_axis                  | String     | 否    | 右眼轴向                                     |
| corneal_os_cliffy                | String     | 否    | 左眼陡峭                                     |
| corneal_os_flat                  | String     | 否    | 左眼平坦                                     |
| corneal_os_axis                  | String     | 否    | 左眼轴向                                     |
| 新处方prescription                  |            |      | OK镜处方                                    |
| orth_od_brand_id                 | String     | 否    | OD-品牌id，右眼镜片品牌id                         |
| orth_od_brand                    | String     | 否    | OD-品牌，右眼镜片品牌名称                           |
| orth_od_rem                      | String     | 否    | OD-备注                                    |
| orth_od_paras                    | ObjectList | 否    | OD-属性列表                                  |
| orth_os_brand_id                 | String     | 否    | OS-品牌id，左眼镜片品牌id                         |
| orth_os_brand                    | String     | 否    | OS-品牌，左眼镜片品牌名称                           |
| orth_os_rem                      | String     | 否    | OS-备注                                    |
| orth_os_paras                    | ObjectList | 否    | OS-属性列表                                  |
| 随访时间next_follow_up_time          |            |      | 病历信息表                                    |
| next_follow_up_time              | Integer    | 是    | 下次随访时间                                   |
| next_follow_up_time_unit         | Integer    | 是    | 下次随访时间单位<br/>1-天;<br/>2-周;<br/>3-月;<br/>4-年 |
| emr_followup_type                | Integer    | 是    | 随访时间类型；0:定期;1:不定期                        |
| emr_followup_notfixed            | String     | 否    | 不定期随访时间                                  |
| 模板数据template_data                |            |      | 模板数据                                     |
| follow_up_time                   | Integer    | 是    | 随访时间选项:<br/>1-一周;<br/>2-1月;<br/>3-3月;<br/>4-6月;<br/>5-12月;<br/>6-不定期; |
| follow_up_time_custom            | String     | 否    | 随访自定义项，选6时有效                             |
| recheck_times                    | Integer    | 否    | 第几次复查                                    |
| bare_vision_od                   | String     | 否    | 裸眼视力OD                                   |
| bare_vision_os                   | String     | 否    | 裸眼视力OS                                   |
| corneal_topography_steep_od      | String     | 否    | 角膜地形图陡峭OD                                |
| corneal_topography_flat_od       | String     | 否    | 角膜地形图平坦OD                                |
| corneal_topography_axis_od       | String     | 否    | 角膜地形图轴向OD                                |
| corneal_topography_steep_os      | String     | 否    | 角膜地形图陡峭OS                                |
| corneal_topography_flat_os       | String     | 否    | 角膜地形图平坦OS                                |
| corneal_topography_axis_os       | String     | 否    | 角膜地形图轴向OS                                |
| iop_od                           | String     | 否    | 眼压OD                                     |
| iop_os                           | String     | 否    | 眼压OS                                     |
| eye_axis_od                      | String     | 否    | 眼轴OD                                     |
| eye_axis_os                      | String     | 否    | 眼轴OS                                     |
| corneal_endothelium_od           | String     | 否    | 角膜内皮OD                                   |
| corneal endothelium_os           | String     | 否    | 角膜内皮OS                                   |
| pupil_diameter_od                | String     | 否    | HVID/瞳孔直径OD                              |
| pupil_diameter_os                | String     | 否    | HVID/瞳孔直径OS                              |
| corneal_thickness_od             | String     | 否    | 角膜厚度OD                                   |
| corneal_thickness_os             | String     | 否    | 角膜厚度OS                                   |
| remark                           | String     | 否    | 备注                                       |
| epithelial_edema_od              | Integer    | 否    | 眼部裂隙灯检查-上皮水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_od                 | Integer    | 否    | 眼部裂隙灯检查-微囊od;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_od                   | Integer    | 否    | 眼部裂隙灯检查-角膜点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_od             | Integer    | 否    | 眼部裂隙灯检查-3、9点染od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_od                | Integer    | 否    | 眼部裂隙灯检查-角膜基质od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_od    | Integer    | 否    | 眼部裂隙灯检查-角膜新生血管od;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_od             | Integer    | 否    | 眼部裂隙灯检查-角膜缘充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_od | Integer    | 否    | 眼部裂隙灯检查-球结膜充血od;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_od     | Integer    | 否    | 眼部裂隙灯检查-球结膜水肿od;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_od          | Integer    | 否    | 眼部裂隙灯检查-脸板结膜异常od;<br/>0;<br/>1;<br/>2;<br/>3; |
| epithelial_edema_os              | Integer    | 否    | 眼部裂隙灯检查-上皮水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| micro_capsule_os                 | Integer    | 否    | 眼部裂隙灯检查-微囊os;<br/>0;<br/>1;<br/>2;<br/>3; |
| dyed_cornea_os                   | Integer    | 否    | 眼部裂隙灯检查-角膜点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| three_nine_cornea_os             | Integer    | 否    | 眼部裂隙灯检查-3、9点染os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_stroma_os                | Integer    | 否    | 眼部裂隙灯检查-角膜基质os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_neovascularization_os    | Integer    | 否    | 眼部裂隙灯检查-角膜新生血管os;<br/>0;<br/>1;<br/>2;<br/>3; |
| corneal_hyperemia_os             | Integer    | 否    | 眼部裂隙灯检查-角膜缘充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctiva_hyperremia_os | Integer    | 否    | 眼部裂隙灯检查-球结膜充血os;<br/>0;<br/>1;<br/>2;<br/>3; |
| bulbar_conjunctival_edema_os     | Integer    | 否    | 眼部裂隙灯检查-球结膜水肿os;<br/>0;<br/>1;<br/>2;<br/>3; |
| conjunctival_anomaly_os          | Integer    | 否    | 眼部裂隙灯检查-脸板结膜异常os;<br/>0;<br/>1;<br/>2;<br/>3; |
| disk_od                          | String     | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_od                            | String     | 否    | 眼底检查-C/D od;常规时默认为：0.3                   |
| rim_od                           | String     | 否    | 眼底检查-盘沿od;常规时默认为：粉红色、清                   |
| peripheral_od                    | String     | 否    | 眼底检查-外周od;常规时默认为：清晰                      |
| av_od                            | String     | 否    | 眼底检查-A/V od;常规时默认为：2:3                   |
| macular_od                       | String     | 否    | 眼底检查-黄斑od;常规时默认为：中心凹反光可见                 |
| disk_os                          | String     | 否    | 眼底检查-视盘od;常规时默认为：透明、无混浊                  |
| cd_os                            | String     | 否    | 眼底检查-C/D os;常规时默认为：0.3                   |
| rim_os                           | String     | 否    | 眼底检查-盘沿os;常规时默认为：粉红色、清                   |
| peripheral_os                    | String     | 否    | 眼底检查-外周os;常规时默认为：清晰                      |
| av_os                            | String     | 否    | 眼底检查-A/V os;常规时默认为：2:3                   |
| macular_os                       | String     | 否    | 眼底检查-黄斑os;常规时默认为：中心凹反光可见                 |




###### 最终处方品牌属性参数

说明
1. 结构为ObjectList

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| para_prop_id   | Long   | 是    | 属性码ID |
| para_prop_name | String | 是    | 属性名称  |
| para_choi_id   | Long   | 否    | 属性值ID |
| para_choi_code | String | 否    | 属性值代码 |
| para_value     | String | 否    | 属性值   |




### 专科检查-OK镜复查保存

```http
[POST]/treat_service/speciality_check/rtho_k_lenses/recheck
```

#### 修改更新记录

|  对应业务 	| 说明 					|
|-----------|---------------------	|
| V1.2.3 	| 新增 					|
| V1.2.3.1 	| 新增本次随访时间及随访次数|
| V1.2.3.2 	| 新增不定期随访数据类型 	|

#### 请求报文参数

|          参数名          	|   类型  	| 长度 	| 必填 	|                           说明                          	|  变更         	|
|--------------------------	|---------	|------	|------	|---------------------------------------------------------	|-------------	|
| trea_id            		| String 	|		| 是   	| 就诊ID   													|				|
| 主觉验光subjective         |  			|   	|		| 主觉验光表表 												|				|
| data_od_sphere   			| String 	|		| 否   	| 主觉验光OD-球镜 											|				|
| data_od_cylinder 			| String 	|		| 否   	| 主觉验光OD-柱镜 											|				|
| data_od_axis     			| String 	|		| 否   	| 主觉验光OD-轴向 											|				|
| data_od_prism    			| String 	|		| 否   	| 主觉验光OD-棱镜 											|				|
| data_od_vision   			| String 	|		| 否   	| 主觉验光OD-视力 											|				|
| data_od_memo     			| String 	|		| 否   	| 主觉验光OD-备注 											|				|
| data_os_sphere   			| String 	|		| 否   	| 主觉验光OS-球镜 											|				|
| data_os_cylinder 			| String 	|		| 否   	| 主觉验光OS-柱镜 											|				|
| data_os_axis     			| String 	|		| 否   	| 主觉验光OS-轴向 											|				|
| data_os_prism    			| String 	|		| 否   	| 主觉验光OS-棱镜 											|				|
| data_os_vision   			| String 	|		| 否   	| 主觉验光OS-视力 											|				|
| data_os_memo     			| String 	|		| 否   	| 主觉验光OS-备注 											|				|
| 角膜曲率corneal_curvature  |  			|    	| 		|	角膜曲率表 												|				|
| corneal_od_cliffy    		| String 	|		| 否   	| 右眼陡峭 													|				|
| corneal_od_flat      		| String 	|		| 否   	| 右眼平坦 													|				|
| corneal_od_axis      		| String 	|		| 否   	| 右眼轴向 													|				|
| corneal_os_cliffy    		| String 	|		| 否   	| 左眼陡峭 													|				|
| corneal_os_flat      		| String 	|		| 否   	| 左眼平坦 													|				|
| corneal_os_axis      		| String 	|		| 否   	| 左眼轴向 													|				|
| 新处方prescription        	|  			|    	|		| OK镜处方   												|				|
| orth_od_brand_id 			| String    |		| 否   	| OD-品牌id，右眼镜片品牌id									|				|
| orth_od_brand    			| String    |		| 否   	| OD-品牌，右眼镜片品牌名称 									|				|
| orth_od_rem      			| String    |		| 否   	| OD-备注                 									|				|
| orth_od_paras    			| ObjectList|		| 否   	| OD-属性列表              									|				|
| orth_os_brand_id 			| String    |		| 否   	| OS-品牌id，左眼镜片品牌id 									|				|
| orth_os_brand    			| String    |		| 否   	| OS-品牌，左眼镜片品牌名称 									|				|
| orth_os_rem      			| String    |		| 否   	| OS-备注                  									|				|
| orth_os_paras    			| ObjectList|		| 否   	| OS-属性列表              									|				|
| 随访时间next_follow_up_time|  			|    	| 		| 病历信息表 													|				|
| next_follow_up_time      	| Integer 	|      	| 否   	| 下次随访时间   	  		                               	    |             	|
| next_follow_up_time_unit 	| Integer 	|      	| 否   	| 下次随访时间单位<br/>1-天;<br/>2-周;<br/>3-月;<br/>4-年 		|             	|
| emr_followup_type        	| Integer 	|      	| 是   	| 随访时间类型；0:定期;1:不定期                           		| WEBV1.2.3.2 	|
| emr_followup_notfixed    	| String  	|   24 	| 否   	| 不定期随访时间                                          	| WEBV1.2.3.2 	|
| 模板数据template_data      |  			|    	| 		| 模板数据 													|				|
| follow_up_time            | Integer 	|      	| 是   	| 随访时间选项:<br/>1-一周;<br/>2-1月;<br/>3-3月;<br/>4-6月;<br/>5-12月;<br/>6-不定期; ||
| follow_up_time_custom     | String  	|      	| 否   	| 随访自定义项，选6时有效                                      |				|
| recheck_times             | Integer 	|      	| 否   	| 第几次复查                                                 	|				|
| bare_vision_od            | String  	|      	| 否   	| 裸眼视力OD                                                 |				|
| bare_vision_os            | String  	|      	| 否   	| 裸眼视力OS                                                 |				|
| corneal_topography_steep_od| String  	|      	| 否   	| 角膜地形图陡峭OD                                           	|				|
| corneal_topography_flat_od| String  	|      	| 否   	| 角膜地形图平坦OD                                           	|				|
| corneal_topography_axis_od| String  	|      	| 否   	| 角膜地形图轴向OD                                           	|				|
| corneal_topography_steep_os| String  	|      	| 否   	| 角膜地形图陡峭OS                                           	|				|
| corneal_topography_flat_os| String  	|      	| 否   	| 角膜地形图平坦OS                                           	|				|
| corneal_topography_axis_os| String  	|      	| 否   	| 角膜地形图轴向OS                                           	|				|
| iop_od                    | String  	|      	| 否   	| 眼压OD                                                    	|				|
| iop_os                    | String  	|      	| 否   	| 眼压OS                                                    	|				|
| eye_axis_od               | String  	|      	| 否   	| 眼轴OD                                                    	|				|
| eye_axis_os               | String  	|      	| 否   	| 眼轴OS                                                    	|				|
| corneal_endothelium_od    | String  	|      	| 否   	| 角膜内皮OD                                                 	|				|
| corneal endothelium_os    | String  	|      	| 否   	| 角膜内皮OS                                                 	|				|
| pupil_diameter_od         | String  	|      	| 否   	| HVID/瞳孔直径OD                                            	|				|
| pupil_diameter_os         | String  	|      	| 否   	| HVID/瞳孔直径OS                                            	|				|
| corneal_thickness_od      | String  	|      	| 否   	| 角膜厚度OD                                                 	|				|
| corneal_thickness_os      | String  	|      	| 否   	| 角膜厚度OS                                                 	|				|
| remark                    | String  	|      	| 否   	| 备注                                                      	|				|
| epithelial_edema_od       | Integer 	|      	| 否   	| 眼部裂隙灯检查-上皮水肿od;<br/>0;<br/>1;<br/>2;<br/>3;     	|				|
| micro_capsule_od          | Integer 	|      	| 否   	| 眼部裂隙灯检查-微囊od;<br/>0;<br/>1;<br/>2;<br/>3;         	|				|
| dyed_cornea_od            | Integer 	|      	| 否   	| 眼部裂隙灯检查-角膜点染od;<br/>0;<br/>1;<br/>2;<br/>3;     	|				|
| three_nine_cornea_od      | Integer 	|      	| 否   	| 眼部裂隙灯检查-3、9点染od;<br/>0;<br/>1;<br/>2;<br/>3;     	|				|
| corneal_stroma_od         | Integer 	|      	| 否   	| 眼部裂隙灯检查-角膜基质od;<br/>0;<br/>1;<br/>2;<br/>3;     	|				|
| corneal_neovascularization_od| Integer|      	| 否  	| 眼部裂隙灯检查-角膜新生血管od;<br/>0;<br/>1;<br/>2;<br/>3; 	|				|
| corneal_hyperemia_od      | Integer 	|      	| 否   	| 眼部裂隙灯检查-角膜缘充血od;<br/>0;<br/>1;<br/>2;<br/>3;   	|				|
| bulbar_conjunctiva_hyperremia_od| Integer	|   | 否   	| 眼部裂隙灯检查-球结膜充血od;<br/>0;<br/>1;<br/>2;<br/>3;   	|				|
| bulbar_conjunctival_edema_od| Integer	|      	| 否   	| 眼部裂隙灯检查-球结膜水肿od;<br/>0;<br/>1;<br/>2;<br/>3;   	|				|
| conjunctival_anomaly_od   | Integer 	|      	| 否   	| 眼部裂隙灯检查-脸板结膜异常od;<br/>0;<br/>1;<br/>2;<br/>3; 	|				|
| epithelial_edema_os       | Integer 	|      	| 否   	| 眼部裂隙灯检查-上皮水肿os;<br/>0;<br/>1;<br/>2;<br/>3;     	|				|
| micro_capsule_os          | Integer 	|      	| 否   	| 眼部裂隙灯检查-微囊os;<br/>0;<br/>1;<br/>2;<br/>3;         	|				|
| dyed_cornea_os            | Integer 	|      	| 否   	| 眼部裂隙灯检查-角膜点染os;<br/>0;<br/>1;<br/>2;<br/>3;     	|				|
| three_nine_cornea_os      | Integer 	|      	| 否   	| 眼部裂隙灯检查-3、9点染os;<br/>0;<br/>1;<br/>2;<br/>3;     	|				|
| corneal_stroma_os         | Integer 	|      	| 否   	| 眼部裂隙灯检查-角膜基质os;<br/>0;<br/>1;<br/>2;<br/>3;     	|				|
| corneal_neovascularization_os| Integer|      	| 否   	| 眼部裂隙灯检查-角膜新生血管os;<br/>0;<br/>1;<br/>2;<br/>3; 	|				|
| corneal_hyperemia_os      | Integer 	|      	| 否   	| 眼部裂隙灯检查-角膜缘充血os;<br/>0;<br/>1;<br/>2;<br/>3;   	|				|
| bulbar_conjunctiva_hyperremia_os| Integer	|   | 否   	| 眼部裂隙灯检查-球结膜充血os;<br/>0;<br/>1;<br/>2;<br/>3;   	|				|
| bulbar_conjunctival_edema_os| Integer	|	 	| 否   	| 眼部裂隙灯检查-球结膜水肿os;<br/>0;<br/>1;<br/>2;<br/>3;   	|				|
| conjunctival_anomaly_os   | Integer 	|		| 否   	| 眼部裂隙灯检查-脸板结膜异常os;<br/>0;<br/>1;<br/>2;<br/>3; 	|				|
| disk_od                   | String  	|		| 否   	| 眼底检查-视盘od;常规时默认为：透明、无混浊                 		|				|
| cd_od                     | String  	|		| 否   	| 眼底检查-C/D od;常规时默认为：0.3                          	|				|
| rim_od                    | String  	|		| 否   	| 眼底检查-盘沿od;常规时默认为：粉红色、清                   		|				|
| peripheral_od             | String  	|		| 否   	| 眼底检查-外周od;常规时默认为：清晰                         	|				|
| av_od                     | String  	|		| 否   	| 眼底检查-A/V od;常规时默认为：2:3                          	|				|
| macular_od                | String  	|		| 否   	| 眼底检查-黄斑od;常规时默认为：中心凹反光可见               		|				|
| disk_os                   | String  	|		| 否   	| 眼底检查-视盘od;常规时默认为：透明、无混浊                 		|				|
| cd_os                     | String  	|		| 否   	| 眼底检查-C/D os;常规时默认为：0.3                          	|				|
| rim_os                    | String  	|		| 否   	| 眼底检查-盘沿os;常规时默认为：粉红色、清                   		|				|
| peripheral_os             | String  	|		| 否   	| 眼底检查-外周os;常规时默认为：清晰                         	|				|
| av_os                     | String  	|		| 否   	| 眼底检查-A/V os;常规时默认为：2:3                          	|				|
| macular_os                | String  	|		| 否   	| 眼底检查-黄斑os;常规时默认为：中心凹反光可见               		|				|




###### 最终处方品牌属性参数

说明
1. 结构为ObjectList

| 参数名            | 类型     | 必填   | 说明    |
| -------------- | ------ | ---- | ----- |
| para_prop_id   | Long   | 是    | 属性码ID |
| para_prop_name | String | 是    | 属性名称  |
| para_choi_id   | Long   | 否    | 属性值ID |
| para_choi_code | String | 否    | 属性值代码 |
| para_value     | String | 否    | 属性值   |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |




##专科检查-斜弱视


### 专科检查-斜弱视获取

```http
[GET]/treat_service/speciality_check/oblique_amblyopia
```

#### 修改更新记录

| 对应业务        | 说明                                |
| ----------- | --------------------------------- |
| V1.2.3      | 新增                                |
| WEBV1.2.3.2 | 眼球震颤数据改为独立表存储、新加角膜映光点备注，新增马氏杆+三菱镜 |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |


#### 回复报文参数

| 参数名                                 | 类型      | 必填   | 说明                                       |
| ----------------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                             | String  | 是    | 就诊ID                                     |
| 基础检查通用数据baseline_exam               |         |      | 基础检查通用数据表                                |
| base_ht_horizontal                  | String  | 否    | 角膜映光点-水平                                 |
| base_ht_vertical_type               | Integer | 是    | 角膜映光点-垂直方向:<br/>1-R/L;<br/>2-L/R         |
| base_ht_vertical                    | String  | 否    | 角膜映光点-垂直                                 |
| base_npc_ttn                        | Integer | 否    | 集合近点-TTN;to the nose;0:未选中（破裂点、恢复点可编辑）；1:选中; |
| base_npc_break                      | String  | 否    | 集合近点-破裂点                                 |
| base_npc_restore                    | String  | 否    | 集合近点-恢复点                                 |
| base_amp_type                       | Integer | 是    | 调节幅度-方法:<br/>1-移近法;<br/>2-负镜片法;<br/>3-移近/移远法 |
| base_amp_od_cm                      | String  | 否    | 调节幅度-OD                                  |
| base_amp_od                         | String  | 否    | 调节幅度-OD                                  |
| base_amp_os_cm                      | String  | 否    | 调节幅度-OS                                  |
| base_amp_os                         | String  | 否    | 调节幅度-OS                                  |
| base_amp_ou_cm                      | String  | 否    | 调节幅度-OU                                  |
| base_amp_ou                         | String  | 否    | 调节幅度-OU                                  |
| 模板数据template_data                   |         |      | 模板数据                                     |
| ref5m_degrees_sc                    | String  | 否    | 遮盖试验+三棱镜REF远距离棱镜度SC                      |
| ref5m_vertical_sc_type              | Integer | 否    | 遮盖试验+三棱镜REF远距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| ref5m_vertical_sc                   | String  | 否    | 遮盖试验+三棱镜REF远距离垂直SC                       |
| ref5m_degrees_cc                    | String  | 否    | 遮盖试验+三棱镜REF远距离棱镜度CC                      |
| ref5m_vertical_cc_type              | Integer | 否    | 遮盖试验+三棱镜REF远距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| ref5m_vertical_cc                   | String  | 否    | 遮盖试验+三棱镜REF远距离垂直CC                       |
| ref33cm_degrees_sc                  | String  | 否    | 遮盖试验+三棱镜REF近距离棱镜度SC                      |
| ref33cm_vertical_sc_type            | Integer | 否    | 遮盖试验+三棱镜REF近距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| ref33cm_vertical_sc                 | String  | 否    | 遮盖试验+三棱镜REF近距离垂直SC                       |
| ref33cm_degrees_cc                  | String  | 否    | 遮盖试验+三棱镜REF近距离棱镜度CC                      |
| ref33cm_vertical_cc_type            | Integer | 否    | 遮盖试验+三棱镜REF近距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| ref33cm_vertical_cc                 | String  | 否    | 遮盖试验+三棱镜REF近距离垂直CC                       |
| lef5m_degrees_sc                    | String  | 否    | 遮盖试验+三棱镜LEF远距离棱镜度SC                      |
| prism_lef5m_vertical_sc_type        | Integer | 否    | 遮盖试验+三棱镜LEF远距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| prism_lef5m_vertical_sc             | String  | 否    | 遮盖试验+三棱镜LEF远距离垂直SC                       |
| lef5m_degrees_cc                    | String  | 否    | 遮盖试验+三棱镜LEF远距离棱镜度CC                      |
| prism_lef5m_vertical_cc_type        | Integer | 否    | 遮盖试验+三棱镜LEF远距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| prism_lef5m_vertical_cc             | String  | 否    | 遮盖试验+三棱镜LEF远距离垂直CC                       |
| lef33cm_degrees_sc                  | String  | 否    | 遮盖试验+三棱镜LEF近距离棱镜度SC                      |
| lef33cm_vertical_sc_type            | Integer | 否    | 遮盖试验+三棱镜LEF近距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| lef33cm_vertical_sc                 | String  | 否    | 遮盖试验+三棱镜LEF近距离垂直SC                       |
| lef33cm_degrees_cc                  | String  | 否    | 遮盖试验+三棱镜LEF近距离棱镜度CC                      |
| lef33cm_vertical_cc_type            | Integer | 否    | 遮盖试验+三棱镜LEF近距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| lef33cm_vertical_cc                 | String  | 否    | 遮盖试验+三棱镜LEF近距离垂直CC                       |
| 马氏杆+三棱镜                             |         |      |                                          |
| maddox_ref5m_degrees_sc             | String  | 否    | 马氏杆+三棱镜REF远距离棱镜度SC                       |
| maddox_ref5m_vertical_sc_type       | Integer | 否    | 马氏杆+三棱镜REF远距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| maddox_ref5m_vertical_sc            | String  | 否    | 马氏杆+三棱镜REF远距离垂直SC                        |
| maddox_ref5m_degrees_cc             | String  | 否    | 马氏杆+三棱镜REF远距离棱镜度CC                       |
| maddox_ref5m_vertical_cc_type       | Integer | 否    | 马氏杆+三棱镜REF远距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| maddox_ref5m_vertical_cc            | String  | 否    | 马氏杆+三棱镜REF远距离垂直CC                        |
| maddox_ref33cm_degrees_sc           | String  | 否    | 马氏杆+三棱镜REF近距离棱镜度SC                       |
| maddox_ref33cm_vertical_sc_type     | Integer | 否    | 马氏杆+三棱镜REF近距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| maddox_ref33cm_vertical_sc          | String  | 否    | 马氏杆+三棱镜REF近距离垂直SC                        |
| maddox_ref33cm_degrees_cc           | String  | 否    | 马氏杆+三棱镜REF近距离棱镜度CC                       |
| maddox_ref33cm_vertical_cc_type     | Integer | 否    | 马氏杆+三棱镜REF近距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| maddox_ref33cm_vertical_cc          | String  | 否    | 马氏杆+三棱镜REF近距离垂直CC                        |
| maddox_lef5m_degrees_sc             | String  | 否    | 马氏杆+三棱镜LEF远距离棱镜度SC                       |
| maddox_prism_lef5m_vertical_sc_type | Integer | 否    | 马氏杆+三棱镜LEF远距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| maddox_prism_lef5m_vertical_sc      | String  | 否    | 马氏杆+三棱镜LEF远距离垂直SC                        |
| maddox_lef5m_degrees_cc             | String  | 否    | 马氏杆+三棱镜LEF远距离棱镜度CC                       |
| maddox_prism_lef5m_vertical_cc_type | Integer | 否    | 马氏杆+三棱镜LEF远距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| maddox_prism_lef5m_vertical_cc      | String  | 否    | 马氏杆+三棱镜LEF远距离垂直CC                        |
| maddox_lef33cm_degrees_sc           | String  | 否    | 马氏杆+三棱镜LEF近距离棱镜度SC                       |
| maddox_lef33cm_vertical_sc_type     | Integer | 否    | 马氏杆+三棱镜LEF近距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| maddox_lef33cm_vertical_sc          | String  | 否    | 马氏杆+三棱镜LEF近距离垂直SC                        |
| maddox_lef33cm_degrees_cc           | String  | 否    | 马氏杆+三棱镜LEF近距离棱镜度CC                       |
| maddox_lef33cm_vertical_cc_type     | Integer | 否    | 马氏杆+三棱镜LEF近距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| maddox_lef33cm_vertical_cc          | String  | 否    | 马氏杆+三棱镜LEF近距离垂直CC                        |
| eye_movement_double_safe            | Integer | 否    | 双眼运动安全:<br/>1-SAFE;<br/>2-异常             |
| eye_movement_double_od1             | String  | 否    | 双眼运动OD第一级别(从上到下，从左到右)                    |
| eye_movement_double_od2             | String  | 否    | 双眼运动OD第二级别(从上到下，从左到右)                    |
| eye_movement_double_od3             | String  | 否    | 双眼运动OD第三级别(从上到下，从左到右)                    |
| eye_movement_double_od4             | String  | 否    | 双眼运动OD第四级别(从上到下，从左到右)                    |
| eye_movement_double_od5             | String  | 否    | 双眼运动OD第五级别(从上到下，从左到右)                    |
| eye_movement_double_od6             | String  | 否    | 双眼运动OD第六级别(从上到下，从左到右)                    |
| eye_movement_double_os1             | String  | 否    | 双眼运动OS第一级别(从上到下，从左到右)                    |
| eye_movement_double_os2             | String  | 否    | 双眼运动OS第二级别(从上到下，从左到右)                    |
| eye_movement_double_os3             | String  | 否    | 双眼运动OS第三级别(从上到下，从左到右)                    |
| eye_movement_double_os4             | String  | 否    | 双眼运动OS第四级别(从上到下，从左到右)                    |
| eye_movement_double_os5             | String  | 否    | 双眼运动OS第五级别(从上到下，从左到右)                    |
| eye_movement_double_os6             | String  | 否    | 双眼运动OS第六级别(从上到下，从左到右)                    |
| eye_movement_double_a               | Integer | 否    | 双眼运动A征:<br/>1-阴性(-);<br/>2-阳性(+)         |
| eye_movement_double_v               | Integer | 否    | 双眼运动V征:<br/>1-阴性(-);<br/>2-阳性(+)         |
| eye_movement_single_od              | String  | 否    | 单眼运动OD                                   |
| eye_movement_single_os              | String  | 否    | 单眼运动OS                                   |
| tilted_head_status                  | Integer | 否    | 歪头试验状态:<br/>1-阴性(-);<br/>2-阳性(+)         |
| tilted_head_positive                | String  | 否    | 歪头试验阳性特征:<br/>1-头向右肩部偏斜R/L;<br/>1-头向右肩部偏斜L/R;<br/>1-头向左肩部偏斜R/L;<br/>1-头向左肩部偏斜L/R; |
| compensation_head_status            | Integer | 否    | 代偿头位状态:<br/>1-不存在;<br/>2-存在              |
| compensation_head_face              | String  | 否    | 代偿头位面部位置:<br/>1-面部正位;<br/>2-面部左边转;<br/>3-面部右边转; |
| compensation_head_head              | String  | 否    | 代偿头位头部位置:<br/>1-头部正位;<br/>2-头部向右肩倾斜;<br/>3-头部向左肩倾斜; |
| compensation_head_jaw               | String  | 否    | 代偿头位下巴位置:<br/>1-下巴正位;<br/>2-下巴上抬;<br/>3-下巴内收; |
| nystagmus_status                    | Integer | 否    | 眼球震颤状态:<br/>1-否;<br/>2-是                 |
| nystagmus_middle_status             | Integer | 否    | 眼球震颤中间带状态:<br/>1-不存在;<br/>2-存在           |
| nystagmus_middle_face               | String  | 否    | 眼球震颤中间带面部朝向:<br/>1-面向正前方;<br/>2-面向左前方;<br/>3-面向右前方; |
| nystagmus_middle_head               | String  | 否    | 眼球震颤中间带头部位置:<br/>1-头部正位;<br/>2-头部向右肩倾斜;<br/>3-头部向左肩倾斜; |
| nystagmus_middle_jaw                | String  | 否    | 眼球震颤中间带下巴位置:<br/>1-下巴正位;<br/>2-下巴上抬;<br/>3-下巴内收; |
| nystagmus_value                     | String  | 否    | 眼震值                                      |
| nystagmus_nature                    | Integer | 否    | 震颤性质:<br/>1-冲动型;<br/>2-钟摆型;              |
| nystagmus_ direction                | Integer | 否    | 震颤方向:<br/>1-水平;<br/>2-垂直;<br/>3-旋转;<br/>3-混合; |




### 专科检查-斜弱视保存

```http
[POST]/treat_service/speciality_check/oblique_amblyopia
```

#### 修改更新记录

| 对应业务        | 说明                                |
| ----------- | --------------------------------- |
| V1.2.3      | 新增                                |
| WEBV1.2.3.2 | 眼球震颤数据改为独立表存储、新加角膜映光点备注，新增马氏杆+三菱镜 |

#### 请求报文参数

| 参数名                          | 类型      | 必填   | 说明                                       |
| ---------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                      | String  | 是    | 就诊ID                                     |
| 基础检查通用数据baseline_exam        |         |      | 基础检查通用数据表                                |
| base_ht_horizontal           | String  | 否    | 角膜映光点-水平                                 |
| base_ht_vertical_type        | Integer | 是    | 角膜映光点-垂直方向:<br/>1-R/L;<br/>2-L/R         |
| base_ht_vertical             | String  | 否    | 角膜映光点-垂直                                 |
| base_npc_ttn                 | Integer | 否    | 集合近点-TTN;to the nose;0:未选中（破裂点、恢复点可编辑）；1:选中; |
| base_npc_break               | String  | 否    | 集合近点-破裂点                                 |
| base_npc_restore             | String  | 否    | 集合近点-恢复点                                 |
| base_amp_type                | Integer | 是    | 调节幅度-方法:<br/>1-移近法;<br/>2-负镜片法;<br/>3-移近/移远法 |
| base_amp_od_cm               | String  | 否    | 调节幅度-OD                                  |
| base_amp_od                  | String  | 否    | 调节幅度-OD                                  |
| base_amp_os_cm               | String  | 否    | 调节幅度-OS                                  |
| base_amp_os                  | String  | 否    | 调节幅度-OS                                  |
| base_amp_ou_cm               | String  | 否    | 调节幅度-OU                                  |
| base_amp_ou                  | String  | 否    | 调节幅度-OU                                  |
| 模板数据template_data            |         |      | 模板数据                                     |
| ref5m_degrees_sc             | String  | 否    | 遮盖试验+三棱镜REF远距离棱镜度SC                      |
| ref5m_vertical_sc_type       | Integer | 否    | 遮盖试验+三棱镜REF远距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| ref5m_vertical_sc            | String  | 否    | 遮盖试验+三棱镜REF远距离垂直SC                       |
| ref5m_degrees_cc             | String  | 否    | 遮盖试验+三棱镜REF远距离棱镜度CC                      |
| ref5m_vertical_cc_type       | Integer | 否    | 遮盖试验+三棱镜REF远距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| ref5m_vertical_cc            | String  | 否    | 遮盖试验+三棱镜REF远距离垂直CC                       |
| ref33cm_degrees_sc           | String  | 否    | 遮盖试验+三棱镜REF近距离棱镜度SC                      |
| ref33cm_vertical_sc_type     | Integer | 否    | 遮盖试验+三棱镜REF近距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| ref33cm_vertical_sc          | String  | 否    | 遮盖试验+三棱镜REF近距离垂直SC                       |
| ref33cm_degrees_cc           | String  | 否    | 遮盖试验+三棱镜REF近距离棱镜度CC                      |
| ref33cm_vertical_cc_type     | Integer | 否    | 遮盖试验+三棱镜REF近距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| ref33cm_vertical_cc          | String  | 否    | 遮盖试验+三棱镜REF近距离垂直CC                       |
| lef5m_degrees_sc             | String  | 否    | 遮盖试验+三棱镜LEF远距离棱镜度SC                      |
| prism_lef5m_vertical_sc_type | Integer | 否    | 遮盖试验+三棱镜LEF远距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| prism_lef5m_vertical_sc      | String  | 否    | 遮盖试验+三棱镜LEF远距离垂直SC                       |
| lef5m_degrees_cc             | String  | 否    | 遮盖试验+三棱镜LEF远距离棱镜度CC                      |
| prism_lef5m_vertical_cc_type | Integer | 否    | 遮盖试验+三棱镜LEF远距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| prism_lef5m_vertical_cc      | String  | 否    | 遮盖试验+三棱镜LEF远距离垂直CC                       |
| lef33cm_degrees_sc           | String  | 否    | 遮盖试验+三棱镜LEF近距离棱镜度SC                      |
| lef33cm_vertical_sc_type     | Integer | 否    | 遮盖试验+三棱镜LEF近距离垂直类型SC:<br/>1-R/L;<br/>2-L/R |
| lef33cm_vertical_sc          | String  | 否    | 遮盖试验+三棱镜LEF近距离垂直SC                       |
| lef33cm_degrees_cc           | String  | 否    | 遮盖试验+三棱镜LEF近距离棱镜度CC                      |
| lef33cm_vertical_cc_type     | Integer | 否    | 遮盖试验+三棱镜LEF近距离垂直类型CC:<br/>1-R/L;<br/>2-L/R |
| lef33cm_vertical_cc          | String  | 否    | 遮盖试验+三棱镜LEF近距离垂直CC                       |
| eye_movement_double_safe     | Integer | 否    | 双眼运动安全:<br/>1-SAFE;<br/>2-异常             |
| eye_movement_double_od1      | String  | 否    | 双眼运动OD第一级别(从上到下，从左到右)                    |
| eye_movement_double_od2      | String  | 否    | 双眼运动OD第二级别(从上到下，从左到右)                    |
| eye_movement_double_od3      | String  | 否    | 双眼运动OD第三级别(从上到下，从左到右)                    |
| eye_movement_double_od4      | String  | 否    | 双眼运动OD第四级别(从上到下，从左到右)                    |
| eye_movement_double_od5      | String  | 否    | 双眼运动OD第五级别(从上到下，从左到右)                    |
| eye_movement_double_od6      | String  | 否    | 双眼运动OD第六级别(从上到下，从左到右)                    |
| eye_movement_double_os1      | String  | 否    | 双眼运动OS第一级别(从上到下，从左到右)                    |
| eye_movement_double_os2      | String  | 否    | 双眼运动OS第二级别(从上到下，从左到右)                    |
| eye_movement_double_os3      | String  | 否    | 双眼运动OS第三级别(从上到下，从左到右)                    |
| eye_movement_double_os4      | String  | 否    | 双眼运动OS第四级别(从上到下，从左到右)                    |
| eye_movement_double_os5      | String  | 否    | 双眼运动OS第五级别(从上到下，从左到右)                    |
| eye_movement_double_os6      | String  | 否    | 双眼运动OS第六级别(从上到下，从左到右)                    |
| eye_movement_double_a        | Integer | 否    | 双眼运动A征:<br/>1-阴性(-);<br/>2-阳性(+)         |
| eye_movement_double_v        | Integer | 否    | 双眼运动V征:<br/>1-阴性(-);<br/>2-阳性(+)         |
| eye_movement_single_od       | String  | 否    | 单眼运动OD                                   |
| eye_movement_single_os       | String  | 否    | 单眼运动OS                                   |
| tilted_head_status           | Integer | 否    | 歪头试验状态:<br/>1-阴性(-);<br/>2-阳性(+)         |
| tilted_head_positive         | String  | 否    | 歪头试验阳性特征:<br/>1-头向右肩部偏斜R/L;<br/>1-头向右肩部偏斜L/R;<br/>1-头向左肩部偏斜R/L;<br/>1-头向左肩部偏斜L/R; |
| compensation_head_status     | Integer | 否    | 代偿头位状态:<br/>1-不存在;<br/>2-存在              |
| compensation_head_face       | String  | 否    | 代偿头位面部位置:<br/>1-面部正位;<br/>2-面部左边转;<br/>3-面部右边转; |
| compensation_head_head       | String  | 否    | 代偿头位头部位置:<br/>1-头部正位;<br/>2-头部向右肩倾斜;<br/>3-头部向左肩倾斜; |
| compensation_head_jaw        | String  | 否    | 代偿头位下巴位置:<br/>1-下巴正位;<br/>2-下巴上抬;<br/>3-下巴内收; |
| nystagmus_status             | Integer | 否    | 眼球震颤状态:<br/>1-否;<br/>2-是                 |
| nystagmus_middle_status      | Integer | 否    | 眼球震颤中间带状态:<br/>1-不存在;<br/>2-存在           |
| nystagmus_middle_face        | String  | 否    | 眼球震颤中间带面部朝向:<br/>1-面向正前方;<br/>2-面向左前方;<br/>3-面向右前方; |
| nystagmus_middle_head        | String  | 否    | 眼球震颤中间带头部位置:<br/>1-头部正位;<br/>2-头部向右肩倾斜;<br/>3-头部向左肩倾斜; |
| nystagmus_middle_jaw         | String  | 否    | 眼球震颤中间带下巴位置:<br/>1-下巴正位;<br/>2-下巴上抬;<br/>3-下巴内收; |
| nystagmus_value              | String  | 否    | 眼震值                                      |
| nystagmus_nature             | Integer | 否    | 震颤性质:<br/>1-冲动型;<br/>2-钟摆型;              |
| nystagmus_ direction         | Integer | 否    | 震颤方向:<br/>1-水平;<br/>2-垂直;<br/>3-旋转;<br/>3-混合; |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 历史记录-斜弱视

> [GET]/diag_service/history_special_check/strabismus

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| reco_id | String | 否    | 记录id |

#### 回复报文参数

| 参数名               | 类型         | 必填   | 说明                             |
| ----------------- | ---------- | ---- | ------------------------------ |
| adjust_amplitude  | String     | 否    | 调节幅度                           |
| near_point        | String     | 否    | 集合近点                           |
| compensation_head | String     | 否    | 代偿头位                           |
| compensation_head | String     | 否    | 代偿头位                           |
| ht_otrho          | String     | 否    | 眼位检查                           |
| items             | ObjectList | 否    | 专科检查信息项列表（眼位检查、遮盖实验、眼球运动、歪头试验） |

专科检查信息项列表说明

| 参数名        | 类型     | 必填   | 说明        |
| ---------- | ------ | ---- | --------- |
| item_id    | Long   | 是    | 专科检查信息项id |
| item_key   | String | 是    | 项关键词      |
| item_value | String | 否    | 数据项内容     |
| parent_id  | Long   | 否    | 父项ID      |



##专科检查-双眼视



### 专科检查-双眼视功能首诊/随访获取

```http
[GET]/treat_service/speciality_check/binocular_visual
```

说明
1. 在模板数据中默认保存一个项目 is_first_follow 值为 1;
2. 首诊随访合成一个协议

#### 修改更新记录

| 对应业务        | 说明         |
| ----------- | ---------- |
| V1.2.3      | 新增         |
| WEBV1.2.3.2 | 调节灵活度添加备注框 |

#### 请求报文参数

| 参数名             | 类型      | 必填   | 说明                  |
| --------------- | ------- | ---- | ------------------- |
| trea_id         | String  | 是    | 就诊ID                |
| is_first_follow | Integer | 是    | 随访类型 0未指定 1 首诊 2 随访 |

#### 回复报文参数


| 参数名                                  | 类型         | 必填   | 说明                                       |
| ------------------------------------ | ---------- | ---- | ---------------------------------------- |
| trea_id                              | String     | 是    | 就诊ID                                     |
| is_first_follow                      | Integer    | 是    | 1-首诊;2-随访;                               |
| 随访时间follow_up_time                   |            | 模板   |                                          |
| follow_up_time                       | Integer    | 是    | 双眼视随访时间选项:<br/>1-一周;<br/>2-1月;<br/>3-3月;<br/>4-6月;<br/>5-12月;<br/>6-不定期; |
| follow_up                            | String     | 否    | 双眼视随访                                    |
| 个人史personal_history                  |            |      | 模板                                       |
| history_diagnosis                    | Integer    | 否    | 医疗诊治史:<br/>1-正常;<br/>2-有;                |
| history_diagnosis_list               | String     | 否    | 医疗诊治史列表:<br/>1-过敏史;<br/>2-鼻窦炎;<br/>3-枯草热;<br/>4-眼、口或粘膜干燥症;<br/>5-抽搐或癫痫;<br/>6-昏厥;<br/>7-糖尿病;<br/>8-怀孕;<br/>9-甲状腺功能异常;<br/>10-精神治疗史; |
| visual_training                      | Integer    | 否    | 是否接受过视觉训练:<br/>1-无;<br/>2-有;             |
| visual_training_time                 | String     | 否    | 视觉训练时间，单位周                               |
| is_squint_correction                 | Integer    | 否    | 是否斜视矫正术后                                 |
| squint_correction                    | String     | 否    | 斜视矫正术后情况:<br/>1-间接性外斜视矫正术后;<br/>2-恒定性外斜视矫正术后;<br/>3-急性共同性内科视矫正术后;<br/>4-部分调节性内斜视矫正术后;<br/>5-麻痹性斜视矫正术后; |
| 症状问卷symptom_questionnaire            |            |      | 模板                                       |
| question_01                          | Integer    | 否    | 阅读或近距离工作时你是否觉得眼部疲劳或不适:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_02                          | Integer    | 否    | 阅读或近距离工作时你是否头痛:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_03                          | Integer    | 否    | 阅读或近距离工作时你是否觉得易困乏:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_04                          | Integer    | 否    | 阅读或近距离工作时，你的注意力是否不集中:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_05                          | Integer    | 否    | 你是否对记住读过的东西感到困难:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_06                          | Integer    | 否    | 阅读或近距离工作时是否出现双影:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_07                          | Integer    | 否    | 阅读或近距离工作时你是否觉得文字移动、跳动、游动或在纸面上漂浮:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_08                          | Integer    | 否    | 你是否觉得阅读速度慢:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_09                          | Integer    | 否    | 阅读或近距离工作时你是否眼痛、眼酸:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_10                          | Integer    | 否    | 阅读或近距离工作时有一种眼球牵拉感:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_11                          | Integer    | 否    | 阅读或近距离工作时你是否出现视物模糊或聚焦不准确:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_12                          | Integer    | 否    | 阅读或近距离工作时你是否会出现串行:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_13                          | Integer    | 否    | 阅读或近距离工作时你是否不得不重复读同一行:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_14                          | Integer    | 否    | 你是否回避阅读或近距离工作:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_15                          | Integer    | 否    | 你是否从视远转到视近或从视近转到视远聚焦困难:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_16                          | Integer    | 否    | 阅读疲劳的症状是否在夜晚会更为明显:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| 眼屈光检查-瞳距pd                           |            |      | 框架处方                                     |
| opto_far_pd                          | String     | 否    | 瞳距-远用                                    |
| opto_near_pd                         | String     | 否    | 瞳距-近用                                    |
| opto_od_pd                           | String     | 否    | 瞳距-单眼OD                                  |
| opto_os_pd                           | String     | 否    | 瞳距-单眼OS                                  |
| opto_pd_rem                          | String     | 否    | 瞳距-备注                                    |
| 眼屈光检查-主觉验光subjective                 |            |      | 主觉验光表                                    |
| data_od_sphere                       | String     | 否    | 主觉验光OD-球镜                                |
| data_od_cylinder                     | String     | 否    | 主觉验光OD-柱镜                                |
| data_od_axis                         | String     | 否    | 主觉验光OD-轴向                                |
| data_od_prism                        | String     | 否    | 主觉验光OD-棱镜                                |
| data_od_vision                       | String     | 否    | 主觉验光OD-视力                                |
| data_od_memo                         | String     | 否    | 主觉验光OD-备注                                |
| data_os_sphere                       | String     | 否    | 主觉验光OS-球镜                                |
| data_os_cylinder                     | String     | 否    | 主觉验光OS-柱镜                                |
| data_os_axis                         | String     | 否    | 主觉验光OS-轴向                                |
| data_os_prism                        | String     | 否    | 主觉验光OS-棱镜                                |
| data_os_vision                       | String     | 否    | 主觉验光OS-视力                                |
| data_os_memo                         | String     | 否    | 主觉验光OS-备注                                |
| 视力数据                                 |            |      |                                          |
| data_od_distance_vision              | String     | 否    | 远用OD-视力                                  |
| data_os_distance_vision              | String     | 否    | 远用OS-视力                                  |
| data_od_near_vision                  | String     | 否    | 近用OD-视力                                  |
| data_os_near_vision                  | String     | 否    | 近用OS-视力                                  |
| 其它模板数据                               |            |      |                                          |
| primary_prescription_od_ball         | String     | 否    | 原镜处方OD球镜                                 |
| primary_prescription_od_column       | String     | 否    | 原镜处方OD柱镜                                 |
| primary_prescription_od_axis         | String     | 否    | 原镜处方OD轴向                                 |
| primary_prescription_os_ball         | String     | 否    | 原镜处方OS球镜                                 |
| primary_prescription_os_column       | String     | 否    | 原镜处方OS柱镜                                 |
| primary_prescription_os_axis         | String     | 否    | 原镜处方OS轴向                                 |
| anterior_segment_check_od            | String     | 否    | 眼前节检查OD                                  |
| anterior_segment_check_os            | String     | 否    | 眼前节检查OS                                  |
| fundus_examination_od                | String     | 否    | 眼底检查OD                                   |
| fundus_examination_os                | String     | 否    | 眼底检查OS                                   |
| dominant_eye                         | String     | 否    | 优势眼:<br/>1-OD;<br/>2-OS;                 |
| 调节幅度amp                              |            |      | 基础检查通用数据表                                |
| base_amp_type                        | Integer    | 是    | 调节幅度-方法:<br/>1-移近法;<br/>2-负镜片法;<br/>3-移近/移远法 |
| base_amp_od_cm                       | String     | 否    | 调节幅度-OD                                  |
| base_amp_od                          | String     | 否    | 调节幅度-OD                                  |
| base_amp_os_cm                       | String     | 否    | 调节幅度-OS                                  |
| base_amp_os                          | String     | 否    | 调节幅度-OS                                  |
| base_amp_ou_cm                       | String     | 否    | 调节幅度-OU                                  |
| base_amp_ou                          | String     | 否    | 调节幅度-OU                                  |
| 视功能检查visual_function_test            |            |      | 模板                                       |
| adjust_flexibility                   | String     | 否    | 调节灵活度视标                                  |
| adjust_flexibility_instrument        | String     | 否    | 调节灵活度仪器                                  |
| regulating_activity_od               | String     | 否    | 调节灵活度OD                                  |
| regulating_activity_os               | String     | 否    | 调节灵活度OS                                  |
| regulating_activity_ou               | String     | 否    | 调节灵活度OU                                  |
| regulating_activity_rem              | String     | 否    | 调节灵活度备注                                  |
| regulating_state                     | Integer    | 否    | 调节状态:<br/>1-FCC;<br/>2-MEM               |
| regulating_state_od                  | String     | 否    | 调节状态OD                                   |
| regulating_state_os                  | String     | 否    | 调节状态OS                                   |
| nra_pra_left                         | String     | 否    | NRA/PRA左                                 |
| nra_pra_right                        | String     | 否    | NRA/PRA右                                 |
| near_point                           | Integer    | 否    | 辐辏近点:<br/>1-调节视标;<br/>2-笔尖;<br/>3-红玻璃    |
| near_point_breaking                  | String     | 否    | 辐辏近点破裂点                                  |
| near_point_recovery                  | String     | 否    | 辐辏近点恢复点                                  |
| coverage_test_distance               | String     | 否    | 遮盖实验远距                                   |
| coverage_test_near                   | String     | 否    | 遮盖实验近距                                   |
| horizontal_oblique_quantity_distance | String     | 否    | 水平隐斜量远距                                  |
| horizontal_oblique_quantity_near     | String     | 否    | 水平隐斜量近距                                  |
| vertical_gradient_distance           | String     | 否    | 垂直隐斜量远距                                  |
| vertical_gradient_near               | String     | 否    | 垂直隐斜量近距                                  |
| ac_a_distance_left                   | String     | 否    | AC/A(△/D)远距-阶梯法                          |
| ac_a_near_left                       | String     | 否    | AC/A(△/D)近距-计算法                          |
| worth_distance                       | String     | 否    | Worth 4 dot远距                            |
| worth_near                           | String     | 否    | Worth 4 dot近距                            |
| bi_fuzzy_point_distance              | String     | 否    | 远距BI模糊点                                  |
| bi_breaking_point_distance           | String     | 否    | 远距BI破裂点                                  |
| bi_recovery_point_distance           | String     | 否    | 远距BI恢复点                                  |
| bi_fuzzy_point_near                  | String     | 否    | 近距BI模糊点                                  |
| bi_breaking_point_near               | String     | 否    | 近距BI破裂点                                  |
| bi_recovery_point_near               | String     | 否    | 近距BI恢复点                                  |
| bo_fuzzy_point_distance              | String     | 否    | 远距BO模糊点                                  |
| bo_breaking_point_distance           | String     | 否    | 远距BO破裂点                                  |
| bo_recovery_point_distance           | String     | 否    | 远距BO恢复点                                  |
| bo_fuzzy_point_near                  | String     | 否    | 近距BO模糊点                                  |
| bo_breaking_point_near               | String     | 否    | 近距BO破裂点                                  |
| bo_recovery_point_near               | String     | 否    | 近距BO恢复点                                  |
| flexibility_distance                 | String     | 否    | 聚散灵活度(CPM)远距                             |
| flexibility_near                     | String     | 否    | 聚散灵活度(CPM)近距                             |
| stereoscopic_vision_optec            | String     | 否    | 立体视觉OPTEC3500                            |
| stereoscopic_vision_tno              | String     | 否    | 立体视觉TNO                                  |
| stereoscopic_vision_titmus           | String     | 否    | 立体视觉Titmus                               |
| refractive_correction_program        | String     | 否    | 屈光矫正方案:<br/>1-双光镜;<br/>2-渐变镜;<br/>3-RGP;<br/>4-OK镜;<br/>5-棱镜;<br/>6-普通单光镜;多个使用逗号分隔。 |
| training_program                     | String     | 否    | 训练方案:<br/>1-弱视训练;<br/>2-调节训练;<br/>3-辐辏训练;<br/>4-眼球运动训练;多个使用逗号分隔。 |
| training_program_other               | String     | 否    | 训练方案其他                                   |
| diagnose                             | ObjectList | 否    | 诊断                                       |


##### 诊断

1. 就诊诊断信息表
2. 类型为ObjectList

| 参数名            | 类型      | 必填   | 说明              |
| -------------- | ------- | ---- | --------------- |
| diag_pre_id    | String  | 否    | 前缀ID            |
| diag_pre_name  | String  | 是    | 前缀内容            |
| diag_id        | String  | 否    | 诊断id            |
| diag_name      | String  | 是    | 诊断名称            |
| diag_icd       | String  | 否    | 诊断ICD编码，剑形编码，病因 |
| diag_attach    | String  | 是    | 附加码             |
| diag_sufx_id   | String  | 否    | 后缀ID            |
| diag_sufx_name | String  | 是    | 后缀内容            |
| diag_master    | Integer | 是    | 是否是主诊断;0-不是;1-是 |




### 专科检查-双眼视功能首诊/随访保存

```http
[POST]/treat_service/speciality_check/binocular_visual
```

说明
1. 在模板数据中默认保存一个项目 is_first_follow 值为 1;

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                                  | 类型         | 必填   | 说明                                       |
| ------------------------------------ | ---------- | ---- | ---------------------------------------- |
| trea_id                              | String     | 是    | 就诊ID                                     |
| is_first_follow                      | Integer    | 是    | 随访类型 1 首诊 2 随访                           |
| 随访时间follow_up_time                   |            | 模板   |                                          |
| follow_up_time                       | Integer    | 是    | 双眼视随访时间选项:<br/>1-一周;<br/>2-1月;<br/>3-3月;<br/>4-6月;<br/>5-12月;<br/>6-不定期; |
| follow_up                            | String     | 否    | 双眼视随访                                    |
| is_first_follow                      | Integer    | 是    | 1-首诊;2-随访;这儿固定默认1                        |
| 个人史personal_history                  |            |      | 模板                                       |
| history_diagnosis                    | Integer    | 否    | 医疗诊治史:<br/>1-正常;<br/>2-有;                |
| history_diagnosis_list               | String     | 否    | 医疗诊治史列表:<br/>1-过敏史;<br/>2-鼻窦炎;<br/>3-枯草热;<br/>4-眼、口或粘膜干燥症;<br/>5-抽搐或癫痫;<br/>6-昏厥;<br/>7-糖尿病;<br/>8-怀孕;<br/>9-甲状腺功能异常;<br/>10-精神治疗史; |
| visual_training                      | Integer    | 否    | 是否接受过视觉训练:<br/>1-无;<br/>2-有;             |
| visual_training_time                 | String     | 否    | 视觉训练时间，单位周                               |
| is_squint_correction                 | Integer    | 否    | 是否斜视矫正术后                                 |
| squint_correction                    | String     | 否    | 斜视矫正术后情况:<br/>1-间接性外斜视矫正术后;<br/>2-恒定性外斜视矫正术后;<br/>3-急性共同性内科视矫正术后;<br/>4-部分调节性内斜视矫正术后;<br/>5-麻痹性斜视矫正术后; |
| 症状问卷symptom_questionnaire            |            |      | 模板                                       |
| question_01                          | Integer    | 否    | 阅读或近距离工作时你是否觉得眼部疲劳或不适:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_02                          | Integer    | 否    | 阅读或近距离工作时你是否头痛:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_03                          | Integer    | 否    | 阅读或近距离工作时你是否觉得易困乏:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_04                          | Integer    | 否    | 阅读或近距离工作时，你的注意力是否不集中:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_05                          | Integer    | 否    | 你是否对记住读过的东西感到困难:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_06                          | Integer    | 否    | 阅读或近距离工作时是否出现双影:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_07                          | Integer    | 否    | 阅读或近距离工作时你是否觉得文字移动、跳动、游动或在纸面上漂浮:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_08                          | Integer    | 否    | 你是否觉得阅读速度慢:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_09                          | Integer    | 否    | 阅读或近距离工作时你是否眼痛、眼酸:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_10                          | Integer    | 否    | 阅读或近距离工作时有一种眼球牵拉感:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_11                          | Integer    | 否    | 阅读或近距离工作时你是否出现视物模糊或聚焦不准确:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_12                          | Integer    | 否    | 阅读或近距离工作时你是否会出现串行:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_13                          | Integer    | 否    | 阅读或近距离工作时你是否不得不重复读同一行:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_14                          | Integer    | 否    | 你是否回避阅读或近距离工作:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_15                          | Integer    | 否    | 你是否从视远转到视近或从视近转到视远聚焦困难:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| question_16                          | Integer    | 否    | 阅读疲劳的症状是否在夜晚会更为明显:<br/>1-从不;<br/>2-有时;<br/>3-经常;<br/>4-频繁 |
| 眼屈光检查                                |            |      |                                          |
| opto_far_pd                          | String     | 否    | 瞳距-远用                                    |
| opto_near_pd                         | String     | 否    | 瞳距-近用                                    |
| opto_od_pd                           | String     | 否    | 瞳距-单眼OD                                  |
| opto_os_pd                           | String     | 否    | 瞳距-单眼OS                                  |
| opto_pd_rem                          | String     | 否    | 瞳距-备注                                    |
| 主觉验光                                 |            |      |                                          |
| data_od_sphere                       | String     | 否    | 主觉验光OD-球镜                                |
| data_od_cylinder                     | String     | 否    | 主觉验光OD-柱镜                                |
| data_od_axis                         | String     | 否    | 主觉验光OD-轴向                                |
| data_od_prism                        | String     | 否    | 主觉验光OD-棱镜                                |
| data_od_vision                       | String     | 否    | 主觉验光OD-视力                                |
| data_od_memo                         | String     | 否    | 主觉验光OD-备注                                |
| data_os_sphere                       | String     | 否    | 主觉验光OS-球镜                                |
| data_os_cylinder                     | String     | 否    | 主觉验光OS-柱镜                                |
| data_os_axis                         | String     | 否    | 主觉验光OS-轴向                                |
| data_os_prism                        | String     | 否    | 主觉验光OS-棱镜                                |
| data_os_vision                       | String     | 否    | 主觉验光OS-视力                                |
| data_os_memo                         | String     | 否    | 主觉验光OS-备注                                |
| 视力数据                                 |            |      |                                          |
| data_od_distance_vision              | String     | 否    | 远用OD-视力                                  |
| data_os_distance_vision              | String     | 否    | 远用OS-视力                                  |
| data_od_near_vision                  | String     | 否    | 近用OD-视力                                  |
| data_os_near_vision                  | String     | 否    | 近用OS-视力                                  |
| 其它模板数据                               |            |      |                                          |
| primary_prescription_od_ball         | String     | 否    | 原镜处方OD球镜                                 |
| primary_prescription_od_column       | String     | 否    | 原镜处方OD柱镜                                 |
| primary_prescription_od_axis         | String     | 否    | 原镜处方OD轴向                                 |
| primary_prescription_os_ball         | String     | 否    | 原镜处方OS球镜                                 |
| primary_prescription_os_column       | String     | 否    | 原镜处方OS柱镜                                 |
| primary_prescription_os_axis         | String     | 否    | 原镜处方OS轴向                                 |
| anterior_segment_check_od            | String     | 否    | 眼前节检查OD                                  |
| anterior_segment_check_os            | String     | 否    | 眼前节检查OS                                  |
| fundus_examination_od                | String     | 否    | 眼底检查OD                                   |
| fundus_examination_os                | String     | 否    | 眼底检查OS                                   |
| dominant_eye                         | String     | 否    | 优势眼:<br/>1-OD;<br/>2-OS;                 |
| 调节幅度amp                              |            |      | 基础检查通用数据表                                |
| base_amp_type                        | Integer    | 是    | 调节幅度-方法:<br/>1-移近法;<br/>2-负镜片法;<br/>3-移近/移远法 |
| base_amp_od_cm                       | String     | 否    | 调节幅度-OD                                  |
| base_amp_od                          | String     | 否    | 调节幅度-OD                                  |
| base_amp_os_cm                       | String     | 否    | 调节幅度-OS                                  |
| base_amp_os                          | String     | 否    | 调节幅度-OS                                  |
| base_amp_ou_cm                       | String     | 否    | 调节幅度-OU                                  |
| base_amp_ou                          | String     | 否    | 调节幅度-OU                                  |
| 视功能检查visual_function_test            |            |      | 模板                                       |
| adjust_flexibility                   | String     | 否    | 调节灵活度视标                                  |
| adjust_flexibility_instrument        | String     | 否    | 调节灵活度仪器                                  |
| regulating_activity_od               | String     | 否    | 调节灵活度OD                                  |
| regulating_activity_os               | String     | 否    | 调节灵活度OS                                  |
| regulating_activity_ou               | String     | 否    | 调节灵活度OU                                  |
| regulating_activity_rem              | String     | 否    | 调节灵活度备注                                  |
| regulating_state                     | Integer    | 否    | 调节状态:<br/>1-FCC;<br/>2-MEM               |
| regulating_state_od                  | String     | 否    | 调节状态OD                                   |
| regulating_state_os                  | String     | 否    | 调节状态OS                                   |
| nra_pra_left                         | String     | 否    | NRA/PRA左                                 |
| nra_pra_right                        | String     | 否    | NRA/PRA右                                 |
| near_point                           | Integer    | 否    | 辐辏近点:<br/>1-调节视标;<br/>2-笔尖;<br/>3-红玻璃    |
| near_point_breaking                  | String     | 否    | 辐辏近点破裂点                                  |
| near_point_recovery                  | String     | 否    | 辐辏近点恢复点                                  |
| coverage_test_distance               | String     | 否    | 遮盖实验远距                                   |
| coverage_test_near                   | String     | 否    | 遮盖实验近距                                   |
| horizontal_oblique_quantity_distance | String     | 否    | 水平隐斜量远距                                  |
| horizontal_oblique_quantity_near     | String     | 否    | 水平隐斜量近距                                  |
| vertical_gradient_distance           | String     | 否    | 垂直隐斜量远距                                  |
| vertical_gradient_near               | String     | 否    | 垂直隐斜量近距                                  |
| ac_a_distance_left                   | String     | 否    | AC/A(△/D)远距-阶梯法                          |
| ac_a_near_left                       | String     | 否    | AC/A(△/D)近距-计算法                          |
| worth_distance                       | String     | 否    | Worth 4 dot远距                            |
| worth_near                           | String     | 否    | Worth 4 dot近距                            |
| bi_fuzzy_point_distance              | String     | 否    | 远距BI模糊点                                  |
| bi_breaking_point_distance           | String     | 否    | 远距BI破裂点                                  |
| bi_recovery_point_distance           | String     | 否    | 远距BI恢复点                                  |
| bi_fuzzy_point_near                  | String     | 否    | 近距BI模糊点                                  |
| bi_breaking_point_near               | String     | 否    | 近距BI破裂点                                  |
| bi_recovery_point_near               | String     | 否    | 近距BI恢复点                                  |
| bo_fuzzy_point_distance              | String     | 否    | 远距BO模糊点                                  |
| bo_breaking_point_distance           | String     | 否    | 远距BO破裂点                                  |
| bo_recovery_point_distance           | String     | 否    | 远距BO恢复点                                  |
| bo_fuzzy_point_near                  | String     | 否    | 近距BO模糊点                                  |
| bo_breaking_point_near               | String     | 否    | 近距BO破裂点                                  |
| bo_recovery_point_near               | String     | 否    | 近距BO恢复点                                  |
| flexibility_distance                 | String     | 否    | 聚散灵活度(CPM)远距                             |
| flexibility_near                     | String     | 否    | 聚散灵活度(CPM)近距                             |
| stereoscopic_vision_optec            | String     | 否    | 立体视觉OPTEC3500                            |
| stereoscopic_vision_tno              | String     | 否    | 立体视觉TNO                                  |
| stereoscopic_vision_titmus           | String     | 否    | 立体视觉Titmus                               |
| refractive_correction_program        | String     | 否    | 屈光矫正方案:<br/>1-双光镜;<br/>2-渐变镜;<br/>3-RGP;<br/>4-OK镜;<br/>5-棱镜;<br/>6-普通单光镜;多个使用逗号分隔。 |
| training_program                     | String     | 否    | 训练方案:<br/>1-弱视训练;<br/>2-调节训练;<br/>3-辐辏训练;<br/>4-眼球运动训练;多个使用逗号分隔。 |
| training_program_other               | String     | 否    | 训练方案其他                                   |
| diagnose                             | ObjectList | 否    | 诊断                                       |


##### 诊断

1. 就诊诊断信息表
2. 类型为ObjectList

| 参数名            | 类型      | 必填   | 说明              |
| -------------- | ------- | ---- | --------------- |
| diag_pre_id    | String  | 否    | 前缀ID            |
| diag_pre_name  | String  | 是    | 前缀内容            |
| diag_id        | String  | 否    | 诊断id            |
| diag_name      | String  | 是    | 诊断名称            |
| diag_icd       | String  | 否    | 诊断ICD编码，剑形编码，病因 |
| diag_attach    | String  | 是    | 附加码             |
| diag_sufx_id   | String  | 否    | 后缀ID            |
| diag_sufx_name | String  | 是    | 后缀内容            |
| diag_master    | Integer | 是    | 是否是主诊断;0-不是;1-是 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


##专科检查-低视力

### 门诊预检评估-低视力首诊获取

```url
[GET]/treat_service/preview/evaluation/low_vision/first
```

1. 数据内容为全模板内容。

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数


| 参数名                   | 类型         | 必填   | 说明                                       |
| --------------------- | ---------- | ---- | ---------------------------------------- |
| trea_id               | String     | 是    | 就诊ID                                     |
| how_to_know           | Integer    | 否    | 你是如何得知我们低视力中心的;<br />1-我/我们自己得知;<br />2-我们医院的医生推荐;<br />3-从筛查中得知;<br />4-其他机构推荐 |
| eye_diagnosis         | ObjectList | 否    | 眼科诊断                                     |
| all_diagnosis_main    | String     | 否    | 全身疾病主诊断                                  |
| all_diagnosis_next    | String     | 否    | 全身疾病次诊断                                  |
| whether_photophobia   | Integer    | 否    | 是否畏光/眩光;1-否;1-是;2-未询问                    |
| whether_raise         | Integer    | 否    | 戴原镜视力是否提高;1-否;1-是;2-未询问                  |
| qlq_select            | Integer    | 否    | 生活质量问卷调查;1-ELVQOL;2-LVQOL;2-未回答          |
| qlq_reason            | Integer    | 否    | 生活质量问卷调查未回答原因;<br />1-拒绝合作;<br />2-不能理解问题的意义;<br />3-语言不通不能交流;<br />4-认知障碍，无法合作;<br />5-仅验光;<br />6-跟踪随访少于6个月; |
| action_chief_select   | String     | 否    | 主诉选择项;<br />1-远视力降低;<br />2-近视力降低;<br />3-行走能力降低;<br />多选时使用逗号分隔 |
| action_chief_else     | String     | 否    | 主诉其他                                     |
| distant_vision_select | String     | 否    | 远视力目标选择;<br />1-看电视看电影;<br />2-做家务;<br />3-从事工作;<br />4-使用公共交通;<br />5-开车;<br />6-室内行走;<br />7-从事业务好爱;<br />8-独立在街上行走;<br/>多选时使用逗号分隔 |
| distant_vision_else   | String     | 否    | 远视力其他                                    |
| near_vision_select    | String     | 否    | 近视力目标选择;<br />1- 提高书写能力;<br />2- 提高阅读能力;<br />3- 从事工作;<br />4- 从事业余爱好;<br />多选时使用逗号分隔 |
| near_vision_else      | String     | 否    | 近视力其他                                    |
| emotion               | Integer    | 否    | 病人情绪是否低落;<br/>1-否;<br/>2-是;              |
| memory                | Integer    | 否    | 病人记忆力/认知能力如何;<br/>1-好;<br/>2-不错;<br/>3-差; |
| walk_select           | Integer    | 否    | 病人是否有行走问题;<br/>1-否;<br/>2-是;             |
| walk_vision           | Integer    | 否    | 病人是否有行走问题-原因;<br/>1-视力问题;<br/>2-身体条件受限;  |
| walk_tool             | Integer    | 否    | 病人是否有行走问题- 帮助行走的工具;<br/>1-盲杖;<br/>2-助行架;<br/>3-轮椅;<br/>4-其他; |
| walk_method           | Integer    | 否    | 病人是否有行走问题-如何来到这里;<br/>1-依靠自己来到这里;<br/>2-依靠他人来到这里; |

眼科诊断列表

| 参数名                | 类型     | 必填   | 说明     |
| ------------------ | ------ | ---- | ------ |
| eye_diagnosis_pre  | String | 否    | 眼科诊断前缀 |
| eye_diagnosis_mian | String | 是    | 眼科诊断诊断 |
| eye_diagnosis_sufx | String | 否    | 眼科诊断后缀 |



### 门诊预检评估-低视力首诊保存

```url
[POST]/treat_service/preview/evaluation/low_vision/first
```

1. 数据内容为全模板内容。

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                   | 类型         | 必填   | 说明                                       |
| --------------------- | ---------- | ---- | ---------------------------------------- |
| trea_id               | String     | 是    | 就诊ID                                     |
| how_to_know           | Integer    | 否    | 你是如何得知我们低视力中心的;<br />1-我/我们自己得知;<br />2-我们医院的医生推荐;<br />3-从筛查中得知;<br />4-其他机构推荐 |
| eye_diagnosis         | ObjectList | 否    | 眼科诊断                                     |
| all_diagnosis_main    | String     | 否    | 全身疾病主诊断                                  |
| all_diagnosis_next    | String     | 否    | 全身疾病次诊断                                  |
| whether_photophobia   | Integer    | 否    | 是否畏光/眩光;1-否;1-是;2-未询问                    |
| whether_raise         | Integer    | 否    | 戴原镜视力是否提高;1-否;1-是;2-未询问                  |
| qlq_select            | Integer    | 否    | 生活质量问卷调查;1-ELVQOL;2-LVQOL;2-未回答          |
| qlq_reason            | Integer    | 否    | 生活质量问卷调查未回答原因;<br />1-拒绝合作;<br />2-不能理解问题的意义;<br />3-语言不通不能交流;<br />4-认知障碍，无法合作;<br />5-仅验光;<br />6-跟踪随访少于6个月; |
| action_chief_select   | String     | 否    | 主诉选择项;<br />1-远视力降低;<br />2-近视力降低;<br />3-行走能力降低;<br />多选时使用逗号分隔 |
| action_chief_else     | String     | 否    | 主诉其他                                     |
| distant_vision_select | String     | 否    | 远视力目标选择;<br />1-看电视看电影;<br />2-做家务;<br />3-从事工作;<br />4-使用公共交通;<br />5-开车;<br />6-室内行走;<br />7-从事业务好爱;<br />8-独立在街上行走;<br/>多选时使用逗号分隔 |
| distant_vision_else   | String     | 否    | 远视力其他                                    |
| near_vision_select    | String     | 否    | 近视力目标选择;<br />1- 提高书写能力;<br />2- 提高阅读能力;<br />3- 从事工作;<br />4- 从事业余爱好;<br />多选时使用逗号分隔 |
| near_vision_else      | String     | 否    | 近视力其他                                    |
| emotion               | Integer    | 否    | 病人情绪是否低落;<br/>1-否;<br/>2-是;              |
| memory                | Integer    | 否    | 病人记忆力/认知能力如何;<br/>1-好;<br/>2-不错;<br/>3-差; |
| walk_select           | Integer    | 否    | 病人是否有行走问题;<br/>1-否;<br/>2-是;             |
| walk_vision           | Integer    | 否    | 病人是否有行走问题-原因;<br/>1-视力问题;<br/>2-身体条件受限;  |
| walk_tool             | Integer    | 否    | 病人是否有行走问题- 帮助行走的工具;<br/>1-盲杖;<br/>2-助行架;<br/>3-轮椅;<br/>4-其他; |
| walk_method           | Integer    | 否    | 病人是否有行走问题-如何来到这里;<br/>1-依靠自己来到这里;<br/>2-依靠他人来到这里; |

眼科诊断列表

| 参数名                | 类型     | 必填   | 说明     |
| ------------------ | ------ | ---- | ------ |
| eye_diagnosis_pre  | String | 否    | 眼科诊断前缀 |
| eye_diagnosis_mian | String | 是    | 眼科诊断诊断 |
| eye_diagnosis_sufx | String | 否    | 眼科诊断后缀 |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 门诊预检评估-低视力随访获取协议

```url
[GET]/treat_service/preview/evaluation/low_vision/second
```

说明：
1. 数据内容为全模板内容。
2. 专科检查信息表的预检标志字段值为：1（预检数据）;

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.2.3 | 新增   |

#### 请求报文参数
| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |



#### 回复报文参数
| 参数名                       | 类型      | 必填   | 说明                                       |
| ------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                   | String  | 是    | 就诊ID                                     |
| pati_id                   | String  | 是    | 患者ID                                     |
| visi_id                   | String  | 是    | 门诊ID                                     |
| operator_depart           | Long    | 是    | 操作部门ID                                   |
| operator_id               | String  | 是    | 操作人ID                                    |
| preview                   | Integer | 是    | 预检标志;0-非预检;1-预检;                         |
| action_chief_select       | String  | 否    | 主诉选择项;<br />1-远视力降低;<br />2-近视力降低;<br />3-行走能力降低;<br />多选时使用逗号分隔 |
| action_chief_else         | String  | 否    | 主诉其他                                     |
| distant_vision_select     | String  | 否    | 远视力目标选择;<br />1-看电视看电影;<br />2-做家务;<br />3-从事工作;<br />4-使用公共交通;<br />5-开车;<br />6-室内行走;<br />7-从事业务好爱;<br />8-独立在街上行走;<br/>多选时使用逗号分隔 |
| near_vision_select        | String  | 否    | 近视力目标选择;<br />1- 提高书写能力;<br />2- 提高阅读能力;<br />3- 从事工作;<br />4- 从事业余爱好;<br />多选时使用逗号分隔 |
| near_vision_else          | String  | 否    | 近视力其他                                    |
| walk_select               | Integer | 否    | 病人是否有行走问题;<br/>1-否;<br/>2-是;             |
| walk_vision               | Integer | 否    | 病人是否有行走问题-原因;<br/>1-视力问题;<br/>2-身体条件受限;  |
| walk_tool                 | Integer | 否    | 病人是否有行走问题- 帮助行走的工具;<br/>1-盲杖;<br/>2-助行架;<br/>3-轮椅;<br/>4-其他; |
| walk_method               | Integer | 否    | 病人是否有行走问题-如何来到这里;<br/>1-依靠自己来到这里;<br/>2-依靠他人来到这里; |
| qlq_select                | Integer | 否    | 生活质量问卷调查;1-ELVQOL;2-LVQOL;2-未回答          |
| qlq_reason                | Integer | 否    | 生活质量问卷调查未回答原因;<br />1-拒绝合作;<br />2-不能理解问题的意义;<br />3-语言不通不能交流;<br />4-认知障碍，无法合作;<br />5-仅验光;<br />6-跟踪随访少于6个月; |
| if_have_audiphone_radio   | Integer | 否    | 是否有助视器;<br />1-是;<br />2-否               |
| if_have_audiphone_reason  | Integer | 否    | 没有助视器原因;<br />1-医生未建议配;<br />2-外观不能接收;<br />3-家人不能接收;<br />4-价格太贵买不起;<br />5-不会使用;<br />6-太麻烦，使用不方便;<br />7-进一步寻求其他治疗;<br />8-感觉没作用; |
| if_have_audiphone_type    | Integer | 否    | 助视器类型;<br />1-远用助视器;<br />2-近用助视器;<br />3-非光学助视器; |
| if_have_audiphone_source  | Integer | 否    | 助视器来源;<br />1-医院;<br />2-残联;<br />3-自购;<br />4-其他; |
| if_have_audiphone_cost    | Integer | 否    | 助视器付费方式;<br />1-自费;<br />2-医院资助;<br />3-残联赠送;<br />4-其他; |
| if_have_audiphone_select  | String  | 否    | 助视器多选框;<br />1-接受现场使用指导;<br />2-掌握使用技能;<br />多选时使用逗号分隔 |
| if_have_audiphone_whyneed | Integer | 否    | 为什么需要助视器;<br />1-阅读;<br />2-使用手机;<br />3-手工;<br />4-其他近距离工作;<br />5-家务;<br />6-麻将;<br />7-工作需求;<br />8-学习需求;<br />9-交通出行;<br />10-看电视;<br />11-其他; |
| if_have_audiphone_day     | Integer | 否    | 助视器频率天;<br />1-每天;<br />2-每周2~3次;<br />3-每周一次;<br />4-每月;<br />5-偶尔;<br />6-不用; |
| if_have_audiphone_minute  | Integer | 否    | 助视器频率分钟;<br />1-10分钟以内;<br />2-30分钟左右;<br />3-1小时;<br />4-1~2小时;<br />5-2小时以上; |


### 门诊预检评估-低视力随访保存协议

```url
[POST]/treat_service/preview/evaluation/low_vision/second
```

说明：
1. 数据内容为全模板内容。
2. 专科检查信息表的预检标志字段值为：1（预检数据）;

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.2.3 | 新增   |

#### 请求报文参数

| 参数名                       | 类型      | 必填   | 说明                                       |
| ------------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                   | String  | 是    | 就诊ID                                     |
| pati_id                   | String  | 是    | 患者ID                                     |
| visi_id                   | String  | 是    | 门诊ID                                     |
| operator_depart           | Long    | 是    | 操作部门ID                                   |
| operator_id               | String  | 是    | 操作人ID                                    |
| preview                   | Integer | 是    | 预检标志;0-非预检;1-预检;                         |
| action_chief_select       | String  | 否    | 主诉选择项;<br />1-远视力降低;<br />2-近视力降低;<br />3-行走能力降低;<br />多选时使用逗号分隔 |
| action_chief_else         | String  | 否    | 主诉其他                                     |
| distant_vision_select     | String  | 否    | 远视力目标选择;<br />1-看电视看电影;<br />2-做家务;<br />3-从事工作;<br />4-使用公共交通;<br />5-开车;<br />6-室内行走;<br />7-从事业务好爱;<br />8-独立在街上行走;<br/>多选时使用逗号分隔 |
| near_vision_select        | String  | 否    | 近视力目标选择;<br />1- 提高书写能力;<br />2- 提高阅读能力;<br />3- 从事工作;<br />4- 从事业余爱好;<br />多选时使用逗号分隔 |
| near_vision_else          | String  | 否    | 近视力其他                                    |
| walk_select               | Integer | 否    | 病人是否有行走问题;<br/>1-否;<br/>2-是;             |
| walk_vision               | Integer | 否    | 病人是否有行走问题-原因;<br/>1-视力问题;<br/>2-身体条件受限;  |
| walk_tool                 | Integer | 否    | 病人是否有行走问题- 帮助行走的工具;<br/>1-盲杖;<br/>2-助行架;<br/>3-轮椅;<br/>4-其他; |
| walk_method               | Integer | 否    | 病人是否有行走问题-如何来到这里;<br/>1-依靠自己来到这里;<br/>2-依靠他人来到这里; |
| qlq_select                | Integer | 否    | 生活质量问卷调查;1-ELVQOL;2-LVQOL;2-未回答          |
| qlq_reason                | Integer | 否    | 生活质量问卷调查未回答原因;<br />1-拒绝合作;<br />2-不能理解问题的意义;<br />3-语言不通不能交流;<br />4-认知障碍，无法合作;<br />5-仅验光;<br />6-跟踪随访少于6个月; |
| if_have_audiphone_radio   | Integer | 否    | 是否有助视器;<br />1-是;<br />2-否               |
| if_have_audiphone_reason  | Integer | 否    | 没有助视器原因;<br />1-医生未建议配;<br />2-外观不能接收;<br />3-家人不能接收;<br />4-价格太贵买不起;<br />5-不会使用;<br />6-太麻烦，使用不方便;<br />7-进一步寻求其他治疗;<br />8-感觉没作用; |
| if_have_audiphone_type    | Integer | 否    | 助视器类型;<br />1-远用助视器;<br />2-近用助视器;<br />3-非光学助视器; |
| if_have_audiphone_source  | Integer | 否    | 助视器来源;<br />1-医院;<br />2-残联;<br />3-自购;<br />4-其他; |
| if_have_audiphone_cost    | Integer | 否    | 助视器付费方式;<br />1-自费;<br />2-医院资助;<br />3-残联赠送;<br />4-其他; |
| if_have_audiphone_select  | String  | 否    | 助视器多选框;<br />1-接受现场使用指导;<br />2-掌握使用技能;<br />多选时使用逗号分隔 |
| if_have_audiphone_whyneed | Integer | 否    | 为什么需要助视器;<br />1-阅读;<br />2-使用手机;<br />3-手工;<br />4-其他近距离工作;<br />5-家务;<br />6-麻将;<br />7-工作需求;<br />8-学习需求;<br />9-交通出行;<br />10-看电视;<br />11-其他; |
| if_have_audiphone_day     | Integer | 否    | 助视器频率天;<br />1-每天;<br />2-每周2~3次;<br />3-每周一次;<br />4-每月;<br />5-偶尔;<br />6-不用; |
| if_have_audiphone_minute  | Integer | 否    | 助视器频率分钟;<br />1-10分钟以内;<br />2-30分钟左右;<br />3-1小时;<br />4-1~2小时;<br />5-2小时以上; |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 低视力-生活质量问卷调查ELVQOL获取

```url
[GET]/treat_service/speciality_check/low_vision/elvqol
```
1. 数据内容为全模板内容。

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明               |
| ------- | ------- | ---- | ---------------- |
| trea_id | String  | 是    | 就诊ID             |
| preview | Integer | 是    | 预检标志;0-非预检;1-预检; |

#### 回复报文参数

| 参数名                    | 类型      | 必填   | 说明                                       |
| ---------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                | String  | 是    | 就诊ID                                     |
| preview                | Integer | 是    | 预检标志;0-非预检;1-预检;                         |
| overall_vision         | Integer | 否    | 总体视力:您觉得您的视力情况怎么样？<br/>4-很好;<br/>3-一般;<br/>2-比较差;<br/>1-极差 |
| psychological_states_1 | Integer | 否    | 您是否担心视力越来越差;<br/>4-从不;<br/>3-偶尔;<br/>2-经常;<br/>1-非常频繁 |
| psychological_states_2 | Integer | 否    | 您是否经常因为视觉问题有些负面的情绪;<br/>4-从不;<br/>3-偶尔;<br/>2-经常;<br/>1-非常频繁 |
| psychological_states_3 | Integer | 否    | 你是否经常感觉易怒、焦虑或者比较脆弱;<br/>4-从不;<br/>3-偶尔;<br/>2-经常;<br/>1-非常频繁 |
| difficult_something_1  | String  | 否    | 白天独自出门;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_2  | String  | 否    | 在夜间或昏暗光线下出行;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_3  | String  | 否    | 在陌生的环境中行走;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_4  | String  | 否    | 在高低不平整的路上行走，如上下台阶、楼梯等;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_5  | String  | 否    | 独自乘车;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_6  | String  | 否    | 辨认路标、门牌、车牌、交通信号灯;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_7  | String  | 否    | 看电视时辨认字幕或者画面;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_8  | String  | 否    | 在比较近的距离内辨认出熟悉人面庞;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_9  | String  | 否    | 购物时选择物品款式、质量、价目表，辨认钱币等;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_10 | String  | 否    | 参加亲朋好友聚会;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_11 | String  | 否    | 在自己熟悉的地方寻找物品;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_12 | String  | 否    | 日常家务活动，如做饭、打扫、洗衣服等;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_13 | String  | 否    | 使用家用电器，如电视机、洗衣机、冰箱等;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_14 | String  | 否    | 使用电话，拨电话号码、辨认来电号码;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_15 | String  | 否    | 阅读常规字体，如报纸和书刊上的常规字体;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |




###低视力-生活质量问卷调查ELVQOL保存协议

```url
[POST]/treat_service/speciality_check/low_vision/elvqol
```
1. 数据内容为全模板内容。

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                    | 类型      | 必填   | 说明                                       |
| ---------------------- | ------- | ---- | ---------------------------------------- |
| trea_id                | String  | 是    | 就诊ID                                     |
| preview                | Integer | 是    | 预检标志;0-非预检;1-预检;                         |
| overall_vision         | Integer | 否    | 总体视力:您觉得您的视力情况怎么样？<br/>4-很好;<br/>3-一般;<br/>2-比较差;<br/>1-极差 |
| psychological_states_1 | Integer | 否    | 您是否担心视力越来越差;<br/>4-从不;<br/>3-偶尔;<br/>2-经常;<br/>1-非常频繁 |
| psychological_states_2 | Integer | 否    | 您是否经常因为视觉问题有些负面的情绪;<br/>4-从不;<br/>3-偶尔;<br/>2-经常;<br/>1-非常频繁 |
| psychological_states_3 | Integer | 否    | 你是否经常感觉易怒、焦虑或者比较脆弱;<br/>4-从不;<br/>3-偶尔;<br/>2-经常;<br/>1-非常频繁 |
| difficult_something_1  | String  | 否    | 白天独自出门;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_2  | String  | 否    | 在夜间或昏暗光线下出行;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_3  | String  | 否    | 在陌生的环境中行走;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_4  | String  | 否    | 在高低不平整的路上行走，如上下台阶、楼梯等;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_5  | String  | 否    | 独自乘车;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_6  | String  | 否    | 辨认路标、门牌、车牌、交通信号灯;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_7  | String  | 否    | 看电视时辨认字幕或者画面;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_8  | String  | 否    | 在比较近的距离内辨认出熟悉人面庞;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_9  | String  | 否    | 购物时选择物品款式、质量、价目表，辨认钱币等;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_10 | String  | 否    | 参加亲朋好友聚会;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_11 | String  | 否    | 在自己熟悉的地方寻找物品;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_12 | String  | 否    | 日常家务活动，如做饭、打扫、洗衣服等;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_13 | String  | 否    | 使用家用电器，如电视机、洗衣机、冰箱等;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_14 | String  | 否    | 使用电话，拨电话号码、辨认来电号码;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |
| difficult_something_15 | String  | 否    | 阅读常规字体，如报纸和书刊上的常规字体;<br/>4-一点也不困难;<br/>3-有一点困难;<br/>2-中等程度困难;<br/>1-非常困难;<br/>0-因视力问题而不做;<br/>N-因非视力问题而不做; |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 低视力-生活质量问卷调查LVQOL获取

```url
[GET]/treat_service/speciality_check/low_vision/lvqol
```
1. 数据内容为全模板内容。

#### 修改更新记录

| 对应业务        | 说明                          |
| ----------- | --------------------------- |
| V1.2.3      | 新增                          |
| WEBV1.2.3.2 | 在室内夜晚视力：需要适量的照明才能看清，折分成两个问题 |

#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明               |
| ------- | ------- | ---- | ---------------- |
| trea_id | String  | 是    | 就诊ID             |
| preview | Integer | 是    | 预检标志;0-非预检;1-预检; |

#### 回复报文参数


| 参数名      | 类型     | 必填   | 说明                     |
| -------- | ------ | ---- | ---------------------- |
| trea_id  | String | 是    | 就诊ID                   |
| lvqol_1  | String | 否    | 综合视力                   |
| lvqol_2  | String | 否    | 眼部疲劳（例如：只能短时间工作）       |
| lvqol_3  | String | 否    | 在室内夜晚视力：需要适量的照明才能看清    |
| lvqol_25 | String | 否    | 需要适量的照明才能看清            |
| lvqol_4  | String | 否    | 在眩光：因车灯或日光灯            |
| lvqol_5  | String | 否    | 看路标                    |
| lvqol_6  | String | 否    | 看电视（看得清图像）             |
| lvqol_7  | String | 否    | 看移动目标（例如：看清路上的车）       |
| lvqol_8  | String | 否    | 判断深度或距离（例如：伸手拿被子）      |
| lvqol_9  | String | 否    | 看台阶或路边                 |
| lvqol_10 | String | 否    | 由于视力关系，在户外活动（在不平坦的人行道） |
| lvqol_11 | String | 否    | 由于视力关系，在交通往来是穿过马路      |
| lvqol_12 | String | 否    | 在生活中不愉快                |
| lvqol_13 | String | 否    | 由于不能做某些事而灰心            |
| lvqol_14 | String | 否    | 访问友人或亲属而受限制            |
| lvqol_15 | String | 否    | 是否对您的眼病做过解释            |
| lvqol_16 | String | 否    | 阅读大字体（新闻标题）            |
| lvqol_17 | String | 否    | 阅读报纸和书刊                |
| lvqol_18 | String | 否    | 阅读标签（药品说明书）            |
| lvqol_19 | String | 否    | 阅读信函                   |
| lvqol_20 | String | 否    | 应用工具（针或刀）              |
| lvqol_21 | String | 否    | 看时间                    |
| lvqol_22 | String | 否    | 书写（支票或卡）               |
| lvqol_23 | String | 否    | 阅读自己的手迹                |
| lvqol_24 | String | 否    | 每日活动（家务劳动）             |

统一候选参数

| 值    | 等级   | 是否对您的眼病做过解释，的等级 |
| ---- | ---- | --------------- |
| 5    | 无    | 好               |
| 4    |      |                 |
| 3    | 中等   |                 |
| 2    |      | 很差              |
| 1    | 重度   |                 |
| X    |      | 无解释             |
| na   |      | 没有这个值           |



### 低视力-生活质量问卷调查LVQOL保存协议

```url
[POST]/treat_service/speciality_check/low_vision/lvqol
```
1. 数据内容为全模板内容。

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名      | 类型      | 必填   | 说明                     |
| -------- | ------- | ---- | ---------------------- |
| trea_id  | String  | 是    | 就诊ID                   |
| preview  | Integer | 是    | 预检标志;0-非预检;1-预检;       |
| lvqol_1  | String  | 否    | 综合视力                   |
| lvqol_2  | String  | 否    | 眼部疲劳（例如：只能短时间工作）       |
| lvqol_3  | String  | 否    | 在室内夜晚视力：需要适量的照明才能看清    |
| lvqol_4  | String  | 否    | 在眩光：因车灯或日光灯            |
| lvqol_5  | String  | 否    | 看路标                    |
| lvqol_6  | String  | 否    | 看电视（看得清图像）             |
| lvqol_7  | String  | 否    | 看移动目标（例如：看清路上的车）       |
| lvqol_8  | String  | 否    | 判断深度或距离（例如：伸手拿被子）      |
| lvqol_9  | String  | 否    | 看台阶或路边                 |
| lvqol_10 | String  | 否    | 由于视力关系，在户外活动（在不平坦的人行道） |
| lvqol_11 | String  | 否    | 由于视力关系，在交通往来是穿过马路      |
| lvqol_12 | String  | 否    | 在生活中不愉快                |
| lvqol_13 | String  | 否    | 由于不能做某些事而灰心            |
| lvqol_14 | String  | 否    | 访问友人或亲属而受限制            |
| lvqol_15 | String  | 否    | 是否对您的眼病做过解释            |
| lvqol_16 | String  | 否    | 阅读大字体（新闻标题）            |
| lvqol_17 | String  | 否    | 阅读报纸和书刊                |
| lvqol_18 | String  | 否    | 阅读标签（药品说明书）            |
| lvqol_19 | String  | 否    | 阅读信函                   |
| lvqol_20 | String  | 否    | 应用工具（针或刀）              |
| lvqol_21 | String  | 否    | 看时间                    |
| lvqol_22 | String  | 否    | 书写（支票或卡）               |
| lvqol_23 | String  | 否    | 阅读自己的手迹                |
| lvqol_24 | String  | 否    | 每日活动（家务劳动）             |

统一候选参数

| 值    | 等级   | 是否对您的眼病做过解释，的等级 |
| ---- | ---- | --------------- |
| 5    | 无    | 好               |
| 4    |      |                 |
| 3    | 中等   |                 |
| 2    |      | 很差              |
| 1    | 重度   |                 |
| X    |      | 无解释             |
| na   |      | 没有这个值           |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 专科检查-低视力首诊获取

```htt
[GET]/treat_service/speciality_check/low_vision/first
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊ID |

#### 回复报文参数

| 参数名                          | 类型         | 必填   | 说明                                       |
| ---------------------------- | ---------- | ---- | ---------------------------------------- |
| trea_id                      | String     | 是    | 就诊ID                                     |
| 低视力首诊问卷部分low_vision_first    |            |      | 模板                                       |
| how_to_know                  | Integer    | 否    | 你是如何得知我们低视力中心的;<br />1-我/我们自己得知;<br />2-我们医院的医生推荐;<br />3-从筛查中得知;<br />4-其他机构推荐 |
| eye_diagnosis                | ObjectList | 否    | 眼科诊断                                     |
| all_diagnosis_main           | String     | 否    | 全身疾病主诊断                                  |
| all_diagnosis_next           | String     | 否    | 全身疾病次诊断                                  |
| whether_photophobia          | Integer    | 否    | 是否畏光/眩光;1-否;1-是;2-未询问                    |
| whether_raise                | Integer    | 否    | 戴原镜视力是否提高;1-否;1-是;2-未询问                  |
| qlq_select                   | Integer    | 否    | 生活质量问卷调查;1-ELVQOL;2-LVQOL;2-未回答          |
| qlq_reason                   | Integer    | 否    | 生活质量问卷调查未回答原因;<br />1-拒绝合作;<br />2-不能理解问题的意义;<br />3-语言不通不能交流;<br />4-认知障碍，无法合作;<br />5-仅验光;<br />6-跟踪随访少于6个月; |
| action_chief_select          | String     | 否    | 主诉选择项;<br />1-远视力降低;<br />2-近视力降低;<br />3-行走能力降低;<br />多选时使用逗号分隔 |
| action_chief_else            | String     | 否    | 主诉其他                                     |
| distant_vision_select        | String     | 否    | 远视力目标选择;<br />1-看电视看电影;<br />2-做家务;<br />3-从事工作;<br />4-使用公共交通;<br />5-开车;<br />6-室内行走;<br />7-从事业务好爱;<br />8-独立在街上行走;<br/>多选时使用逗号分隔 |
| distant_vision_else          | String     | 否    | 远视力其他                                    |
| near_vision_select           | String     | 否    | 近视力目标选择;<br />1- 提高书写能力;<br />2- 提高阅读能力;<br />3- 从事工作;<br />4- 从事业余爱好;<br />多选时使用逗号分隔 |
| near_vision_else             | String     | 否    | 近视力其他                                    |
| emotion                      | Integer    | 否    | 病人情绪是否低落;<br/>1-否;<br/>2-是;              |
| memory                       | Integer    | 否    | 病人记忆力/认知能力如何;<br/>1-好;<br/>2-不错;<br/>3-差; |
| walk_select                  | Integer    | 否    | 病人是否有行走问题;<br/>1-否;<br/>2-是;             |
| walk_vision                  | Integer    | 否    | 病人是否有行走问题-原因;<br/>1-视力问题;<br/>2-身体条件受限;  |
| walk_tool                    | Integer    | 否    | 病人是否有行走问题- 帮助行走的工具;<br/>1-盲杖;<br/>2-助行架;<br/>3-轮椅;<br/>4-其他; |
| walk_method                  | Integer    | 否    | 病人是否有行走问题-如何来到这里;<br/>1-依靠自己来到这里;<br/>2-依靠他人来到这里; |
| 临床检查结果-视功能computer_optometry |            |      | 模板加表                                     |
| 电脑验光computer_optometry       |            |      | 电脑验光                                     |
| data_od_sphere               | String     | 否    | 电脑验光球镜od                                 |
| data_od_cylinder             | String     | 否    | 电脑验光柱镜od                                 |
| data_od_axis                 | String     | 否    | 电脑验光轴向od                                 |
| data_od_rem                  | String     | 否    | 电脑验光OD备注                                 |
| data_os_sphere               | String     | 否    | 电脑验光球镜os                                 |
| data_os_cylinder             | String     | 否    | 电脑验光柱镜os                                 |
| data_os_axis                 | String     | 否    | 电脑验光轴向os                                 |
| data_os_rem                  | String     | 否    | 电脑验光OS备注                                 |
| 瞳距pd                         |            |      | 框架眼镜处方                                   |
| opto_far_pd                  | String     | 否    | 瞳距-远用                                    |
| opto_near_pd                 | String     | 否    | 瞳距-近用                                    |
| opto_od_pd                   | String     | 否    | 瞳距-单眼OD                                  |
| opto_os_pd                   | String     | 否    | 瞳距-单眼OS                                  |
| opto_pd_rem                  | String     | 否    | 瞳距-备注                                    |
| 检影验光retinoscopy              |            |      | 检影验光表                                    |
| retinoscopy_od_sphere        | String     | 否    | 检影验光OD-球镜                                |
| retinoscopy_od_cylinder      | String     | 否    | 检影验光OD-柱镜                                |
| retinoscopy_od_axis          | String     | 否    | 检影验光OD-轴向                                |
| retinoscopy_od_vision        | String     | 否    | 检影验光OD-视力                                |
| retinoscopy_od_memo          | String     | 否    | 检影验光OD-备注                                |
| retinoscopy_os_sphere        | String     | 否    | 检影验光OS-球镜                                |
| retinoscopy_os_cylinder      | String     | 否    | 检影验光OS-柱镜                                |
| retinoscopy_os_axis          | String     | 否    | 检影验光OS-轴向                                |
| retinoscopy_os_vision        | String     | 否    | 检影验光OS-视力                                |
| retinoscopy_os_memo          | String     | 否    | 检影验光OS-备注                                |
| 主觉验光subjective               |            |      | 主觉验光数据表                                  |
| subjective_od_sphere         | String     | 否    | 主觉验光OD-球镜                                |
| subjective_od_cylinder       | String     | 否    | 主觉验光OD-柱镜                                |
| subjective_od_axis           | String     | 否    | 主觉验光OD-轴向                                |
| subjective_od_prism          | String     | 否    | 主觉验光OD-棱镜                                |
| subjective_od_vision         | String     | 否    | 主觉验光OD-视力                                |
| subjective_od_memo           | String     | 否    | 主觉验光OD-备注                                |
| subjective_os_sphere         | String     | 否    | 主觉验光OS-球镜                                |
| subjective_os_cylinder       | String     | 否    | 主觉验光OS-柱镜                                |
| subjective_os_axis           | String     | 否    | 主觉验光OS-轴向                                |
| subjective_os_prism          | String     | 否    | 主觉验光OS-棱镜                                |
| subjective_os_vision         | String     | 否    | 主觉验光OS-视力                                |
| subjective_os_memo           | String     | 否    | 主觉验光OS-备注                                |
| 近附加presbyopicadd             | String     | 否    | 近附加数据表                                   |
| 其他模板数据template_data          |            |      | 模板数据                                     |
| wear_distant_vision_od       | String     | 否    | 戴眼镜远视力od                                 |
| wear_distant_vision_os       | String     | 否    | 戴眼镜远视力os                                 |
| wear_distant_vision_ou       | String     | 否    | 戴眼镜远视力ou                                 |
| wear_near_vision_od          | String     | 否    | 戴眼镜近视力od                                 |
| wear_near_vision_os          | String     | 否    | 戴眼镜近视力os                                 |
| wear_near_vision_ou          | String     | 否    | 戴眼镜近视力ou                                 |
| correct_distant_vision_od    | String     | 否    | 最佳远矫正视力od                                |
| correct_distant_vision_os    | String     | 否    | 最佳远矫正视力os                                |
| correct_distant_vision_ou    | String     | 否    | 最佳远矫正视力ou                                |
| correct_near_vision_od       | String     | 否    | 最佳近矫正视力od                                |
| correct_near_vision_os       | String     | 否    | 最佳近矫正视力os                                |
| correct_near_vision_ou       | String     | 否    | 最佳近矫正视力ou                                |
| contrast_sensitivity_od      | String     | 否    | 对比敏感度od                                  |
| contrast_sensitivity_os      | String     | 否    | 对比敏感度os                                  |
| contrast_sensitivity_ou      | String     | 否    | 对比敏感度ou                                  |
| eye_movement                 | String     | 否    | 眼球运动                                     |
| eye_movement_od              | String     | 否    | 眼球运动od;<br/>1-SAFE;<br/>2-受限制;           |
| eye_movement_os              | String     | 否    | 眼球运动os;<br/>1-SAFE;<br/>2-受限制;           |
| view                         | String     | 否    | 视野;<br />1-无缺损;<br />2-轻度缩窄;<br />3-中度缩窄;<br />4-高度缩窄;<br />5-暗点;<br/>6-象限缺损;<br/>7-半缺损;<br/>8-无检查; |
| 裂隙灯检查slit_lamp_check         |            |      | 模板                                       |
| eye_appear_select_od         | String     | 否    | 眼睛外观od:<br/>1-正常;<br/>2-异常;              |
| eye_appear_describe_od       | String     | 否    | 眼睛外观描述od:<br/>水平性眼球震颤;<br/>垂直性眼球震颤;<br/>外斜视;<br/>内斜视;<br/>上睑下垂;<br/>水肿; |
| eye_appear_select_os         | String     | 否    | 眼睛外观os:<br/>1-正常;<br/>2-异常;              |
| eye_appear_describe_os       | String     | 否    | 眼睛外观描述os:<br/>水平性眼球震颤;<br/>垂直性眼球震颤;<br/>外斜视;<br/>内斜视;<br/>上睑下垂;<br/>水肿; |
| sclera_select_od             | String     | 否    | 巩膜od:<br/>1-正常;<br/>2-异常;                |
| sclera_describe_od           | String     | 否    | 巩膜描述od                                   |
| sclera_select_os             | String     | 否    | 巩膜os:<br/>1-正常;<br/>2-异常;                |
| sclera_describe_os           | String     | 否    | 巩膜描述os                                   |
| conjunctiva_select_od        | String     | 否    | 结膜od:<br/>1-正常;<br/>2-异常;                |
| conjunctiva_describe_od      | String     | 否    | 结膜描述od                                   |
| conjunctiva_select_os        | String     | 否    | 结膜os:<br/>1-正常;<br/>2-异常;                |
| conjunctiva_describe_os      | String     | 否    | 结膜描述os                                   |
| pterygium_select_od          | String     | 否    | 翼状胬肉od:<br/>1-正常;<br/>2-异常;              |
| pterygium_describe_od        | String     | 否    | 翼状胬肉描述od                                 |
| pterygium_select_os          | String     | 否    | 翼状胬肉os:<br/>1-正常;<br/>2-异常;              |
| pterygium_describe_os        | String     | 否    | 翼状胬肉描述os                                 |
| cornea_select_od             | String     | 否    | 角膜od:<br/>1-正常;<br/>2-异常;                |
| cornea_describe_od           | String     | 否    | 角膜描述od:<br />创伤/疤痕;<br />溃疡;<br />水肿;<br />手术切口; |
| cornea_select_os             | String     | 否    | 角膜os:<br/>1-正常;<br/>2-异常;                |
| cornea_describe_os           | String     | 否    | 角膜描述os:<br/>创伤/疤痕;<br />溃疡;<br />水肿;<br />手术切口; |
| atria_select_od              | String     | 否    | 前房od;<br/>1-正常;<br/>2-异常;                |
| atria_describe_od            | String     | 否    | 前房描述od:<br/>狭窄;<br/>关闭;<br/>无法观察;        |
| atria_select_os              | String     | 否    | 前房os:<br/>1-正常;<br/>2-异常;                |
| atria_describe_os            | String     | 否    | 前房描述os:<br/>狭窄;<br/>关闭;<br/>无法观察;        |
| iris_select_od               | String     | 否    | 虹膜od:<br/>1-正常;<br/>2-异常;                |
| iris_describe_od             | String     | 否    | 虹膜描述od:<br/>褪色;<br/>无法观察;                |
| iris_select_os               | String     | 否    | 虹膜os:<br/>1-正常;<br/>2-异常;                |
| iris_describe_os             | String     | 否    | 虹膜描述os<br/>褪色;<br/>无法观察;                 |
| pupil_select_od              | String     | 否    | 瞳孔od:<br/>1-正常;<br/>2-异常;                |
| pupil_describe_od            | String     | 否    | 瞳孔描述od:<br/>不规划;<br/>闭锁;<br/>不可见;        |
| pupil_select_os              | String     | 否    | 瞳孔os;<br/>1-正常;<br/>2-异常;                |
| pupil_describe_os            | String     | 否    | 瞳孔描述os:<br/>不规划;<br/>闭锁;<br/>不可见;        |
| crystalline_lens_select_od   | String     | 否    | 晶状体od;<br/>1-正常;<br/>2-异常;               |
| crystalline_lens_describe_od | String     | 否    | 晶状体描述od:<br/>轻度不透明;<br/>重度不透明;<br/>严重不透明;<br/>人工晶体;<br/>无晶体;<br/>不可见; |
| crystalline_lens_select_os   | String     | 否    | 晶状体os;<br/>1-正常;<br/>2-异常;               |
| crystalline_lens_describe_os | String     | 否    | 晶状体描述os:<br/>轻度不透明;<br/>重度不透明;<br/>严重不透明;<br/>人工晶体;<br/>无晶体;<br/>不可见; |
| 眼底检查fundus_check             | Object     | 否    | 模板                                       |
| yellow_spot_select_od        | String     | 否    | 黄斑od:<br/>1-正常;<br/>2-异常                 |
| yellow_spot_describe_od      | String     | 否    | 黄斑描述od:<br/>黄斑前膜;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>不可见; |
| yellow_spot_select_os        | String     | 否    | 黄斑os:<br/>1-正常;<br/>2-异常                 |
| yellow_spot_describe_os      | String     | 否    | 黄斑描述os:<br/>黄斑前膜;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>不可见; |
| optic_disk_select_od         | String     | 否    | 视盘od:<br/>1-正常;<br/>2-异常                 |
| optic_disk_describe_od       | String     | 否    | 视盘描述od:<br/>出血;<br/>萎缩;<br/>怀盘比异常;<br/>不可见; |
| optic_disk_select_os         | String     | 否    | 视盘os:<br/>1-正常;<br/>2-异常                 |
| optic_disk_describe_os       | String     | 否    | 视盘描述os:<br/>出血;<br/>萎缩;<br/>怀盘比异常;<br/>不可见; |
| blood_vessel_select_od       | String     | 否    | 血管od:<br/>1-正常;<br/>2-异常                 |
| blood_vessel_describe_od     | String     | 否    | 血管描述od:<br/>出血;<br/>渗出;<br/>新生血管;<br/>不可见; |
| blood_vessel_select_os       | String     | 否    | 血管os:<br/>1-正常;<br/>2-异常                 |
| blood_vessel_describe_os     | String     | 否    | 血管描述os:<br/>出血;<br/>渗出;<br/>新生血管;<br/>不可见; |
| total_select_od              | String     | 否    | 总体情况od:<br/>1-正常;<br/>2-异常               |
| total_describe_od            | String     | 否    | 总体情况描述od:<br/>豹纹状眼底;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>水肿;<br/>不可见; |
| total_select_os              | String     | 否    | 总体情况os:<br/>1-正常;<br/>2-异常               |
| total_describe_os            | String     | 否    | 总体情况描述os:<br/>豹纹状眼底;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>水肿;<br/>不可见; |
| else_od                      | String     | 否    | 其他od                                     |
| else_os                      | String     | 否    | 其他os                                     |
| 诊断diagnose                   | ObjectList | 否    | 诊断表                                      |
| prescription                 | String     | 否    | 处方<br/>1-仅验光，不需要治疗;<br/>2-常规眼镜;<br/>3-低视力助视器;<br/>4-技能训练;多选时逗号分隔 |
| recommend_audiphone          | ObjectList | 否    | 推荐助视器                                    |
| 完成低视力检查和康复后after_check       |            |      | 模板                                       |
| can_distance                 | Integer    | 否    | 患者是否达到远距离视物的目标？<br/>1-是;<br/>2-否;<br/>3-部分可以; |
| can_near                     | Integer    | 否    | 患者是否达到近距离视物的目标？<br/>1-是;<br/>2-否;<br/>3-部分可以; |
| who_review                   | Integer    | 否    | 谁来完成低视力康复:<br/>1-护士;<br/>2-医生;           |
| if_visit                     | Integer    | 否    | 是否有下一次随访的安排:<br/>1-是;<br/>2-否;           |
| refuse_reason                | Integer    | 否    | 拒绝助视器的原因:<br/>1-太贵;<br/>2-考虑其他医学治疗;<br/>3-外观上无法接受;<br/>4-不确信是否需要;<br/>5-其他 |
| refuse_reason_else           | String     | 否    | 拒绝助视器的原因其他                               |
| 花费cost                       |            |      | 花费                                       |
| check_cost                   | String     | 否    | 检查费用                                     |
| review_cost                  | String     | 否    | 康复费用                                     |
| typoscope_cost               | String     | 否    | 助听器费用                                    |
| total_cast                   | String     | 否    | 合计，总共费用，单位元                              |
| patient_pay                  | String     | 否    | 病人支付                                     |
| charity_pay                  | String     | 否    | 慈善机构支付                                   |
| insurance_pay                | String     | 否    | 保险支付                                     |
| else_pay                     | String     | 否    | 其他                                       |


###### 眼科诊断列表

| 参数名                | 类型     | 必填   | 说明     |
| ------------------ | ------ | ---- | ------ |
| eye_diagnosis_pre  | String | 否    | 眼科诊断前缀 |
| eye_diagnosis_mian | String | 是    | 眼科诊断诊断 |
| eye_diagnosis_sufx | String | 否    | 眼科诊断后缀 |


##### 诊断

1. 就诊诊断信息表
2. 类型为ObjectList

| 参数名            | 类型      | 必填   | 说明              |
| -------------- | ------- | ---- | --------------- |
| diag_pre_id    | String  | 否    | 前缀ID            |
| diag_pre_name  | String  | 是    | 前缀内容            |
| diag_id        | String  | 否    | 诊断id            |
| diag_name      | String  | 是    | 诊断名称            |
| diag_icd       | String  | 否    | 诊断ICD编码，剑形编码，病因 |
| diag_attach    | String  | 是    | 附加码             |
| diag_sufx_id   | String  | 否    | 后缀ID            |
| diag_sufx_name | String  | 是    | 后缀内容            |
| diag_master    | Integer | 是    | 是否是主诊断;0-不是;1-是 |

##### 推荐助视器

1. 全为模板数据
2. 模板项存储时，在原来的key后面添加 _{第几条数据的index，从1开始}; 如第一条 recommend_audiphone_2_1;
3. 选择不同的推荐助听器后，商品内容会改变。

| 参数名                       | 类型      | 必填   | 说明                                       |
| ------------------------- | ------- | ---- | ---------------------------------------- |
| recommend_audiphone_1     | Integer | 是    | 推荐助听器-类型<br/>1-近用助视器;<br/>2-远用助视器;<br/>3-非光学助视器;<br/>4-其他助视器和训练;<br/>5-其他 |
| recommend_audiphone_2     | Integer | 是    | 推荐助听器-商品，具体内容见下表                         |
| recommend_audiphone_3     | String  | 否    | 推荐助听器-放大率，当类型选择1-近用助视器、2-远用助视器时有效        |
| recommend_audiphone_4     | String  | 否    | 使用助听器后的视力                                |
| recommend_audiphone_radio | Integer | 是    | 推荐助听器<br/>1-接受;<br/>2-不接受                |

###### 推荐助听器-商品

| 值    | 说明      | 所属类型    |
| ---- | ------- | ------- |
| 1    | 手持放大镜   | 1-近用助视器 |
| 2    | 立式放大镜   | 1-近用助视器 |
| 3    | 袖珍放大镜   | 1-近用助视器 |
| 4    | 高度数眼镜   | 1-近用助视器 |
| 5    | 便携式CCTV | 1-近用助视器 |

| 值    | 说明     | 所属类型    |
| ---- | ------ | ------- |
| 1    | 眼镜式望远镜 | 2-远用助视器 |
| 2    | 手持望远镜  | 2-远用助视器 |

| 值    | 说明        | 所属类型     |
| ---- | --------- | -------- |
| 1    | 盲杖        | 3-非光学助视器 |
| 2    | 其他帮助行走的设备 | 3-非光学助视器 |
| 3    | 大字体电脑     | 3-非光学助视器 |
| 4    | 水位报警器     | 3-非光学助视器 |
| 5    | 裂口阅读器     | 3-非光学助视器 |
| 6    | 标记笔       | 3-非光学助视器 |
| 7    | 护指套       | 3-非光学助视器 |





### 专科检查-低视力首诊保存

```htt
[POST]/treat_service/speciality_check/low_vision/first
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                          | 类型         | 必填   | 说明                                       |
| ---------------------------- | ---------- | ---- | ---------------------------------------- |
| trea_id                      | String     | 是    | 就诊ID                                     |
| 低视力首诊问卷部分low_vision_first    |            |      | 模板                                       |
| how_to_know                  | Integer    | 否    | 你是如何得知我们低视力中心的;<br />1-我/我们自己得知;<br />2-我们医院的医生推荐;<br />3-从筛查中得知;<br />4-其他机构推荐 |
| eye_diagnosis                | ObjectList | 否    | 眼科诊断                                     |
| all_diagnosis_main           | String     | 否    | 全身疾病主诊断                                  |
| all_diagnosis_next           | String     | 否    | 全身疾病次诊断                                  |
| whether_photophobia          | Integer    | 否    | 是否畏光/眩光;1-否;1-是;2-未询问                    |
| whether_raise                | Integer    | 否    | 戴原镜视力是否提高;1-否;1-是;2-未询问                  |
| qlq_select                   | Integer    | 否    | 生活质量问卷调查;1-ELVQOL;2-LVQOL;2-未回答          |
| qlq_reason                   | Integer    | 否    | 生活质量问卷调查未回答原因;<br />1-拒绝合作;<br />2-不能理解问题的意义;<br />3-语言不通不能交流;<br />4-认知障碍，无法合作;<br />5-仅验光;<br />6-跟踪随访少于6个月; |
| action_chief_select          | String     | 否    | 主诉选择项;<br />1-远视力降低;<br />2-近视力降低;<br />3-行走能力降低;<br />多选时使用逗号分隔 |
| action_chief_else            | String     | 否    | 主诉其他                                     |
| distant_vision_select        | String     | 否    | 远视力目标选择;<br />1-看电视看电影;<br />2-做家务;<br />3-从事工作;<br />4-使用公共交通;<br />5-开车;<br />6-室内行走;<br />7-从事业务好爱;<br />8-独立在街上行走;<br/>多选时使用逗号分隔 |
| distant_vision_else          | String     | 否    | 远视力其他                                    |
| near_vision_select           | String     | 否    | 近视力目标选择;<br />1- 提高书写能力;<br />2- 提高阅读能力;<br />3- 从事工作;<br />4- 从事业余爱好;<br />多选时使用逗号分隔 |
| near_vision_else             | String     | 否    | 近视力其他                                    |
| emotion                      | Integer    | 否    | 病人情绪是否低落;<br/>1-否;<br/>2-是;              |
| memory                       | Integer    | 否    | 病人记忆力/认知能力如何;<br/>1-好;<br/>2-不错;<br/>3-差; |
| walk_select                  | Integer    | 否    | 病人是否有行走问题;<br/>1-否;<br/>2-是;             |
| walk_vision                  | Integer    | 否    | 病人是否有行走问题-原因;<br/>1-视力问题;<br/>2-身体条件受限;  |
| walk_tool                    | Integer    | 否    | 病人是否有行走问题- 帮助行走的工具;<br/>1-盲杖;<br/>2-助行架;<br/>3-轮椅;<br/>4-其他; |
| walk_method                  | Integer    | 否    | 病人是否有行走问题-如何来到这里;<br/>1-依靠自己来到这里;<br/>2-依靠他人来到这里; |
| 临床检查结果-视功能computer_optometry |            |      | 模板加表                                     |
| 电脑验光computer_optometry       |            |      | 电脑验光                                     |
| data_od_sphere               | String     | 否    | 电脑验光球镜od                                 |
| data_od_cylinder             | String     | 否    | 电脑验光柱镜od                                 |
| data_od_axis                 | String     | 否    | 电脑验光轴向od                                 |
| data_od_rem                  | String     | 否    | 电脑验光OD备注                                 |
| data_os_sphere               | String     | 否    | 电脑验光球镜os                                 |
| data_os_cylinder             | String     | 否    | 电脑验光柱镜os                                 |
| data_os_axis                 | String     | 否    | 电脑验光轴向os                                 |
| data_os_rem                  | String     | 否    | 电脑验光OS备注                                 |
| 瞳距pd                         |            |      | 框架眼镜处方                                   |
| opto_far_pd                  | String     | 否    | 瞳距-远用                                    |
| opto_near_pd                 | String     | 否    | 瞳距-近用                                    |
| opto_od_pd                   | String     | 否    | 瞳距-单眼OD                                  |
| opto_os_pd                   | String     | 否    | 瞳距-单眼OS                                  |
| opto_pd_rem                  | String     | 否    | 瞳距-备注                                    |
| 检影验光retinoscopy              |            |      | 检影验光表                                    |
| retinoscopy_od_sphere        | String     | 否    | 检影验光OD-球镜                                |
| retinoscopy_od_cylinder      | String     | 否    | 检影验光OD-柱镜                                |
| retinoscopy_od_axis          | String     | 否    | 检影验光OD-轴向                                |
| retinoscopy_od_vision        | String     | 否    | 检影验光OD-视力                                |
| retinoscopy_od_memo          | String     | 否    | 检影验光OD-备注                                |
| retinoscopy_os_sphere        | String     | 否    | 检影验光OS-球镜                                |
| retinoscopy_os_cylinder      | String     | 否    | 检影验光OS-柱镜                                |
| retinoscopy_os_axis          | String     | 否    | 检影验光OS-轴向                                |
| retinoscopy_os_vision        | String     | 否    | 检影验光OS-视力                                |
| retinoscopy_os_memo          | String     | 否    | 检影验光OS-备注                                |
| 主觉验光subjective               |            |      | 主觉验光数据表                                  |
| subjective_od_sphere         | String     | 否    | 主觉验光OD-球镜                                |
| subjective_od_cylinder       | String     | 否    | 主觉验光OD-柱镜                                |
| subjective_od_axis           | String     | 否    | 主觉验光OD-轴向                                |
| subjective_od_prism          | String     | 否    | 主觉验光OD-棱镜                                |
| subjective_od_vision         | String     | 否    | 主觉验光OD-视力                                |
| subjective_od_memo           | String     | 否    | 主觉验光OD-备注                                |
| subjective_os_sphere         | String     | 否    | 主觉验光OS-球镜                                |
| subjective_os_cylinder       | String     | 否    | 主觉验光OS-柱镜                                |
| subjective_os_axis           | String     | 否    | 主觉验光OS-轴向                                |
| subjective_os_prism          | String     | 否    | 主觉验光OS-棱镜                                |
| subjective_os_vision         | String     | 否    | 主觉验光OS-视力                                |
| subjective_os_memo           | String     | 否    | 主觉验光OS-备注                                |
| 近附加presbyopicadd             | String     | 否    | 近附加数据表                                   |
| 其他模板数据template_data          |            |      | 模板数据                                     |
| wear_distant_vision_od       | String     | 否    | 戴眼镜远视力od                                 |
| wear_distant_vision_os       | String     | 否    | 戴眼镜远视力os                                 |
| wear_distant_vision_ou       | String     | 否    | 戴眼镜远视力ou                                 |
| wear_near_vision_od          | String     | 否    | 戴眼镜近视力od                                 |
| wear_near_vision_os          | String     | 否    | 戴眼镜近视力os                                 |
| wear_near_vision_ou          | String     | 否    | 戴眼镜近视力ou                                 |
| correct_distant_vision_od    | String     | 否    | 最佳远矫正视力od                                |
| correct_distant_vision_os    | String     | 否    | 最佳远矫正视力os                                |
| correct_distant_vision_ou    | String     | 否    | 最佳远矫正视力ou                                |
| correct_near_vision_od       | String     | 否    | 最佳近矫正视力od                                |
| correct_near_vision_os       | String     | 否    | 最佳近矫正视力os                                |
| correct_near_vision_ou       | String     | 否    | 最佳近矫正视力ou                                |
| contrast_sensitivity_od      | String     | 否    | 对比敏感度od                                  |
| contrast_sensitivity_os      | String     | 否    | 对比敏感度os                                  |
| contrast_sensitivity_ou      | String     | 否    | 对比敏感度ou                                  |
| eye_movement                 | String     | 否    | 眼球运动                                     |
| eye_movement_od              | String     | 否    | 眼球运动od;<br/>1-SAFE;<br/>2-受限制;           |
| eye_movement_os              | String     | 否    | 眼球运动os;<br/>1-SAFE;<br/>2-受限制;           |
| view                         | String     | 否    | 视野;<br />1-无缺损;<br />2-轻度缩窄;<br />3-中度缩窄;<br />4-高度缩窄;<br />5-暗点;<br/>6-象限缺损;<br/>7-半缺损;<br/>8-无检查; |
| 裂隙灯检查slit_lamp_check         |            |      | 模板                                       |
| eye_appear_select_od         | String     | 否    | 眼睛外观od:<br/>1-正常;<br/>2-异常;              |
| eye_appear_describe_od       | String     | 否    | 眼睛外观描述od:<br/>水平性眼球震颤;<br/>垂直性眼球震颤;<br/>外斜视;<br/>内斜视;<br/>上睑下垂;<br/>水肿; |
| eye_appear_select_os         | String     | 否    | 眼睛外观os:<br/>1-正常;<br/>2-异常;              |
| eye_appear_describe_os       | String     | 否    | 眼睛外观描述os:<br/>水平性眼球震颤;<br/>垂直性眼球震颤;<br/>外斜视;<br/>内斜视;<br/>上睑下垂;<br/>水肿; |
| sclera_select_od             | String     | 否    | 巩膜od:<br/>1-正常;<br/>2-异常;                |
| sclera_describe_od           | String     | 否    | 巩膜描述od                                   |
| sclera_select_os             | String     | 否    | 巩膜os:<br/>1-正常;<br/>2-异常;                |
| sclera_describe_os           | String     | 否    | 巩膜描述os                                   |
| conjunctiva_select_od        | String     | 否    | 结膜od:<br/>1-正常;<br/>2-异常;                |
| conjunctiva_describe_od      | String     | 否    | 结膜描述od                                   |
| conjunctiva_select_os        | String     | 否    | 结膜os:<br/>1-正常;<br/>2-异常;                |
| conjunctiva_describe_os      | String     | 否    | 结膜描述os                                   |
| pterygium_select_od          | String     | 否    | 翼状胬肉od:<br/>1-正常;<br/>2-异常;              |
| pterygium_describe_od        | String     | 否    | 翼状胬肉描述od                                 |
| pterygium_select_os          | String     | 否    | 翼状胬肉os:<br/>1-正常;<br/>2-异常;              |
| pterygium_describe_os        | String     | 否    | 翼状胬肉描述os                                 |
| cornea_select_od             | String     | 否    | 角膜od:<br/>1-正常;<br/>2-异常;                |
| cornea_describe_od           | String     | 否    | 角膜描述od:<br />创伤/疤痕;<br />溃疡;<br />水肿;<br />手术切口; |
| cornea_select_os             | String     | 否    | 角膜os:<br/>1-正常;<br/>2-异常;                |
| cornea_describe_os           | String     | 否    | 角膜描述os:<br/>创伤/疤痕;<br />溃疡;<br />水肿;<br />手术切口; |
| atria_select_od              | String     | 否    | 前房od;<br/>1-正常;<br/>2-异常;                |
| atria_describe_od            | String     | 否    | 前房描述od:<br/>狭窄;<br/>关闭;<br/>无法观察;        |
| atria_select_os              | String     | 否    | 前房os:<br/>1-正常;<br/>2-异常;                |
| atria_describe_os            | String     | 否    | 前房描述os:<br/>狭窄;<br/>关闭;<br/>无法观察;        |
| iris_select_od               | String     | 否    | 虹膜od:<br/>1-正常;<br/>2-异常;                |
| iris_describe_od             | String     | 否    | 虹膜描述od:<br/>褪色;<br/>无法观察;                |
| iris_select_os               | String     | 否    | 虹膜os:<br/>1-正常;<br/>2-异常;                |
| iris_describe_os             | String     | 否    | 虹膜描述os<br/>褪色;<br/>无法观察;                 |
| pupil_select_od              | String     | 否    | 瞳孔od:<br/>1-正常;<br/>2-异常;                |
| pupil_describe_od            | String     | 否    | 瞳孔描述od:<br/>不规划;<br/>闭锁;<br/>不可见;        |
| pupil_select_os              | String     | 否    | 瞳孔os;<br/>1-正常;<br/>2-异常;                |
| pupil_describe_os            | String     | 否    | 瞳孔描述os:<br/>不规划;<br/>闭锁;<br/>不可见;        |
| crystalline_lens_select_od   | String     | 否    | 晶状体od;<br/>1-正常;<br/>2-异常;               |
| crystalline_lens_describe_od | String     | 否    | 晶状体描述od:<br/>轻度不透明;<br/>重度不透明;<br/>严重不透明;<br/>人工晶体;<br/>无晶体;<br/>不可见; |
| crystalline_lens_select_os   | String     | 否    | 晶状体os;<br/>1-正常;<br/>2-异常;               |
| crystalline_lens_describe_os | String     | 否    | 晶状体描述os:<br/>轻度不透明;<br/>重度不透明;<br/>严重不透明;<br/>人工晶体;<br/>无晶体;<br/>不可见; |
| 眼底检查fundus_check             | Object     | 否    | 模板                                       |
| yellow_spot_select_od        | String     | 否    | 黄斑od:<br/>1-正常;<br/>2-异常                 |
| yellow_spot_describe_od      | String     | 否    | 黄斑描述od:<br/>黄斑前膜;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>不可见; |
| yellow_spot_select_os        | String     | 否    | 黄斑os:<br/>1-正常;<br/>2-异常                 |
| yellow_spot_describe_os      | String     | 否    | 黄斑描述os:<br/>黄斑前膜;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>不可见; |
| optic_disk_select_od         | String     | 否    | 视盘od:<br/>1-正常;<br/>2-异常                 |
| optic_disk_describe_od       | String     | 否    | 视盘描述od:<br/>出血;<br/>萎缩;<br/>怀盘比异常;<br/>不可见; |
| optic_disk_select_os         | String     | 否    | 视盘os:<br/>1-正常;<br/>2-异常                 |
| optic_disk_describe_os       | String     | 否    | 视盘描述os:<br/>出血;<br/>萎缩;<br/>怀盘比异常;<br/>不可见; |
| blood_vessel_select_od       | String     | 否    | 血管od:<br/>1-正常;<br/>2-异常                 |
| blood_vessel_describe_od     | String     | 否    | 血管描述od:<br/>出血;<br/>渗出;<br/>新生血管;<br/>不可见; |
| blood_vessel_select_os       | String     | 否    | 血管os:<br/>1-正常;<br/>2-异常                 |
| blood_vessel_describe_os     | String     | 否    | 血管描述os:<br/>出血;<br/>渗出;<br/>新生血管;<br/>不可见; |
| total_select_od              | String     | 否    | 总体情况od:<br/>1-正常;<br/>2-异常               |
| total_describe_od            | String     | 否    | 总体情况描述od:<br/>豹纹状眼底;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>水肿;<br/>不可见; |
| total_select_os              | String     | 否    | 总体情况os:<br/>1-正常;<br/>2-异常               |
| total_describe_os            | String     | 否    | 总体情况描述os:<br/>豹纹状眼底;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>水肿;<br/>不可见; |
| else_od                      | String     | 否    | 其他od                                     |
| else_os                      | String     | 否    | 其他os                                     |
| 诊断diagnose                   | ObjectList | 否    | 诊断表                                      |
| prescription                 | String     | 否    | 处方<br/>1-仅验光，不需要治疗;<br/>2-常规眼镜;<br/>3-低视力助视器;<br/>4-技能训练;多选时逗号分隔 |
| recommend_audiphone          | ObjectList | 否    | 推荐助视器                                    |
| 完成低视力检查和康复后after_check       |            |      | 模板                                       |
| can_distance                 | Integer    | 否    | 患者是否达到远距离视物的目标？<br/>1-是;<br/>2-否;<br/>3-部分可以; |
| can_near                     | Integer    | 否    | 患者是否达到近距离视物的目标？<br/>1-是;<br/>2-否;<br/>3-部分可以; |
| who_review                   | Integer    | 否    | 谁来完成低视力康复:<br/>1-护士;<br/>2-医生;           |
| if_visit                     | Integer    | 否    | 是否有下一次随访的安排:<br/>1-是;<br/>2-否;           |
| refuse_reason                | Integer    | 否    | 拒绝助视器的原因:<br/>1-太贵;<br/>2-考虑其他医学治疗;<br/>3-外观上无法接受;<br/>4-不确信是否需要;<br/>5-其他 |
| refuse_reason_else           | String     | 否    | 拒绝助视器的原因其他                               |
| 花费cost                       |            |      | 花费                                       |
| check_cost                   | String     | 否    | 检查费用                                     |
| review_cost                  | String     | 否    | 康复费用                                     |
| typoscope_cost               | String     | 否    | 助听器费用                                    |
| total_cast                   | String     | 否    | 合计，总共费用，单位元                              |
| patient_pay                  | String     | 否    | 病人支付                                     |
| charity_pay                  | String     | 否    | 慈善机构支付                                   |
| insurance_pay                | String     | 否    | 保险支付                                     |
| else_pay                     | String     | 否    | 其他                                       |


###### 眼科诊断列表

| 参数名                | 类型     | 必填   | 说明     |
| ------------------ | ------ | ---- | ------ |
| eye_diagnosis_pre  | String | 否    | 眼科诊断前缀 |
| eye_diagnosis_mian | String | 是    | 眼科诊断诊断 |
| eye_diagnosis_sufx | String | 否    | 眼科诊断后缀 |


##### 诊断

1. 就诊诊断信息表
2. 类型为ObjectList

| 参数名            | 类型      | 必填   | 说明              |
| -------------- | ------- | ---- | --------------- |
| diag_pre_id    | String  | 否    | 前缀ID            |
| diag_pre_name  | String  | 是    | 前缀内容            |
| diag_id        | String  | 否    | 诊断id            |
| diag_name      | String  | 是    | 诊断名称            |
| diag_icd       | String  | 否    | 诊断ICD编码，剑形编码，病因 |
| diag_attach    | String  | 是    | 附加码             |
| diag_sufx_id   | String  | 否    | 后缀ID            |
| diag_sufx_name | String  | 是    | 后缀内容            |
| diag_master    | Integer | 是    | 是否是主诊断;0-不是;1-是 |

##### 推荐助视器

1. 全为模板数据
2. 模板项存储时，在原来的key后面添加 _{第几条数据的index，从1开始}; 如第一条 recommend_audiphone_2_1;
3. 选择不同的推荐助听器后，商品内容会改变。

| 参数名                       | 类型      | 必填   | 说明                                       |
| ------------------------- | ------- | ---- | ---------------------------------------- |
| recommend_audiphone_1     | Integer | 是    | 推荐助听器-类型<br/>1-近用助视器;<br/>2-远用助视器;<br/>3-非光学助视器;<br/>4-其他助视器和训练;<br/>5-其他 |
| recommend_audiphone_2     | Integer | 是    | 推荐助听器-商品，具体内容见下表                         |
| recommend_audiphone_3     | String  | 否    | 推荐助听器-放大率，当类型选择1-近用助视器、2-远用助视器时有效        |
| recommend_audiphone_4     | String  | 否    | 使用助听器后的视力                                |
| recommend_audiphone_radio | Integer | 是    | 推荐助听器<br/>1-接受;<br/>2-不接受                |

###### 推荐助听器-商品

| 值    | 说明      | 所属类型    |
| ---- | ------- | ------- |
| 1    | 手持放大镜   | 1-近用助视器 |
| 2    | 立式放大镜   | 1-近用助视器 |
| 3    | 袖珍放大镜   | 1-近用助视器 |
| 4    | 高度数眼镜   | 1-近用助视器 |
| 5    | 便携式CCTV | 1-近用助视器 |

| 值    | 说明     | 所属类型    |
| ---- | ------ | ------- |
| 1    | 眼镜式望远镜 | 2-远用助视器 |
| 2    | 手持望远镜  | 2-远用助视器 |

| 值    | 说明        | 所属类型     |
| ---- | --------- | -------- |
| 1    | 盲杖        | 3-非光学助视器 |
| 2    | 其他帮助行走的设备 | 3-非光学助视器 |
| 3    | 大字体电脑     | 3-非光学助视器 |
| 4    | 水位报警器     | 3-非光学助视器 |
| 5    | 裂口阅读器     | 3-非光学助视器 |
| 6    | 标记笔       | 3-非光学助视器 |
| 7    | 护指套       | 3-非光学助视器 |


#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 专科检查-低视力随访获取

```htt
[GET]/treat_service/speciality_check/low_vision/second
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数


| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数


| 参数名                          | 类型         | 必填   | 说明                                       |
| ---------------------------- | ---------- | ---- | ---------------------------------------- |
| trea_id                      | String     | 是    | 就诊ID                                     |
| 低视力首诊问卷部分low_vision_first    |            |      | 模板                                       |
| how_to_know                  | Integer    | 否    | 你是如何得知我们低视力中心的;<br />1-我/我们自己得知;<br />2-我们医院的医生推荐;<br />3-从筛查中得知;<br />4-其他机构推荐 |
| eye_diagnosis                | ObjectList | 否    | 眼科诊断                                     |
| all_diagnosis_main           | String     | 否    | 全身疾病主诊断                                  |
| all_diagnosis_next           | String     | 否    | 全身疾病次诊断                                  |
| whether_photophobia          | Integer    | 否    | 是否畏光/眩光;1-否;1-是;2-未询问                    |
| whether_raise                | Integer    | 否    | 戴原镜视力是否提高;1-否;1-是;2-未询问                  |
| qlq_select                   | Integer    | 否    | 生活质量问卷调查;1-ELVQOL;2-LVQOL;2-未回答          |
| qlq_reason                   | Integer    | 否    | 生活质量问卷调查未回答原因;<br />1-拒绝合作;<br />2-不能理解问题的意义;<br />3-语言不通不能交流;<br />4-认知障碍，无法合作;<br />5-仅验光;<br />6-跟踪随访少于6个月; |
| action_chief_select          | String     | 否    | 主诉选择项;<br />1-远视力降低;<br />2-近视力降低;<br />3-行走能力降低;<br />多选时使用逗号分隔 |
| action_chief_else            | String     | 否    | 主诉其他                                     |
| distant_vision_select        | String     | 否    | 远视力目标选择;<br />1-看电视看电影;<br />2-做家务;<br />3-从事工作;<br />4-使用公共交通;<br />5-开车;<br />6-室内行走;<br />7-从事业务好爱;<br />8-独立在街上行走;<br/>多选时使用逗号分隔 |
| distant_vision_else          | String     | 否    | 远视力其他                                    |
| near_vision_select           | String     | 否    | 近视力目标选择;<br />1- 提高书写能力;<br />2- 提高阅读能力;<br />3- 从事工作;<br />4- 从事业余爱好;<br />多选时使用逗号分隔 |
| near_vision_else             | String     | 否    | 近视力其他                                    |
| emotion                      | Integer    | 否    | 病人情绪是否低落;<br/>1-否;<br/>2-是;              |
| memory                       | Integer    | 否    | 病人记忆力/认知能力如何;<br/>1-好;<br/>2-不错;<br/>3-差; |
| walk_select                  | Integer    | 否    | 病人是否有行走问题;<br/>1-否;<br/>2-是;             |
| walk_vision                  | Integer    | 否    | 病人是否有行走问题-原因;<br/>1-视力问题;<br/>2-身体条件受限;  |
| walk_tool                    | Integer    | 否    | 病人是否有行走问题- 帮助行走的工具;<br/>1-盲杖;<br/>2-助行架;<br/>3-轮椅;<br/>4-其他; |
| walk_method                  | Integer    | 否    | 病人是否有行走问题-如何来到这里;<br/>1-依靠自己来到这里;<br/>2-依靠他人来到这里; |
| 临床检查结果-视功能computer_optometry |            |      | 模板加表                                     |
| 电脑验光computer_optometry       |            |      | 电脑验光                                     |
| data_od_sphere               | String     | 否    | 电脑验光球镜od                                 |
| data_od_cylinder             | String     | 否    | 电脑验光柱镜od                                 |
| data_od_axis                 | String     | 否    | 电脑验光轴向od                                 |
| data_od_rem                  | String     | 否    | 电脑验光OD备注                                 |
| data_os_sphere               | String     | 否    | 电脑验光球镜os                                 |
| data_os_cylinder             | String     | 否    | 电脑验光柱镜os                                 |
| data_os_axis                 | String     | 否    | 电脑验光轴向os                                 |
| data_os_rem                  | String     | 否    | 电脑验光OS备注                                 |
| 瞳距pd                         |            |      | 框架眼镜处方                                   |
| opto_far_pd                  | String     | 否    | 瞳距-远用                                    |
| opto_near_pd                 | String     | 否    | 瞳距-近用                                    |
| opto_od_pd                   | String     | 否    | 瞳距-单眼OD                                  |
| opto_os_pd                   | String     | 否    | 瞳距-单眼OS                                  |
| opto_pd_rem                  | String     | 否    | 瞳距-备注                                    |
| 检影验光retinoscopy              |            |      | 检影验光表                                    |
| retinoscopy_od_sphere        | String     | 否    | 检影验光OD-球镜                                |
| retinoscopy_od_cylinder      | String     | 否    | 检影验光OD-柱镜                                |
| retinoscopy_od_axis          | String     | 否    | 检影验光OD-轴向                                |
| retinoscopy_od_vision        | String     | 否    | 检影验光OD-视力                                |
| retinoscopy_od_memo          | String     | 否    | 检影验光OD-备注                                |
| retinoscopy_os_sphere        | String     | 否    | 检影验光OS-球镜                                |
| retinoscopy_os_cylinder      | String     | 否    | 检影验光OS-柱镜                                |
| retinoscopy_os_axis          | String     | 否    | 检影验光OS-轴向                                |
| retinoscopy_os_vision        | String     | 否    | 检影验光OS-视力                                |
| retinoscopy_os_memo          | String     | 否    | 检影验光OS-备注                                |
| 主觉验光subjective               |            |      | 主觉验光数据表                                  |
| subjective_od_sphere         | String     | 否    | 主觉验光OD-球镜                                |
| subjective_od_cylinder       | String     | 否    | 主觉验光OD-柱镜                                |
| subjective_od_axis           | String     | 否    | 主觉验光OD-轴向                                |
| subjective_od_prism          | String     | 否    | 主觉验光OD-棱镜                                |
| subjective_od_vision         | String     | 否    | 主觉验光OD-视力                                |
| subjective_od_memo           | String     | 否    | 主觉验光OD-备注                                |
| subjective_os_sphere         | String     | 否    | 主觉验光OS-球镜                                |
| subjective_os_cylinder       | String     | 否    | 主觉验光OS-柱镜                                |
| subjective_os_axis           | String     | 否    | 主觉验光OS-轴向                                |
| subjective_os_prism          | String     | 否    | 主觉验光OS-棱镜                                |
| subjective_os_vision         | String     | 否    | 主觉验光OS-视力                                |
| subjective_os_memo           | String     | 否    | 主觉验光OS-备注                                |
| 裂隙灯检查slit_lamp_check         |            |      | 模板                                       |
| eye_appear_select_od         | String     | 否    | 眼睛外观od:<br/>1-正常;<br/>2-异常;              |
| eye_appear_describe_od       | String     | 否    | 眼睛外观描述od:<br/>水平性眼球震颤;<br/>垂直性眼球震颤;<br/>外斜视;<br/>内斜视;<br/>上睑下垂;<br/>水肿; |
| eye_appear_select_os         | String     | 否    | 眼睛外观os:<br/>1-正常;<br/>2-异常;              |
| eye_appear_describe_os       | String     | 否    | 眼睛外观描述os:<br/>水平性眼球震颤;<br/>垂直性眼球震颤;<br/>外斜视;<br/>内斜视;<br/>上睑下垂;<br/>水肿; |
| sclera_select_od             | String     | 否    | 巩膜od:<br/>1-正常;<br/>2-异常;                |
| sclera_describe_od           | String     | 否    | 巩膜描述od                                   |
| sclera_select_os             | String     | 否    | 巩膜os:<br/>1-正常;<br/>2-异常;                |
| sclera_describe_os           | String     | 否    | 巩膜描述os                                   |
| conjunctiva_select_od        | String     | 否    | 结膜od:<br/>1-正常;<br/>2-异常;                |
| conjunctiva_describe_od      | String     | 否    | 结膜描述od                                   |
| conjunctiva_select_os        | String     | 否    | 结膜os:<br/>1-正常;<br/>2-异常;                |
| conjunctiva_describe_os      | String     | 否    | 结膜描述os                                   |
| pterygium_select_od          | String     | 否    | 翼状胬肉od:<br/>1-正常;<br/>2-异常;              |
| pterygium_describe_od        | String     | 否    | 翼状胬肉描述od                                 |
| pterygium_select_os          | String     | 否    | 翼状胬肉os:<br/>1-正常;<br/>2-异常;              |
| pterygium_describe_os        | String     | 否    | 翼状胬肉描述os                                 |
| cornea_select_od             | String     | 否    | 角膜od:<br/>1-正常;<br/>2-异常;                |
| cornea_describe_od           | String     | 否    | 角膜描述od:<br />创伤/疤痕;<br />溃疡;<br />水肿;<br />手术切口; |
| cornea_select_os             | String     | 否    | 角膜os:<br/>1-正常;<br/>2-异常;                |
| cornea_describe_os           | String     | 否    | 角膜描述os:<br/>创伤/疤痕;<br />溃疡;<br />水肿;<br />手术切口; |
| atria_select_od              | String     | 否    | 前房od;<br/>1-正常;<br/>2-异常;                |
| atria_describe_od            | String     | 否    | 前房描述od:<br/>狭窄;<br/>关闭;<br/>无法观察;        |
| atria_select_os              | String     | 否    | 前房os:<br/>1-正常;<br/>2-异常;                |
| atria_describe_os            | String     | 否    | 前房描述os:<br/>狭窄;<br/>关闭;<br/>无法观察;        |
| iris_select_od               | String     | 否    | 虹膜od:<br/>1-正常;<br/>2-异常;                |
| iris_describe_od             | String     | 否    | 虹膜描述od:<br/>褪色;<br/>无法观察;                |
| iris_select_os               | String     | 否    | 虹膜os:<br/>1-正常;<br/>2-异常;                |
| iris_describe_os             | String     | 否    | 虹膜描述os<br/>褪色;<br/>无法观察;                 |
| pupil_select_od              | String     | 否    | 瞳孔od:<br/>1-正常;<br/>2-异常;                |
| pupil_describe_od            | String     | 否    | 瞳孔描述od:<br/>不规划;<br/>闭锁;<br/>不可见;        |
| pupil_select_os              | String     | 否    | 瞳孔os;<br/>1-正常;<br/>2-异常;                |
| pupil_describe_os            | String     | 否    | 瞳孔描述os:<br/>不规划;<br/>闭锁;<br/>不可见;        |
| crystalline_lens_select_od   | String     | 否    | 晶状体od;<br/>1-正常;<br/>2-异常;               |
| crystalline_lens_describe_od | String     | 否    | 晶状体描述od:<br/>轻度不透明;<br/>重度不透明;<br/>严重不透明;<br/>人工晶体;<br/>无晶体;<br/>不可见; |
| crystalline_lens_select_os   | String     | 否    | 晶状体os;<br/>1-正常;<br/>2-异常;               |
| crystalline_lens_describe_os | String     | 否    | 晶状体描述os:<br/>轻度不透明;<br/>重度不透明;<br/>严重不透明;<br/>人工晶体;<br/>无晶体;<br/>不可见; |
| 眼底检查fundus_check             | Object     | 否    | 模板                                       |
| yellow_spot_select_od        | String     | 否    | 黄斑od:<br/>1-正常;<br/>2-异常                 |
| yellow_spot_describe_od      | String     | 否    | 黄斑描述od:<br/>黄斑前膜;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>不可见; |
| yellow_spot_select_os        | String     | 否    | 黄斑os:<br/>1-正常;<br/>2-异常                 |
| yellow_spot_describe_os      | String     | 否    | 黄斑描述os:<br/>黄斑前膜;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>不可见; |
| optic_disk_select_od         | String     | 否    | 视盘od:<br/>1-正常;<br/>2-异常                 |
| optic_disk_describe_od       | String     | 否    | 视盘描述od:<br/>出血;<br/>萎缩;<br/>怀盘比异常;<br/>不可见; |
| optic_disk_select_os         | String     | 否    | 视盘os:<br/>1-正常;<br/>2-异常                 |
| optic_disk_describe_os       | String     | 否    | 视盘描述os:<br/>出血;<br/>萎缩;<br/>怀盘比异常;<br/>不可见; |
| blood_vessel_select_od       | String     | 否    | 血管od:<br/>1-正常;<br/>2-异常                 |
| blood_vessel_describe_od     | String     | 否    | 血管描述od:<br/>出血;<br/>渗出;<br/>新生血管;<br/>不可见; |
| blood_vessel_select_os       | String     | 否    | 血管os:<br/>1-正常;<br/>2-异常                 |
| blood_vessel_describe_os     | String     | 否    | 血管描述os:<br/>出血;<br/>渗出;<br/>新生血管;<br/>不可见; |
| total_select_od              | String     | 否    | 总体情况od:<br/>1-正常;<br/>2-异常               |
| total_describe_od            | String     | 否    | 总体情况描述od:<br/>豹纹状眼底;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>水肿;<br/>不可见; |
| total_select_os              | String     | 否    | 总体情况os:<br/>1-正常;<br/>2-异常               |
| total_describe_os            | String     | 否    | 总体情况描述os:<br/>豹纹状眼底;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>水肿;<br/>不可见; |
| else_od                      | String     | 否    | 其他od                                     |
| else_os                      | String     | 否    | 其他os                                     |
| diagnose                     | ObjectList | 否    | 诊断                                       |
| prescription                 | String     | 否    | 处方<br/>1-仅验光，不需要治疗;<br/>2-常规眼镜;<br/>3-低视力助视器;<br/>4-技能训练;多选时逗号分隔 |
| recommend_audiphone          | ObjectList | 否    | 推荐助视器                                    |
| 完成低视力检查和康复后after_check       |            |      | 模板                                       |
| can_distance                 | Integer    | 否    | 患者是否达到远距离视物的目标？<br/>1-是;<br/>2-否;<br/>3-部分可以; |
| can_near                     | Integer    | 否    | 患者是否达到近距离视物的目标？<br/>1-是;<br/>2-否;<br/>3-部分可以; |
| who_review                   | Integer    | 否    | 谁来完成低视力康复:<br/>1-护士;<br/>2-医生;           |
| if_visit                     | Integer    | 否    | 是否有下一次随访的安排:<br/>1-是;<br/>2-否;           |
| refuse_reason                | Integer    | 否    | 拒绝助视器的原因:<br/>1-太贵;<br/>2-考虑其他医学治疗;<br/>3-外观上无法接受;<br/>4-不确信是否需要;<br/>5-其他 |
| refuse_reason_else           | String     | 否    | 拒绝助视器的原因其他                               |
| 花费cost                       |            |      | 花费                                       |
| check_cost                   | String     | 否    | 检查费用                                     |
| review_cost                  | String     | 否    | 康复费用                                     |
| typoscope_cost               | String     | 否    | 助听器费用                                    |
| total_cast                   | String     | 否    | 合计，总共费用，单位元                              |
| patient_pay                  | String     | 否    | 病人支付                                     |
| charity_pay                  | String     | 否    | 慈善机构支付                                   |
| insurance_pay                | String     | 否    | 保险支付                                     |
| else_pay                     | String     | 否    | 其他                                       |



###### 眼科诊断列表

| 参数名                | 类型     | 必填   | 说明     |
| ------------------ | ------ | ---- | ------ |
| eye_diagnosis_pre  | String | 否    | 眼科诊断前缀 |
| eye_diagnosis_mian | String | 是    | 眼科诊断诊断 |
| eye_diagnosis_sufx | String | 否    | 眼科诊断后缀 |



##### 诊断

1. 就诊诊断信息表
2. 类型为ObjectList

| 参数名            | 类型      | 必填   | 说明              |
| -------------- | ------- | ---- | --------------- |
| diag_pre_id    | String  | 否    | 前缀ID            |
| diag_pre_name  | String  | 是    | 前缀内容            |
| diag_id        | String  | 否    | 诊断id            |
| diag_name      | String  | 是    | 诊断名称            |
| diag_icd       | String  | 否    | 诊断ICD编码，剑形编码，病因 |
| diag_attach    | String  | 是    | 附加码             |
| diag_sufx_id   | String  | 否    | 后缀ID            |
| diag_sufx_name | String  | 是    | 后缀内容            |
| diag_master    | Integer | 是    | 是否是主诊断;0-不是;1-是 |

##### 推荐助视器

1. 全为模板数据
2. 模板项存储时，在原来的key后面添加 _{第几条数据的index，从1开始}; 如第一条 recommend_audiphone_2_1;
3. 选择不同的推荐助听器后，商品内容会改变。

| 参数名                       | 类型      | 必填   | 说明                                       |
| ------------------------- | ------- | ---- | ---------------------------------------- |
| recommend_audiphone_1     | Integer | 是    | 推荐助听器-类型<br/>1-近用助视器;<br/>2-远用助视器;<br/>3-非光学助视器;<br/>4-其他助视器和训练;<br/>5-其他 |
| recommend_audiphone_2     | Integer | 是    | 推荐助听器-商品，具体内容见下表                         |
| recommend_audiphone_3     | String  | 否    | 推荐助听器-放大率，当类型选择1-近用助视器、2-远用助视器时有效        |
| recommend_audiphone_4     | String  | 否    | 使用助听器后的视力                                |
| recommend_audiphone_radio | Integer | 是    | 推荐助听器<br/>1-接受;<br/>2-不接受                |

###### 推荐助听器-商品

| 值    | 说明      | 所属类型    |
| ---- | ------- | ------- |
| 1    | 手持放大镜   | 1-近用助视器 |
| 2    | 立式放大镜   | 1-近用助视器 |
| 3    | 袖珍放大镜   | 1-近用助视器 |
| 4    | 高度数眼镜   | 1-近用助视器 |
| 5    | 便携式CCTV | 1-近用助视器 |

| 值    | 说明     | 所属类型    |
| ---- | ------ | ------- |
| 1    | 眼镜式望远镜 | 2-远用助视器 |
| 2    | 手持望远镜  | 2-远用助视器 |

| 值    | 说明        | 所属类型     |
| ---- | --------- | -------- |
| 1    | 盲杖        | 3-非光学助视器 |
| 2    | 其他帮助行走的设备 | 3-非光学助视器 |
| 3    | 大字体电脑     | 3-非光学助视器 |
| 4    | 水位报警器     | 3-非光学助视器 |
| 5    | 裂口阅读器     | 3-非光学助视器 |
| 6    | 标记笔       | 3-非光学助视器 |
| 7    | 护指套       | 3-非光学助视器 |






### 专科检查-低视力随访保存

```htt
[POST]/treat_service/speciality_check/low_vision/second
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |

#### 请求报文参数

| 参数名                          | 类型         | 必填   | 说明                                       |
| ---------------------------- | ---------- | ---- | ---------------------------------------- |
| trea_id                      | String     | 是    | 就诊ID                                     |
| 低视力首诊问卷部分low_vision_first    |            |      | 模板                                       |
| how_to_know                  | Integer    | 否    | 你是如何得知我们低视力中心的;<br />1-我/我们自己得知;<br />2-我们医院的医生推荐;<br />3-从筛查中得知;<br />4-其他机构推荐 |
| eye_diagnosis                | ObjectList | 否    | 眼科诊断                                     |
| all_diagnosis_main           | String     | 否    | 全身疾病主诊断                                  |
| all_diagnosis_next           | String     | 否    | 全身疾病次诊断                                  |
| whether_photophobia          | Integer    | 否    | 是否畏光/眩光;1-否;1-是;2-未询问                    |
| whether_raise                | Integer    | 否    | 戴原镜视力是否提高;1-否;1-是;2-未询问                  |
| qlq_select                   | Integer    | 否    | 生活质量问卷调查;1-ELVQOL;2-LVQOL;2-未回答          |
| qlq_reason                   | Integer    | 否    | 生活质量问卷调查未回答原因;<br />1-拒绝合作;<br />2-不能理解问题的意义;<br />3-语言不通不能交流;<br />4-认知障碍，无法合作;<br />5-仅验光;<br />6-跟踪随访少于6个月; |
| action_chief_select          | String     | 否    | 主诉选择项;<br />1-远视力降低;<br />2-近视力降低;<br />3-行走能力降低;<br />多选时使用逗号分隔 |
| action_chief_else            | String     | 否    | 主诉其他                                     |
| distant_vision_select        | String     | 否    | 远视力目标选择;<br />1-看电视看电影;<br />2-做家务;<br />3-从事工作;<br />4-使用公共交通;<br />5-开车;<br />6-室内行走;<br />7-从事业务好爱;<br />8-独立在街上行走;<br/>多选时使用逗号分隔 |
| distant_vision_else          | String     | 否    | 远视力其他                                    |
| near_vision_select           | String     | 否    | 近视力目标选择;<br />1- 提高书写能力;<br />2- 提高阅读能力;<br />3- 从事工作;<br />4- 从事业余爱好;<br />多选时使用逗号分隔 |
| near_vision_else             | String     | 否    | 近视力其他                                    |
| emotion                      | Integer    | 否    | 病人情绪是否低落;<br/>1-否;<br/>2-是;              |
| memory                       | Integer    | 否    | 病人记忆力/认知能力如何;<br/>1-好;<br/>2-不错;<br/>3-差; |
| walk_select                  | Integer    | 否    | 病人是否有行走问题;<br/>1-否;<br/>2-是;             |
| walk_vision                  | Integer    | 否    | 病人是否有行走问题-原因;<br/>1-视力问题;<br/>2-身体条件受限;  |
| walk_tool                    | Integer    | 否    | 病人是否有行走问题- 帮助行走的工具;<br/>1-盲杖;<br/>2-助行架;<br/>3-轮椅;<br/>4-其他; |
| walk_method                  | Integer    | 否    | 病人是否有行走问题-如何来到这里;<br/>1-依靠自己来到这里;<br/>2-依靠他人来到这里; |
| 临床检查结果-视功能computer_optometry |            |      | 模板加表                                     |
| 电脑验光computer_optometry       |            |      | 电脑验光                                     |
| data_od_sphere               | String     | 否    | 电脑验光球镜od                                 |
| data_od_cylinder             | String     | 否    | 电脑验光柱镜od                                 |
| data_od_axis                 | String     | 否    | 电脑验光轴向od                                 |
| data_od_rem                  | String     | 否    | 电脑验光OD备注                                 |
| data_os_sphere               | String     | 否    | 电脑验光球镜os                                 |
| data_os_cylinder             | String     | 否    | 电脑验光柱镜os                                 |
| data_os_axis                 | String     | 否    | 电脑验光轴向os                                 |
| data_os_rem                  | String     | 否    | 电脑验光OS备注                                 |
| 瞳距pd                         |            |      | 框架眼镜处方                                   |
| opto_far_pd                  | String     | 否    | 瞳距-远用                                    |
| opto_near_pd                 | String     | 否    | 瞳距-近用                                    |
| opto_od_pd                   | String     | 否    | 瞳距-单眼OD                                  |
| opto_os_pd                   | String     | 否    | 瞳距-单眼OS                                  |
| opto_pd_rem                  | String     | 否    | 瞳距-备注                                    |
| 检影验光retinoscopy              |            |      | 检影验光表                                    |
| retinoscopy_od_sphere        | String     | 否    | 检影验光OD-球镜                                |
| retinoscopy_od_cylinder      | String     | 否    | 检影验光OD-柱镜                                |
| retinoscopy_od_axis          | String     | 否    | 检影验光OD-轴向                                |
| retinoscopy_od_vision        | String     | 否    | 检影验光OD-视力                                |
| retinoscopy_od_memo          | String     | 否    | 检影验光OD-备注                                |
| retinoscopy_os_sphere        | String     | 否    | 检影验光OS-球镜                                |
| retinoscopy_os_cylinder      | String     | 否    | 检影验光OS-柱镜                                |
| retinoscopy_os_axis          | String     | 否    | 检影验光OS-轴向                                |
| retinoscopy_os_vision        | String     | 否    | 检影验光OS-视力                                |
| retinoscopy_os_memo          | String     | 否    | 检影验光OS-备注                                |
| 主觉验光subjective               |            |      | 主觉验光数据表                                  |
| subjective_od_sphere         | String     | 否    | 主觉验光OD-球镜                                |
| subjective_od_cylinder       | String     | 否    | 主觉验光OD-柱镜                                |
| subjective_od_axis           | String     | 否    | 主觉验光OD-轴向                                |
| subjective_od_prism          | String     | 否    | 主觉验光OD-棱镜                                |
| subjective_od_vision         | String     | 否    | 主觉验光OD-视力                                |
| subjective_od_memo           | String     | 否    | 主觉验光OD-备注                                |
| subjective_os_sphere         | String     | 否    | 主觉验光OS-球镜                                |
| subjective_os_cylinder       | String     | 否    | 主觉验光OS-柱镜                                |
| subjective_os_axis           | String     | 否    | 主觉验光OS-轴向                                |
| subjective_os_prism          | String     | 否    | 主觉验光OS-棱镜                                |
| subjective_os_vision         | String     | 否    | 主觉验光OS-视力                                |
| subjective_os_memo           | String     | 否    | 主觉验光OS-备注                                |
| 裂隙灯检查slit_lamp_check         |            |      | 模板                                       |
| eye_appear_select_od         | String     | 否    | 眼睛外观od:<br/>1-正常;<br/>2-异常;              |
| eye_appear_describe_od       | String     | 否    | 眼睛外观描述od:<br/>水平性眼球震颤;<br/>垂直性眼球震颤;<br/>外斜视;<br/>内斜视;<br/>上睑下垂;<br/>水肿; |
| eye_appear_select_os         | String     | 否    | 眼睛外观os:<br/>1-正常;<br/>2-异常;              |
| eye_appear_describe_os       | String     | 否    | 眼睛外观描述os:<br/>水平性眼球震颤;<br/>垂直性眼球震颤;<br/>外斜视;<br/>内斜视;<br/>上睑下垂;<br/>水肿; |
| sclera_select_od             | String     | 否    | 巩膜od:<br/>1-正常;<br/>2-异常;                |
| sclera_describe_od           | String     | 否    | 巩膜描述od                                   |
| sclera_select_os             | String     | 否    | 巩膜os:<br/>1-正常;<br/>2-异常;                |
| sclera_describe_os           | String     | 否    | 巩膜描述os                                   |
| conjunctiva_select_od        | String     | 否    | 结膜od:<br/>1-正常;<br/>2-异常;                |
| conjunctiva_describe_od      | String     | 否    | 结膜描述od                                   |
| conjunctiva_select_os        | String     | 否    | 结膜os:<br/>1-正常;<br/>2-异常;                |
| conjunctiva_describe_os      | String     | 否    | 结膜描述os                                   |
| pterygium_select_od          | String     | 否    | 翼状胬肉od:<br/>1-正常;<br/>2-异常;              |
| pterygium_describe_od        | String     | 否    | 翼状胬肉描述od                                 |
| pterygium_select_os          | String     | 否    | 翼状胬肉os:<br/>1-正常;<br/>2-异常;              |
| pterygium_describe_os        | String     | 否    | 翼状胬肉描述os                                 |
| cornea_select_od             | String     | 否    | 角膜od:<br/>1-正常;<br/>2-异常;                |
| cornea_describe_od           | String     | 否    | 角膜描述od:<br />创伤/疤痕;<br />溃疡;<br />水肿;<br />手术切口; |
| cornea_select_os             | String     | 否    | 角膜os:<br/>1-正常;<br/>2-异常;                |
| cornea_describe_os           | String     | 否    | 角膜描述os:<br/>创伤/疤痕;<br />溃疡;<br />水肿;<br />手术切口; |
| atria_select_od              | String     | 否    | 前房od;<br/>1-正常;<br/>2-异常;                |
| atria_describe_od            | String     | 否    | 前房描述od:<br/>狭窄;<br/>关闭;<br/>无法观察;        |
| atria_select_os              | String     | 否    | 前房os:<br/>1-正常;<br/>2-异常;                |
| atria_describe_os            | String     | 否    | 前房描述os:<br/>狭窄;<br/>关闭;<br/>无法观察;        |
| iris_select_od               | String     | 否    | 虹膜od:<br/>1-正常;<br/>2-异常;                |
| iris_describe_od             | String     | 否    | 虹膜描述od:<br/>褪色;<br/>无法观察;                |
| iris_select_os               | String     | 否    | 虹膜os:<br/>1-正常;<br/>2-异常;                |
| iris_describe_os             | String     | 否    | 虹膜描述os<br/>褪色;<br/>无法观察;                 |
| pupil_select_od              | String     | 否    | 瞳孔od:<br/>1-正常;<br/>2-异常;                |
| pupil_describe_od            | String     | 否    | 瞳孔描述od:<br/>不规划;<br/>闭锁;<br/>不可见;        |
| pupil_select_os              | String     | 否    | 瞳孔os;<br/>1-正常;<br/>2-异常;                |
| pupil_describe_os            | String     | 否    | 瞳孔描述os:<br/>不规划;<br/>闭锁;<br/>不可见;        |
| crystalline_lens_select_od   | String     | 否    | 晶状体od;<br/>1-正常;<br/>2-异常;               |
| crystalline_lens_describe_od | String     | 否    | 晶状体描述od:<br/>轻度不透明;<br/>重度不透明;<br/>严重不透明;<br/>人工晶体;<br/>无晶体;<br/>不可见; |
| crystalline_lens_select_os   | String     | 否    | 晶状体os;<br/>1-正常;<br/>2-异常;               |
| crystalline_lens_describe_os | String     | 否    | 晶状体描述os:<br/>轻度不透明;<br/>重度不透明;<br/>严重不透明;<br/>人工晶体;<br/>无晶体;<br/>不可见; |
| 眼底检查fundus_check             | Object     | 否    | 模板                                       |
| yellow_spot_select_od        | String     | 否    | 黄斑od:<br/>1-正常;<br/>2-异常                 |
| yellow_spot_describe_od      | String     | 否    | 黄斑描述od:<br/>黄斑前膜;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>不可见; |
| yellow_spot_select_os        | String     | 否    | 黄斑os:<br/>1-正常;<br/>2-异常                 |
| yellow_spot_describe_os      | String     | 否    | 黄斑描述os:<br/>黄斑前膜;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>不可见; |
| optic_disk_select_od         | String     | 否    | 视盘od:<br/>1-正常;<br/>2-异常                 |
| optic_disk_describe_od       | String     | 否    | 视盘描述od:<br/>出血;<br/>萎缩;<br/>怀盘比异常;<br/>不可见; |
| optic_disk_select_os         | String     | 否    | 视盘os:<br/>1-正常;<br/>2-异常                 |
| optic_disk_describe_os       | String     | 否    | 视盘描述os:<br/>出血;<br/>萎缩;<br/>怀盘比异常;<br/>不可见; |
| blood_vessel_select_od       | String     | 否    | 血管od:<br/>1-正常;<br/>2-异常                 |
| blood_vessel_describe_od     | String     | 否    | 血管描述od:<br/>出血;<br/>渗出;<br/>新生血管;<br/>不可见; |
| blood_vessel_select_os       | String     | 否    | 血管os:<br/>1-正常;<br/>2-异常                 |
| blood_vessel_describe_os     | String     | 否    | 血管描述os:<br/>出血;<br/>渗出;<br/>新生血管;<br/>不可见; |
| total_select_od              | String     | 否    | 总体情况od:<br/>1-正常;<br/>2-异常               |
| total_describe_od            | String     | 否    | 总体情况描述od:<br/>豹纹状眼底;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>水肿;<br/>不可见; |
| total_select_os              | String     | 否    | 总体情况os:<br/>1-正常;<br/>2-异常               |
| total_describe_os            | String     | 否    | 总体情况描述os:<br/>豹纹状眼底;<br/>萎缩;<br/>出血;<br/>渗出;<br/>变性;<br/>水肿;<br/>不可见; |
| else_od                      | String     | 否    | 其他od                                     |
| else_os                      | String     | 否    | 其他os                                     |
| diagnose                     | ObjectList | 否    | 诊断                                       |
| prescription                 | String     | 否    | 处方<br/>1-仅验光，不需要治疗;<br/>2-常规眼镜;<br/>3-低视力助视器;<br/>4-技能训练;多选时逗号分隔 |
| recommend_audiphone          | ObjectList | 否    | 推荐助视器                                    |
| 完成低视力检查和康复后after_check       |            |      | 模板                                       |
| can_distance                 | Integer    | 否    | 患者是否达到远距离视物的目标？<br/>1-是;<br/>2-否;<br/>3-部分可以; |
| can_near                     | Integer    | 否    | 患者是否达到近距离视物的目标？<br/>1-是;<br/>2-否;<br/>3-部分可以; |
| who_review                   | Integer    | 否    | 谁来完成低视力康复:<br/>1-护士;<br/>2-医生;           |
| if_visit                     | Integer    | 否    | 是否有下一次随访的安排:<br/>1-是;<br/>2-否;           |
| refuse_reason                | Integer    | 否    | 拒绝助视器的原因:<br/>1-太贵;<br/>2-考虑其他医学治疗;<br/>3-外观上无法接受;<br/>4-不确信是否需要;<br/>5-其他 |
| refuse_reason_else           | String     | 否    | 拒绝助视器的原因其他                               |
| 花费cost                       |            |      | 花费                                       |
| check_cost                   | String     | 否    | 检查费用                                     |
| review_cost                  | String     | 否    | 康复费用                                     |
| typoscope_cost               | String     | 否    | 助听器费用                                    |
| total_cast                   | String     | 否    | 合计，总共费用，单位元                              |
| patient_pay                  | String     | 否    | 病人支付                                     |
| charity_pay                  | String     | 否    | 慈善机构支付                                   |
| insurance_pay                | String     | 否    | 保险支付                                     |
| else_pay                     | String     | 否    | 其他                                       |



###### 眼科诊断列表

| 参数名                | 类型     | 必填   | 说明     |
| ------------------ | ------ | ---- | ------ |
| eye_diagnosis_pre  | String | 否    | 眼科诊断前缀 |
| eye_diagnosis_mian | String | 是    | 眼科诊断诊断 |
| eye_diagnosis_sufx | String | 否    | 眼科诊断后缀 |



##### 诊断

1. 就诊诊断信息表
2. 类型为ObjectList

| 参数名            | 类型      | 必填   | 说明              |
| -------------- | ------- | ---- | --------------- |
| diag_pre_id    | String  | 否    | 前缀ID            |
| diag_pre_name  | String  | 是    | 前缀内容            |
| diag_id        | String  | 否    | 诊断id            |
| diag_name      | String  | 是    | 诊断名称            |
| diag_icd       | String  | 否    | 诊断ICD编码，剑形编码，病因 |
| diag_attach    | String  | 是    | 附加码             |
| diag_sufx_id   | String  | 否    | 后缀ID            |
| diag_sufx_name | String  | 是    | 后缀内容            |
| diag_master    | Integer | 是    | 是否是主诊断;0-不是;1-是 |

##### 推荐助视器

1. 全为模板数据
2. 模板项存储时，在原来的key后面添加 _{第几条数据的index，从1开始}; 如第一条 recommend_audiphone_2_1;
3. 选择不同的推荐助听器后，商品内容会改变。

| 参数名                       | 类型      | 必填   | 说明                                       |
| ------------------------- | ------- | ---- | ---------------------------------------- |
| recommend_audiphone_1     | Integer | 是    | 推荐助听器-类型<br/>1-近用助视器;<br/>2-远用助视器;<br/>3-非光学助视器;<br/>4-其他助视器和训练;<br/>5-其他 |
| recommend_audiphone_2     | Integer | 是    | 推荐助听器-商品，具体内容见下表                         |
| recommend_audiphone_3     | String  | 否    | 推荐助听器-放大率，当类型选择1-近用助视器、2-远用助视器时有效        |
| recommend_audiphone_4     | String  | 否    | 使用助听器后的视力                                |
| recommend_audiphone_radio | Integer | 是    | 推荐助听器<br/>1-接受;<br/>2-不接受                |

###### 推荐助听器-商品

| 值    | 说明      | 所属类型    |
| ---- | ------- | ------- |
| 1    | 手持放大镜   | 1-近用助视器 |
| 2    | 立式放大镜   | 1-近用助视器 |
| 3    | 袖珍放大镜   | 1-近用助视器 |
| 4    | 高度数眼镜   | 1-近用助视器 |
| 5    | 便携式CCTV | 1-近用助视器 |

| 值    | 说明     | 所属类型    |
| ---- | ------ | ------- |
| 1    | 眼镜式望远镜 | 2-远用助视器 |
| 2    | 手持望远镜  | 2-远用助视器 |

| 值    | 说明        | 所属类型     |
| ---- | --------- | -------- |
| 1    | 盲杖        | 3-非光学助视器 |
| 2    | 其他帮助行走的设备 | 3-非光学助视器 |
| 3    | 大字体电脑     | 3-非光学助视器 |
| 4    | 水位报警器     | 3-非光学助视器 |
| 5    | 裂口阅读器     | 3-非光学助视器 |
| 6    | 标记笔       | 3-非光学助视器 |
| 7    | 护指套       | 3-非光学助视器 |



#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |




##质控管理


###就诊记录列表

```htt
[GET]/treat_service/qc/treatment_list
```

#### 修改更新记录

| 对应业务     | 说明                            |
| -------- | ----------------------------- |
| V1.2.3   | 新增                            |
| V1.2.3.3 | 新增医生、初诊／复诊、时间改为时间段            |
| V1.3.5   | 修改 对于有病历号(pati_mrno)字段的，显示病历号 |

#### 请求报文参数

| 参数名               | 类型      | 必填   | 说明             |
| ----------------- | ------- | ---- | -------------- |
| start_time        | String  | 是    | 就诊开始时间         |
| end_time          | String  | 是    | 就诊结束时间         |
| key               | String  | 否    | 姓名、手机号 精确查询    |
| doctor_id         | String  | 否    | 医生ID           |
| trea_return_visit | Integer | 否    | 查询类型，0:初诊、1:复诊 |
| page_size         | Integer | 否    | 每页条数 空表示10条    |
| page_num          | Integer | 否    | 第几页 空表示第1页     |


#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| list      | ObjectList | 否    | 就诊记录列表      |

就诊记录列表

| 参数名               | 类型      | 必填   | 说明                |
| ----------------- | ------- | ---- | ----------------- |
| trea_id           | String  | 是    | 就诊号               |
| trea_visi_time    | String  | 是    | 就诊日期              |
| depa_name         | String  | 是    | 挂号就诊科室名称          |
| visi_serialno     | String  | 是    | 就诊序号              |
| pati_id           | String  | 是    | 患者ID              |
| pati_name         | String  | 是    | 姓名                |
| pati_gender       | String  | 是    | 性别代码 0 未知 1男  2 女 |
| pati_age          | String  | 是    | 年龄                |
| pati_phone        | String  | 是    | 手机号               |
| doct_id           | String  | 否    | 挂号就诊医生            |
| doct_name         | String  | 是    | 挂号就诊医生姓名          |
| visi_no           | String  | 是    | 门诊号               |
| trea_return_visit | Integer | 是    | 0:初诊、1:复诊         |



### 病历修订记录列表

```htt
[GET]/treat_service/qc/modify_record_list
```

#### 修改更新记录

| 对应业务   | 说明   |
| ------ | ---- |
| V1.2.3 | 新增   |


#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊号  |

#### 回复报文参数

| 参数名         | 类型     | 必填   | 说明     |
| ----------- | ------ | ---- | ------ |
| reco_id     | String | 是    | 操作记录ID |
| pati_id     | String | 是    | 患者ID   |
| visi_id     | String | 是    | 门诊ID   |
| record_time | String | 是    | 操作时间   |
| doct_name   | String | 是    | 操作医生姓名 |



### 病历修订记录详情

```htt
[GET]/treat_service/qc/modify_record/{pattern}
```

#### 修改更新记录

| 对应业务   | 说明                                       |
| ------ | ---------------------------------------- |
| V1.2.3 | 新增                                       |
| V1.3.5 | 修改 对于有病历号(pati_mrno)字段的，显示病历号，显示签名 支持pdf |

#### 请求报文参数

| 参数名     | 类型      | 必填   | 说明             |
| ------- | ------- | ---- | -------------- |
| reco_id | String  | 是    | 操作记录ID         |
| flag    | Integer | 否    | 留痕标志 0 最终 1 留痕 |

#### 回复报文参数

| 参数名         | 类型   | 必填   | 说明   |
| ----------- | ---- | ---- | ---- |
| InputStream |      | 是    |      |


## 医嘱

### 保存医嘱

> [POST]/diag_service/order 

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.2.3 | 实现修改 |

#### 请求报文参数

| 参数名     | 类型         | 必填   | 说明     |
| ------- | ---------- | ---- | ------ |
| trea_id | String     | 是    | 就诊ID   |
| orders  | ObjectList | 是    | 医嘱列表信息 |

##### 医嘱列表信息

| 参数名                 | 类型      | 必填   | 说明                                      |
| ------------------- | ------- | ---- | --------------------------------------- |
| drug_code           | String  | 是    | 药品编码                                    |
| drug_name           | String  | 是    | 药品名称                                    |
| drug_dose_units     | String  | 是    | 剂量单位                                    |
| drug_dosage         | Double  | 是    | 一次使用剂量                                  |
| drug_administration | String  | 是    | 给药途径                                    |
| drug_usag_place     | String  | 是    | 给药部位                                    |
| drug_freq_id        | Long    | 否    | 默认执行频率ID                                |
| drug_frequency      | String  | 是    | 默认执行频率                                  |
| drug_total_amount   | Double  | 是    | 包装数量总量                                  |
| pric_package_spec   | String  | 是    | 包装规格                                    |
| drug_pack_units     | String  | 是    | 包装单位                                    |
| drug_price          | Integer | 是    | 售价 单价,单位分                               |
| drug_memo           | String  | 否    | 备注                                      |
| drug_charge         | Integer | 是    | 实付费用,单位分                                |
| charge_state        | Integer | 否    | 收费状态<br/>1:未收费;2:已收费;3:未退费;4:已退费;5:超时失效 |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |


### 获取医嘱列表

> [GET]/diag_service/order/list

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.2.3 | 实现修改 |

#### 请求报文参数

| 参数名     | 类型         | 必填   | 说明     |
| ------- | ---------- | ---- | ------ |
| trea_id | String     | 是    | 就诊号    |
| orders  | ObjectList | 是    | 医嘱列表信息 |

##### 医嘱列表信息

| 参数名                 | 类型      | 必填   | 说明                                      |
| ------------------- | ------- | ---- | --------------------------------------- |
| drug_code           | String  | 是    | 药品编码                                    |
| drug_name           | String  | 是    | 药品名称                                    |
| drug_dose_units     | String  | 是    | 剂量单位                                    |
| drug_dosage         | Double  | 是    | 一次使用剂量                                  |
| drug_administration | String  | 是    | 给药途径                                    |
| drug_usag_place     | String  | 是    | 给药部位                                    |
| drug_freq_id        | Long    | 否    | 默认执行频率ID                                |
| drug_frequency      | String  | 是    | 默认执行频率                                  |
| drug_total_amount   | Double  | 是    | 包装数量总量                                  |
| pric_package_spec   | String  | 是    | 包装规格                                    |
| drug_pack_units     | String  | 是    | 包装单位                                    |
| drug_price          | Integer | 是    | 售价 单价,单位分                               |
| drug_memo           | String  | 否    | 备注                                      |
| drug_charge         | Integer | 是    | 实付费用,单位分                                |
| charge_state        | Integer | 是    | 收费状态<br/>1:未收费;2:已收费;3:未退费;4:已退费;5:超时失效 |

### 医嘱打印

> [GET]/diag_service/order/print

#### 修改更新记录

| 对应业务      | 说明   |
| --------- | ---- |
| WEBV1.2.3 | 实现修改 |

#### 请求报文参数

| 参数名     | 类型   | 必填   | 说明   |
| ------- | ---- | ---- | ---- |
| trea_id | Long | 是    | 就诊ID |

#### 回复报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |



### 获取综合验光详情

> [GET]/diag_service/his_reco/opto/view

获取历史医嘱详情

#### 请求报文参数

| 参数名     | 类型     | 必填   | 说明   |
| ------- | ------ | ---- | ---- |
| trea_id | String | 是    | 就诊号  |

#### 回复报文参数Object

| 参数名                      | 类型     | 必填   | 说明     |
| ------------------------ | ------ | ---- | ------ |
| bare_vision              | String | 否    | 裸眼视力   |
| bare_near_vision         | String | 否    | 裸眼近视力  |
| origin_glass_vision      | String | 否    | 原镜视力   |
| origin_glass_near_vision | String | 否    | 原镜近视力  |
| origin_glass_data        | String | 否    | 原镜度数   |
| pupil_light_reflection   | String | 否    | 瞳孔对光反射 |
| cornea_map_point         | String | 否    | 角膜映光点  |
| cover_test               | String | 否    | 遮盖实验   |
| corneal_curvature        | String | 否    | 角膜曲率   |
| eyeball_movement         | String | 否    | 眼球运动   |
| set_near_point           | String | 否    | 集合近点   |
| adjust_amplitude         | String | 否    | 调节幅度   |
| computer_optometry       | String | 否    | 电脑验光   |
| main_vision              | String | 否    | 主觉验光   |
| retinoscopy              | String | 否    | 检影验光   |
| nearly_attached          | String | 否    | 近附加    |
| opto_pd                  | String | 否    | 瞳距     |
| opto_ph                  | String | 否    | 瞳高     |
| far_pres                 | String | 否    | 远用处方   |
| near_pres                | String | 否    | 近用处方   |
| cont_lens                | String | 否    | 隐形眼镜   |
| slit_lamp_check          | String | 否    | 裂隙灯检查  |
| eye_bott_check           | String | 否    | 眼底检查   |
| iop_data                 | String | 否    | 眼压     |

## 用户

### 所有用户列表检索

> [GET]/common_service/user_list

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明                         |
| ---- | ------ | ---- | -------------------------- |
| key  | String | 否    | 五笔码不区分大小写、拼音码不区分大小写、中文模糊匹配 |

#### 回复报文参数

| 参数名         | 类型     | 必填   | 说明   |
| ----------- | ------ | ---- | ---- |
| doctor_id   | String | 是    | 医生id |
| doctor_name | String | 是    | 姓名   |


##其他

### 训练仪器商品列表

> [GET]/diag_service/special_check/goods_list

#### 修改更新记录

| 对应业务        | 说明     |
| ----------- | ------ |
| WEBV1.3.3.1 | 增加排序规则 |

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

| 参数名         | 类型     | 必填   | 说明       |
| ----------- | ------ | ---- | -------- |
| goods_id    | String | 是    | 商品ID     |
| goods_name  | String | 是    | 商品名称     |
| goods_unit  | String | 是    | 商品单位     |
| goods_price | Double | 是    | 商品售价 单位元 |

### 根据手机号、姓名、首字母获取患者列表

```http
[GET]/patient_service/patient/list/for_preview
```

####修改更新记录

| 对应版本     | 说明             |
| -------- | -------------- |
| V1.3.4.1 | 新增 添加患者ID的检索条件 |

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明                               |
| ---- | ------ | ---- | -------------------------------- |
| key  | String | 是    | 手机号、姓名、首字母（手机号全匹配、姓名模糊匹配、首字母左匹配） |

#### 回复报文参数ObjectList

| 参数名            | 类型     | 必填   | 说明                |
| -------------- | ------ | ---- | ----------------- |
| pati_id        | Long   | 是    | 患者ID              |
| pati_name      | String | 是    | 姓名                |
| pati_py        | String | 否    | 姓名拼音首字母           |
| pati_gender    | String | 是    | 性别代码 0 未知 1男  2 女 |
| pati_age       | String | 是    | 年龄                |
| pati_birthday  | Date   | 是    | 出生年月              |
| pati_phone     | String | 是    | 手机号码              |
| pati_id_number | String | 是    | 身份证               |
| pati_address   | String | 否    | 地址                |

### 根据流水号、姓名查询挂号记录

```http
[GET]/book_service/book/query_book_record
```

####修改更新记录

| 对应版本     | 说明             |
| -------- | -------------- |
| V1.3.4.1 | 新增 添加患者ID的检索条件 |

#### 请求报文参数

| 参数名  | 类型     | 必填   | 说明         |
| ---- | ------ | ---- | ---------- |
| key  | String | 否    | 流水号、姓名、手机号 |

#### 回复报文参数ObjectList

| 参数名         | 类型     | 必填   | 说明           |
| ----------- | ------ | ---- | ------------ |
| visi_id     | String | 是    | 门诊ID         |
| pati_name   | String | 是    | 患者姓名         |
| pati_phone  | String | 是    | 患者手机号        |
| visi_memo   | String | 是    | 挂号信息         |
| visi_cancel | String | 是    | 状态 0- 有效 1已退 |


### 根据预约号、姓名查询预约信息

```
[GET]/book_service/book/query_bookappo_record
```

####修改更新记录

| 对应版本     | 说明             |
| -------- | -------------- |
| V1.3.4.1 | 新增 添加患者ID的检索条件 |

#### 请求报文参数

| 参数名  | 类型      | 必填   | 说明               |
| ---- | ------- | ---- | ---------------- |
| key  | String  | 否    | 预约号、姓名、手机号       |
| type | Integer | 是    | 类型 1：预约取号 2：取消预约 |

#### 回复报文参数

| 参数名          | 类型      | 必填   | 说明                     |
| ------------ | ------- | ---- | ---------------------- |
| appo_id      | String  | 是    | 预约id                   |
| appo_pati_id | String  | 否    | 预约患者id                 |
| appo_name    | String  | 是    | 姓名                     |
| appo_gender  | Integer | 是    | 性别代码 0 未知 1男  2 女      |
| appo_phone   | String  | 是    | 手机号码                   |
| appo_idno    | String  | 是    | 身份证号                   |
| appo_memo    | String  | 是    | 预约信息                   |
| appo_status  | Integer | 是    | 预约状态;0:已预约;1:已取消;2:已挂号 |
| appo_date    | String  | 是    | 预约日期                   |
| appo_rela_id    | String  | 是    | 就诊人ID                   |

### 获取就诊患者列表

```http
[GET] /treat_service/treatment/list
```

####修改更新记录

| 对应版本     | 说明             |
| -------- | -------------- |
| V1.3.4.1 | 新增 添加患者ID的检索条件 |

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明                                   |
| --------- | ------- | ---- | ------------------------------------ |
| key       | String  | 否    | 姓名、手机号、门诊号                           |
| pati_type | Integer | 否    | 患者列表类型 ，不传默认获取全部病人列表， 1:候诊  2诊中 3 已诊 |

#### 回复报文参数（ObjectList）

| 参数名         | 类型         | 必填   | 说明   |
| ----------- | ---------- | ---- | ---- |
| total_num   | Integer    | 是    | 患者总数 |
| wait_num    | Integer    | 是    | 候诊总数 |
| diaging_num | Integer    | 是    | 诊中总数 |
| diaged_num  | Integer    | 是    | 已诊总数 |
| treat_list  | ObjectList | 是    | 就诊列表 |

就诊列表结构

| 参数名                 | 类型      | 必填   | 说明     |
| ------------------- | ------- | ---- | ------ |
| trea_id             | Long    | 是    | 就诊号    |
| visi_no             | Long    | 是    | 门诊号    |
| pati_id             | Integer | 是    | 患者ID   |
| trea_status         | Integer | 是    | 就诊状态   |
| pati_name           | String  | 是    | 姓名     |
| pati_gender         | String  | 是    | 性别     |
| pati_birthday       | Date    | 是    | 出生日期   |
| age                 | Integer | 是    | 年龄     |
| pati_phone          | String  | 是    | 手机号码   |
| prev_event          | String  | 是    | 就诊事项   |
| trea_crea_user      | Integer | 是    | 登记人id  |
| trea_crea_user_name | String  | 是    | 登记人姓名  |
| trea_crea_time      | Date    | 是    | 登记时间   |
| trea_visi_user      | Integer | 是    | 接诊医生id |
| trea_visi_user_name | String  | 是    | 接诊医生姓名 |
| trea_visi_time      | Date    | 是    | 接诊时间   |


### 销售单列表

```http
[GET]/sale_service/sales_order/list
```

####修改更新记录

| 对应版本     | 说明             |
| -------- | -------------- |
| V1.2.3.2 | 修改 为再开一单       |
| V1.3.4.1 | 新增 添加患者ID的检索条件 |

#### 请求报文参数

| 参数名          | 类型      | 必填   | 说明                                    |
| ------------ | ------- | ---- | ------------------------------------- |
| key          | String  | 否    | 订单号、客户姓名、手机号码                         |
| pati_id      | String  | 否    | 患者id 刷卡查询时用该字段                        |
| state        | Integer | 否    | 状态;1-待付款;2-已付款;3-已撤销;4-待退费;5-已退费 空为全部 |
| sale_user_id | String  | 否    | 销售员id  新增                             |
| start_time   | String  | 是    | 开始时间                                  |
| end_time     | String  | 是    | 结束时间                                  |
| page_size    | Integer | 否    | 每页条数 空表示10条                           |
| page_num     | Integer | 否    | 第几页 空表示第1页                            |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明    |
| --------- | ---------- | ---- | ----- |
| page_num  | Integer    | 是    | 当前页   |
| page_size | Integer    | 是    | 每页的数量 |
| total     | Integer    | 是    | 总记录数  |
| pages     | Integer    | 是    | 总页数   |
| list      | ObjectList | 是    | 销售单列表 |

销售单列表说明

| 参数名            | 类型      | 必填   | 说明                                       |
| -------------- | ------- | ---- | ---------------------------------------- |
| sale_id        | String  | 是    | 销售单id                                    |
| sale_no        | String  | 是    | 订单号                                      |
| sale_time      | String  | 是    | 订单时间                                     |
| sale_pati_id   | String  | 是    | 客户id                                     |
| pait_name      | String  | 是    | 客户名称                                     |
| pati_gender    | String  | 是    | 客户性别  性别代码 0 未知 1男  2 女                  |
| pati_age       | String  | 是    | 客户年龄                                     |
| opto_id        | String  | 是    | 处方ID                                     |
| opto_type      | Integer | 是    | 处方类型包含：0 远视处方 1-近视处方、2-隐形眼镜处方、3-RGP处方、4-OK镜处方、9-其他处方 |
| sale_user_id   | String  | 是    | 制单人id                                    |
| sale_user_name | String  | 是    | 制单人                                      |
| sale_state     | Integer | 是    | 状态;1-待付款;2-已付款;3-已撤销;4-待退费;5-已退费         |


### OK镜品牌参数表

> [GET]/diag_service/special_check/brand_para/list

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数ObjectList

| 参数名       | 类型         | 必填   | 说明        |
| --------- | ---------- | ---- | --------- |
| brand_id  | String     | 是    | 品牌id      |
| brand     | String     | 是    | 品牌名称      |
| para_list | ObjectList | 是    | OK镜品牌参数列表 |

OK镜品牌参数列表说明

| 参数名             | 类型         | 必填   | 说明                |
| --------------- | ---------- | ---- | ----------------- |
| para_prop_id    | String     | 是    | 属性id              |
| para_prop_name  | String     | 是    | 属性名称              |
| prop_prop_type  | Integer    | 是    | 1-自由录入属性;2-候选选择属性 |
| para_choi_id    | String     | 否    | 属性值ID             |
| para_choi_code  | String     | 否    | 属性值代码             |
| prop_prop_value | String     | 是    | 属性值               |
| list            | ObjectList | 否    | 备选列表说明            |

备选列表说明

| 参数名             | 类型     | 必填   | 说明    |
| --------------- | ------ | ---- | ----- |
| para_choi_id    | String | 否    | 属性值ID |
| para_choi_code  | String | 否    | 属性值代码 |
| prop_prop_value | String | 是    | 属性值   |

### RGP材质列表

> [GET]/diag_service/special_check/rgp/material_list

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数ObjectList

| 参数名           | 类型     | 必填   | 说明   |
| ------------- | ------ | ---- | ---- |
| material_id   | Long   | 是    | 材质id |
| material_name | String | 是    | 材质名称 |


### RGP品牌列表

> [GET]/diag_service/special_check/rgp/brand_list

#### 请求报文参数

| 参数名  | 类型   | 必填   | 说明   |
| ---- | ---- | ---- | ---- |
| 无    |      |      |      |

#### 回复报文参数ObjectList

| 参数名        | 类型     | 必填   | 说明   |
| ---------- | ------ | ---- | ---- |
| brand_id   | Long   | 是    | 品牌id |
| brand_name | String | 是    | 品牌名称 |


### 屈光检查列表

> [GET]/treat_service/speciality_check/list

#### 请求报文参数

| 参数名       | 类型      | 必填   | 说明             |
| --------- | ------- | ---- | -------------- |
| state     | Integer | 否    | 状态 1 未填写 2 已填写 全部则不传 |
| key       | String  | 否    | 姓名、手机号、门诊号     |
| page_size | Integer | 否    | 每页条数 空表示10条    |
| page_num  | Integer | 否    | 第几页 空表示第1页     |

#### 回复报文参数

| 参数名       | 类型         | 必填   | 说明          |
| --------- | ---------- | ---- | ----------- |
| page_size | Integer    | 是    | 每页条数 空表示10条 |
| page_num  | Integer    | 是    | 第几页 空表示第1页  |
| total     | Integer    | 是    | 总记录数        |
| pages     | Integer    | 是    | 总页数         |
| wait_num  | Integer    | 是    | 待预检数量       |
| total_num | Integer    | 是    | 全部数量        |
| list      | ObjectList | 否    | 预检列表        |

检查列表说明

| 参数名           | 类型      | 必填   | 说明                |
| ------------- | ------- | ---- | ----------------- |
| trea_id       | String  | 是    | 就诊号               |
| state         | Integer | 否    | 预检状态 1 未填写  2已填写  |
| depa_id       | String  | 是    | 挂号就诊科室            |
| depa_name     | String  | 是    | 挂号就诊科室名称          |
| visi_serialno | String  | 是    | 就诊序号              |
| pati_name     | String  | 是    | 姓名                |
| pati_gender   | String  | 是    | 性别代码 0 未知 1男  2 女 |
| pati_age      | String  | 是    | 年龄                |
| pati_phone    | String  | 是    | 手机号               |
| doct_id       | String  | 否    | 挂号就诊医生            |
| doct_name     | String  | 是    | 挂号就诊医生姓名          |
| visi_no       | String  | 是    | 门诊号               |
| fee_type      | String  | 是    | 费用类型 1-自费，2- 市医保  |
| trea_status   | Integer | 是    | 就诊状态              |
| prev_event    | String  | 是    | 就诊事项（拼接展示）        |
| trea_visi_time    | String  | 是    | 接诊时间        |
|book_time    | String  | 是    | 挂号时间        |
| head_photo_url    | String  | 是    | 患者头像地址        |

