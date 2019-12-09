<template lang="pug">
.slidewide__wrap
  ul.slidewide
    li.shadow.slidewide__list(v-for="skill in skills" :key="skill.id")
      figure.slidewide__img
        img(:src="skill.img" :alt="skill.title")
      div
        h3.slidewide__title {{skill.title}}
        //- p(:class!="$style.slidewide__text") {{skill.despriction}}
        p.slidewide__text {{skill.despriction}}
        button.modal.button.button__secondary(:style="{ width: '70%' }" @click="openModal(skill)") Read More
  modal(:val="postItem",v-if="showModal",@close="showModal = false")

</template>

<script>
import ico_right from '@/assets/images/svg/ico_right.svg'
import Button from '~/components/organisms/button/index.vue'
import Modal from '~/components/organisms/modal/index.vue'

export default {
  name: 'SlideWide',

  // props: ["id", "title", "text"]
  props: {
    skills: {
      type: Array
    },
    type: {
      type: String,
      default: ''
    },
    width: {
      type: String,
      default: ''
    }
  },

  components: {
    Button,
    Modal,
    ico_right
  },

  data() {
    return {
      showModal: false,
      postItem: ''
    }
  },

  openModal(skill) {
    this.postItem = skill
    this.showModal = true
  },

  methods: {
    openModal(skill) {
      this.postItem = skill
      this.showModal = true
    },
    closeModal() {
      this.showModal = false
    }
  }
}
</script>

<style lang="scss" scope>
.slidewide {
  margin: auto;
  padding: 2.4rem 3.2rem;
  display: flex;
  overflow-x: auto;
  overflow-y: hidden;
  white-space: nowrap;
  margin-bottom: 32px;

  &__wrap {
    overflow-y: hidden;
    -webkit-overflow-scrolling: touch;
  }

  figure {
    width: 100%;
    height: 280px;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      /* transition: transform 0.1s linear;
      &:hover {
        transform: scale(1.1);
      } */
    }
  }

  &__list {
    text-align: center;
    margin-bottom: 40px;
    margin-right: 1.6rem;
    background: $white;
    @include radius;
    overflow: hidden;
    padding: 1.2em 2em;
    width: 100%;
    min-width: 300px;
  }

  &__title {
    font-size: 2rem;
    font-family: $fontFamilyEng200;
    font-weight: 400;
    text-align: center;
  }

  &__text {
    @include justify;
    margin: 0 auto 19px;
    display: block;
    text-align: center;
  }
}

@include md {
  .slidewide {
    figure {
      height: 200px;
    }

    &__list {
      min-width: auto;
      margin-bottom: 0;
    }

    &__title {
      font-size: 4rem;
    }

    &__text {
      margin: 0 0 32px;
    }
  }
}
</style>

<style lang="scss">
.is-modal {
  overflow-y: hidden;
}
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

  svg {
    width: 2.4rem;
    height: 2.4rem;
    fill: currentColor;
    position: absolute;
    right: 0;
    top: 50%;
    transform: translateY(-50%);
  }

  @include md {
    &__primary {
      max-width: 420px;
      min-width: 120px;
      width: 100%;
    }
  }
}
</style>
