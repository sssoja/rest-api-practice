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
`GET /index.html`
Accept: `text/html` Response - 200 (OK) Content-type: `text/html`</li>
<li>Request - <code>GET /style.css</code> Accept: `text/css` Response - 200 (OK) Content-type: `text/css`</li>
<li>Request - `GET /venues` Accept: `application/json` Response - 200 (OK) Content-type: `application/json`</li>
<li>Request - `GET /venues/:id` Accept: `application/json` Response - 200 (OK) Content-type: `application/json`</li>
<li>Request - `GET /venues/:id/photos` Accept: `application/json` Response - 200 (OK) Content-type: `application/json` </li>
<li>Request - `GET /venues/:id/photos/:id` Accept: `image/png` Response - 200 (OK) Content-type: `image/png` </li>
<li>Request - `GET /users` Accept: `application/json` Response - 200 (OK) Content-type: `application/json`</li>
<li>Request - `GET /users/:id` Accept: `application/json` Response - 200 (OK) Content-type: `application/json`</li>
</ul>

<h3>POST Requests</h3>

<ul>
<li>Request - `POST /users` Accept: `application/json` Response - 201 (CREATED) Content-type: `application/json`</li>
<li>Request - `POST /venues` Accept: `application/json` Response - 201 (CREATED) Content-type: `application/json`</li>
<li>Request - `POST /venues/:id/photos` Accept: `application/json` Response - 201 (CREATED) Content-type: `application/json` </li>
</ul>

<h3>PUT Requests</h3>

<ul>
<li>Request - `PUT /users/:id` Response - 200 (OK)</li>
<li>Request - `PUT /venues/:id` Response - 200 (OK)</li>
<li>Request - `PUT /venues/:id/photos/:id` Response - 200 (OK)</li>
</ul>

<h3>DELETE Requests</h3>

<ul>
<li>Request - `DELETE /users/:id` Response - 204 (NO CONTENT)</li>
<li>Request - `DELETE /venues/:id` Response - 204 (NO CONTENT)</li>
<li>Request - `DELETE /venues/:id/photos/:id` Response - 204 (NO CONTENT)</li>
</ul>

Taken from CodeAcademy's What is REST article - https://www.codecademy.com/articles/what-is-rest
