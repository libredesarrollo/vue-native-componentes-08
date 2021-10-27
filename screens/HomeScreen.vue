<template>
    <view :style="{minHeight:'100%', justifyContent:'center'}">
        <!-- <bubbles color="#F0A" /> -->
        <!-- <input-text1 @change="change" />
        <input-text1 @change="change"/>
        <input-text2 @change="change" /> -->

        <Expanded/>

    </view>
</template>

<script>
import Expanded from '../components/ExpandedComponent.vue'
import ButtonFlat from '../components/ButtonFlatComponent.vue'
import ButtonModern from '../components/ButtonModernComponent.vue'
import InputText1 from '../components/InputText1Component.vue'
import InputText2 from '../components/InputText2Component.vue'
import Bubbles from '../components/BubblesComponent.vue'
export default {
  components: { Bubbles, InputText1,InputText2, ButtonModern, ButtonFlat, Expanded },
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