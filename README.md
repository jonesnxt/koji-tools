# koji-tools
*A simple library for adding koji-specific features to a node project.*
## Usage
1. `npm install --save koji-tools` of course!
2. Add a watcher to your development setup
    In your `package.json` file, add a prestart script to your scripts section.
```
"scripts": {
    ...
    "prestart": "koji-tools watch &",
    ...
}
```

3. Add a `Koji.pageLoad()`, function to your app's main js file.
**App.js**
```
import Koji from 'koji-tools';
...
Koji.pageLoad();
...
```
4. Use `koji-tools` in your application to get Koji Customization options and other features:
```
import Koji from 'koji-tools';
// If I had a 'backgroundColor' property in a 'colors' customization file. 
console.log(Koji.config.colors.backgroundColor);
// If I had a route TestRoute
Koji.request(Koji.routes.TestRoute).then((response) => {
    console.log(response);
})

```

## API

- `Koji.watch()`
    Server Side function that sets file watchers on all .koji customization files and allows for hot reloading of these properties.

- `Koji.pageLoad()`
    Sets up `Koji.config` parameters for each client and handles communication between the Koji live preview iframe and your app.

- `Koji.request()`
    Wrapper for fetch that takes objects from `Koji.routes`.
- `Koji.config`
    An autogenerated list of all of the Koji Customization Controls (CVV's) your application has setup. when `Koji.watch()` is being used this list updates automatically.

- `Koji.routes`
    A autogenerated list of routes based on koji.json files in your project that are used in `Koji.request()` to request the backend of you app.

Get Started at [GoKoji.com](https://gokoji.com)