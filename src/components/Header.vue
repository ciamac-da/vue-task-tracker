<template>
  <header>
    {{title}}
    <Button
    v-show="homePage"
    @btn-click="$emit('toggle-add-task')"
    :text="showAddTask ? 'Close' : 'Add Task'" 
    :color="showAddTask ? 'red' : 'green'"/>
  </header>
</template>
<script>
import Button from './Button.vue';

export default {
  components: { Button },
  name: "Header",
  props: {
    title: String,
    showAddTask: Boolean
    },
    computed: {
      homePage() {
        if(this.$route.path === "/") {
          return true
        } else {
          return false
        }
      }
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