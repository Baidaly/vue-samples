<template>
  <div class="row">
    <div class="col">
      <label>First Name</label>
      <input type="text" class="form-control" :value="firstName" @input="valueChanged(true, $event)">
    </div>

    <div class="col">
      <label>Last Name</label>
      <input type="text" class="form-control" :value="lastName" @input="valueChanged(false, $event)">
    </div>
  </div>
</template>

<script>
  export default {
    name: "FullName",
    props: {
      value: {
        type: String
      }
    },
    computed: {
      firstName() {
        return this.value.split(' ')[0];
      },
      lastName() {
        return this.value.split(' ')[1];
      }
    },
    methods: {
      valueChanged(isFirst, {target: { value }}) {
        this.$emit('input', isFirst ? `${value} ${this.lastName}` : `${this.firstName} ${value}`);
      }
    }
  }
</script>

<style>

</style>