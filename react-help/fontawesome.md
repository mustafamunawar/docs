# Font Awesome Icons in React

- For FA version-6

- The `@fortawesome/fontawesome-svg-core` package provides the functionality but not any of the icon content.

- `npm install @fortawesome/fontawesome-svg-core`

- The free icons are in following three libraries:

```bsh
npm install @fortawesome/free-solid-svg-icons
npm i --save @fortawesome/free-regular-svg-icons
npm i --save @fortawesome/free-brands-svg-icons
```

- or install all in one go:

- npm install @fortawesome/react-fontawesome @fortawesome/fontawesome-svg-core @fortawesome/free-solid-svg-icons @fortawesome/free-regular-svg-icons @fortawesome/free-brands-svg-icons

## Dynamic Icon Importing

- Need to install babel-plugin-macros

  `npm install babel-plugin-macros`

- Add following babel.config.js file in project's main folder

```js
module.exports = function (api) {
  api.cache(true);
  return {
    plugins: ["macros"],
  };
};
```

- Also add following babel-plugin-macros.config.js file in project's main folder

```js
module.exports = {
  "fontawesome-svg-core": {
    license: "free", // or license: "pro" for pro (paid) version
  },
};
```

- Example of use:

```jsx
import React from "react";

import { FontAwesomeIcon } from "@fortawesome/react-fontawesome";
import {
  solid,
  regular,
  brands,
  icon,
} from "@fortawesome/fontawesome-svg-core/import.macro"; // <-- import styles to be used

export default function Home() {
  return (
    <>
      <div>Home</div>
      <FontAwesomeIcon
        // color="red"
        icon={solid("user-secret")}
        className="scale-[5] bg-red-800"
      />
      <FontAwesomeIcon icon={solid("coffee")} />
      <FontAwesomeIcon icon={icon({ name: "coffee", style: "solid" })} />
      <FontAwesomeIcon icon={brands("twitter")} />
    </>
  );
}
```

## Add Individual Icons Explicitly

```js
import ReactDOM from "react-dom";
import { FontAwesomeIcon } from "@fortawesome/react-fontawesome";
import { faEnvelope, faCoffee } from "@fortawesome/free-solid-svg-icons";

export default function Home() {
  return (
    <>
      <div>Home</div>
      <FontAwesomeIcon icon={faEnvelope} />
      <FontAwesomeIcon icon={faCoffee} />
    </>
  );
}
```
