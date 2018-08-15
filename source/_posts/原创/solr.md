---
title: solr
date: 2018-08-15 15:28:59
category: [solr]
tags: [solr]
---

## 1. solr查询解析器

1. 默认是**Standard Query Parser(lucene)**
2. **DisMaxquery parser**
3. **Extended DisMax(eDisMax) query parser**

## 2. solr搜索解析器区别

The standard query parser's syntax allows for greater precision in searches,but the DisMax query parser is much more tolerant of errors.The DisMax query parser is designed	to provide an experience similar to that of popular search engines such as Google,which	rarely display syntax errors to users.The Extended DIsMax query parser is an improved version of DisMax that handles the full Lucene query syntax while still tolerating syntax	errors.It also includes several additional features.
		
* In addition, there are common query parameters that are accepted by all query parsers.
		
## 3. solr搜索

### 3.1 Input to a query parser can include:

- search strings ---that is,terms to search for in the index
- parameters for fine-tuning the query by increasing the importance of particular strings or fields,by applying Boolean logic among the search terms,or by excluding content from the search results
- parameters for controlling the presentation of the query response,such as specifying the order in whic results are to be presented or limiting the response to particular fields of the serach appliction's schema.
		
### 3.2 filter search 
	
search parameters may also specify specify a filter query . As part of a search response,a filter query runs a query against the entire index and caches the results.Because Solr allocates a separte cache for filter queries,the startegic use of filter queries can improve search performance.(Despite their similar names,query filters are not related to analysis filters.Filter queries perform queries at search time against data already in the index,while analysis filters,such as Tokenizers,parse content for indexing,following specified rules).
		
### 3.3 highlighted responses 

A search query can request that certain tems be highlighted in the search response;that is,the selected terms will be displayed in colored boxes so that thy "jump out" on the screen of search results.

Highlighting can make it easier to find relevant passages in long documents returned in a search.Solr supports multi-term highlighting.Solr includes a rich set of search parameters for controlling how terms are highlighted.
		
Search responses can also be configured to include snippets(document excerpts)featuring highlighted text.Popular search engines such as Google and Yahoo!return snippets in their search results:3-4 lines or text offering a descrition of a search results.
		

### 3.4 Grouping search results(Tow specif ways:faceting and clustering)

- **Facting**:Faceting is the arrangement of search results into categories(which are based on indexed terms).Within each category,Solr reprots on the number of hits for relevant term, which is called a facet constraint.Faceting makes it easy for users to explore search results on sites such as movie sites and product review sites,where there are many categories and many items within a category.
		
- **Clstering**：Clstering groups search results by similarities discovered when a search is executed,rather than when content is indexed.The results of clustering often lack the neat hierarchical organization found in facted search results,but clustering can be useful nonetheless.It can reveal unexpected commonalities among search results,and it can help users rule out content that isn't pertinent to what they're really searching for.
		
Solr als supports a feature called MoreLikeThis,which enables users to submit new queries that focus on particular terms returned in an earlier query.MoreLikeThis queries can make use of faceting or clustering to provide additional aid to users.
			
### 3.5 response writer

A Solr component called a response writer manages the final presentation of the query response.Solr includes ad variety of response writers,including an XML Response Writer and a JSON Response Writer.