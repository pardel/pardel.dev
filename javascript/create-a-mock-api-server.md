# Create a Mock API server

During the development lifecycle, we often encounter situations where we need to mock an external API server - either because it's temporarily unavailable \(we might be offline\) or because it simply wasn't built yet.

Here is how to get one running in no time.

```bash
$ mkdir ApiServer
$ cd ApiServer
$ npm install -g json-server
  /usr/local/bin/json-server -> /usr/local/lib/node_modules/json-server/
    lib/cli/bin.js
  + json-server@0.15.1
  added 237 packages from 128 contributors in 12.542s
```

Let's now create a file that will contain the data to be served. Create a **data.json** file with the following content

```javascript
{
  "tasks": [
    {
      "id": 1,
      "name": "Buy some milk"
    },
    {
      "id": 2,
      "name": "Renew insurance"
    }
  ]
}
```

Let's now start the server:

```text
$ json-server -p 8080 --watch data.json 

   \{^_^}/ hi!
  
  Loading data.json
  Done
  
  Resources
  http://localhost:8080/tasks
  
  Home
  http://localhost:8080
  
  Type s + enter at any time to create a snapshot of the database
  Watching...

```

Navigate to [http://localhost:8080](http://localhost:8080/) to see an overview page, or to [http://localhost:8080/tasks](http://localhost:8080/tasks) to retrieve the tasks.

![](https://learn-js-dev.herokuapp.com/images/js/tools/json_server.png)

**json-server** has loads of other options that you might find useful:

```text
$ json-server --help
json-server [options] 

Options:
  --config, -c               Path to config file   [default: "json-server.json"]
  --port, -p                 Set port                            [default: 3000]
  --host, -H                 Set host                     [default: "localhost"]
  --watch, -w                Watch file(s)                             [boolean]
  --routes, -r               Path to routes file
  --middlewares, -m          Paths to middleware files                   [array]
  --static, -s               Set static files directory
  --read-only, --ro          Allow only GET requests                   [boolean]
  --no-cors, --nc            Disable Cross-Origin Resource Sharing     [boolean]
  --no-gzip, --ng            Disable GZIP Content-Encoding             [boolean]
  --snapshots, -S            Set snapshots directory              [default: "."]
  --delay, -d                Add delay to responses (ms)
  --id, -i                   Set database id property (e.g. _id) [default: "id"]
  --foreignKeySuffix, --fks  Set foreign key suffix (e.g. _id as in post_id)
                                                                 [default: "Id"]
  --quiet, -q                Suppress log messages from output         [boolean]
  --help, -h                 Show help                                 [boolean]
  --version, -v              Show version number                       [boolean]

Examples:
  json-server db.json
  json-server file.js
  json-server http://example.com/db.json

https://github.com/typicode/json-server
```

That's it. You can now consume the contents of data.json using simple local requests.

