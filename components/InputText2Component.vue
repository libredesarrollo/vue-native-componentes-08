<template>
  <view
    :style="{
      width: '90%',
      marginLeft: 'auto',
      marginRight: 'auto',
      marginTop: 15,
    }"
  >
    <animated:view
      :style="{
        width: width,
        borderBottomWidth:2,
        borderColor: color,
      }"
    >
      <text-input class="input" :onFocus="() => focus()" :onChangeText="textChange"/>
    </animated:view>
  </view>
</template>

<script>
import { Animated, Easing } from "react-native";
export default {
  data() {
    return {
      width: 10,
      color: 0,
      colorInter: 0,
    };
  },
  methods: {
    focus: function () {
      this.crecerAnimacion();
      this.colorAnimacion();
    },
    crecerAnimacion: function () {
      Animated.spring(this.width, {
        toValue: 300,
        easing: Easing.linear,
        useNativeDriver: false,
      }).start(() => {
        this.width = new Animated.Value(10);
      });
    },

    textChange: function(val){
      this.$emit("change",val)
    },
    colorAnimacion: function () {
      Animated.timing(this.colorInter, {
        toValue: 1,
        duration: 300,
        easing: Easing.linear,
        useNativeDriver: false,
      }).start(() => {
        //this.colorInter.setValue(0);
      });
    },
  },
  created() {
    this.width = new Animated.Value(10);

    this.colorInter = new Animated.Value(0);
    this.color = this.colorInter.interpolate({
      inputRange: [0, 1],
      outputRange: ["rgb(0,0,0)", "rgb(255,0,0)"],
    });
  },
};
</script>

<style scoped>
.input {
  width: 100%;
  height: 40px;
  padding: 5px;
}
</style>