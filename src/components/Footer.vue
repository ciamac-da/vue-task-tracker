<template>
    <footer>
        <p 
        v-show="year"
        >
        Copyright &copy; 2021 
        <!--{{time}}-->
        </p>
        <router-link to="/about">About</router-link>
    </footer>
</template>

<script>
export default {
    name: "Footer",
    data: () => ({
            year: ""
    }),
    methods: {
        printYear: function () {
            return new Date().getFullYear();
        }
    },
    mounted: function () {
        this.year = this.printYear()
    }
}
</script>

<style scoped>
 a {
     color: #333
 }
 footer {
     margin-top: 30px;
     text-align: center;
 }
</style>