<template lang="pug">
- var img_path = '@/assets/images/top/'

article
  //- hero
  div(:class="$style.hero")
    div(:class="$style.hero__block",v-scroll="handleScroll")
      div(:class="$style.hero__info")
        h1(:class="$style.hero__logo")
          span(:class="$style.small") Design & Frontend
          span(:class="$style.medium")
            //- img(:class="$style.hero__logo")(src="@/assets/images/svg/logo.svg", alt="naomoon")
            | Naomi
            br
            | Murakami
        p(:class="$style.hero__text") aaaaaaaaaaaaaaaaaaaaaaaaaaaa
      div(:class="$style.hero__imgcontainer")
        //- img(src="@/assets/images/svg/dsmmy_02.svg", alt="")
        //- picture
        //-   source(media="(min-width: 1000px)" srcset="@/assets/images/top/hero_bg_pc.jpg")
        //-   source(media="(min-width: 480px)" srcset="@/assets/images/top/hero_bg_sp.jpg")
        //-   img(src="@/assets/images/top/hero_bg_sp.jpg", alt="")

        div(:class="$style.hero__scroll",v-scroll="handleScroll")
          a(href="#concept")
            span
            em Scroll


  //-consept
  section#concept.maxWidth(:class="$style.concept ",v-scroll="handleScroll")
    div(:class="$style.concept__block")
      Title(title='Design & Frontend')
      p(:class="$style.concept__deco") Concept Work
      p(:class="$style.concept__text")
        | デザインとフロントエンドが好き
        br
        | デザインとフロントエンドが好きデザインとフロロントエンドが好きデザインとフロロントエンドが好き
        br
        | デザインとフロントエンドが好きデザインとフロロントエンドが好きデザインとフロロントエンドが好き
      div(:class="$style.concept__catch")
        div(:class="$style.concept__catch__container")
          div(:class="$style.concept__catch__img")

  //-skill
  section(:class="$style.skill",)
    Title(title='skill')
    slide-wide(:skills="skills" v-scroll="handleScroll")
    section(:class="$style.skillmap")
      h4(:class="$style.skillmap__title")
        |  使用可能ツール
      ul(:class="$style.skillmap__list")
        li(v-for="skillmap in skillmaps" :secondary="skillmap.id" :class="$style.skillmap__item") {{skillmap}}

  //-profile
  div(:class="$style.profile" v-scroll="handleScroll")
    section(:class="$style.profile__block")
      Title(title='Naomi Murakami')
      p(:class="$style.profile__deco") profile
      p(:class="$style.profile__text")
        | 一般職、ゲームイラストレーターを経てWEB業界へきました。受託制作会社でWEBデザイナー・コーダー・ディレクター兼任後、インハウスのUIデザイナーとして働いています。
      p(:class="$style.profile__text")
        | 普段はGAなどのデータ分析をもとに、WEBサービスのUI開発でLPOやABテストを行うことで、PDCAを回しています。
      p(:class="$style.profile__text")
        | マークアップ（CSS,アニメーション）が得意で、趣味はフロンエンドの個人開発です。Vue(Nuxt),Reactチョットデキル。
      p(:class="$style.profile__sns")
        a(href="https://twitter.com/yamanayama" target="_blank")
          ico_twitter

  //-portfolio
  div(:class="$style.portfolio")
    section(:class="$style.portfolio__block")
      Title(title='portfolio')
      p(:class="$style.profile__text") お尋ねください。
      //- nuxt-link(v-scroll-to='"#contact"' to)
      button.button__secondary(:class="$style.button",v-scroll-to='"#contact"') お問い合わせへ


  //-contact
  section#contact(:class="$style.contact")
    Title(title='contact')
    p(:class="$style.profile__text") お急ぎの方はSNSからお願いします。
    Forms



</template>

