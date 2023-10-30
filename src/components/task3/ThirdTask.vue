<template>
  <div>
    <label>
      {{ title }}
      <input v-model="emailValue" type="email" :class="inpColor" />
    </label>
  </div>
</template>

<script>
export default {
  name: "ThirdTask",
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
      inpColor: null,
      emailPart: null,
    };
  },
  computed: {
    emailValue: {
      get() {
        return this.modelValue;
      },
      set(newVal) {
        if (this.modelModifiers.check) {
          this.setColor(newVal);
          const val = /^[A-Za-z0-9._%+-]+@edu$/;
          const fullEmail = this.emailValue + "@inv.mn.edu";
          this.emailPart = val.test(fullEmail);
        }
        this.$emit("update:modelValue", newVal);
      },
    },
  },
  methods: {
    setColor(val) {
      let currentVal = "@inv.mn.edu";
      if (val) {
        if (val !== val + currentVal) {
          this.inpColor = "incorrect";
        } else this.inpColor = null;
      } else this.inpColor = null;
    },
  },
};

// Треба доробити!!!
</script>

<style lang="scss" scoped></style>
