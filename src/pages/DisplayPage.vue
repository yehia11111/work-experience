<template>
  <q-page class="flex flex-center q-pa-md">
    <div class="column items-center q-gutter-md">
      <q-btn label="Back" @click="goBack" />
      <iframe v-if="url" :src="url" class="iframe-width" frameborder="0"></iframe>
      <div v-else>No URL provided</div>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();
const url = ref(localStorage.getItem('submittedUrl') || '');

const goBack = () => {
  // Navigate back to the previous page
  router.go(-1);
};
</script>

<style>
.iframe-width {
  width: 1200px;
  height: 90vh;
}
</style>

  