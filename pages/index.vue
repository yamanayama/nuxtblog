<template lang="pug">
- var img_path = '@/assets/images/top/'

article
  //- hero
  .hero
    .hero__block(v-scroll="handleScroll")
      .hero__info
        h1.hero__logo
          span.small Design & Frontend
          span.medium
            //- img(:class="$style.hero__logo")(src="@/assets/images/svg/logo.svg", alt="naomoon")
            | Naomi
            br
            | Murakami
        p.hero__text Hi, I'm <strong>Naomi Murakami</strong>. I am a UI / UX designer and front-end engineer. Have fun!
      .hero__imgcontainer
        //- picture
        //-   source(media="(min-width: 1000px)" srcset="@/assets/images/top/hero_bg_pc.jpg")
        //-   source(media="(min-width: 480px)" srcset="@/assets/images/top/hero_bg_sp.jpg")
        //-   img(src="@/assets/images/top/hero_bg_sp.jpg", alt="")

        .hero__scroll(v-scroll="handleScroll")
          a(href="#concept")
            span
            em Scroll


  //-consept
  section#concept.maxWidth.concept(v-scroll="handleScroll")
    .concept__block
      Title(title='Design & Frontend')
      //- p.concept__deco Concept Work
      p.concept__text
        | 巷ではデザイナー3.0だとか、UXデザインが叫ばれていますね。
        br
        | 私はBTCでいうところの、T/Cタイプのデザイナーです。
      p.concept__text
        | 「ユーザーの抱えた課題を解決したい<br>何を考えて、今何に困り、何を望んでいるのか
        <br>ストーリーとコンテキストを理解した上で、プロダクトに落としこみたい」
      p.concept__text
        | 結果、ユーザーインタビューからUI設計、フロントエンド開発まで行う、ちょっと変わった越境型デザイナーとなってしまいました。
        br
        | ツールが普及し誰もが簡単にWebサービスを作れるようになった現代で、「つくる」「かんがえる」どちらも欠けることなく、磨きつづけることが自分の生存戦略です。
      .concept__catch
        .concept__catch__container
          .concept__catch__img
      .concept__circle
        span.circle(v-for="circle in circles" :key="circle.id")

  //-skill
  section.skill
    Title(title='skill')
    slide-wide(v-bind:skills="skills" @close="closeModal")
    section.skillmap
      h4.skillmap__title
        |  使用可能ツール
      ul.skillmap__list
        li.skillmap__item(v-for="skillmap in skillmaps" :secondary="skillmap.id") {{skillmap}}

  //-profile
  .profile(v-scroll="handleScroll")
    section.shadow.profile__block
      Title(title='Naomi Murakami')
      //- .profile__deco profile
      .profile__text
        | 自称Qiita生まれ、Qiita育ちのインハウスデザイナーです。<br>一般職、ゲームイラストレーターを経てWEB業界へきました。受託制作会社でWEBデザイナー・コーダー・ディレクター兼任後、インハウスのUIデザイナーとして働いています。
      p.profile__text
        | 普段はGAなどのデータ分析をもとに、WEBサービスのUI開発でLPOやABテストを行うことで、PDCAを回しています。
      p.profile__text
        | マークアップ（CSS,アニメーション）が得意で、趣味はフロンエンドの個人開発です。Vue(Nuxt),Reactチョットデキル。
      p.profile__sns
        a(href="https://twitter.com/yamanayama" target="_blank")
          ico_twitter

  //-portfolio
  .portfolio
    section.portfolio__block
      Title(title='portfolio')
      p.profile__text お尋ねください。
      //- nuxt-link(v-scroll-to='"#contact"' to)
      button.button.button__secondary(v-scroll-to='"#contact"') お問い合わせへ

  .blog
    section.blog__block
      Title(title='blog')
       card(
        v-for="(post,i ) in posts"
        :key="i"
        :title="post.fields.title"
        :id="post.sys.id"
        :date="post.sys.updatedAt")

  //-contact
  section#contact.contact
    svg.waveline(xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewbox="0 24 150 28 " preserveaspectratio="none")
      defs
        path#gentle-wave(d="M-160 44c30 0 58-18 88-18s 58 18 88 18 58-18 88-18 58 18 88 18 v44h-352z")
      g.wave1
        use(xlink:href="#gentle-wave" x="50" y="3" fill="#cfafff")
      g.wave2
        use(xlink:href="#gentle-wave" x="50" y="0" fill="#ae78ff")
      g.wave3
        use(xlink:href="#gentle-wave" x="50" y="9" fill="#2f0075")
    Title(title='contact')
    p.profile__text お急ぎの方はSNSからお願いします。
    Forms



