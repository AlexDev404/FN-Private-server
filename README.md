# FN-Private-server
A Markdown explanation of how work private server in Fortnite.

## What's a Fortnite private server
A Fortnite private server is a Fortnite "client" that got customized informations like: added skins, edited news, new emotes, etc...
You can interact with some Fortnite features like: join friends, add friends, and all online **lobby** features.

## How it's works
A Fortnite private server change the EPIC Game API Host to another host, the edited host will be send customized infos.
This is just an example and the name and endpoints are fakes:
```
# not edited
(GET) api.epicgame.com/ACCOUNT-ID/get-skins:
    return => "real skins of the player"


# edited
(GET) api.epicgame.com/ACCOUNT-ID/get-skins:
    return => "all skins"
```
In Python using Flask

```python
from flask import Flask

app = Flask(__name__)

@app.route('/<accountId>/get-skins', methods = ['GET'])
def get_skins(accountId: str) -> list[str]:
    return 'all skins'
```

## There are some problems
Our API need a lot of endpoints, but the Fortnite backend is not open source and we dont have access to the Fortnite Database 🙁 and if we dont place required endpoints,
Fortnite need to intercact with our custom API.

### Solution 1
Make a robbery in EpicGames
<br>
❌ we cant

<hr>

### Solution 2
Place all required endpoints
<br>
❌ we cant

<hr>

### Solution 3
Make Fortnite interact with our custom API
<br>
✅ we can
 
 To make Fortnite interact with our custom API, wee need to have access to the Fortnite binary.
 We can inject a dll in the Fortnite binary to change some api endpoints to our.
 
 Finally, when you inject the DLL into the Fortnite binary, it change some endpoints and redirected to our and the responses are like we changed it.
