<template>
    <view>
        <!-- <bubbles color="#F0A" /> -->
        <input-text1 @change="change" />
        <input-text1 @change="change"/>
        <input-text2 @change="change" />
    </view>
</template>

<script>
import InputText1 from '../components/InputText1Component.vue'
import InputText2 from '../components/InputText2Component.vue'
import Bubbles from '../components/BubblesComponent.vue'
export default {
  components: { Bubbles, InputText1,InputText2 },
    props: {
        navigation: {
            Object
        }
    },
    methods: {
        change:function(text){
            console.log(text)
        }
    },
}
</script>