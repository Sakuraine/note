# 贯通Java开发规范

## 业务规范

1. 所有的新增操作（先查询是否有数据，然后添加新数据或更新），必须使用分布式锁进行控制。
2. 所有的update操作，必须判断返回修改的条数，进行验证与判断。
3. 所有修改状态类的数据库操作，where部分必须包含原状态条件。
4. 所有数据库写操作（insert,update）必须包含chan_user,chan_request,chan_time三个字段的信息。
5. 所有update与select操作，where部分必须包含租户条件。

## 结构规范

1. 要求符合 controller、service、mapper 三层的代码结构。
2. controller层进行结构验证，数据合法性验证，分布式锁控制及接口适配处理。
3. service层进行真正的业务处理，包含事务管理。
4. mapper层为数据操作层；一个mapper类，必须以某一个表为主表进行操作，不允许一个表在多个mapper中成为主表。
5. 三层代码中不允许使用Map<>进行数据内容的传输与读取，如Controller使用Map进行Json数据的接收，Mapper层使用List<Map<>接收查询出的数据，这都是不允许的。

## 异常规范

所有业务异常请使用SeeingRuntimeException和SeeingException进行封装。

正常业务中不允许进行try catch的异常捕获，如业务中对错误有特殊的处理，那么捕获的异常必须打印日志，且要写明什么业务发生的异常。

## 书写规范

1. 遵循 Alibaba Java Coding Guidelines，可使用IDEA的 Alibaba Java Coding Guidelines 进行检测。

## 规范检查工具

IDE统一使用 IntelliJ IDEA 为例，要求安装 FindBugs-IDEA 与 Alibaba Java Coding Guidelines。未通过这两个插件检查的代码不允许发布。
注：FindBugs-IDEA 的检查较严，可视具体内容决定。