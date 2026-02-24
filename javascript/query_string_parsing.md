# Query String Parsing

```javascript
/*
Example url: https://domain.com/index.html?foo=one&bar=two
`window.location.search` contains the search/query string i.e "?foo=one&bar=two".
URLSearchParams constructor takes the query string and returns a URLSearchParams object.
The object has utility methods for working with the query string.
One of those methods is "get" which takes a search parameter and returns the first value associated with it.
*/
const searchParams = new URLSearchParams(window.location.search);
console.log(searchParams.get("foo")); // "one"
console.log(searchParams.get("bar")); // "two"
```
