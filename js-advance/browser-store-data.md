### Cookie
- usually set by a web server using the response `Set-Cookie` HTTP header. Then, the browser automatically adds them to (almost) every request to the same domain using the Cookie HTTP header.
- `document.cookie`: cookie1=value1; cookie2=value2;...
- `document.cookie="user=John"`: to append cookie pair
- `encodeURIComponent(str)`: keep key/value string valid

#### Cookie attributes
- `domain=site.com`: A domain defines where the cookie is accessible. Another 2nd-level domain, like `other.com` will never receive a cookie set at `site.com` while `a.site.com` can access cookie.
- `path=/mypath`: makes the cookie accessible for pages under that path, usually "/"
- `expires=Tue, 19 Jan 2038 03:14:07 GMT`: defines the time when the browser will automatically delete the cookie
- `max-age=3600`: specifies the cookie’s expiration in seconds from the current moment.
- `secure`: cookie should be transferred only over HTTPS. With this attribute, if a cookie is set by https://site.com, then it doesn’t appear when the same site is accessed by HTTP, as http://site.com


### Browser storage
- `LocalStorage, sessionStorage`
- The storage is bound to the origin (`domain/protocol/port` triplet). That is, different protocols or subdomains infer different storage objects, they can’t access data from each other.
- both key and value must be strings.
- `setItem(key, value)` – store key/value pair.
- `getItem(key)` – get the value by key.
- `removeItem(key)` – remove the key with its value.
- `clear()` – delete everything.
- `key(index)` – get the key on a given position.
- `length` – the number of stored items.
- sessionStorage exists only within the current browser tab

### IndexedDB
upside:
1. Stores almost any kind of values by keys, multiple key types.
2. Supports transactions for reliability.
3. Supports key range queries, indexes.
4. Can store much bigger volumes of data than localStorage.

usage:
- let openRequest = indexedDB.open(name, version);