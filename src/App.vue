<template>
  <div>
    <nav id="nav">
      <button class="button button__menu">
        <svg
          width="20"
          height="12"
          viewBox="0 0 20 12"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <rect width="20" height="2" fill="black" />
          <rect y="10" width="20" height="2" fill="black" />
        </svg>
      </button>
      <div class="logo">MILIEU GROTESQUE</div>
      <button class="button button__cta">
        (0)
        <div class="text-wrapper">
          <div class="main-text">
            <span>A</span>
            <span>D</span>
            <span>D</span>
            <span class="ml">T</span>
            <span class="mr">O</span>
            <span>C</span>
            <span>A</span>
            <span>R</span>
            <span>T</span>
          </div>
          <div class="sub-text">
            <span>A</span>
            <span>D</span>
            <span>D</span>
            <span class="ml">T</span>
            <span class="mr">O</span>
            <span>C</span>
            <span>A</span>
            <span>R</span>
            <span>T</span>
          </div>
        </div>
      </button>
    </nav>
    <div ref="scrollSections">
      <header>
        <div class="intro__container">
          <div class="intro__text">
            <div class="intro__text--wrapper">
              <span>Designed by Timo Gaessner<br /></span>
            </div>
            <div class="intro__text--wrapper">
              <span>Available in 40 Styles and 3 Subfamilies</span>
            </div>
          </div>
          <div class="intro__text">
            <div class="intro__text--wrapper">
              <span>Released in 2012, Revised in 2017<br /></span>
            </div>
            <div class="intro__text--wrapper">
              <span>Current Version: 3.002</span>
            </div>
          </div>

          <div class="intro__detail">
            <img class="" src="/detail.png" />
          </div>
        </div>

        <div class="marquee__container">
          <div class="marquee__wrapper">
            <vue3-marquee id="marquee1" :clone="true" :duration="8">
              <div class="continuous-text__content">MAISON NEUE</div>
              <img class="continuous-text__spiral" src="/spiral.png" />
            </vue3-marquee>
          </div>
          <div class="marquee__wrapper">
            <vue3-marquee
              id="marquee2"
              :clone="true"
              :duration="8"
              direction="reverse"
            >
              <div class="continuous-text__content">MAISON NEUE</div>
              <img class="continuous-text__spiral" src="/spiral.png" />
            </vue3-marquee>
          </div>
        </div>
      </header>

      <main>
        <ul class="sticky-menu">
          <li class="sticky-menu__item"><a href="#anchor1">Infos</a></li>
          <li class="sticky-menu__item"><a href="#anchor2">Styles</a></li>
          <li class="sticky-menu__item"><a href="#anchor3">Characters</a></li>
          <li class="sticky-menu__item"><a href="#anchor4">In Use</a></li>
        </ul>
        <div class="content__container paragraph">
          <p class="content__paragraph">
            Maison Neue is the completely reworked version of our original
            Maison typeface family. While the earlier version was constructed
            using rigid elements, Maison Neue has been meticulously redrawn to
            be less formulaic and have a stronger focus on optical criteria to
            create a distinct grotesque paying greater attention to harmony,
            rhythm and flow. In 2017, Maison Neue was further developed and
            expanded into a super family of 40 styles. This includes the subtly
            condensed original version, an extended counterpart, a mono-spaced
            alignment—all featuring additional weights within each family.
            <span id="anchor2"></span>
          </p>
        </div>
        <span id="anchor1"></span>
        <div class="options">
          <div>
            <span>Size</span>
            <input
              ref="slider"
              id="slider"
              class="options__slider"
              type="range"
              v-model="font.size"
              :min="8"
              :max="56"
            />
            <span>{{ font.size }}</span>
          </div>
          <dropdown :list="styleList" @onStyleChange="updateStyle" />
        </div>
        <div class="content__container text-size">
          <div class="content__playground">
            <p
              :style="{
                fontSize: font.size + 'px',
                fontWeight: font.weight,
                fontFamily: font.family,
                fontStyle: font.style,
              }"
            >
              Typography is the art and technique of arranging type to make
              written language legible, readable, and appealing when displayed.
              The arrange­ment of type involves selecting type­faces, point
              sizes, line lengths, line-spacing, and letter-spacing, and
              adjusting the space between pairs of letters. The term typo­graphy
            </p>
          </div>
        </div>
        <style-list class="list-grid-1" :list="maisonNueList" />
        <style-list class="list-grid-2" :list="maisonNueExtList" />
        <style-list class="list-grid-3" :list="maisonNueMonoList" />
        <span id="anchor3"></span>
        <div class="content__container characters">
          <h2>Characters</h2>
          <div v-for="characterCat in characterList" :key="characterCat">
            <h3 @click="characterCat.open = !characterCat.open">
              {{ characterCat.title }}
              <span
                ><svg
                  :style="[
                    characterCat.open
                      ? { transform: 'rotate(0)' }
                      : { transform: 'rotate(180deg)' },
                  ]"
                  width="15"
                  height="11"
                  viewBox="0 0 15 11"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path d="M0 11L7.5 0L15 11H0Z" fill="black" />
                </svg>
              </span>
            </h3>
            <div
              :class="[characterCat.open ? '' : 'close', 'characters__wrapper']"
            >
              <div
                v-for="character in characterCat.content"
                :key="character"
                class="characters__item"
                :style="{
                  fontWeight: font.weight,
                  fontFamily: font.family,
                  fontStyle: font.style,
                }"
              >
                {{ character }}
              </div>
            </div>
          </div>
          <span id="anchor4"></span>
        </div>
      </main>
      <div class="font-use__container">
        <h2>Maison Neue in Use</h2>
        <div class="font-use__item">
          <img
            class="font-use__image"
            src="https://www.milieugrotesque.com/uploads/MilieuGrotesque_MaisonNeue_Critical00---625.webp"
            alt=""
          />
          <p class="font-use__legend">
            Critical By Design? by Meike Hardt (m—d—buero) & Moritz <br />
            Greiner-Petter
          </p>
        </div>

        <div class="font-use__item">
          <img
            class="font-use__image"
            src="https://www.milieugrotesque.com/uploads/MilieuGrotesque_MaisonNeue_A3A02---625.webp"
            alt=""
          />
          <p class="font-use__legend">A3! <br />by Balcolony</p>
        </div>

        <div class="font-use__item">
          <img
            class="font-use__image"
            src="https://www.milieugrotesque.com/uploads/MilieuGrotesque_MaisonNeue_Bunch05---625.webp"
            alt=""
          />
          <p class="font-use__legend">
            Bunch <br />
            by Bunch
          </p>
        </div>

        <div class="font-use__item">
          <img
            class="font-use__image"
            src="https://www.milieugrotesque.com/uploads/58107d62794ab---625.webp"
            alt=""
          />
          <p class="font-use__legend">
            Youngchang Chung — Exhibition Catalogue <br />
            by Morphoria design collective
          </p>
        </div>
      </div>
    </div>
  </div>
