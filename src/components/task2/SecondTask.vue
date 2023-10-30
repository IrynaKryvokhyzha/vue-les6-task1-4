<template>
  <div>
    <label>
      {{ title }}
      <input v-model="currentPath" type="text" :class="pathColor" />
    </label>
  </div>
</template>

<script>
export default {
  name: "SecondTask",
  props: {
    title: {
      type: String,
      default: "",
    },
    modelValue: {
      type: String,
    },
    modelModifiers: {
      default: () => ({}),
    },
  },
  data() {
    return {
      pathColor: null,
    };
  },
  computed: {
    currentPath: {
      get() {
        return this.modelValue;
      },
      set(newVal) {
        if (this.modelModifiers.checkPath) {
          this.checkPath(newVal);
        }
        this.$emit("update:modelValue", newVal);
      },
    },
  },
  methods: {
    checkPath(val) {
      let correctPath = /\.js$/;
      if (val) {
        if (!correctPath.test(val)) {
          this.pathColor = "incorrect";
        } else this.pathColor = null;
      } else this.pathColor = null;
    },
  },
};
</script>

<style lang="scss" scoped></style>
