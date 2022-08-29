# Portal Test

This repo demonstrates how to leverage portals to show modals, alerts and other overlay components. The intent is for every application to have a `Layout` at its root, which includes multiple portals in it after the content so that they layer on top of eachother as desired. Views then open layers by putting the right components in the right layers.

### Pros vs Provide/Inject
* Conceptually easier than provide/inject
* No requirement of parent files

### Cons vs Provide/Inject
* Lots of manual setup

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```