</template>




<script>
import fontLists from "./datas/styles.json";
import characterList from "./datas/characters.json";
import styleList from "./components/styleList.vue";
import dropdown from "./components/dropdown.vue";
import gsap from "gsap";
import "vue3-marquee/dist/style.css";

export default {
  components: {
    styleList,
    dropdown,
  },
  data: () => {
    return {
      font: {
        size: 16,
        weight: 600,
        family: "Maison Neue",
      },
      maisonNueList: {
        title: "Maison Neue",
        content: fontLists.maisonNue,
      },
      maisonNueExtList: {
        title: "Maison Neue Ext",
        content: fontLists.maisonNueExtended,
      },
      maisonNueMonoList: {
        title: "Maison Neue Mono",
        content: fontLists.maisonNueMono,
      },
      characterList,
    };
  },
  computed: {
    styleList() {
      //  return {this.maisonNueList}
      return [
        this.maisonNueList,
        this.maisonNueExtList,
        this.maisonNueMonoList,
      ];
    },
  },
  methods: {
    animationSequence() {
      gsap.to("#marquee1", {
        duration: 0.8,
        y: "0%",
        ease: "Circ.easeOut",
      });

      gsap.to("#marquee2", {
        duration: 0.5,
        y: "0%",
        ease: "Circ.easeOut",
      });

      gsap.to(".marquee__container", {
        duration: 0.8,
        delay: 1,
        bottom: 0,
        y: 0,
        ease: "Pow2.easeOut",
      });

      gsap.to(".intro__text--wrapper span", {
        y: "0",
        delay: 1,
        duration: 0.8,
      });

      gsap.to(".intro__detail img", {
        x: "0",
        delay: 1,
        duration: 0.8,
      });

      gsap.to("#nav", {
        y: "0",
        delay: 1,
        duration: 0.8,
      });
    },
    updateStyle(payload) {
      this.font.weight = payload.fontWeight;
      this.font.family = payload.fontFamily;
      this.font.style = payload.fontStyle;
      console.log(payload)
    },
  },
  mounted() {
    // Start Animations
    this.$nextTick(function () {
      setTimeout(() => {
        this.animationSequence();
      }, 1000);
    });

    let slider = document.getElementById("slider");

    let value = ((slider.value - slider.min) / (slider.max - slider.min)) * 100;
    slider.style.background =
      "linear-gradient(to right, #000 0%, #000 " +
      value +
      "%, #C4C4C4 " +
      value +
      "%, #C4C4C4 100%)";

    slider.oninput = function () {
      var value = ((this.value - this.min) / (this.max - this.min)) * 100;
      this.style.background =
        "linear-gradient(to right, #000 0%, #000 " +
        value +
        "%, #C4C4C4 " +
        value +
        "%, #C4C4C4 100%)";
    };
  },
};
</script>

