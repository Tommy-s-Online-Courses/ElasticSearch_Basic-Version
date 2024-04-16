## 2. 第二部分：基础部分入门

### **`2.1 创建索引`**

### **`2.2 写入文档`**

### **`2.3 根据_id搜索文档`**

### **`2.4 根据字段搜索文档`**

### **`2.5 根据文本字段搜索文档`**

### **`2.6 批量写入数据`**

### **`2.7 根据条件删除文档`**

### **`2.8 删除索引`**

```python
// 2.1 创建索引
PUT /hotel
{
  "mappings":{
    "properties": {
      "name":{
        "type":"text"
      },
      "city":{
        "type":"keyword"
      },
      "price":{
        "type":"double"
      }
    }
  }
}

// 2.2 写入文档数据
// 可以不指定文档_id，该_id值将由ES自动生成
POST /hotel/_doc/001
{
  "name":"希尔顿好朋友国际酒店",
  "city":"深圳",
  "price":999.99
}

// 2.3 根据_id搜索文档
GET /hotel/_doc/001

// 2.4 根据普通字段搜索文档
GET /hotel/_search
{
  "query":{
    "term":{
      "city":{
        "value":"深圳"
      }
    }
  }
}

// 2.5 根据文本字段搜索文档
GET /hotel/_search
{
  "query":{
    "match":{
      "name":"好朋友"
    }
  }
}

// 2.6 批量写入数据
PUT /hotel/_bulk
{"index":{}}
{"name":"万豪国际度假旅游酒店","city":"三亚","price":1111.99}
{"index":{}}
{"name":"菲利克斯国际博览中心酒店","city":"深圳","price":688.79}

// 2.7 根据条件删除文档
// 例如：删除city="三亚"的文档
POST /hotel/_delete_by_query
{
  "query":{
    "term":{
      "city":{
        "value":"三亚"
      }
    }
  }
}

// 2.8 删除索引
DELETE hotel
```


