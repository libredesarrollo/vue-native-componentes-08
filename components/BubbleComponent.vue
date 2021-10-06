<template>
  <animated:view
    :style="{
      marginLeft: positionFixedX,
      width: sizeBubble,
      height: sizeBubble,
      backgroundColor: color,
      opacity:animation.toOpacity,
      transform: [
        { translateX: animation.toSide },
        { translateY: animation.toTop },
      ],
    }"
    class="bubble"
  >
    <touchable-opacity :on-press="() => $emit('select')">
      <image class="img" :source="img" />
    </touchable-opacity>
  </animated:view>
</template>


<script>
import { Animated, Easing, Dimensions } from "react-native";

export default {
  props: {
    img: {
      default: require("../assets/img/granjera.png")
    },
    width: {
      type: Number,
      default: -150,
    },
    height: {
      type: Number,
      default: Dimensions.get("window").height,
    },
    durationY: {
      type: Number,
      default: 5000,
    },
    durationX: {
      type: Number,
      default: 800,
    },
    moveSide: {
      type: Number,
      default: 10,
    },
    positionFixedX: {
      type: Number,
      default: 50,
    },
    sizeBubble: {
      type: Number,
      default: 70,
    },
    color: {
      default: "#ffcd53",
    },
  },
  data() {
    return {
      animation: {
        toTop: 0,
        toSide: 0,
        toTopInter: 0,
        toOpacity: 0
      },
      toSidePivote: 1,
    };
  },
  created() {
    //this.toTop = new Animated.Value(90)
    this.animation.toSide = new Animated.Value(100);
    this.animation.toOpacity = new Animated.Value(1);

    this.animation.toTopInter = new Animated.Value(90);
    this.animation.toTop = this.animation.toTopInter.interpolate({
      inputRange: [10, 90],
      outputRange: [this.width, this.height],
    });

    this.animateToTopUp();
    this.animateToSide();
    this.animateOpacity();
  },
  methods: {
    animateToTopUp() {
      Animated.timing(this.animation.toTopInter, {
        toValue: 10,
        duration: this.durationY,
        easing: Easing.linear,
        useNativeDriver: true,
      }).start(() => {
        this.animation.toTopInter.setValue(90);
        this.animateToTopUp();
      });
    },
    animateToSide() {
      Animated.timing(this.animation.toSide, {
        toValue: this.moveSide * this.toSidePivote,
        duration: this.durationX,
        easing: Easing.linear,
        useNativeDriver: true,
      }).start(() => {
        this.animation.toSide.setValue(this.moveSide * this.toSidePivote);
        this.toSidePivote *= -1;
        this.animateToSide();
      });
    },
    animateOpacity() {
      Animated.timing(this.animation.toOpacity, {
        toValue: 0,
        duration: 1500,
        easing: Easing.linear,
        delay: this.durationY - 1500,
        useNativeDriver: true,
      }).start(() => {
        this.animation.toOpacity.setValue(1);
        this.animateOpacity();
      });
    },
  },
};
</script>

<style scoped>
.bubble {
  position: absolute;
  border-radius: 500px;
  padding: 5px;
}
.img {
  width: 100%;
  height: 100%;
}
</style>