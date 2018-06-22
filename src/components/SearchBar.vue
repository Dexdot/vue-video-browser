<template>
  <div>
    <input class="form-control" type="text" placeholder="Search..." v-model="text" @input="onInput">
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  data: () => ({
    text: ''
  }),
  methods: {
    onInput() {
      this.$emit('termChange', this.text);
    }
  }
};
</script>

<style scoped>
input {
  width: 75%;
}
div {
  text-align: center;
  margin: 24px auto;
}
</style>
