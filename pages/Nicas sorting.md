---
title: Nicas sorting
---

- https://documentation.laborator.co/kb/kalium/ordering-post-types/

- I couldn’t create a category filter with a custom query as indicated in this topic but I found another solution that may help other users.

To apply the custom order (created with this plugin) for the wpbakery post grid (without a custom query, just using the standard choice “data source” tab, “narrow data source” tab, and selecting “Post order by Id” and “Descending” in data settings), you need to modify the module filters as reported here:

https://wpml.org/forums/topic/visual-composer-custom-grids-problem/

- In /js_composer/include/classes/shortcodes/vc-basic-grid.php, set suppress filter to false instead of true

- Current code:
‘suppress_filters’ => apply_filters( ‘vc_basic_grid_filter_query_suppress_filters’, true ),​

Fix:
‘suppress_filters’ => apply_filters( ‘vc_basic_grid_filter_query_suppress_filters’, false ),​

And that’s it.

- 

- ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FGijs%2FOCBeaqaKNZ.png?alt=media&token=4cd00aee-93ae-436d-b300-8ddc14ffd910)

- 

- ```html
post_type=tribe_events
&posts_per_page=3
&post_status=publish
&orderby=_EventStartDate
&order=ASC
```

- post_type=tribe_events&posts_per_page=20

- 

- _EventStartDate

- post_type%5B%5D=Tribe_events
&posts_per_page=1&order_by=_EventStartDate
&order=ASC

- 

- post_type%5B%5D=tribe_events

- &posts_per_page=1&order_by=_EventStartDate

- &order=ASC
