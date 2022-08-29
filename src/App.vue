<template>
  <div id="app">
    <Layout>
      <Button @click="showModal">
        Show Modal
      </Button>
      <br><br>
      <Button
        variant="outline"
        @click="showAlert"
      >
        Show Alert
      </Button>

      <portal
        to="modal-layer"
        v-if="modalShown"
      >
        <MyModal @close="closeModal" />
      </portal>
      <portal
        to="alert-layer"
        v-if="alertShown"
      >
        <Alert
          title="Alert Example"
          @close="closeModal"
        >
          This is a sample alert to show that they can mount on their own.
          <template #actions>
            <Button
              fullwidth
              @click="closeAlert"
            >
              Close
            </Button>
          </template>
        </Alert>
      </portal>
    </Layout>
  </div>
</template>

<script lang="ts">
import Layout from './components/Layout.vue';
import Button from './components/Button.vue';
import MyModal from './components/MyModal.vue';
import Alert from './components/Alert.vue';
import { Portal } from 'portal-vue';

export default {
  components: {
    Layout,
    Button,
    MyModal,
    Alert,
    Portal
  },
  data() {
    return {
      modalShown: false,
      alertShown: false
    }
  },
  methods: {
    showModal() {
      this.modalShown = true
    },
    closeModal() {
      this.modalShown = false
    },
    showAlert() {
      this.alertShown = true
    },
    closeAlert() {
      this.alertShown = false
    },
    closeAll() {
      this.closeModal();
      this.closeAlert();
    }
  }
}
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
}

h1,h2,h3,h4,h5 {
  margin: 0;
}
</style>