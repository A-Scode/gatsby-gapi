# gatsby-gapi-ssr

## 🛸 Intro
npm package that loads gapi script and initialize some functions.which supports server-side-rendering in gatsby.

There is a package which loads the gapi functions for us `gapi-script` , this package uses modified code of `gapi-script` make build possible in gatsby with google login. You can either call `loadGapiInsideDOM` to load the gatsby-gapi-ssr inside a `<script>` tag on your browser. Or use the static gapi value that was copied from [google api platform](https://apis.google.com/js/platform.js), pasted to this project and exported as `gapi`.

## 👨‍🔧 How to use
Add the package to your project:

```
npm install gatsby-gapi-ssr

//or

yarn add gatsby-gapi-ssr
```

You can load gapi with following approach
1 - import `gapi` where you need it:
```javascript
import { gapi } from 'gatsby-gapi-ssr';
```

2 - import `gapi`  in your react app:
```javascript 

useEffect(() => {
    function start() {
      gapi.client.init({
        clientId: "client-id",
        scope: 'email',
      });
    }

    gapi.load('client:auth2', start);
  }, []);


```
### After loading gatsby-gapi-ssr you can access as  `window.gapi` in your component

Once you have gapi you can use it in other functions to make your life easier

If you need to use `gapi auth2` the package already has a function to initialize it:

```javascript
import { loadAuth2, loadAuth2WithProps, loadClientAuth2 } from 'gatsby-gapi-ssr';

let a2 = await loadAuth2(gapi, clientId, scopes);

// or if you need to use more props from gapi you can use this method:
let a2 = await loadAuth2WithProps(gapi, { /* object with props from gapi */ });

// if you want to use the gapi client itself
let gClient = loadClientAuth2(gapi, clientId, scopes);
```

# 🎁 How to contribute

Can make pull requst with a good description about feature or bug fix.
