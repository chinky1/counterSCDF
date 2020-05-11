# counterSCDF

#payload



[
 {
  "content": "test",
  "id": "1",
  "metaData": {
    "Language": ["en","de"]
    
  }
},
 {
  "content": "test",
  "id": "2",
  "metaData": {
    "Language": ["de","en"]
  }
}
]

# defination


stream create Docs --definition "http | log"

stream create TestCounter  --definition ":Docs.http > Custom_counter --counter.name=lang --counter.tag.expression.lang=#jsonPath(payload,'$.[*].metaData.Language')" --deploy


