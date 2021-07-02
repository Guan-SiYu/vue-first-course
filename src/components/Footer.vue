<template>
    <footer>
        <p>Copyright &copy; Guan SiYu 2021</p>
        <router-link to="/about">关于...</router-link>
    </footer>
</template>
<script>
export default {
    name: "Footer",
};
</script>
<style scoped>
a {
    color: #333;
}
footer {
    margin-top: 30px;
    text-align: center;
}
</style>
