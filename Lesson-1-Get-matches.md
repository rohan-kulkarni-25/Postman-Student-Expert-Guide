<h1>GET REQUEST</h1>

```
GET {{training_api}}/matches
```

<ul>
<li>When you send the request you get data about matches. You can also read more in VISULIZE</li>
<li>Our first task is to get the matches with status as pending. We can do this with help of query parameters</li>

```
GET {{training_api}}/matches?status=pending
```
<li>You need to send this route.You will get the matches which are pending as a response.</li>
<li>This is how you can sort data coming from API ( The sorting must be provided by the server also. )</li>
<li>You need to save this request and create a new request "2. Add match</li>
</ul>

<h1>POST Request</h1>

<ul>
<li>You need to send a POST Request now</li>

```
POST {{training_api}}/match
```
<li>This will give you authentication error because we need to be authenticated to get some response for this request. You can understand auth as login to account.</li>

<li>Click on three dots near collection name and this will give you option to edit then click on that.</li>
<li>When you see under authorization you can see key as matchkey and value as emailkey which means you need to provide your email as emailkey</li>
<li>We need to create a varible with name emailkey and value as email we used for registration.</li>
<li>Click on variable tab and create a new variable under training_api.</li>

```
variable : email_key
initial_value : rohank2502@gmail.com
```
<li>Now after sending requst it will give you Bad Request - Check your body data because in POST request we need to provide some data in body.</li>
<li>Click on BODY then Click on TEXT and convert it to JSON</li>
<li>Add the given object in the body and send request again.</li>

```
{
  "match": "Cup Final",
  "when": "{{$randomDateFuture}}",
  "against": "Academical"
}
```

<li>This time you will see SUCCESS MESSAGE. You can check about the added data in get matches request.</li>
<li>Now next step is PUT Request.Save this request and create a new request "3. Update Score"</li>
</ul>

<h1>PUT REQUEST</h1>

```
PUT {{training_api}}/match
```