<style lang="scss">
@import "./scss/index.scss";

nav {
  z-index: 100;
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 8px 48px;
  background: white;
  transform: translateY(-100%);

  .button {
    position: relative;
    cursor: pointer;
    border: none;
    background: transparent;

    &__cta {
      display: flex;
      color: white;
      background: black;
      font-size: 18px;
      font-weight: 700;
      padding: 16px 24px;
      border-radius: 100px;

      .text-wrapper {
        position: relative;
        margin-left: 8px;
      }

      .ml {
        margin-left: 4px;
      }

      .mr {
        margin-right: 4px;
      }

      $delay: 0.06s;

      span:nth-of-type(2) {
        transition-delay: $delay;
      }
      span:nth-of-type(3) {
        transition-delay: calc($delay * 2);
      }
      span:nth-of-type(4) {
        transition-delay: calc($delay * 3);
      }
      span:nth-of-type(5) {
        transition-delay: calc($delay * 4);
      }
      span:nth-of-type(6) {
        transition-delay: calc($delay * 5);
      }
      span:nth-of-type(7) {
        transition-delay: calc($delay * 6);
      }
      span:nth-of-type(8) {
        transition-delay: calc($delay * 7);
      }
      span:nth-of-type(9) {
        transition-delay: calc($delay * 8);
      }

      .main-text {
        span {
          opacity: 1;
          display: inline-block;
          transform: scaleY(1);
          transition: 0.3s ease;
          transform-origin: top;
        }

        span:nth-of-type(2) {
          transition-delay: $delay;
        }
        span:nth-of-type(3) {
          transition-delay: calc($delay * 2);
        }
        span:nth-of-type(4) {
          transition-delay: calc($delay * 3);
        }
        span:nth-of-type(5) {
          transition-delay: calc($delay * 4);
        }
        span:nth-of-type(6) {
          transition-delay: calc($delay * 5);
        }
        span:nth-of-type(7) {
          transition-delay: calc($delay * 6);
        }
        span:nth-of-type(8) {
          transition-delay: calc($delay * 7);
        }
        span:nth-of-type(9) {
          transition-delay: calc($delay * 8);
        }
      }

      .sub-text {
        height: 0;
        top: 0;
        position: absolute;

        span {
          opacity: 0;
          display: inline-block;
          transform: scaleY(0);
          transition: 0.5s ease;
          transform-origin: bottom;
        }

        span:nth-of-type(2) {
          transition-delay: $delay;
        }
        span:nth-of-type(3) {
          transition-delay: calc($delay * 2);
        }
        span:nth-of-type(4) {
          transition-delay: calc($delay * 3);
        }
        span:nth-of-type(5) {
          transition-delay: calc($delay * 4);
        }
        span:nth-of-type(6) {
          transition-delay: calc($delay * 5);
        }
        span:nth-of-type(7) {
          transition-delay: calc($delay * 6);
        }
        span:nth-of-type(8) {
          transition-delay: calc($delay * 7);
        }
        span:nth-of-type(9) {
          transition-delay: calc($delay * 8);
        }
      }

      &:hover {
        .main-text span {
          transform: scaleY(0);
          opacity: 0;
        }

        .sub-text span {
          transform: scaleY(1);
          opacity: 1;
        }
      }
    }
  }

  .logo {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    font-size: 17px;
  }
}

