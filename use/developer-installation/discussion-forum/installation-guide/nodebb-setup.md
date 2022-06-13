# Nodebb setup

Before using the discussion forum we have to do below configurations.

### Nodebb:

NodeBB is an open source project which can be forked on GitHub ([Link](https://github.com/NodeBB/NodeBB)). It have plugin support. We can create new plugins for our requirement and link to nodebb.

### How to setup nodebb in local environment <a href="#how-to-setup-nodebb-in-local-environment" id="how-to-setup-nodebb-in-local-environment"></a>

**Note:** Before staring nodebb setup in local. check redis is up and running. If not start redis first and do the setup.

**Step:1**

Clone the nodebb repo

```
git clone -b v1.18.x https://github.com/NodeBB/NodeBB.git nodebb
```

**Step:2**

Navigate to nodebb folder and do setup of nodebb using below command

```
./nodebb setup
```

While running the setup, nodebb will ask below question for initial setup.

```
>> URL used to access this NodeBB (http://localhost:4567) : Press Enter 
>> Please enter a NodeBB secret (44abfc50-3d6a-4e6c-a258-9f551f9faa5a) : Press Enter 
>> Would you like to submit anonymous plugin usage to nbbpm? (yes) : Press Enter 
>> Which database to use (mongo) : redis

Now configuring redis database:
>> Host IP or address of your Redis instance (127.0.0.1) : Press Enter 
>> Host port of your Redis instance (6379) : Press Enter 
>> Password of your Redis database : Press Enter 
>> Which database to use (0..n) (0) : 3 (redis db number)

Admin User details
>> Administrator username : admin 
>> Administrator email address : admin@test.com
>> Password : Your password
>> Confirm Password : Your password
```

**Step:3**

Now start the nodebb, Using below command.

```
./nodebb start
```

**Step:4**

Build the nodebb using the below command.

```
./nodebb build
```

**Step:5**

Open the browser with fallowing link [http://localhost:4567](http://localhost:4567/)

**Use full commands**

```
./nodebb log -> To see the logs
./nodebb status -> To check is nodebb running or not
./nodebb activate plugin-name -> To activate the plugin
./nodebb reset -p plugin-name -> To reset/disable the plugin
./nodebb stop -> To stop nodebb
```

### Mandatory Plugins <a href="#mandatory-plugins" id="mandatory-plugins"></a>

We have built our own plugins based on our need. We need to enable those plugins.

| nodebb-plugin-create-forum | Contains all custom api | [https://github.com/Sunbird-Ed/nodebb-plugin-sunbird-api.git](https://github.com/Sunbird-Ed/nodebb-plugin-sunbird-api.git)   |
| -------------------------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| nodebb-plugin-sunbird-oidc | User login api          | [https://github.com/Sunbird-Ed/nodebb-plugin-sunbird-oidc.git](https://github.com/Sunbird-Ed/nodebb-plugin-sunbird-oidc.git) |

#### Activating Plugins <a href="#activating-plugins" id="activating-plugins"></a>

In this plugins, We added our own apis. Like User login, Enable discussion, read discussion context, disable discussion, user read based on sunbird id …. etc.

To activate plugin. Use below command.

a. Using repo as a npm module.

```
npm install https://github.com/Sunbird-Ed/nodebb-plugin-sunbird-api.git
./nodebb activate nodebb-plugin-create-forum
```

b. Using from local

* clone the repo `https://github.com/Sunbird-Ed/nodebb-plugin-sunbird-api.git`\`
* Execute command `npm install`
* Execute command `npm link`
* Go to nodebb terminal and execute command `npm link nodebb-plugin-create-forum`
* Execute command `./nodebb activate nodebb-plugin-create-forum`
* And execute command `./nodebb build`

**Note**: When you enable or disable any plugin, You have to rebuild and restart your nodebb. Then only the changes will reflects.

Do the same thing for other plugin.

#### Write api plugin <a href="#write-api-plugin" id="write-api-plugin"></a>

This in an important plugin, By using this we can do all write operation in nodebb. Like create category/topic/post, updating topic/post, delete topic/post…..etc.

**Install nodebb-plugin-write-api**

1. Login to nodebb as a admin user.
2. Go to admin pannel.
3. Go to `EXTEND => PLUGINS => FIND PLUGINS`
4. Search for `nodebb-plugin-write-api`
5. Click on `Install`
6. Rebuild and restart nodebb.
7. Reload the admin panel.
8. Go to `EXTEND => PLUGINS => INSTALLED`
9. Search for `nodebb-plugin-write-api`
10. Click on `Activate`
11. Rebuild and restart nodebb.

**What is Master token**

To perform any write operations in nodebb we need write api plugin. And this plugin provides apis to do those write operations but If you want to use this apis we have to pass a master token (in request `headers` as Authorization token) and nodebb user id(add `_uid` as query param or with in request body ).

**How to create master**

1. Login to nodebb as a admin user.
2. Go to admin pannel.
3. Go to `PLUGINS => WRITE API`
4. Left side panel you can see `MASTER TOKENS` Section.
5. Click on `CREATE TOKEN`

Refer this link also: [Nodebb Plugins](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/1981546511/Discussion+Forum+Deployment).