</template>

<script>
//contentful
import { createClient } from '~/plugins/contentful.js'

//compornent
import Forms from '~/components/organisms/Forms.vue'
import Title from '~/components/atoms/title/index.vue'
import SlideWide from '~/components/organisms/slideWide/index.vue'
import Card from '~/components/organisms/card/index.vue'
// import Subtitle from "~/components/atoms/subtitle/index.vue";

//svg
import ico_twitter from '@/assets/images/svg/ico_twitter.svg'

const client = createClient()

export default {
  transition: 'slide-left',
  //blog
  asyncData({ env, params }) {
    return client
      .getEntries(env.CTF_BLOG_POST_TYPE_ID)
      .then((entries) => {
        return {
          posts: entries.items
        }
      })
      .catch(console.error)
  },

  head: {
    title: 'Naomi Murakami'
  },

  components: {
    Forms,
    Title,
    SlideWide,
    Card,
    //svg
    ico_twitter
  },

  data: function() {
    return {
      circles: ['circle1', 'circle2', 'circle3'],
      skills: [
        {
          id: 1,
          img: require('@/assets/images/top/skill_01.png'),
          title: 'Design',
          despriction: 'ユーザーインタビュー・UI設計など',
          text:
            'ワイヤー制作、UI設計、ユーザーインタビュー、LPO、Storybookを用いたデザインフレームワークの作成など幅広く対応できます。受託制作でCMSデザインを経験し、インハウスでサービスUI、LPOでPDCAを回しながら、スタートアップならではDPCAも展開中です。UX勉強中。'
        },
        {
          id: 2,
          img: require('@/assets/images/top/skill_02.png'),
          title: 'Frontend',
          despriction: 'マークアップからフロントエンドまで対応',
          text:
            'マークアップ、スタイルからCSSアニメーション、JSフレームワーク制作まで行います。セマンティックで秩序あるコーディングを行います。アクセシビリティやりたい勢です。状態管理を勉強中です。今回のポートフォリオはJAMstack（Nuxt・Contentful・Netlify）で構成しています。'
        },
        {
          id: 3,
          img: require('@/assets/images/top/skill_03.png'),
          title: 'Marketing',
          despriction: 'GAなどの数値を元に、仮説検証・効果検証',
          text:
            'GAなどの数値を元に、仮説検証・効果検証をしながらPDCAを回していきます。ユーザーが何に課題を感じ、どこにアプローチすれば改善されるのか、というユーザーストーリーを検討しながらPDCAを回します。'
        },
        {
          id: 4,
          img: require('@/assets/images/top/skill_03.png'),
          title: 'Illustration',
          despriction: '実は元イラストレーターです',
          text:
            '実はゲーム業界のイラストレーターを4年近く経験しました。ラインイラスト、アイコンイラストなど得意ですが、こちらはサブスキルです。'
        }
      ],
      skillmaps: [
        'Photoshop',
        'XD',
        'Illustrator',
        'HTML/CSS',
        'Pug',
        'Sass',
        'Git',
        'Gulp',
        'jQuery',
        'WordPress',
        'React',
        'Vue(Nuxt)',
        'SpriteStudio'
      ]
    }

    active: false
  },
  computed: {
    limitCount() {
      return this.skill.slice(0, 3)
    }
  },

  methods: {
    closeModal() {
      this.showModal = false
    },
    handleScroll: function(evt, el) {
      console.log(window.scrollY)
      if (window.scrollY > 50) {
        el.setAttribute(
          'style',
          'opacity: 1; transform: translate3d(0, -10px, 0)'
        )
      }
      return window.scrollY > 100
    }
  },
  head() {
    return {
      bodyAttrs: {
        class: this.showModal ? 'modal__overlay' : ''
      }
    }
  }
}
</script>

