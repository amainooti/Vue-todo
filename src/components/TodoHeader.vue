<script>

import { RouterLink } from "vue-router";
export default {
    setup () {


        return {}
    }
}
</script>


<template>
    <header>
        <nav class="container">
            <div class="branding">
                <RouterLink to="/"> LOGO </RouterLink>
            </div>
            <ul class="nav-routes">
                <RouterLink to="/"> Home </RouterLink>
                <RouterLink to="/about"> About </RouterLink>
            </ul>
        </nav>
    </header>
</template>


<style lang="scss" scoped>


a,
a:visited,
a:active{
    text-decoration: none;
    color: black;

}

li {
    list-style: none;
}
.container {
    height: 12vh;
    width: 100%;
    background: #eee;
    padding: 10px 0;
    display: flex;
    align-items: center;
    justify-content: space-around;
    .branding{


    }

    .nav-routes {
        display: flex;
        justify-content: space-around;
        gap: 1rem;

    }
    .nav-routes, .branding > * {
        text-transform: uppercase;
    }
}
</style>