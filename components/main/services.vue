<template>
  <section id="design-process" class="service-section service-2">
    <div class="container">
      <div class="row">
        <div class="col">
          <div class="title-2 mb-4">
            <h2>{{ $t("ourDesignProcess.title") }}</h2>
            <svg class="title-svg">
              <use xlink:href="/svg/icons.svg#title-line"></use>
            </svg>
          </div>
          <div class="row property-service column-space about-service">
            <div
              class="col-xl-3 mx-auto fadeInUp d-flex flex-column flex-xl-row align-items-center"
              v-for="(item, index) in Services_data"
              :key="index"
              :style="{
                width: index === Services_data.length - 1 && 'fit-content',
              }"
            >
              <div class="flip-card-click">
                <div class="flip-card-inner" tab-index="0">
                  <div class="flip-card-front">
                    <div class="service-box">
                      <div class="hover-line">
                        <svg class="service-icon">
                          <use :xlink:href="item.svg"></use>
                        </svg>
                        <div>
                          <svg class="icon-line-color">
                            <use :xlink:href="item.svg1"></use>
                          </svg>
                        </div>
                      </div>
                      <h3>{{ index + 1 }}. {{ item.title }}</h3>
                      <button class="btn btn-light-bg">Learn more</button>
                    </div>
                  </div>
                  <div class="flip-card-back">
                    <div class="service-box">
                      <h3>{{ item.title }}</h3>
                      <p class="font-roboto">{{ item.details }}</p>
                    </div>
                  </div>
                </div>
              </div>
              <div
                v-if="index !== Services_data.length - 1"
                class="arrow-1"
              ></div>
            </div>
            <div class="d-flex align-items-center justify-content-center mt-3">
              <a
                class="btn btn-gradient btn-pill color-2 me-1"
                @click="handleBookSession"
                >Book Your Session</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts" setup>
import { useI18n } from "vue-i18n";
import { onMounted } from "vue";
const { t } = useI18n();

let route = useRoute();
let router = useRouter();
function handleBookSession(e: any) {
  e.preventDefault();
  console.log("clicked");
  router.push({ path: "/main/signup" });
}
const Services_data = [
  {
    svg: "/svg/icons.svg#home-heart",
    svg1: "/svg/icons.svg#line-straight",
    title: "Get your vision",
    details: t("ourDesignProcess.para1"),
  },
  {
    svg: "/svg/icons.svg#customer-service",
    svg1: "/svg/icons.svg#line-straight",
    title: "Design your idea",
    details: t("ourDesignProcess.para2"),
  },
  {
    svg: "/svg/icons.svg#key",
    svg1: "/svg/icons.svg#line-straight",
    title: "Worry-free installation",
    details: t("ourDesignProcess.para3"),
  },
  {
    svg: "/svg/icons.svg#shield",
    svg1: "/svg/icons.svg#line-straight",
    title: "Review process",
    details: t("ourDesignProcess.para4"),
  },
];
onMounted(() => {
  document
    .querySelectorAll(".flip-card-click .flip-card-inner")
    .forEach(function (item) {
      item.addEventListener("keypress", function (evt) {
        if (evt.keyCode == 13 || evt.keyCode == 32) {
          item.click();
        }
      });
    });
  // click to flip
  document.querySelectorAll(".flip-card-click").forEach(function (item) {
    item.addEventListener("click", function () {
      this.classList.toggle("flipped");
    });
  });
});
</script>
<style scoped>
.flip-card-click {
  display: inline-block;
  background-color: transparent;
  width: 250px;
  height: 350px;
  margin-right: 12px;
  margin-bottom: 12px;
  perspective: 1000px;
  transition: height 0.8s;
}
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}
.flip-card-click:focus .flip-card-inner,
.flip-card-click:active .flip-card-inner,
.flip-card-click.flipped .flip-card-inner {
  transform: rotateY(180deg);
  cursor: pointer;
}
.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}
.flip-card-back {
  flex-direction: column;
  display: block;
}
@media (max-width: 575px) {
  .flip-card-front,
  .flip-card-back {
    display: block;
  }

  .flip-card-click:not(.flipped) {
    height: 200px !important;
  }
}
.flip-card-back .service-box {
  padding: 30px 10px !important;
  justify-content: flex-start !important;
}
.flip-card-back .service-box h3 {
  font-size: 16px;
  text-align: center;
}
.flip-card-front p,
.flip-card-back p {
  padding: 10px;
  font-size: 12px;
  color: black;
  -webkit-line-clamp: initial !important;
}
@media (max-width: 1460px) {
  .service-section.service-2 .property-service > div .service-box p {
    -webkit-line-clamp: initial !important;
  }
}
.flip-card-back {
  transform: rotateY(180deg);
}

.arrow-1 {
  margin-top: 20px;
  width: 30px;
  height: clamp(20px, 50px, 100px);
  display: flex;
  flex-direction: column;
  color: #ed1f26;
}

.arrow-1:before {
  content: "";
  background: currentColor;
  width: 100%;
  height: clamp(20px, 50px, 100px);
  clip-path: polygon(
    10px 0,
    10px calc(100% - 15px),
    0 calc(100% - 15px),
    50% 100%,
    100% calc(100% - 15px),
    calc(100% - 10px) calc(100% - 15px),
    calc(100% - 10px) 0
  );
  /* animation: a1 1.5s infinite linear; */
}
@media (min-width: 1200px) {
  .arrow-1 {
    margin-left: 20px;
    width: clamp(20px, 50px, 100px);
    height: 30px;
    display: flex;
    color: #ed1f26;
  }
  .arrow-1:before {
    content: "";
    background: currentColor;
    width: clamp(20px, 50px, 100px);
    clip-path: polygon(
      0 10px,
      calc(100% - 15px) 10px,
      calc(100% - 15px) 0,
      100% 50%,
      calc(100% - 15px) 100%,
      calc(100% - 15px) calc(100% - 10px),
      0 calc(100% - 10px)
    );
    /*   animation: a1 1.5s infinite linear; */
  }
}
@media (min-width: 1024px) {
  .service-box {
    width: 250px;
    text-align: center;
  }
}
</style>
