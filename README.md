# Portal Test

This repo demonstrates how to leverage portals to show modals, alerts and other overlay components. The intent is for every application to have a `Layout` at its root, which includes multiple portals in it after the content so that they layer on top of eachother as desired. Views then open layers by putting the right components in the right layers.

## Demo
To open a layer, you use a portal with a v-if.

```vue
<template>
  <Layout>
    <Button @click="showModal">
      Show Modal
    </Button>
    <portal
      to="modal-layer"
      v-if="modalShown"
    >
      <MyModal @close="closeModal" />
    </portal>
  </Layout>
</template>
<script>
// ...
showModal() {
  this.modalShown = true
},
closeModal() {
  this.modalShown = false
},
</script>
```

### Pros vs Provide/Inject
* Explicit and can be done with readable code
* No requirement of parent files, since portals can be in the template

### Cons vs Provide/Inject
* Manual v-if vs api
* Prone to manually error, like selecting the right portal
* Complex markup/constants
* Not possible to have nested portals

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```