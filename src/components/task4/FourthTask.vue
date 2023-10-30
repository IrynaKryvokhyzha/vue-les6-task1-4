<template>
  <div>
    <label>
      Введіть Ваш вік:
      <input v-model="ageValue" :class="inpColor" type="number" />
    </label>
    <label>
      Введіть Ваше ім'я:
      <input v-model="nameValue" :class="nameInpColor" type="text" />
    </label>
  </div>
</template>

<script>
export default {
  name: "FourthTask",
  props: {
    age: {
      type: Number,
    },
    ageModifiers: {
      default: () => ({}),
    },
    name: {
      type: String,
    },
    nameModifiers: {
      default: () => ({}),
    },
  },
  data() {
    return {
      ageInpColor: null,
      nameInpColor: "incorrect",
    };
  },
  computed: {
    ageValue: {
      get() {
        return this.age;
      },
      set(newVal) {
        if (this.ageModifiers.checkAge) {
          if (newVal) {
            if (newVal < 18) this.inpColor = "incorrect";
            else this.inpColor = "correct";
          } else this.inpColor = null;
        }
        this.$emit("update:age", newVal);
      },
    },
    nameValue: {
      get() {
        return this.name;
      },
      set(newVal) {
        if (this.nameModifiers.checkInput) {
          if (newVal) this.nameInpColor = null;
        } else this.nameInpColor = null;
        this.$emit("update:name", newVal);
      },
    },
  },
};
</script>

<style lang="scss" scoped></style>
