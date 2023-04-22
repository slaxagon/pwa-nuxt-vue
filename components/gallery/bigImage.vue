<template>
    <div>
        <img :src="image" class="img" />
    </div>
</template>
<script>
export default {
  name: 'BigImage',
  props: {
    image: {
        type: String,
        default: () => 'Pusty string'
    }
  }
}
</script>
<style scoped>
.img {
    width: 100%;
}
</style>