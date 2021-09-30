<template>
  <div :class="{ 'cover-slide': true, 'hover-darken': true, 'in-view': isInView }">
    <div
        class="bg-img-zoom img-bg50"
        :style="'background-image: url(' + pictureUrl + ');'"
    ></div>
  </div>
</template>

<script lang="ts">
import {Component, Prop, Vue} from 'vue-property-decorator'
@Component
export default class SlideInPicture extends Vue {
  isInView = false

  @Prop({ default: false, required: true })
  waitSeconds!: number

  @Prop({ default: false, required: true })
  pictureName!: string

  get waitMS(): number {
    return this.waitSeconds * 1000
  }

  get pictureUrl(): string {
    console.log("../../assets/image/" + this.pictureName)
    return require("../../assets/image/" + this.pictureName)
  }

  mounted(): void {
    console.log("セット")
    const changeAfterInterval = setInterval(
        () => {this.isInView = true; clearInterval(changeAfterInterval)},
        this.waitMS
    )
  }
}
</script>

<style lang="scss" scoped>
@import '../../assets/scss/mixin';
.cover-slide {
  position: relative;
  overflow: hidden;

  &::after {
    content: "";
    position: absolute;
    z-index: 2;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #eaebe6;
    opacity: 0;
  }
  &.in-view {
    &::after {
      opacity: 1;

      @include animation(
          $name: kf-cover-slide,
          $duration: 1.6s,
          $timing-function: ease-in-out,
          $fill-mode: both
      );
    }
  }
}

@keyframes kf-cover-slide {
  0% {
    transform-origin: left;
    transform: scaleX(0);
  }
  50% {
    transform-origin: left;
    transform: scaleX(1);
  }
  50.1% {
    transform-origin: right;
    transform: scaleX(1);
  }
  100% {
    transform-origin: right;
    transform: scaleX(0);
  }
}

.img-zoom {
  opacity: 0;

  .in-view & {
    opacity: 1;
    transition: transform 0.3s ease;
    @include animation(
        $name: kf-img-show,
        $duration: 1.6s,
        $timing-function: ease-in-out,
        $fill-mode: none
    );

    &:hover {
      transform: scale(1.05);
    }
  }
}

@keyframes kf-img-show {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 0;
  }
  50.1% {
    opacity: 1;
    transform: scale(1.5);
  }
  100% {
    opacity: 1;
  }
}

.hover-darken {
  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    transition: background-color 0.3s ease;
    pointer-events: none;

    @include animation(
        $name: kf-img-show,
        $duration: 1.6s,
        $timing-function: ease-in-out,
        $fill-mode: none
    );
  }
  &:hover::before {
    background-color: rgba(0, 0, 0, 0.4);
  }
}

.bg-img-zoom {
  //background-image: url("../../assets/image/slide-picture-1.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  width: 100%;
  @extend .img-zoom;
}

.img-bg50 {
  position: relative;

  &::before {
    display: block;
    content: '';
    padding-top: 50%;
  }
}

</style>
