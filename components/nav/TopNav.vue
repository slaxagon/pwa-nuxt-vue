<template>
    <div class="nav">
        <div class="left-nav item2">
            <span><NuxtLink class ="text" to="/">Home</NuxtLink></span>
        </div>
        <div class="left-nav item2">
            <span><NuxtLink class = "text" to ="/onas">About</NuxtLink></span>
        </div>
        <div class="left-nav item2">
            <span><NuxtLink class = "text" to ="/nasa">NASA</NuxtLink></span>
        </div>
    </div>
</template>

<script>

</script>

<style scoped>

.nav{
    display: flex;
    /*flex-direction: column;*/
    background-color: black;
    border-bottom: 5px solid yellow;
    height: 100%;
    width: 100%;
    max-height: 70px;
    min-height: 70px;
    max-width: 100vw;
    min-width: 200px;
    flex-wrap: wrap;

}
.text{
    text-decoration: none;
    color: white;
    padding: 10px;
    font-size: 24px;

}
.left-nav {
    text-decoration: none;
    margin-right: 20px;
}
/* px,, rem, em, vh, vw, % */
.item2{
    display: flex;
    align-self: center;
    flex-direction: row;
    text-decoration: none;

}

</style>
