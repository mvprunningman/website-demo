<template>
  <div>
    <div
      v-for="index in maxValue"
      :key="index"
      class="iconfont icon-star star-item star-placeholder"
    >
      <div
        class="iconfont icon-star star-item star-active"
        :style="{ width: getWidth(index), color: activeColor }"
      />
    </div>
    <!-- <span class="star-value">
      {{ starValue }}
    </span> -->
  </div>
</template>

<script>
import "./icon-star.css";

export default {
  props: {
    maxValue: {
      type: Number,
      default: 5,
    },
    value: {
      type: Number,
      default: 4.5,
    },
    activeColor: {
      type: String,
      default: "#ff7e28",
    },
  },
  computed: {
    starValue() {
      return this.value.toFixed(1);
    },
  },
  methods: {
    getWidth(index) {
      const gap = this.value - index + 1;
      if (gap >= 1) {
        return "100%";
      } else if (gap <= 0) {
        return 0;
      } else {
        return gap * 100 + "%";
      }
    },
  },
};
</script>

<style scoped>
.star-item {
  display: inline-block;
  font-size: 16px;
}

.star-placeholder {
  position: relative;
  color: #e9e9e9;
}
.star-active {
  position: absolute;
  top: 0;
  left: 0;
  overflow: hidden;
}
.star-value {
  font-size: 40px;
  margin-left: 10px;
}
</style>
