<template>
  <Form @submit="register($event)">
    <Field name="login"></Field>
  </Form>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { Field, Form } from 'vee-validate';

export default defineComponent({
  name: 'App',
  components: {
    Form,
    Field
  },
  setup() {
    return {
      register(user: { login: string }) {
        console.log(user)
      }
    }
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
