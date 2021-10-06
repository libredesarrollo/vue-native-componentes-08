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
        borderRadius: 5,
        backgroundColor: color,
        padding: 10,
      }"
    >
      <text-input
        class="input"
        :onFocus="() => focus()"
        :onChangeText="textChange"
      />
    </animated:view>
  </view>
</template>

<script>
import { Animated, Easing } from "react-native";

export default {
  data() {
    return {
      color: 0,
      colorInter: 0,
    };
  },
  created() {
    this.colorInter = new Animated.Value(0);
    this.color = this.colorInter.interpolate({
      inputRange: [0, 1],
      outputRange: ["rgb(0,0,0)", "rgb(255,0,0)"],
    });
  },
  methods: {
    focus: function () {
      this.colorAnimacion();
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
    textChange: function(val){
      this.$emit("change",val)
    }
  },
};
</script>

<style scoped>
.input {
  width: 100%;
  height: 40px;
  padding: 5px;
  background-color: white;
}
</style>

