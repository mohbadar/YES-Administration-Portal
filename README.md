# Strapi application

# How to install Strapi with Mongo DB

```
1: Create a new Strapi project
⚡️ npx create-strapi-app project-name
2: Choose your installation type Custom (manual settings)
3: Choose your main database: MongoDB
4: Database name: my-project
5: Host: 127.0.0.1
6: +srv connection: false
7: Port (It will be ignored if you enable +srv): 27017
8: Username:
9: Password:
10: Authentication database (Maybe "admin" or blank):
11: Enable SSL connection: false

⏳ Testing database connection...
The app has been connected to the database successfully!

🏗  Application generation:
✔ Copy dashboard
✔ Installed dependencies.

👌 Your new application my-project is ready at /Users/Username/Desktop/Projects/my-project.

⚡️ Change directory:
$ cd my-project

⚡️ Start application:
$ strapi develop
```

# Update Strapi version

### Start by upgrading all your Strapi packages in your package.json.

- For example upgrading from 3.2.4 to 3.2.5

```
{
  //...
  "dependencies": {
    "strapi": "3.2.5",
    "strapi-admin": "3.2.5",
    "strapi-connector-bookshelf": "3.2.5",
    "strapi-plugin-content-manager": "3.2.5",
    "strapi-plugin-content-type-builder": "3.2.5",
    "strapi-plugin-email": "3.2.5",
    "strapi-plugin-graphql": "3.2.5",
    "strapi-plugin-upload": "3.2.5",
    "strapi-plugin-users-permissions": "3.2.5",
    "strapi-utils": "3.2.5"
    //...
  }
}
```

### After editing the file run `npm install` to install the specified version.

- If the operation doesn't work, you should probably remove your package-lock.json. If it still does not work, try again after also removing the folder node_modules.

### Rebuild your administration panel

- `npm run build -- --clean`

### Migration guides

- Sometimes Strapi introduces breaking changes that need more than just the previous steps. That is the reason for the [Migration guides page](https://strapi.io/documentation/developer-docs/latest/migration-guide/).

### Start your application

If you have followed the information above, you can start your application with:

- `npm run develop`

# Deployment

### Launch the server

- Before running your server in production you need to build your admin panel for production

`NODE_ENV=production npm run build`

### Start application with pm2

create a ./server.js file in root directory as follows:

```
const strapi = require('strapi');

strapi(/* {...} */).start();
```

`Run the server with the development settings:`

```
sudo pm2 start server.js --name api
```

`Run the server with the production settings.:`

```
NODE_ENV=production pm2 start server.js --name api
```
