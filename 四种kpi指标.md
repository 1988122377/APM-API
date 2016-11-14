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
| toponum | int | | 是 | 拓扑图编号 |
| rule | int | | 否 | 规定id |

**响应数据：**

| **字段** | **类型** | **说明** | **备注** |
| --- | --- | --- | --- |
| status | int | 状态 | |
| msg | string | 返回信息 | |
| data | jsonArray | 返回数据 | 表1 |

**表1：**

| **字段** | **类型** | **说明** | **备注** |
| --- | --- | --- | --- |
| list | jsonArray | 数据列表 | 表2 |

**表2：**

| **字段** | **类型** | **说明** | **备注** |
| --- | --- | --- | --- |
| name | string | 业务名称 | |
| num | float | 业务量 | |
| unit | string | 单位 | - |

---

**后台说明：**

查询表：app\_kpi\_

查询字段\(交易量,成功量,响应时间,响应量\)：numreq,successfultran,pagetranstime,numreply

计算方法\(交易量,成功率,响应时间,响应率\)：SUM\(numreq\),SUM(successfultran)/SUM\(numreq\),AVG(pagetranstime),SUM(numreply)/SUM(numreq)

说明：根据时间聚合统计相应数值。

---

**请求示例：**

> ```js

> http://ip:8080/APM/apm/app-performance-count.html?starttime=1478048400&endtime=1478052000

> ```

**响应示例：**

> ```js
> {
>     "status":0,
>     "msg":"成功",
>     "data":{
>         "list":[
>             {
>                 "name":"交易量",
>                 "num":49235,
>                 "unit":"笔"
>             },
>             {
>                 "name":"成功率",
>                 "num":98.55,
>                 "unit":"%"
>             },
>             {
>                 "name":"响应时间",
>                 "num":451.57,
>                 "unit":"ms"
>             },
>             {
>                 "name":"响应率",
>                 "num":82.28,
>                 "unit":"%"
>             }
>         ]
>     }
> }
> ```


