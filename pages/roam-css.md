---
title: roam/css
---

- Youtube about this:
	 - https://www.youtube.com/watch?time_continue=2&v=UY-sAC2eGyI&feature=emb_logo

- Themes:
	 - https://github.com/theianjones/roam-research-themes 

	 - https://github.com/apg-dev/roam-theme-bear

- Helppage:
	 - https://roamresearch.com/#/app/help/page/ilbMpkUFC 

- [[Custom tags]]
	 - ```javascript

/* Custom data tags */
span.rm-page-ref[data-tag="Tweets"] {
    background: #2980b9 !important;
    color: white !important;
    padding: 3px 7px;
    line-height: 2em;
    font-weight: 500;
}

span.rm-page-ref[data-tag="Projects"] {
    background: #2980b9 !important;
    color: white !important;
    padding: 3px 7px;
    line-height: 2em;
    font-weight: 500;
}

span.rm-page-ref[data-tag="Books"] {
    background: #8e44ad !important;
    color: white !important;
    padding: 3px 7px;
    font-weight: 500;
    line-height: 2em;
}

span.rm-page-ref[data-tag="People"] {
    background: #8e44ad !important;
    color: white !important;
    padding: 3px 7px;
    font-weight: 500;
    line-height: 2em;
}

span.rm-page-ref[data-tag="Ideas"] {
    background: #e67e22 !important;
    color: white !important;
    padding: 3px 7px;
    font-weight: 500;
    line-height: 2em;
}

span.rm-page-ref[data-tag="Recipes"] {
    background: #e67e22 !important;
    color: white !important;
    padding: 3px 7px;
    font-weight: 500;
    line-height: 2em;
}

span.rm-page-ref[data-tag="Videos"] {
    background: #f1c40f !important;
    color: white !important;
    padding: 3px 7px;
    font-weight: 500;
    line-height: 2em;
}

span.rm-page-ref[data-tag="Articles"] {
    background: #27ae60;
    color: #fff;
    padding: 3px 7px;
    line-height: 2em;
    font-weight: 500;
}

span.rm-page-ref[data-tag="Goals"] {
    background: #27ae60;
    color: #fff;
    padding: 3px 7px;
    line-height: 2em;
    font-weight: 500;
}

span.rm-page-ref[data-tag="Podcasts"] {
    background: #7f8c8d;
    color: #fff;
    padding: 3px 7px;
    line-height: 2em;
    font-weight: 500;
}

span.rm-page-ref[data-tag="Waiting"] {
    background: #f39c12;
    color: #fff;
    padding: 3px 7px;
    line-height: 2em;
    font-weight: 500;
}

span.rm-page-ref[data-tag="Inbox"] {
    background: #e74c3c;
    color: #fff;
    padding: 3px 7px;
    line-height: 2em;
    font-weight: 500;
}

span.rm-page-ref[data-tag="Meeting"] {
    background: #4CAF50;
    color: #fff;
    padding: 3px 7px;
    line-height: 2em;
    font-weight: 500;
}

span.rm-page-ref[data-tag="Waitingfor"] {
    background: #607D8B;
    color: #fff;
    padding: 3px 7px;
    line-height: 2em;
    font-weight: 500;
}
```

- [[Minimal query]]
	 - ```css
/* RR change: MINIMIZE QUERIES: add any one of the following tags before the beginning of your query (in the same block):

    #min-title = hides the page reference link / page title
    #min-con = hides the contextual reference information (breadcrumbs)
    #minimal = hides both the title and the context
    #min-q = hides the query string, similar to legacy behavior
    #min-all = hides everything — title, context, and query string

inspired by Matt Goldenberg */

[data-tag="minimal2"], 
[data-tag="minimal2"] + .rm-query .rm-title-arrow-wrapper,
[data-tag="minimal2"] + .rm-query .zoom-mentions-view {
  display:none!important; /* hide page reference (title) and mention context (breadcrumbs) */
}



[data-tag="min-intro"],
[data-tag="min-intro"] + .rm-query .rm-reference-item {
  display:none!important; /* hide page reference (title) and mention context (breadcrumbs) */
}




[data-tag="min-title"], [data-tag="min-title"] + .rm-query .rm-title-arrow-wrapper {
display:none!important; /* hide page reference (title) */
}
[data-tag="min-con"], [data-tag="min-con"] + .rm-query .zoom-mentions-view {
  display:none !important;  /* hide mention context (breadcrumbs) */
}
[data-tag="min-q"], 
[data-tag="min-q"] + .rm-query .rm-query-title {
  display:none !important;  /* hide the query string */
}
[data-tag="min-all"], 
[data-tag="min-all"] + .rm-query .zoom-mentions-view,
[data-tag="min-all"] + .rm-query .rm-title-arrow-wrapper,
[data-tag="min-all"] + .rm-query .rm-query-title {
  display:none !important;  /* hide everything */
}


```

- [[Minimal query new]]
	 - ```python
/* --- Query --- */

div.rm-query {
    border-top: 1px solid var(--fg-query-title) !important;
  	border-left:none;
    border-bottom:none;
   /* border-radius: var(--query-border-radius); */
	border-top-right-radius: 5px;
  	border-top-left-radius: 0px;
    border-bottom-right-radius: 0px;
    border-bottom-left-radius: 0px;
    margin-bottom: 10px;
    margin-right: 20px !important;
  
   /* border-image: linear-gradient(to bottom, red, green) 1 100%; */
}

/* Modified Queries - Inspired by @MattGoldenberg */

/* Minimal Queries */ 
[data-tag="min-title"], 
[data-tag="min-title"] + .rm-query .rm-title-arrow-wrapper, 
[data-tag="min-title"] + .rm-query .rm-query-title::after {
display:none!important; /* hide page reference (title) */
}
[data-tag="min-page"], 
[data-tag="min-page"] + .rm-query .rm-reference-item,
[data-tag="min-page"] + .rm-query .rm-query-title {
  display:none !important;  /* Page Only */
}

[data-tag="min-con"], 
[data-tag="min-con"] + .rm-query .zoom-mentions-view {
  display:none !important;  /* hide mention context (breadcrumbs) */
}
[data-tag="min-q"], 
[data-tag="min-q"] + .rm-query .rm-query-title {
  display:none !important;  /* hide the query string */
}
[data-tag="min-b"], /* This line ensures the tag doesn't show up (?)*/
[data-tag="min-b"]+ .rm-query .rm-query-title, 
[data-tag="min-b"]+ .rm-query .zoom-mentions-view{
  display:none !important;  /* hide the query string  & breadcrumb */
  
}


[data-tag="min-all"], 
[data-tag="min-all"] + .rm-query .zoom-mentions-view,
[data-tag="min-all"] + .rm-query .rm-title-arrow-wrapper,
[data-tag="min-all"] + .rm-query .rm-query-title {
  display:none !important;  /* hide everything */
}
[data-tag="minimal"] + .rm-query .rm-query-title::after,
[data-tag="min-title"] + .rm-query .rm-query-title::after,
[data-tag="min-con"] + .rm-query .rm-query-title::after,
[data-tag="min-b"] + .rm-query .rm-query-title::after{
  content: " #minimal" /* add a tag to the query string to indicate this query has been minimized */
}
```
