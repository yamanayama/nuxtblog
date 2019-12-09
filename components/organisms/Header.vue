<template lang="pug">
  header#header
    //- #js-menu-bg(@click="menuBg" :class="[$style.menu__bg, {active:modal_bk}]" v-show="modal_bk")
    #js-menu-bg(@click="menuBg" :class="{active:modal_bk}" v-show="modal_bk")
    nuxt-link.header__title(to="/")
      ico_logo
      button.nav__menu#js-open-menu(type="button" @click="menuToggle")
        span.nav__line(v-for="bar of 3" :key="bar")

    .nav.shadow
      .nav__block
        ul.nav__list
          li.nav__item(v-for="menuList of limitCount" :key="menuList.name")
            nuxt-link.nav__item__link(:to="menuList.url") {{ menuList.name }}
        p.nav__sns
          a(href="https://twitter.com/yamanayama" target="_blank")
            ico_twitter

    .nav__sp(:class="{active:headerMenu_active}" v-show="headerMenu_active")
      transition
        .nav__block
          ul.nav__list
            li.nav__item(v-for="menuList of limitCount" :key="menuList.name")
              nuxt-link.nav__item__link(:to="menuList.url") {{ menuList.name }}
          p.nav__sns
            a(href="https://twitter.com/yamanayama" target="_blank")
              ico_twitter

</template>

<script>
import ico_twitter from '@/assets/images/svg/ico_twitter.svg'
import ico_logo from '@/assets/images/svg/logo.svg'

export default {
  components: {
    ico_twitter,
    ico_logo
  },

  data() {
    return {
      headerMenu_active: false,
      modal_bk: false,

      menuList: [
        { url: '/', name: 'home' },
        { url: 'about', name: 'about' },
        { url: 'work', name: 'work' },
        { url: 'blog', name: 'blog' }
      ]
    }
  },
  methods: {
    menuToggle: function() {
      if (this.headerMenu_active == true) {
        this.modal_bk = false
        this.headerMenu_active = false
        return
      }
      this.modal_bk = true
      this.headerMenu_active = true
    },

    menuBg: function() {
      this.modal_bk = false
      this.headerMenu_active = false
    }
  },
  computed: {
    limitCount() {
      return this.menuList.slice(0, 4)
    }
  }
}
</script>

<style lang="scss" scope>
.menu {
  list-style: none;
  padding: 0;
  background-color: #eee;
  font-family: $fontFamilyEng200;

  li {
    display: inline-block;
    padding: var(--space-sm);
  }
}

#header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;

  .header__title {
    padding: 20px;

    > svg {
      width: 120px;
      height: 40px;
    }
  }
}

.nav {
  display: none;

  &__block {
    background: $white;
    @include radius;
    position: fixed;
    right: 0;
    top: 40px;
    padding: 24px 32px;
  }

  &__item {
    font-family: $fontFamilyEng200;
    font-weight: 400;
    padding: 0 0 16px 0;
    text-transform: capitalize;
    line-height: 1;
  }

  &__menu {
    position: relative;
    width: 44px;
    height: 46px;
    padding: 12px 8px;
    transition: all 0.4s;

    .nav__line {
      position: relative;
      width: 17px;

      &:nth-of-type(1) {
        top: -2px;
        transform: translateY(5px) rotate(-45deg);
      }
      &:nth-of-type(2) {
        opacity: 0;
      }
      &:nth-of-type(3) {
        top: 0;
        width: 17px;
        transform: translateY(-10px) rotate(45deg);
      }
    }
  }

  &__line {
    display: block;
    width: 15px;
    height: 2px;
    margin: 0 auto 0 0;
    background: $key;
    transition: all 0.4s;

    &:not(:nth-of-type(3)) {
      margin-bottom: 4px;
    }

    &:nth-of-type(3) {
      width: 10px;
    }
  }

  &__sns {
    width: 32px;
    height: 32px;

    circle {
      fill: $bg100;
    }

    path {
      fill: $text100;
    }
  }
}

.nav__sp {
  top: 0;
  background: $white;
  color: $text100;
  text-align: left;
  z-index: 700;
  font-size: 1.6rem;
  letter-spacing: 0.05em;
  height: 100%;
  display: block;
  position: relative;
}

.menu__bg {
  position: fixed;
  z-index: 12;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.4);
  transition: all 0.3s;
}

@include md {
  #nav {
    display: block;
    padding: 32px 16px 24px;
    position: fixed;
    width: 130px;
    right: 0;
    top: 70px;
    height: auto;
    border-radius: 4px 0 0 4px;
    ul {
      padding: 0;
    }
  }

  .nav {
    display: block;

    &__menu {
      display: none;
    }
  }
}
</style>