<style lang="scss" scope>
@import '@/assets/scss/config/scrollicon';
$imgPath: '../assets/images/top/';

/* hero
----------------------------------------------*/

.hero {
  position: relative;
  align-items: center;
  z-index: 10;
  margin: 0 auto 80px;
  padding: 0 20px;
  background: url(#{$imgPath}hero_bg.png) no-repeat right top;

  &__block {
    display: flex;
    position: relative;
    height: 100%;
    max-width: 1240px;
    width: 100%;
    height: 90vmax;
  }

  &__info {
    font-size: 3.2rem;
    display: flex;
    justify-content: center;
    flex-direction: column;
    height: 100%;

    span {
      display: block;
      font-size: 2rem;
    }
  }

  &__img {
    width: 50vw;
  }

  &__text {
    font-size: 1.2vw;
    line-height: 2.25;
  }

  &__scroll {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);

    a {
      &:hover {
        text-decoration: none;
        opacity: 0.6;
        display: block;
        transition: 0.2s ease;
      }

      > em {
        font-size: 1.2rem;
        padding-top: 56px;
        display: block;
      }

      > span {
        position: absolute;
        top: 0;
        left: 50%;
        width: 30px;
        height: 50px;
        margin-left: -15px;
        border: 2px solid $text100;
        border-radius: 50px;
        box-sizing: border-box;

        &::before {
          position: absolute;
          top: 10px;
          left: 50%;
          content: '';
          width: 6px;
          height: 6px;
          margin-left: -3px;
          background-color: $text100;
          border-radius: 100%;
          animation: scroll 2s infinite;
          box-sizing: border-box;
        }
      }

      @keyframes scroll {
        0% {
          transform: translate(0, 0);
          opacity: 0;
        }
        40% {
          opacity: 1;
        }
        80% {
          transform: translate(0, 20px);
          opacity: 0;
        }
        100% {
          opacity: 0;
        }
      }
    }
  }

  &__box {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;

    span {
      font-size: 2rem;
    }
  }
}

h1 {
  .small {
    line-height: 1;
    font-size: 2rem;
    margin-bottom: 1em;
    letter-spacing: 0.05em;
    font-family: $fontFamilyEng100;
    // transform: rotate(-8deg);
    color: $primary;
  }

  .medium {
    font-size: 8rem;
    font-family: $fontFamilyEng200;
    font-weight: 700;
    text-transform: uppercase;
    line-height: 1;
    letter-spacing: 0.05em;
  }
}

//tab
@include md {
  .hero {
    &__block {
      height: 90vh;
      min-height: 720px;
      max-height: 1080px;
      margin: 0 auto 180px;
    }
  }

  h1 {
    .medium {
      font-size: 14rem;
    }

    .small {
      font-size: 3rem;
    }
  }
}

/* concept
----------------------------------------------*/
.concept {
  margin: auto;
  padding-top: 80px;
  @include inView;
  @include secP;

  &__block {
    @include secP;
    @include radius;
    position: relative;
  }

  &__deco {
    position: absolute;
    top: -4rem;
    left: -1rem;
    font-family: $fontFamilyEng100;
    font-size: 3rem;
    transform: rotate(-8deg);
    color: $primary;
  }

  &__circle {
    position: absolute;
    $size: 380px;
    width: $size;
    height: $size;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: -1;

    &::after {
      border-radius: 48%;
      content: '';
      display: block;
      width: 100%;
      height: 100%;
      /* background: linear-gradient(
        to bottom,
        lighten($key, 60%),
        rgba(211, 127, 247, 0.3) 90%,
        rgba(106, 150, 245, 0.5)
      ); */
      background: linear-gradient(
        to bottom,
        #8dbeffbb,
        rgb(255, 204, 250) 90%,
        rgba(245, 106, 171, 0.5)
      );
      animation: circleGrade 8s infinite linear;
    }
  }
}

