<template lang="pug">
  transition(name="dialog")
    div(:class="$style.dialog__overlay",@click="$emit('close')")
      div(:class="$style.dialog")
        div(:class="$style.dialog__block")
          p(:class!="$style.dialog__text") {{val.despriction}}
          button.dialog__close(type="button",@click="$emit('close')")
            ico_close

</template>

<script>
export default {}
</script>

<style lang='scss' scope>
.dialog {
  @include centerF;
  position: absolute;
  bottom: 10px;
  right: 10px;

  &__overlay {
    position: fixed;
    z-index: 1000;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100%;
    background: $bgOVR;
    transition: opacity 0.3s ease;
  }

  &__block {
    min-width: 680px;
    margin: 0px auto;
    padding: 20px 30px;
    background: $white;
    @include radius;
    /* box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33); */
    transition: all 0.3s ease;
    position: relative;
  }

  &__box {
    margin: 2em;
  }

  &__img {
    width: 60%;
  }

  &__title {
    font-size: 3rem;
    font-weight: 700;
    color: $primary;
    position: relative;
    margin-bottom: 3rem;
    font-family: $fontFamilyEng200;

    &::after {
      position: absolute;
      background: $primary;
      border-radius: 5px;
      content: '';
      width: 40px;
      height: 4px;
      bottom: -1rem;
      left: 0;
    }
  }

  &__text {
    text-align: center;
    @include justify();
  }

  &__close {
    position: absolute;
    top: -80px;
    right: -16px;

    svg {
      $size: 64px;
      stroke: $white;
      width: $size;
      height: $size;
    }
    &:hover {
      cursor: pointer;
    }
  }
}
@include md {
  .dialog {
    &__block {
      display: flex;
    }

    &__img {
      max-width: 200px;
    }
  }
}
</style>