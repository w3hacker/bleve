# ![bleve](docs/bleve.png) bleve

[![Join the chat at https://gitter.im/blevesearch/bleve](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/blevesearch/bleve?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

modern text indexing in go - [blevesearch.com](http://www.blevesearch.com/)

Try out bleve live by [searching our wiki](http://wikisearch.blevesearch.com/search/).

## Features
* Index any go data structure (including JSON)
* Intelligent defaults backed up by powerful configuration
* Supported field types:
    * Text, Numeric, Date
* Supported query types:
    * Term, Phrase, Match, Match Phrase, Prefix
    * Conjunction, Disjunction, Boolean
    * Numeric Range, Date Range
    * Simple query [syntax](https://github.com/blevesearch/bleve/wiki/Query-String-Query) for human entry
* tf-idf Scoring
* Search result match highlighting
* Supports Aggregating Facets:
    * Terms Facet
    * Numeric Range Facet
    * Date Range Facet

## Discussion

Discuss usage and development of bleve in the [google group](https://groups.google.com/forum/#!forum/bleve).

## Indexing

		message := struct{
			Id   string
			From string
			Body string
		}{
			Id:   "example",
			From: "marty.schoch@gmail.com",
			Body: "bleve indexing is easy",
		}

		mapping := bleve.NewIndexMapping()
		index, err := bleve.New("example.bleve", mapping)
		if err != nil {
			panic(err)
		}
		index.Index(message.Id, message)

## Querying

		index, _ := bleve.Open("example.bleve")
		query := bleve.NewQueryStringQuery("bleve")
		searchRequest := bleve.NewSearchRequest(query)
		searchResult, _ := index.Search(searchRequest)
		
## License

Apache License Version 2.0

## Status

[![Build Status](https://travis-ci.org/blevesearch/bleve.svg?branch=master)](https://travis-ci.org/blevesearch/bleve)
[![Coverage Status](https://coveralls.io/repos/blevesearch/bleve/badge.png?branch=master)](https://coveralls.io/r/blevesearch/bleve?branch=master)
