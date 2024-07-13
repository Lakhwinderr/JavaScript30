The issue with your code is that `this` inside the `handleChange` function does not refer to the input element as you might expect. In a regular function, `this` depends on how the function is called. However, in this case, since `handleChange` is being called as a callback, `this` will not automatically refer to the input element.

To fix this, you can use an arrow function for the `handleChange` callback, which does not have its own `this` context and instead inherits `this` from its surrounding context. Alternatively, you can pass the event object to the `handleChange` function and access the value through `event.target`.

Here's how you can do it using the event object:

```javascript
<script>
  const handleChange = (event) => {
    console.log(event.target.value);
  };

  const inputs = document.querySelectorAll(".controls input");
  inputs.forEach((input) => input.addEventListener("change", handleChange));
</script>
```

In this code, `event.target` refers to the input element that triggered the event, and `event.target.value` gives you the value of that input element.

The difference lies in how the functions are defined and how `this` is handled in JavaScript.

In the first example you provided, you used an arrow function for the `handleChange` function:

```javascript
const handleChange = () => {
  console.log(this.value);
};
```

Arrow functions do not have their own `this` context; they inherit `this` from their enclosing lexical context. In this case, `this` does not refer to the input element as expected.

In the second example, you used a regular function for `handleUpdate`:

```javascript
function handleUpdate() {
  const suffix = this.dataset.sizing || '';
  document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
}
```

Regular functions have their own `this` context, and when used as event handlers, `this` correctly refers to the element that triggered the event (the input element in this case).

To make your first example work with `this`, you should use a regular function instead of an arrow function:

```javascript
<script>
  function handleChange() {
    console.log(this.value);
  }

  const inputs = document.querySelectorAll(".controls input");
  inputs.forEach((input) => input.addEventListener("change", handleChange));
</script>
```

Using a regular function ensures that `this` inside `handleChange` refers to the input element that triggered the event, allowing you to access its value correctly.