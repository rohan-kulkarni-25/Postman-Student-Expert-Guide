<h1>Begin Training - Requests</h1>
<hr>

<p>Let's Start with our Collections.You can understand request as per the word says that you are requesting data from the server.</p>

<ul>
<li>For starting learning you need to click on SEND which means you are Sending a request to given route ( URL ) which is "postman-student-expert.glitch.me/training" in this case as you can see there.</li>
<li>When send the request you will get response</li>
<li>In this collection response will help you to do next steps</li>
</ul>

<h3>This Particular Request will teach you how to setup a variable</h3>
<ul>
<li>You need to select the "postman-student-expert.glitch.me" After hovering the selected area you will be able to SET AS VARIABLE.</li>
<li>For setting up variable you need to provide name "training_api" and scope as Collection.</li>
<li>When you need to use the url "postman-student-expert.glitch.me" for sending request you can now use {{training_api}}.</li>
<li>For eg: "{{training_api}}/matches"</li>
<li>With this note let's move to next request in our Folder which is GET MATCHES ! Don't Forget to SAVE THE REQUEST from top right area in Navbar.</li>
</ul>


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

<ul>
<li>When you send this PUT request you will get an error which will ask you to provide match id.</li>
<li>You can go to GET request and then send it again and copy the match id of the match you added ( ONLY MATCH YOU ADDED CAN BE UPDATED BY YOU )</li>
<li>You need to provide this id as params</li>

```
PUT {{training_api}}/match?match_id=LwDlF-mHt
```
<li>Your request will look like this.</li>
<li>This reqeust will give you error becuase in PUT requset you need to send data to be updated in body</li>
<li>Go to body select raw and type as json</li>

```
{
    "points":3
}
```
<li>Send this Object as JSON</li>
<li>You will get a success message now. Next Task is to DELETE the match.</li>
<li>Don't forget to save this request and create a new request "4. Remove match"</li>
</ul>


<h1>DELETE REQUEST</h1>

```
DELETE {{training_api}}/match/:match_id
```

<ul>
<li>You need to pass this request in DELETE and this will delete the match with this id. ( YOU CAN ONLY DELETE THE MATCH YOU ADDED )</li>

```
/:match_id
```
<li>This is a PATH Variable which will help to know which match you want to delete.</li>
<li>That's it for this part and you will save the request and move to the next part.</li>
</ul>