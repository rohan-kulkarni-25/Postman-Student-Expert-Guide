<h1>TEST SCRIPTS</h1>


<h1>GET ALL PLAYERS</h1>

<ul>
<li>In this section we will learn how the testing of POSTMAN works !!</li>
<li>Send the GET request to the given route</li>

```
GET {{mock_url}}/players
```

<li>You need to add the test script in test tab.</li>

```
pm.test('Status code is 200', function () {
    pm.response.to.have.status(200); 
});
```
<li>This test will check that is the status code of the response coming from the API is 200 or not if it is not 200 then the test will fail</li>

<li>When you will send the request the test will pass becuase the response is 200.</li>

<li>To fail the test we need to change the test script. This time we will send the test with status code 400</li>

```
pm.test('Status code is 400', function () {
    pm.response.to.have.status(400); 
});
```
<li>After sending this test you will get test failed response because the status is 200 and we are asking to test for status 400</li>
<li>You have to save this request and open the GET SPECIFIC PLAYER Request</li>
<li>Make sure you save the request with code 400</li>
</ul>

<h1>GET SPECIFIC PLAYER</h1>

<ul>
<li>In this route you will get data about a single player</li>
<li>You need to provide id of player as key.</li>

```
GET {{mock_url}}/player?id={{player_id}}
```

<li>By seeing this request you are now able to understand that "player_id" will be a variable.</li>
<li>When you hover on that varible it shows "unresolved variable"</li>
<li>To solve this issue we need to create an Environment for this test</li>
<li>To create and environment we will click on the eye icon in top right section</li>
<li>Create a new environment from there and add "player_id" as a varible. You can give the environment name of your choice</li>
<li>You don't need to write the value as of now we will add that using test script</li>
<li>After adding the variable you need to select the environment as an acitve environment with help of drop down near the eye icon</li>
<li>After this the issue of unresolved variable will be solved</li>
<li>Now we need to setup the value of "player_id" with help of test.</li>
<li>Go to Get all players request and in the test all the following lines after our old test to check the status code.</li>

```
var player_list=pm.response.json().data.players;
pm.environment.set('player_id', player_list[Math.floor(Math.random() * player_list.length)].id);
```

<li>The test of Get all players will look like this now</li>

```
pm.test('Status code is 400', function () {
    pm.response.to.have.status(400); 
});
var player_list=pm.response.json().data.players;
pm.environment.set('player_id', player_list[Math.floor(Math.random() * player_list.length)].id);
```

<li>After sending request Click save and open Get specific player.</li>
<li>In this when you hover on the "player_id" you will be able to see a number assigned to it</li>
<li>That is because the test we ran in get all players. In that test enviroment varible with name player id was set to random number between player list.</li>
<li>The player id variable got it's value as number because we run the test in get all players request but what if we don't do that. The player id will be having no value. For this condition of player id having no value we will write one pre-request-script which will run before sending the request.</li>

```
if(!pm.variables.get('player_id')) pm.variables.set('player_id', -1);
```
<li>Write this script in pre-request script section of get specific player request. This will check that is player id variable present and if it is not present then it will set player id variable as -1</li>
<li>To check this pre-request script we will change our environment to no environment and send request 2 times.</li>
<li>When you check the player id now it is resolved now open console which is present in left bottom. And check the last request it will be like this</li>

```
GET https://6d338fbc-93bd-456e-85a0-818bd4cd3177.mock.pstmn.io/player?id=-1
```
<li>As we can see inplace of player id -1 was sent it means that our pre request script was successfully executed.</li>
<li>Now you need to provide a description to this request.</li>
<li>Go to documentation which is on right side below the eye logo click on it and when you hover below the url you will be able to get a pencile icon to edit it you can just write anything into description like "Learning API DEVELOPMENT" and anything related to this request.</li>
<li>Click on save and also save the request and open next request which is GET STATS</li>

</ul>

<h1>GET STATS</h1>

<ul>
<li>Send the request.<li>
<li>First thing we need to do is that we need to add the status check test in all three request of this folder.We have added it to get all player so add it to get specific player and to get stats</li>

```
pm.test('Status code is 200', function () {
    pm.response.to.have.status(200); 
});
```
<li>Make sure you save each request</li>
<li>Now you need to add one more test in Get stats request which will check that does the data contains all the required fileds</li>

```
pm.test('Stats include all fields', function () {
    var jsonData = pm.response.json().data;
    pm.expect(jsonData).to.have.all.keys('won', 'lost', 'drew');
});
```
<li>Test tab in the GET STATS Request will look like this</li>

```
pm.test('Status code is 200', function () {
    pm.response.to.have.status(200); 
});
pm.test('Stats include all fields', function () {
    var jsonData = pm.response.json().data;
    pm.expect(jsonData).to.have.all.keys('won', 'lost', 'drew');
});
```

<li>Now we need to run all the tests from this folder so we will use the runner which will help us to run all the test.</li>
<li>Click on the three dots after our Collection folder and click on "run collection"</li>
<li>Keep only 3 request selected of this folder and remove others</li>

```
GET ALL PLAYERS
GET SPECIFIC PLAYER
GET STATS
```
<li>Click on RUN</li>
<li>This will provide you result of all tests.In this our 1 test will fail as we have added 400 code in our test so don't worry.</li>
<li>Now in the test of Get Specific player we need to add one more test</li>

```
if(pm.response.json().data.played<750) postman.setNextRequest('Get all players');
```

<li>Now run the runner once again. Check that if your failed request only contains failure due to error 400 if this is the case you are good to go on next level. Open the folder Check progress and send the request.</li>
</ul>