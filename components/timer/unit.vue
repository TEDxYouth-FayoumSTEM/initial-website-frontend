<template>
  <div class="container">
    <span class="title font-bold text-primary-400">{{ title }}</span>
    <div class="digital-container">
      <span class="single-digit">
        {{ leftDigit }}
      </span>
      <span class="single-digit">
        {{ rightDigit }}
      </span>
      <span v-if="thirdDigit" class="single-digit">
        {{ thirdDigit }}
      </span>
    </div>
  </div>
</template>

<script lang="ts" setup>
const props = defineProps({
  digit: {
    type: Number,
    required: true,
  },
  title: {
    type: String,
    default: "",
  },
});

const leftDigit = computed(() =>
  props.digit >= 10 ? props.digit.toString()[0] : "0"
);
const rightDigit = computed(() =>
  props.digit >= 10 ? props.digit.toString()[1] : props.digit.toString()
);
const thirdDigit = computed(() =>
  props.digit > 99 ? props.digit.toString()[2] : null
);
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0 5px;
}
.container:first-child {
  margin-left: 0;
}
.title {
  font-size: 14px;
  margin-bottom: 5px;
}
.digital-container {
  display: flex;
  flex-direction: row;
  padding: 0;
}
.single-digit {
  position: relative;
  display: flex;
  flex: 0 1 25%;
  font-size: 32px;
  background-color: #404549;
  border-radius: 5px;
  padding: 10px 12px;
  color: white;
}
.single-digit:not(:last-child) {
  margin-right: 2px;
}
.single-digit:after {
  position: absolute;
  left: 0px;
  right: 0px;
  top: 50%;
  bottom: 50%;
  content: "";
  width: "100%";
  height: 2px;
  background-color: #232323;
  opacity: 0.4;
}
</style>
