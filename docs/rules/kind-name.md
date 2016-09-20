# Prevent missing name in an Enact kind component definition (kind-name)

The `name` string property allows you to name your component. This name is used
by Enact/React in debugging messages.

## Rule Details

The following patterns are considered warnings:

```js
var Hello = kind({
  render: function() {
    return <div>Hello World</div>;
  }
});
```

The following patterns are not considered warnings:

```js
var Hello = kind({
  name: 'Example',
  render: function() {
    return <div>Hello World</div>;
  }
});
```

## Rule Options

```js
...
"kind-name": [<enabled>]
...
```

## About component detection

For this rule to work, it needs to detect valid applicable components. Specifically, this
rule targets stateless Enact components created via the `kind()` factory.

Higher-order components created via the Enact `hoc()` factory are currently not being processed,
though that may change in the future.

For React components (created via `React.creatClass()`, ES6 React classes, and stateless functional
components), please use the eslint-plugin-react's display-name rule instead.
