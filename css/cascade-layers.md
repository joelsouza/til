# Cascade Layers

Managing cascade conflicts and selector specificity has often been considered one of the harder — or at least more confusing — aspects of CSS.

It allows to create  "specificity based layers" and help organize css architecture without appealing to selectors specificity or `!important` rule;

```css
// Component styles from third-party
// component-lib.css
.table-bordered {
  border: 1px solid;
}
// Website styles
// main.css
.table-bordered {
  border: 2px solid red !important;
}
```

To prevent that, cascade layers provide control

```css
// component-lib.css
@layer components {
  .table-bordered {
    border: 1px solid;
  }
}

// main.css

// Here we specify layers by order of importance/specification.
@layer defaults, components, website;

@layer defaults {
  .table {
    border: none;
  }
}

@layer website {
  .table-bordered {
    border: 2px solid red !important;
  }
}
```
