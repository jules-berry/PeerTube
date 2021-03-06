# Welcome to the contributing guide for PeerTube

Interesting in contributing? Awesome!

**Quick Links:**

  * [Give your feedback](#give-your-feedback)
  * [Write documentation](#write-documentation)
  * [Develop](#develop)


## Give your feedback

You don't need to know how to code to start contributing to PeerTube! Other
contributions are very valuable too, among which: you can test the software and
report bugs, you can give feedback on potential bugs, features that you are
interested in, user interface, design, decentralized architecture...


## Write documentation

You can help to write the documentation of the REST API, code, architecture,
demonstrations...

## Develop

Don't hesitate to talk about features you want to develop by creating an issue
before you start working on them :).

### Prerequisites

First, make sure that you have followed 
[the steps](/support/doc/dependencies.md) 
to install the dependencies.

Then clone the sources and install node modules:

```
$ git clone -b master https://github.com/Chocobozzz/PeerTube
$ cd PeerTube
$ yarn install --pure-lockfile
```

Then, create a postgres database and user with the values set in the
`config/default.yaml` file. For instance, if you do not change the values
there, the following commands would create a new database called `peertube_dev`
and a postgres user called `peertube` with password `peertube`:

```
# sudo -u postgres createuser -P peertube
Enter password for new role: peertube
# sudo -u postgres createdb -O peertube peertube_dev
```

In dev mode, administrator username is **root** and password is **test**.

### Server side

You can find a documentation of the server code/architecture [here](/support/doc/development/server/code.md).

To develop on the server-side:

```
$ npm run dev:server
```

Then, the server will listen on `localhost:9000`. When server source files
change, these are automatically recompiled and the server will automatically
restart. Server is in `TEST` mode so it will run requests between instances more quickly.

### Client side

You can find a documentation of the server code/architecture
[here](/support/doc/development/client/code.md).


To develop on the client side:

```
$ npm run dev:client
```

The API will listen on `localhost:9000` and the frontend on `localhost:3000`.
Client files are automatically compiled on change, and the web browser will
reload them automatically thanks to hot module replacement.

### Test federation

This will run 3 nodes:

```
$ npm run clean:server:test
$ npm run play
```

Then you will get access to the three nodes at `http://localhost:900{1,2,3}`
with the `root` as username and `test{1,2,3}` for the password.
