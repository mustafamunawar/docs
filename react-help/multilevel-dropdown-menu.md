# Navbar with Multilevel Dropdown Menus (MDM)

- MDM is implemented by recursive calls of following two components:

  1. "Menus" component
  2. "Dropdown" component

  - The data for MDM is in an array of objects called menusData in a file called menus-data.js.

  - Individual objects in menusData array are called menuData objects, and have the following form:

  ```js
  {
    title: "some title",
    url: "some url",
    subMenu: {
      title: "some title",
      url: "some url",
      subMenu: {
      title: "some title",
      url: "some url",
      }
    }
  }
  ```

```

 - A higher level component (Navbar or Header) sets up a <ul> </ul>

 - inside this <ul> </ul> the menusData array is mapped to call the Menus component.

 - For each object of menusData array The Menus component returns <li>
```
