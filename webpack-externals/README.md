# webpack externals

When importing a matter-js plugin via webpack, it complains that Matter is not found.

Repro steps:

1. clone the repo.
2. `cd` into this directory
3. `yarn` or `npm install`
4. `npm run build`

It will try to build the following four lines of code (found in `index.js`):

```
import Matter from 'matter-js';
import MatterCollisionEvents from 'matter-collision-events';
import MatterAttractors from 'matter-attractors';

Matter.use('matter-attractors');
```

The console output is as follows:

```
> webpack-externals@1.0.0 build /Users/dxu/code/dxu/matter-test/webpack-externals
> webpack --config webpack.config.js

Hash: 43d138e26db902c7dbc8
Version: webpack 1.14.0
Time: 1191ms
        Asset    Size  Chunks             Chunk Names
    output.js  362 kB       0  [emitted]  main
output.js.map  423 kB       0  [emitted]  main
   [0] multi main 28 bytes {0} [built]
    + 4 hidden modules

WARNING in ./~/matter-js/build/matter.js
Critical dependencies:
31:479-486 This seems to be a pre-built javascript file. Though this is possible, it's not recommended. Try to require the original source to get better results.
 @ ./~/matter-js/build/matter.js 31:479-486

ERROR in ./~/matter-attractors/build/matter-attractors.js
Module not found: Error: Cannot resolve module 'Matter' in /Users/dxu/code/dxu/matter-test/webpack-externals/node_modules/matter-attractors/build
 @ ./~/matter-attractors/build/matter-attractors.js 8:27-44
 ```
