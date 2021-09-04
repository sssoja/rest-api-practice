<h1>Practice with REST</h1>

Let’s imagine we are building a photo-collection site. We want to make an API to keep track of users, venues, and photos of those venues. This site has an index.html and a style.css. Each user has a username and a password. Each photo has a venue and an owner (i.e. the user who took the picture). Each venue has a name and street address. Can you design a REST system that would accommodate:

<ul>
<li>storing users, photos, and venues</li>
<li>accessing venues and accessing certain photos of a certain venue</li>
</ul>

Start by writing out:

<ul>
<li>what kinds of requests we would want to make</li>
<li>what responses the server should return</li>
<li>what the `content-type` of each response should be</li>
</ul>

<h2>Possible Solution - Models</h2>

<h4>User</h4>

```
{
  "user": {
    "id": <Integer>,
    "username": <String>,
    "password":  <String>
  }
}
```

<h4>Photo</h4>

```
{
  "photo": {
    "id": <Integer>,
    "venue_id":  <String>,
    "user_id": <String>
   }
}
```

<h4>Venue</h4>

```
{
  "venue": {
    "id": <Integer>,
    "name":  <String>,
    "address": <String>
   }
}
```

<h2>Possible Solution - Requests/Responses</h2>

<h3>GET Requests</h3>

<ul>
<li>Request - 
<code>GET /index.html</code>
Accept: <code>text/html</code> Response - 200 (OK) Content-type: <code>text/html</code></li>
<li>Request - <code>GET /style.css</code> Accept: <code>text/css</code> Response - 200 (OK) Content-type: <code>text/css</code></li>
<li>Request - <code>GET /venues</code> Accept: <code>application/json</code> Response - 200 (OK) Content-type: <code>application/json</code></li>
<li>Request - <code>GET /venues/:id</code> Accept: <code>application/json</code> Response - 200 (OK) Content-type: <code>application/json</code></li>
<li>Request - <code>GET /venues/:id/photos</code> Accept: <code>application/json</code> Response - 200 (OK) Content-type: <code>application/json</code></li>
<li>Request - <code>GET /venues/:id/photos/:id</code> Accept: <code>image/png</code> Response - 200 (OK) Content-type: <code>image/png</code></li>
<li>Request - <code>GET /users</code> Accept: <code>application/json</code> Response - 200 (OK) Content-type: <code>application/json</code> </li>
<li>Request - <code>GET /users/:id</code> Accept: <code>application/json</code> Response - 200 (OK) Content-type: <code>application/json</code></li>
</ul>

<h3>POST Requests</h3>

<ul>
<li>Request - <code>POST /users</code> Accept: <code>application/json</code> Response - 201 (CREATED) Content-type: <code>application/json</code></li>
<li>Request - <code>POST /venues</code> Accept: <code>application/json</code> Response - 201 (CREATED) Content-type: <code>application/json</code></li>
<li>Request - <code>POST /venues/:id/photos</code> Accept: <code>application/json</code> Response - 201 (CREATED) Content-type: <code>application/json</code></li>
</ul>

<h3>PUT Requests</h3>

<ul>
<li>Request - <code>PUT /users/:id</code> Response - 200 (OK)</li>
<li>Request - <code>PUT /venues/:id</code> Response - 200 (OK)</li>
<li>Request - <code>PUT /venues/:id/photos/:id</code> Response - 200 (OK)</li>
</ul>

<h3>DELETE Requests</h3>

<ul>
<li>Request - <code>DELETE /users/:id</code> Response - 204 (NO CONTENT)</li>
<li>Request - <code>DELETE /venues/:id</code> Response - 204 (NO CONTENT)</li>
<li>Request - <code>DELETE /venues/:id/photos/:id</code> Response - 204 (NO CONTENT)</li>
</ul>

Taken from CodeAcademy's What is REST article - https://www.codecademy.com/articles/what-is-rest
