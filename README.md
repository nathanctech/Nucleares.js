# Nucleares.js
API Wrapper for the Nucleares game.

## Usage

The API supports all [currently published](https://nuclearesgame.blogspot.com/2023/11/webserver.html) variables for the Nucleares API.

Example:

```js

const { Sensors, NuclearesAPI } = require("./nucleares.js");

const api = new NuclearesAPI();

(async () => {
    const core_temp = await api.getData(Sensors.CORE_TEMP);
    console.log(core_temp.value);
})();
```

Returns object:

```js
{
    value, // the actual value
    value_str // some variables resolve to a particular status, such as pump statuses
}
```

The `Sensors` enum contains all currently valid calls. You may pass an arbitrary string to `getData` if required.