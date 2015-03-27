# go-connpass
CONNPASS の API (http://connpass.com/about/api/) を Go で実装したものです。

## 使い方

	query := connpass.Query{Start: 1, Order: connpass.CREATE}
	query.KeywordOr = []string{"go", "golang"}
	query.Time = []connpass.Time{connpass.Time{Year: 2015, Month: 3}, connpass.Time{Year: 2015, Month: 4}}
	result, e := query.Search()
	
	if e != nil {
	   log.Errorf("Failed to fetch the result: %v\n", e)
	} else {
	   fmt.Printf("Num returned: %d\n", res.Returned)
	   fmt.Printf("Num available: %d\n", res.Available)
	   fmt.Printf("Start position: %d\n", res.Start)
	   for _, e := range res.Events {
	      fmt.Printf("\t%s\t%d\t%s\n", e.Start, e.Id, e.Title)
	   }
	}
