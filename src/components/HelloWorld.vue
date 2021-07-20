<template>
  <Form @submit="register($event)">
    <Field name="name" rules="required" v-slot="{ field, meta }" v-model="user.name">
      <label for="name-input" :class="{ 'text-danger': meta.dirty && !meta.valid }">Name</label>
      <input id="name-input" :class="{ 'is-invalid': meta.dirty && !meta.valid }" v-bind="field" />
      <ErrorMessage name="name" class="error" />
    </Field>
  </Form>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import { ErrorMessage, Field, Form } from 'vee-validate';

import { configure, defineRule } from 'vee-validate';
import { required } from '@vee-validate/rules';

defineRule('required', required);
configure({
  validateOnInput: true
});

export default defineComponent({
  name: 'HelloWorld',
  components: {
    ErrorMessage,
    Field,
    Form
  },
  setup() {
    const user = reactive({ name: 'JB', password: null, confirmPassword: null });

    function register(values: any) {
      console.log(values);
    }

    return { user, register };
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.text-danger {
  color: red;
}
.is-invalid {
  border: red 1px solid;
}
</style>
