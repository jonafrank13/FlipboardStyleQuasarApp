<template>
  <div v-if="index === 0" class="first-card"></div>
  <div v-else-if="index === (noOfArticles - 1)" class="last-card"></div>
  <section v-else class="container section" :class="{ hide: index > 1 }">
    <div id="card" v-touch-swipe.vertical="foldSection">
      <figure class="front"><img :src="article.thumbnail" :alt="article.title" width="100%" height="100%"></figure>
      <figure class="back">{{article.title}}</figure>
    </div>
  </section>
</template>
<script>
export default {
  data () {
    return {
      id: 1
    }
  },
  props: ['index', 'article', 'noOfArticles'],
  methods: {
    foldSection (eventObject) {
      eventObject.evt.target.parentElement.parentElement.classList.toggle('flipped')

      let sibling = eventObject.evt.target.parentElement.parentElement.parentElement.nextElementSibling

      if (eventObject.direction === 'up' && sibling) {
        sibling.style.visibility = 'visible'
      }
      else if (eventObject.direction === 'down' && sibling) {
        sibling.style.zIndex = -1
        setTimeout(() => {
          sibling.style.visibility = 'hidden'
          sibling.style.zIndex = null
        }, 800)
      }
    }
  }
}

</script>
<style scoped>
.container {
  width: 100%;
  height: 50%;
  position: relative;
  perspective: 800px;
}

#card {
  width: 100%;
  height: 100%;
  position: absolute;
  transform-style: preserve-3d;
  transition: transform 1s;
  transform-origin: top;
  background: #666666;
}

.section {
  position: absolute;
  top: 50%;
}

#card figure {
  margin: 0;
  display: block;
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}

#card .front {
  /*background: red;*/
}

#card .back {
  /*background: blue;*/
  transform: rotateY(180deg) rotateZ(180deg);
}

.flipped {
  transform: rotateX(180deg);
}

.hide {
  visibility: hidden;
}

.first-card {
  width: 100%;
  height: 50%;
  position: absolute;
}

.last-card {
  top: 50%;
  visibility: hidden;
}
</style>
