<template>
  <header>
    {{title}}
    <Button text="Add Task" color="green"/>
  </header>
</template>

<script>
import Button from './Button.vue';

export default {
  components: { Button },
  name: "Header",
  props: {
    title: String
    }
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  font-weight: bolder;
}
</style>