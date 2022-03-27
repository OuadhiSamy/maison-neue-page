<template>
  <div id="app">
    <nav>
      <button class="button button__menu">M</button>
      <span>MILIEU GROTESQUE</span>
      <button class="button button__cta">(0) ADD TO CART</button>
    </nav>

    <header>
      <div class="intro__container">
        <p>
          Designed by Timo Gaessner<br />
          Available in 40 Styles and 3 Subfamilies
        </p>
        <p>
          Released in 2012, Revised in 2017<br />
          Current Version: 3.002
        </p>
      </div>

      <div class="marquee__container">
        <vue3-marquee :clone="true" :duration="8">
          <div class="continuous-text__content">MAISON NEUE</div>
          <img class="continuous-text__spiral" src="/spiral.png" />
        </vue3-marquee>
        <vue3-marquee :clone="true" :duration="8" direction="reverse">
          <div class="continuous-text__content">MAISON NEUE</div>
          <img class="continuous-text__spiral" src="/spiral.png" />
        </vue3-marquee>
      </div>
    </header>

    <main>
      <!-- <ul class="sticky-menu">
        <li class="sticky-menu__item">Infos</li>
        <li class="sticky-menu__item">Styles</li>
        <li class="sticky-menu__item">Characters</li>
        <li class="sticky-menu__item">In Use</li>
      </ul> -->
      <div class="content__container paragraph">
        <p class="content__paragraph">
          Maison Neue is the completely reworked version of our original Maison
          typeface family. While the earlier version was constructed using rigid
          elements, Maison Neue has been meticulously redrawn to be less
          formulaic and have a stronger focus on optical criteria to create a
          distinct grotesque paying greater attention to harmony, rhythm and
          flow. In 2017, Maison Neue was further developed and expanded into a
          super family of 40 styles. This includes the subtly condensed original
          version, an extended counterpart, a mono-spaced alignment—all
          featuring additional weights within each family.
        </p>
      </div>
      <div class="content__container text-size">
        <div class="content__sticky">
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
            <div>Extended Demi</div>
          </div>
          <p :style="{ fontSize: font.size + 'px' }">
            Typography is the art and technique of arranging type to make
            written language legible, readable, and appealing when displayed.
            The arrange­ment of type involves selecting type­faces, point sizes,
            line lengths, line-spacing, and letter-spacing, and adjusting the
            space between pairs of letters. The term typo­graphy
          </p>
        </div>
      </div>
      <style-list class="list-grid-1" :list="maisonNueList" />
      <style-list class="list-grid-2" :list="maisonNueExtList" />
      <style-list class="list-grid-3" :list="maisonNueMonoList" />
      <div class="content__container characters">
        <h2>Characters</h2>
        <div v-for="characterCat in characterList" :key="characterCat">
          <h3 @click="characterCat.open = !characterCat.open">
            {{ characterCat.title }}
            <span
              ><svg
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
            >
              {{ character }}
            </div>
          </div>
        </div>
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
</template>




<script>
import fontLists from "./datas/styles.json";
import characterList from "./datas/characters.json";
import styleList from "./components/styleList.vue";
import "vue3-marquee/dist/style.css";

export default {
  components: {
    styleList,
  },
  data: () => {
    return {
      font: {
        size: 16,
        style: 600,
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
  computed: {},
  mounted() {
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
  position: sticky;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 8px 48px;
  background: red;
  background: white;

  .button {
    cursor: pointer;
    border: none;
    background: transparent;

    &__cta {
      color: white;
      background: black;
      font-size: 18px;
      font-weight: 700;
      padding: 16px 24px;
      border-radius: 100px;
    }
  }

  span {
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
  margin-top: -68px;

  .intro {
    &__container {
      display: flex;
      gap: 48px;
      padding: 0 48px;
      height: 100%;
      align-items: center;
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
    display: flex;
    flex-direction: column;
    grid-column: 1/2;
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
        border-bottom: 1px solid black;
      }

      &.paragraph {
        grid-column: 3/10;
        border-top: none;
      }
    }

    &__sticky {
      position: sticky;

      .options {
        display: flex;
        flex-direction: row;
        gap: 116px;
        margin-bottom: 32px;

        &__slider {
          margin: 0 16px;
          width: 200px;
          transform: translateY(-3px);
        }
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
      max-height: 500px;
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
    }
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

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
