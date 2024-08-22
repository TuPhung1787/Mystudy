# Guide for Express JS

## Start the initialize project

+ Step 1: install `npm init`
+ Step 2: `npm i express`
+ Step 3: create file `server.js`
+ Step 4: `npm install nodemon -g`
+ Step 5: `npm install body-parser`
+ Set for test mongodb:
  + cd to `C:\Program Files\MongoDB\Server\7.0\bin` and run `./mongod --dbpath D:\DataMongo\db` 
+ Step 6: START PROJECT `npm start` which is defined `start` into the package.json
  
### Change repository into Github

+ Step 1: `cd pathOfProfject`
+ Step 2 `git init`
+ Step 3: `git status`
+ Step 4: `git add ....`
+ Step 5: `git commit -m ""`
+ Step 6: `git remote add origin https://github.com/TuPhung369/tuphung010787.git`
  + check `git remote -v`
+ Step 7: `git push -u origin main`
  
## OpenSSL

+ download and open directly as cmd (double click as normal)
+ add new path to environment of computer (for run anywhere)
+ `openssl` by cmd
+ `openssl genrsa -out private.pem 2048`
+ `openssl rsa -in private.pem -pubout -out publickey.crt`
+ `openssl pkcs8 -topk8 -inform PEM -outform PEM -nocrypt -in private.pem -out pkcs8.key`

+ P/S : we can change to different algorithms (can read into the demoOpenSSL.js for more algorithms)
  + Generate an Ed25519 private key
    openssl genpkey -algorithm ed25519 -out private.pem
  + Extract the corresponding Ed25519 public key
    openssl pkey -in private.pem -pubout -out publickey.pem
`
+ session
`npm install express-session connect-redis redis`
`npm install ioredis`

### ngrok download and run file .exe get Authtoken from ngrok account and put into commmand

`ngrok config add-authtoken 2isq6ubIlELkddwqEoPi7chKgnw_2PyvUDqiSZdJpjdTZoVmW`

### Heroku

+ heroku logs --tail --app tuphung010787

### Start and run the project

+ Step 1: run server by `npm start` at the project
+ Step 2: run Backend server cd to `C:\Program Files\MongoDB\Server\7.0\bin` and run `./mongod --dbpath D:\DataMongo\db`
+ Step 3: go to the url `http://localhost:3000/login`
+ Step 3.1: go to `http://localhost:3000/register`
+ Step 4: go to file `server.js` file to see all off setup.
+ Step 5: go to app MongoDBCompass to see the structure of DataBase
  + `mongodb://localhost:27017` connect to `ExpressJS` name of app's Database.
+ Step 6: `http://localhost:3000/auth/facebook` login with facebook
+ Step 6.1: `http://localhost:3000/auth/github` login with github
+ Step 6.2: `http://localhost:3000/auth/google` login with google
+ Step 6.3: `http://localhost:3000/register` create account.
+ Step 6.4: `http://localhost:3000/login` need 3 things for login, userName, password (otherId received when login auth/google or auth/facebook), and OTP (smsPhone/email/2FA by Microsoft or Google from STEP 7:) `phone need to check again`
+ Step 7: 2FA by Microsoft or Google - Function to generate OTP Auth URL
  + 1st time after login we need to use Application to scan QR code 

### How to move file between version (commit a vs commit b), git log.

+ ***APPROACH 1***:
  + Step 1: `git branch` to get 2 branch name
    + `p-hmm6286/chore/reset-password`
    + `HEAD .... a9a1f08`
  + Step 2: `git checkout p-hmm6286/chore/reset-password` ==> branch would like to update.
  + Step 3: `git merge a9a1f08` --> merge the branch HEAD (a9a1f08) to the branch (p-hmm6286/chore/reset-password)
  + Step 4: `git rebase a9a1f08` --> resolve the conflict
  + Step 5: `git status` ---> verify again the Updated files
  + Step 6: `git commit -m "..." --no-verify` --> commit the files change
  + Step 7: `git push -u origin p-hmm6286/chore/reset-password`

+ APPROACH 2: **need to verify again**.
  + Step 1: `git branch` to get 2 branch name
    + `p-hmm6286/chore/reset-password`
    + `HEAD .... a9a1f08`
  + Step 2: Check the file diff 2 branches (file name at the path `shared/utils/index.ts`)
    + `git diff a9a1f08 p-hmm6286/chore/reset-password -- shared/utils/index.ts`
  + Step 3: Check Out the Old Version of the File
    + `git checkout a9a1f08 -- shared/utils/index.ts`
  + Step 4: Verify the file: check content of the file before update.
    + `cat shared/utils/index.ts`
  + Step 5: Stage the File for Commit
    + `git add shared/utils/index.ts`
  + Step 6: Commit the Change
    + `git commit -m "Reverted shared/utils/index.ts to the version from commit a9a1f08"`
  + Step 7: Push the Changes
    + `git push -u origin p-hmm6286/chore/reset-password`

### How to synchronize Submodule (packages) vs Main Module (hnv-fe)

Current path: at /hnv-fe

+ Step 1: `cd packages`
+ Step 2: `git checkout p-hmm6286/chore/reset-password`
+ Step 3: `git status`
+ Step 4: `git add .` or `git add files`
+ Step 5: `git commit -m "content of your commits" --no-verify`
+ Step 6: `git push -u origin p-hmm6286/chore/reset-password` ==> go to github of hnv-fe-packages (Submodule's repos) to create PR.
+ Step 7: `cd ../`
+ Step 8: `git checkout hmm6286/chore/reset-password`
+ Step 9: `git status`
+ Step 10: `git add .` or `git add files`
+ Step 11: `git commit -m "content of your commits" --no-verify`
+ Step 12: `git push -u origin hmm6286/chore/reset-password` ==> go to github of hnv-fe (Main module's repos) to create PR.
+ Step 13: `git submodule update` --> **update the latest commit** This updates the submodule reference in the main module to the **latest** commit on the submodule branch (p-hmm6286/chore/reset-password). This ensures the main module is pointing to the latest state of the submodule after your changes.