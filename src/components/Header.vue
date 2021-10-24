<template>
  <header>
    {{title}}
    <Button
    @btn-click="$emit('toggle-add-task')"
    :text="showAddTask ? 'Close' : 'Add Task'" 
    :color="showAddTask ? 'red' : 'green'"/>
  </header>
</template>
<script>
import Button from './Button.vue';

export default {
  // First of all importing Button component
  components: { Button },
  // Naming the current component which is Header
  name: "Header",
  // Define 2 props! 
  props: {
    //the first one is title which is a string
    title: String,
    // The second one is showAddTask which is a Boolean and we need this to switch addTasks!!!
    showAddTask: Boolean
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