//tab
@include md {
  .concept {
    @include maxW;
    width: 100%;
    padding: 0;

    &__deco {
      top: -4rem;
      left: -8rem;
      font-size: 4rem;
    }

    &__text {
      text-align: center;
    }
  }
}

//pc
@include lg {
}

/* skill
----------------------------------------------*/
.skill {
  margin: auto;
  @include secP;

  &map {
    margin: auto;
    text-align: center;

    &__title {
      text-align: center;
      margin-bottom: 16px;
      font-size: 2.4rem;
    }

    &__list {
      display: flex;
      max-width: 680px;
      width: 100%;
      font-size: 1.2rem;
      flex-wrap: wrap;
      margin: auto;
      padding: 0;
      justify-content: center;
    }

    &__item {
      background: $gray100;
      margin-bottom: 10px;
      border-radius: 20px;
      padding: 1px 20px;
      font-weight: 700;
      color: $primary;

      &:not(:last-child) {
        margin-right: 2vw;
      }
    }
  }
}

//tab
@include md {
  .skill {
    &map {
      &__item {
        &:not(:last-child) {
          margin-right: 1vw;
        }
      }
    }
  }
}

/* profile
----------------------------------------------*/
.profile {
  margin: auto;
  @include inView;
  @include secP;

  &__block {
    width: 98%;
    padding: 32px 24px;
    @include radius;
    @include justify();
    position: relative;
    z-index: 1;
  }

  &__deco {
    position: absolute;
    top: -3rem;
    left: -4rem;
    font-family: $fontFamilyEng100;
    font-size: 3rem;
    transform: rotate(-10deg);
    text-transform: capitalize;
    color: $primary;
  }

  &__sns {
    width: 32px;
    height: 32px;
    margin: auto;

    circle {
      fill: $bg100;
    }

    path {
      fill: $bg200;
    }
  }
}

//tab
@include md {
  .profile {
    padding: 72px 24px 88px;
    // border: 1px solid $bg100;

    &__block {
      max-width: 450px;

      // &::after {
      //   content: "";
      //   position: absolute;
      //   top: 8%;
      //   left: 8%;
      //   z-index: -1;
      //   border: 10px solid $bg100;
      //   width: 450px;
      //   height: 510px;
      //   @include radius;
      // }
    }

    &__deco {
      top: -5rem;
      left: -4rem;
      font-size: 4rem;
    }
  }
}

/* portfolio
----------------------------------------------*/
.portfolio {
  margin: auto;
  overflow: hidden;
  text-align: center;
  @include secP;
  margin-bottom: 80px;
  /* border: 1px solid $bg300; */
  background: $bg300;

  &:hover {
    transition: transform 0.5s linear;
  }
}

//tab
@include md {
  .portfolio {
  }
}

.links {
  padding-top: 15px;
}

/* contact
----------------------------------------------*/
.contact {
  padding: 80px 20px;
  text-align: center;
  background: $key;
  position: relative;
  color: $white;
  background: linear-gradient(to bottom, $key, darken($key, 8%));
}

.waveline {
  display: block;
  width: 100%;
  height: 60px;
  max-height: 60px;
  margin: 0;
  z-index: 5;
  top: -40px;
  position: absolute;
  left: 0px;
  float: left;
  padding-top: 4px;
}

@mixin move($id: 1, $speed: 10s) {
  .wave#{$id} > use {
    animation: move#{$id} $speed linear infinite;
    &:nth-child(1) {
      animation-delay: -2s;
    }
  }
}

@include move();
@include move($id: 2, $speed: 8s);
@include move($id: 3, $speed: 6s);

@mixin keyMove($id: 1, $start: 85, $end: -90) {
  @keyframes move#{$id} {
    0% {
      transform: translate(85px, 0%);
    }
    100% {
      transform: translate(-90px, 0%);
    }
  }
}

@include keyMove();
@include keyMove($id: 2, $start: -90, $end: 85);
@include keyMove($id: 3);

//tab
@include md {
  .portfolio {
    text-align: center;
  }
}

.links {
  padding-top: 15px;
}
</style>