header {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100vh;
  position: relative;
  padding-top: 68px;

  .intro {
    &__container {
      display: flex;
      gap: 48px;
      padding: 0 48px 226px;
      height: 100%;
      align-items: center;
    }

    &__text {
      font-size: 12px;
      line-height: 19px;

      &--wrapper {
        overflow: hidden;
        span {
          display: block;
          transform: translateY(24px);
        }
      }
    }

    &__detail {
      flex-grow: 1;
      display: flex;
      justify-content: flex-end;
      overflow: hidden;

      img {
        width: 14px;
        transform: translateX(100%);
      }
    }
  }

  .continuous-text {
    &__content {
      font-size: 194px;
      font-family: "Maison Neue";
      font-weight: 600;
      line-height: 0.8;
    }

    &__spiral {
      width: 108px;
      height: 108px;
      margin: 0 24px;
      animation-name: spin;
      animation-duration: 5000ms;
      animation-iteration-count: infinite;
      animation-timing-function: linear;
    }
  }
}
.marquee {
  &__container {
    position: absolute;
    bottom: 50%;
    transform: translateY(50%);
  }

  &__wrapper {
    overflow: hidden;
  }
}

#marquee1 {
  transform: translateY(100%);
}

#marquee2 {
  transform: translateY(-100%);
}

.vue3-marquee {
  overflow: hidden;
}

main {
  display: grid;
  margin: 0 48px;
  column-gap: 48px;
  grid-template-columns: repeat(12, 1fr);
  @include fluid-gap($min-width, $max-width, $min-gap, $max-gap);

  .sticky-menu {
    position: sticky;
    top: 120px;
    display: flex;
    flex-direction: column;
    grid-column: 1/3;
    margin: 80px 0 0 0;
    gap: 24px;

    &__item {
    }
  }

  .content {
    &__container {
      grid-column: 3/13;
      padding: 40px 0;
      border-top: 1px solid black;

      &.text-size {
        margin-bottom: 40px;
      }

      &.paragraph {
        margin-top: 40px;
        grid-column: 3/11;
        font-size: 12px;
        line-height: 1.5;
        font-weight: 500;
        border-top: none;
      }
    }

    &__playground {
      p {
        line-height: 1.5;
      }
    }
  }

  .list-grid-1 {
    grid-column: 3/6;
  }

  .list-grid-2 {
    grid-column: 6/10;
  }

  .list-grid-3 {
    grid-column: 10/13;
  }

  .characters {
    margin-top: 40px;
    svg {
      transform: rotate(180deg);
      transition: 0.3s ease;
    }

    h2 {
      font-size: 16px;
      margin-bottom: 32px;
    }

    h3 {
      font-size: 16px;
      margin-bottom: 24px;
      cursor: pointer;
    }

    &__wrapper {
      display: grid;
      grid-template-columns: repeat(9, 1fr);
      gap: 8px;
      margin-bottom: 40px;
      max-height: 800px;
      transition: 0.2s ease;

      &.close {
        max-height: 0;
        overflow: hidden;
      }
    }

    &__item {
      display: flex;
      justify-content: center;
      align-items: center;
      border: 1px solid black;
      aspect-ratio: 1;
      font-size: 40px;
      font-family: "Maison Neue Mono";
      cursor: pointer;
    }
  }
}

.options {
  position: sticky;
  z-index: 3;
  top: 68px;
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 116px;
  padding: 24px 0;
  grid-column: 3/13;
  background: white;

  &__slider {
    margin: 0 16px;
    width: 200px;
    transform: translateY(-3px);
  }
}

.font-use {
  &__container {
    display: grid;
    margin: 0 48px;
    column-gap: 48px;
    grid-template-columns: repeat(12, 1fr);
    @include fluid-gap($min-width, $max-width, $min-gap, $max-gap);
    padding: 40px 0;
    border-top: 1px solid black;

    h2 {
      margin-bottom: 40px;
      grid-column: 1/-1;
    }

    div:nth-child(2) {
      grid-column: 1/7;
    }

    div:nth-child(3) {
      margin-top: 122px;
      grid-column: 7/13;

      p {
        padding-left: 40px;
      }
    }

    div:nth-child(4) {
      margin-top: -53px;
      grid-column: 8/13;
    }

    div:nth-child(5) {
      margin-top: -328px;
      grid-column: 2/7;
    }
  }

  &__image {
    width: 100%;
    height: auto;
    margin-bottom: 12px;
  }

  &__legend {
    font-size: 12px;
  }
}

#anchor2 {
  height: 0;
  grid-column: 1/-1;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
