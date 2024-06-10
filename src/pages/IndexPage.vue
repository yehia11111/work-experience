<template>
  <q-page class="flex flex-center q-pa-md">
    <div class="column items-center q-gutter-md">
      <q-form @submit="handleSubmit">
      <q-input
        filled
        v-model="url"
        label="Enter a web URL"
        class="input-width"
        :rules="[val => !!val || 'Field is required', val => isValidURL(val) || 'Enter a valid HTTPS URL']"
      />
      <q-btn label="Submit" type="submit" /></q-form>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue';
import { useQuasar } from 'quasar';

const url = ref('');
const $q = useQuasar();

const handleSubmit = () => {
  console.log('test')
  if (url.value && isValidURL(url.value)) {
    $q.notify({
      message: `URL submitted: ${url.value}`,
      color: 'green',
      position: 'top'
    });
  } else {
    $q.notify({
      message: 'Please enter a valid HTTPS URL',
      color: 'red',
      position: 'top'
    });
  }
};

const isValidURL = (string) => {
  const pattern = new RegExp(
    '^https:\\/\\/' 
  );
  return !!pattern.test(string);
};

defineOptions({
  name: 'IndexPage'
});
</script>

<style>
.input-width {
  width: 500px;
}
</style>



