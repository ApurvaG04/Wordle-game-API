# Wordle game API

# Configuration files:
1. Procfile is a mechanism for declaring what commands are run by your application to start the app 
2. Update the nginx.config from nginx_config/tutorial into default file present in /etc/nginx/sites-enabled

# The following are the steps to run the project:
1. Installing and configuring Nginx:
```bash
sudo apt update
sudo apt install --yes nginx-extras
```
2. Clone the github repository:
```bash
git clone https://github.com/Sravani-Kallmepudi/CPSC449-Project3.git
```
3. Then cd into the CPSC449-Project3 folder and run the following commands:
```bash
cd bin
chmod u+x lifefs
sh init_dir.sh
cd ..
```
4. Start the services
```bash
foreman start 
```
5. Run both the init scripts to populate the database and automatically connect the api to the database. 
```bash
./bin/init_auth.sh
./bin/init_game.sh
```
Now the API can be run using Postman(the method which we followed) or using curl or httpie.

## ENDPOINT 1:
For registering an user: @app.route("/register", methods=["POST"])
```bash
http POST http://tuffix-vm/register/ username=Rain password=rain@123
```
## ENDPOINT 2:
For authenticating the user:@app.route("/auth", methods=["GET"])
```bash
Ex: On postman with Basic-Auth: http://tuffix-vm/auth
```
## ENDPOINT 3: 
For creating a new game for an authenticated user:@app.route("/game/", methods=["POST"])
```bash
Ex: On postman with Basic-Auth: http://tuffix-vm/game
```
## ENDPOINT 4:
For getting the game state of the authenticated user:@app.route("/game/:gameId", methods=["GET"])
```bash
Ex: On postman with Basic-Auth: http://tuffix-vm/game/:gameId
``` 
## ENDPOINT 5:
List all the games for the authenticated user:@app.route("/my-games", methods=["GET"])
```bash
Ex: On postman with Basic-Auth: http://tuffix-vm/my-games  
```
## ENDPOINT 6:
Guessing a word: @app.route("/game/:gameId", methods=["PATCH"])
```bash
Ex: On postman with Basic-Auth: http://tuffix-vm/game/:gameId
note: In the body, select raw - JSON and then {"word":"apple"}
```
## ENDPOINT 7:
Reporting a game to the leaderboard: @app.route("/reportgame", methods=["POST"])
```bash
Ex: On postman: http://127.0.0.1:5400/reportgame
note: In the body, select raw - JSON and then {"username":"Rain", "result":1, "guesses":3}
note2: result is a 1 for win and 0 for loss
```
## ENDPOINT 8:
Resetting the leaderboard to empty: @app.route("/resetleaderboard", methods=["POST"])
```bash
Ex: On postman: http://127.0.0.1:5400/resetleaderboard
```
## ENDPOINT 9:
Viewing the top 10 on the leaderboard: @app.route("/leaderboard", methods=["GET"])
```bash
Ex: On postman: http://tuffix-vm/leaderboard
```
