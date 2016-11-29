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
DELETE https://api.liruan.cn/v1/articles
DELETE https://api.liruan.cn/v1/articles?id=1,2,3
GET    https://api.liruan.cn/v1/articles/1/authors/2
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
