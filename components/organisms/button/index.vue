<template lang="pug">
  //- button(:class="$style.button",@click="openModal(skill)",)
  button.button(:class="{'bg-teal': primary,'hover:bg-teal-dark': primary,'bg-red-lighter': danger,'hover:bg-red-light': danger,}" @click="$emit('click', $event)" ) {{label}}
    slot


</template>

<script>
export default {
  name: 'Button',
  props: {
    primary: {
      type: Boolean,
      default: false
    },
    danger: {
      type: Boolean,
      default: false
    },
    label: {
      type: String,
      required: true
    },
    type: {
      type: String,
      default: ''
    },
    width: {
      type: String,
      default: ''
    },
    methods: {
      click() {
        this.$emit('myclick')
      }
    }
  }
}
</script>

<style lang='scss' module>
.button {
  transition: 0.3s ease 0s;
  font-size: 1.3rem;
  position: relative;
  border-radius: 30px;
  font-weight: 700;
  letter-spacing: 0.05em;
  height: 48px;
  line-height: 0;
  border-radius: 30px;
  cursor: pointer;

  &__primary {
    color: $white;
    border: none;
    min-width: 120px;
    background: $primary;

    &:hover {
      background: darken($primary, 30%);
      color: $white;
    }
  }

  &__secondary {
    color: $primary;
    border: 1px solid $primary;

    &:hover {
      background: $primary;
      color: $white;
    }
  }
}
</style>
