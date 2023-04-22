<template>
  <div>
    
    <h1>Strona domowa</h1>
    <bigImage image="https://hubertkajdan.com/wp-content/uploads/2019/06/2019-06-20-Jezioro-Lednickie-010-Pano-1024x663.jpg"/>
  </div>
</template>

<script>
import TopNav from '../components/nav/TopNav.vue'
import bigImage from '../components/gallery/bigImage.vue'
export default {
  name: 'IndexPage',
  components: {TopNav, bigImage}
}
</script>
