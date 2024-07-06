<template>
    <!--Button takes onclick event which is defined in methods-->
    <!--style attribute -->
    <button 
    @click="onClick()"
    :style="{ background : color}"
     class="btn">
      {{ text }}  
    </button>
</template>

<script>
export default {
    // Exporting the component that called Button
    name: "Button",
    // Need 2 Props
    props: {
        // The first one text which is a string, required for changing the text depending on showAddTasks section
        text: String,
        // The second one is the color which is also a string which is also required for changing the color depending on shwAddTask section!
        color: String
    },
    // Events
    methods: {
        // onClick event on button!
        onClick() {
            this.$emit("btn-click")
        }
    }
}
</script>
