# Elasticsearch/Luence Tips

## Tip 1
For documents has an ID as a Number. Lucence Query Numbers as Ranges.  Making ID as a keyword value is faster    
Looking for exact value, better to make it has string    

```
PUT my_index
{
  "mappings": {
    "properties": {
      "status_code": { 
        "type":       "keyword"
      },
      "session_id": { 
        "type":       "keyword",
        "doc_values": false
      }
    }
  }
}
```

# Tip 2 
If you are sure that you don’t need to sort or aggregate on a field, or access the field value from a script, you can `disable doc` values in order to save disk space.

# Top 3
Dynamic mapping determines the datatype for the field and automatically adds the new field to the type mapping.    

It is a good idea to make the `dynamic mapping` as `strict`.
`strict` Throw an exception if an unknown field is encountered

```
PUT /my_index
{
    "mappings": {
        "my_type": {
            "dynamic":      "strict", 
            "properties": {
                "title":  { "type": "string"}
            }
        }
    }
}
```





# Links
[Lucene Upgrade in Jira 8.0 How we fought and killed the code debt beast ](https://youtu.be/WDPe4cjURNI)
