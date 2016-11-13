**基本信息：**

请求类型：HTTP

接口地址：app-performance-count.html

请求方式：GET

数据类型：X-WWW-FORM-URLENCODED

响应类型：JSON

接口状态：未启用

**请求参数：**

| **字段** | **类型** | **默认值** | **是否必须** | **说明** |
| --- | --- | --- | --- | --- |
| starttime | long | | 否 | 查询开始时间 |
| endtime | long | | 否 | 查询结束时间\(如果不写默认查询最近1小时\) |
| precision | int | 否 | 查询精度 | - |

**响应数据：**


| **字段** | **类型** | **说明** | **备注** |
| --- | --- | --- | --- |
| status | int | 状态 | |
| msg | string | 返回信息 | |
| data | jsonArray | 返回数据 | 表1 |

**表1：**

| **字段** | **类型** | **说明** | **备注** |
| --- | --- | --- | --- |
| unit | string | 单位 | |
| list | jsonArray | 应用列表 | 表2 |

**表2：**

| **字段** | **类型** | **说明** | **备注** |
| --- | --- | --- | --- |
| utc | string | 时间 | new Date\(2016,11,01,09,02\) |
| num | float | 交易量 | - |

---

**后台说明：**

查询表：app\_kpi\_

查询字段\(交易量\)：numreq

计算方法：SUM\(numreq\)

说明：根据时间精度聚合统计相应数值。

---

**请求示例：**

> ```js

> http://ip:8080/APM/apm/reqnum-line.html?starttime=1478048400&endtime=1478052000&precision=1

> ```



**响应示例：**



> ```js

> {

> "status":0,

> "msg":"成功",

> "data":{

> "unit":"笔",

> "list":[

> {

> "utc":"new Date(2016,11,01,09,01)",

> "num":10

> },

> {

> "utc":"new Date(2016,11,01,09,02)",

> "num":34

> }

> ]

> }

> }

> ```


