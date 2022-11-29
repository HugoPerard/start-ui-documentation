# Generate custom icons components from svg files

Put the custom svg files into the `src/components/Icons/svg-sources` folder and then run the following command:

```bash
yarn theme:generate-icons
```

> ⚠️ All svg icons should be svg files prefixed by `icon-` (example: `icon-externel-link`) with **24x24px** size, only **one shape** and **filled with `#000` color** (will be replaced by `currentColor`).
