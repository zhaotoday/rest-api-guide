## 接口返回错误
```js
{
  "error": {
    "code": "RESOURCE/ARTICLE_NOT_FOUND",
    "message": "文章不存在"
  },
  "data": null
}
```

## 接口返回成功
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

## 分页
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
