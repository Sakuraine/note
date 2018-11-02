# PAT_V1.0.2.1协议一览表



## 消息中心服务协议.md

协议地址所在位置： seeing\wiki\协议文档\消息中心服务协议.md

| 协议地址                                     | 协议名称         | 人员   | 备注   |
| ---------------------------------------- | ------------ | ---- | ---- |
| 患者聊天                                     |              |      |      |
| [GET]/msg_service/msg/patient/session_list | 患者获取历史会话列表   |      |      |
| [GET]/msg_service/msg/patient/new_session | 患者获取最新会话     |      |      |
| [GET]/msg_service/msg/patient/msg_list   | 患者获取历史消息列表   |      |      |
| [GET]/msg_service/msg/patient/new_msg    | 患者获取当前会话最新消息 |      |      |
| [POST]/msg_service/msg/patient/send_text_msg | 患者选择医生发送文字消息 |      |      |
| [POST]/msg_service/msg/patient/send_res_msg | 患者选择医生发送资源消息 |      |      |
| [POST]/msg_service/msg/patient/session_del | 患者删除会话       |      |      |
| 医生咨询                                     |              |      |      |
| [GET]/msg_service/msg/doctor/session_list | 医生获取会话列表     |      |      |
| [GET]/msg_service/msg/doctor/new_session | 医生获取最新会话     |      |      |
| [GET]/msg_service/msg/doctor/msg_list    | 医生获取会话历史消息列表 |      |      |
| [GET]/msg_service/msg/doctor/new_msg     | 医生获取会话最新消息   |      |      |
| [POST]/msg_service/msg/doctor/send_text_msg | 医生发送文字消息     |      |      |
| [POST]/msg_service/msg/doctor/send_res_msg | 医生发送资源消息     |      |      |
| [POST]/msg_service/msg/doctor/session_del | 医生删除会话       |      |      |
| 文件上传                                     |              |      |      |
| [POST]/msg_service/msg/doctor/file/pre_upload | 聊天文件预上传      |      |      |
| [POST]/msg_service/msg/doctor/file/upload_access | 聊天文件确认已上传    |      |      |

## 门诊电子病历.md

协议地址所在位置： seeing\wiki\协议文档\门诊电子病历.md

| 协议地址                                     | 协议名称    | 人员   | 备注   |
| ---------------------------------------- | ------- | ---- | ---- |
| 患者聊天                                     |         |      |      |
| [GET]/pati_service/manager_service/doctor_list | 咨询时医生列表 |      |      |

