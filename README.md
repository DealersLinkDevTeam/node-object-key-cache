# node-object-key-cache

`node-object-key-cache` is a promise-based, object-key, cache extension for the [Redis](https://www.npmjs.com/package/redis) and [memory-cache](https://www.npmjs.com/package/@mediaxpost/memory-cache) modules.

Object Key Cache provides the ability to use JavaScript Objects as keys values when committing to cache.

During connection to Redis, it defaults to fail-back to the memory cache when when connecting to Redis fails.

Object Keys that are passed into the associated "O"-functions (e.g. oget, oset, etc.) are JSON stringified and then SHA256 hashed in an attempt to preserve the uniqueness of the key. *Note:* No additional mitigation of potential collision of key spaces with SHA256 is being performed. With one billion messages there is approximately a 1 in 4.3 x 10<sup>60</sup> chance with SHA256 that two separate strings will generate an identical hash. The probability is negligible for most use cases; however, if very, very large numbers of keys are likely to be stored then consideration should be given to name-spacing or segregating data by how it will be used within the cache to avoid any potential for collisions.

# [Installation](#installation)
<a name="installation"></a>

```shell
npm install @dealerslink/node-object-key-cache
```

# [Usage](#usage)
<a name="usage"></a>

```js
const ObjectKeyCache = require('@dealerslink/node-object-key-cache');
const objKeyCache = new ObjectKeyCache();
```

See wiki for more details.
