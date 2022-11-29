# Styled Components (SC) for React

- The basic concept of SC is to apply CSS to otherwise unstyled React component to create "styled" React components as building blocks.
- To install in a React project: `npm install --save styled-components`
- SC automatically apply vendor-prefixes to CSS rules (it uses stylis.js for this purpose)

- SC example:

```jsx
// Create a Title component that'll render an <h1> tag with some styles
const Title = styled.h1`
  font-size: 1.5em;
  text-align: center;
  color: palevioletred;
`;

// Create a Wrapper component that'll render a <section> tag with some styles
const Wrapper = styled.section`
  padding: 4em;
  background: papayawhip;
`;

// Use Title and Wrapper like any other React component – except they're styled!
render(
  <Wrapper>
    <Title>Hello World!</Title>
  </Wrapper>
);
```

- Pass dynamic values using props with the styled-component call:

```jsx
const Button = styled.button`
  /* Adapt the colors based on primary prop */
  background: ${(props) => (props.primary ? "palevioletred" : "white")};
  color: ${(props) => (props.primary ? "white" : "palevioletred")};

  font-size: 1em;
  margin: 1em;
  padding: 0.25em 1em;
  border: 2px solid palevioletred;
  border-radius: 3px;
`;

render(
  <div>
    <Button>Normal</Button>
    <Button primary>Primary</Button>
  </div>
);
```

- `${(props) => (props.primary ? "white" : "palevioletred")}` is the way of passing and using values via props

- In the above example the prop 'primary' does not have a value. In such cases it is used as boolean signal. If included then true, if not then false.

- But of course props can have values that can be used in CSS
-
- A SC1 can be extended like `` const SC2 = styled(SC1)`....`  ``
