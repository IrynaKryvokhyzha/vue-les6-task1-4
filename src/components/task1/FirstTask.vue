<template>
  <div>
    <label>
      {{ title }}
      <input type="number" :class="ageColor" v-model="currentAge" />
    </label>
    <div class="error-message">{{ message }}</div>
  </div>
</template>

<script>
export default {
  name: "FirstTask",
  props: {
    title: {
      type: String,
      default: "",
    },
    modelValue: {
      type: Number,
    },
    ageVal: {
      type: String,
    },
    ageValModifiers: {
      default: () => ({}),
    },
  },
  data() {
    return {
      message: null,
      ageColor: null,
    };
  },
  computed: {
    currentAge: {
      get() {
        return this.ageVal;
      },
      set(newVal) {
        if (this.ageValModifiers.check) {
          this.checkVal(newVal);
        }
        if (this.ageValModifiers.setColor) {
          this.setColorVal(newVal);
        }
        this.$emit("update:ageVal", newVal);
      },
    },
  },
  methods: {
    checkVal(val) {
      if (val > 150) {
        this.message = "Вік не може бути більшим за 150";
        val = null;
      } else this.message = null;
    },
    setColorVal(val) {
      if (val) {
        if (val < 10) {
          this.ageColor = "child";
        } else if (val > 10 && val < 21) {
          this.ageColor = "youth";
        } else if (val > 21) {
          this.ageColor = "adult";
        }
      } else this.ageColor = null;
    },
  },
};
</script>

<style lang="scss" scoped>
.child {
  background-color: green;
}
.youth {
  background-color: yellow;
}
.adult {
  background-color: orange;
}
</style>
