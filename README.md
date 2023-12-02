# Nucleares.js
API Wrapper for the Nucleares game.

## Requirements

- Modern Node.js version supporting native fetch (tested on v19.1.0)
- Nucleares Web Server running, tested on v0.2.11.106

## Usage

The API supports all [currently published](https://nuclearesgame.blogspot.com/2023/11/webserver.html) variables for the Nucleares API.

If unspecified, connects to the default listener for the game on `localhost`, port `8080`.

Example:

```js

const { Sensors, NuclearesAPI } = require("./nucleares.js");

const api = new NuclearesAPI("localhost", 8080); // optional parameters

(async () => {
    const core_temp = await api.getData(Sensors.CORE_TEMP);
    console.log(core_temp.value);
})();
```

Returns object:

```js
{
    value, // the actual value
    value_str, // some variables resolve to a particular status, such as pump statuses
    errors // returns error object if some problem was encountered (such as game not running), null on success.
}
```

The `Sensors` enum contains all currently valid calls. You may pass an arbitrary string to `getData` if required.