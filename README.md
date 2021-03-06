# PuSu Engine client for JavaScript

This is a client for the PuSu Engine written in Go. PuSu Engine is a Pub-Sub engine.

More information on the server repository at [https://github.com/PuSuEngine/pusud](https://github.com/PuSuEngine/pusud).

```
bower install pusu
```

## Usage

There is an usage example in `tests/test_example.html`, but here's the short
version (for use in a browser):

```javascript
var client = new PuSu("ws://127.0.0.1:55000");
client.connect().promise.then(function () {
    client.authorize("foo").promise.then(function () {
        client.subscribe("channel.1", function(msg) {
            console.log(msg);
        });
        client.publish("channel.2", {"foo": ["bar"]})
    });
});
```



## Development

To build this, you'll want to do the following:

```bash
npm install -g gulp
npm install
gulp
```

You'll get `dist/pusu.js` as the end result.

## Working with lockdown

The project is using [npm-lockdown](https://github.com/mozilla/npm-lockdown) to try and avoid some issues with NPM.

Basically if you update/add dependencies you should
run `npm run relock` and
commit changes to `package.json` + `lockdown.json`.

 
# Publishing new versions

(This doesn't happen often so it's easy to forget)

1. Update new version number in package.json
2. Commit a new tag pointing to the correct revision 


## License

Short version: MIT + New BSD.

Long version: Read the LICENSE.md -file.

Includes `typescript-deferred` from [https://github.com/DirtyHairy/typescript-deferred](https://github.com/DirtyHairy/typescript-deferred) which uses the MIT license.
