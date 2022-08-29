<template>
  <Modal
    title="Modal Title"
    @close="showAlert"
  >
    <div class="my-modal">
      I'm a modal.
    </div>
    <portal
      to="modal-component-layer"
      v-if="alertShown"
    >
      <Alert
        title="Hold on"
        mode="confirmation"
      >
        Are you sure you want to close this modal?
        <template #actions>
          <Button
            fullwidth
            @click="closeModal"
          >
            Yes
          </Button>
          <Button
            variant="outline"
            fullwidth
            @click="closeAlert"
          >
            No
          </Button>
        </template>
      </Alert>
    </portal>
    <template #actions>
      <Button
        variant="outline"
        @click="showAlert"
      >
        Cancel
      </Button>
      <Button
        @click="closeModal"
      >
        Save
      </Button>
    </template>
  </Modal>
</template>

<script lang="ts">
import Button from './Button.vue';
import Modal from './Modal.vue';
import Alert from './Alert.vue';
import { Portal } from 'portal-vue';

export default {
  components: {
    Button,
    Modal,
    Alert,
    Portal
  },
  data() {
    return {
      alertShown: false,
    }
  },
  methods: {
    showAlert() {
      this.alertShown = true;
    },
    closeAlert() {
      this.alertShown = false;
    },
    closeModal() {
      this.$emit('close');
    }
  }
}
</script>

<style scoped>
.my-modal {
  height: 250px;
}
</style>