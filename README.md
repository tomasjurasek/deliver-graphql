# Delivery GraphQL Prototype


We are providing two types of query:  
* item(codename: String!): ContentItem  
* items(type: String!, limit: Int, depth: Int, order: String, language: String): [ContentItem]

All content types are inherited from the ContentItem object. If you need a specific content type from your query you need to use explicit typing **... on 'SpecificContentType'**. Also if you are using a deeping in the query you need to provide **depth** property.


### Example 
Sample project - https://deliver-graphql-euwest.azurewebsites.net/975bf280-fd91-488c-994c-2f04416e5ee3/graphql
#### Get Articles
```
query{
  items(type:"article", depth: 2){
    ... on ArticleContentType {
      title {
        value
      }
      summary{
        value
      }
      related_articles{
	name
        value{
          ... on ArticleContentType {
            title {
              value
            }
            summary{
              value
            }
          }
        }
      }
    }
  }
}
```
#### Get Article
```
query{
  item(codename: "coffee_beverages_explained"){
     ... on ArticleContentType {
      title {
        value
      }
      summary{
        value
      }
    }
  }
}
```

This product is not a production-ready yet.
