## HTTP 动词
```
GET（SELECT）：从服务器取出资源（一项或多项）。
POST（CREATE）：在服务器新建一个资源。
PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。
DELETE（DELETE）：从服务器删除资源。

HEAD：获取资源的元数据。
OPTIONS：获取信息，关于资源的哪些属性是客户端可以改变的。
```

## 例子
```
GET    https://api.liruan.cn/v1/articles?[offset=0][&limit=10][&title=文章标题][&order_by=views]
GET    https://api.liruan.cn/v1/articles/1
POST   https://api.liruan.cn/v1/articles
PATCH  https://api.liruan.cn/v1/articles
DELETE https://api.liruan.cn/v1/articles/1
DELETE https://api.liruan.cn/v1/articles?id=1,2,3
GET    https://api.liruan.cn/v1/articles/1/authors/2
```

## 状态码
```
200 OK - [GET]：服务器成功返回用户请求的数据，该操作是幂等的（Idempotent）。
201 CREATED - [POST/PUT/PATCH]：用户新建或修改数据成功。
202 Accepted - [*]：表示一个请求已经进入后台排队（异步任务）
204 NO CONTENT - [DELETE]：用户删除数据成功。
400 INVALID REQUEST - [POST/PUT/PATCH]：用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的。
401 Unauthorized - [*]：表示用户没有权限（令牌、用户名、密码错误）。
403 Forbidden - [*] 表示用户得到授权（与401错误相对），但是访问是被禁止的。
404 NOT FOUND - [*]：用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的。
406 Not Acceptable - [GET]：用户请求的格式不可得（比如用户请求JSON格式，但是只有XML格式）。
410 Gone -[GET]：用户请求的资源被永久删除，且不会再得到的。
422 Unprocesable entity - [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误。
500 INTERNAL SERVER ERROR - [*]：服务器发生错误，用户将无法判断发出的请求是否成功。
```

### 接口返回错误
```js
{
  "error": {
    "code": "ARTICLE/NOT_FOUND",
    "message": "文章不存在"
  },
  "data": null
}
```

### 接口返回成功
```js
{
  "error": null,
  "data": {
    "id": 11,
    "title": "文章标题",
    "content": "文章内容",
    "author": "作者",
    "created_at": 1475855919,
    "updated_at": 1475855919
  }
}
```

### 分页
```js
{
  "error": null,
  "data": {
    "total": 120,
    "items": [
      {
        "title": "标题一",
        "content": "内容一"
      },
      {
        "title": "标题二",
        "content": "内容二"
      }
    ]
  }
}
```