<script>
import Forms from "~/components/organisms/Forms.vue";
import Title from "~/components/atoms/title/index.vue";
import ico_twitter from "@/assets/images/svg/ico_twitter.svg";
import SlideWide from "~/components/organisms/slidewide/index.vue";
// import Subtitle from "~/components/atoms/subtitle/index.vue";

export default {
  head: {
    title: "Naomoon"
  },

  components: {
    Forms,
    Title,
    SlideWide,
    ico_twitter
  },

  data: function() {
    return {
      skills: [
        {
          id: 1,
          img: require("@/assets/images/svg/dammy_01.svg"),
          title: "Design",
          despriction: "Design",
          text:
            "ワイヤー制作、UI設計、ユーザーインタビュー、LPO、デザインガイドライン作成など幅広く対応できます。受託制作でCMSデザインを経験し、インハウスでサービスUI、LPOでPDCAを回しながら、スタートアップならではDPCAも展開中です。UX勉強中。"
        },
        {
          id: 2,
          img: require("@/assets/images/svg/dammy_01.svg"),
          title: "Cording",
          despriction: "Cording",
          text:
            "マークアップ、スタイルからCSSアニメーション、JSフレームワーク制作まで行います。セマンティックで秩序あるコーディングを行います。アクセシビリティやりたい勢です。"
        },
        {
          id: 3,
          img: require("@/assets/images/svg/dammy_01.svg"),
          title: "Marketing",
          despriction: "Marketing",
          text: "GAなどの解析"
        },
        {
          id: 4,
          img: require("@/assets/images/svg/dammy_01.svg"),
          title: "Illustration",
          despriction: "Illustration",
          text: "イラスト"
        }
      ],
      skillmaps: [
        "Photoshop",
        "XD",
        "Illustrator",
        "HTML/CSS",
        "Pug",
        "Sass",
        "Git",
        "Gulp",
        "jQuery",
        "WordPress",
        "React",
        "Vue(Nuxt)",
        "SpriteStudio"
      ]
    };
  },
  computed: {
    limitCount() {
      return this.skill.slice(0, 3);
    }
  },

  methods: {
    handleScroll: function(evt, el) {
      console.log(window.scrollY);
      if (window.scrollY > 50) {
        el.setAttribute(
          "style",
          "opacity: 1; transform: translate3d(0, -10px, 0)"
        );
      }
      return window.scrollY > 100;
    }
  }
};
</script>

<style lang="scss" module>
@import "@/assets/scss/config/scrollicon";
$imgPath: "../assets/images/top/";

/* hero
----------------------------------------------*/

.hero {
  position: relative;
  align-items: center;
  z-index: 10;
  /* background: url("#{$imgPath}hero_bg_pc.jpg") no-repeat center center/cover; */
  margin: 0 auto 80px;
  padding: 0 20px;

  &__block {
    display: flex;
    position: relative;
    height: 100%;
    color: $white;
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
          content: "";
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

    &__block{
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
  background: $bg100;
  @include inView;
  @include secP;

  &__block {
    @include radius;
    position: relative;
    background: $primary;
    padding: var(--space-md);
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

  &__text {
  }
}

//tab
@include md {
  .concept {

    &__block{
      @include maxW;
      width: 100%;
      margin: auto;
    }

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
  background: $bg100;
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
  background: $bg200;

  &__block {
    width: 98%;
    padding: 3.2rem 1.6rem;
    @include radius;
    @include justify();
    position: relative;
    z-index: 1;
    color: $white;
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
  background: $bg100;
  @include secP;
  /* background: $bg200 url("#{$imgPath}portfolio_bg.jpg") no-repeat center
    center/cover; */

  &:hover {
    transition: transform 0.5s linear;
  }
}

//tab
@include md {
  .portfolio {
    text-align: center;
  }
}

.links {
  padding-top: 15px;
}

/* contact
----------------------------------------------*/
.contact {
  @include secP;
  text-align: center;
  color: $white;
}
</style>
