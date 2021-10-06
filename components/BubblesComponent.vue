<template>
    <view>
        <bubble @select="select('granjero')" :positionFixedX="250" color="#8ac8f0" :durationY="8000" :img="require('../assets/img/granjero.png')" />
        <bubble @select="select('papa')" :positionFixedX="350" color="#aad963" :img="require('../assets/img/papa.png')" :durationY="3000" />
        <bubble @select="select('granjero')" :positionFixedX="80" :moveSide="10" :durationY="16000"  color="#8ac8f0" :img="require('../assets/img/granjero.png')"  />
        <bubble :positionFixedX="120" color="#ffcd53" :durationX="300" />
        <bubble @select="select('papa 2')" :sizeBubble="40" :positionFixedX="320" :durationY="5000"  color="#aad963"  :img="require('../assets/img/papa.png')"/>
        <bubble :positionFixedX="160" :durationY="6000" color="#ffcd53" :durationX="500" />
        <bubble @select="select('papa 3')" :positionFixedX="450" color="#aad963" :durationY="11000" :img="require('../assets/img/papa.png')"/>
        <bubble color="#0FF" :durationY="12000" />
    </view>
</template>
<script>
import Bubble from './BubbleComponent.vue'
export default {
  components: { Bubble },
    methods: {
      select: function(name){
        alert(name)
      }
    },
}
</script>