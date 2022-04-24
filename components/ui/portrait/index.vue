<template>
  <div :class="$style.container" :style="style">
    <svg :class="$style.decorTop" width="74" height="181" viewBox="0 0 74 181" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M0 18.9077C0 13.0775 4.36868 7.841 9.78278 7.18158L64.0771 0.568688C69.5459 -0.097399 74 4.1565 74 10.0456V162.092C74 167.923 69.6313 173.159 64.2172 173.818L9.92293 180.431C4.4541 181.097 0 176.843 0 170.954V18.9077Z" fill="#796FC3"/>
    </svg>
    <svg :class="$style.decorBottom" width="45" height="109" viewBox="0 0 45 109" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M0 15.3752C0 9.5281 4.40359 4.27637 9.86096 3.61503L34.9978 0.568888C40.5103 -0.0991337 45 4.16712 45 10.0733V93.6248C45 99.4719 40.5964 104.724 35.139 105.385L10.0022 108.431C4.48968 109.099 0 104.833 0 98.9267V15.3752Z" fill="#34D1BF"/>
    </svg>
    <img :src="image" :class="$style.image" alt="" />
  </div>
</template>

<script>
export default {
  name: 'UiPortrait',
  components: {},
  props: {
    image: {
      type: [Object, String],
      required: true
    }
  },
  computed: {
    style () {
      return {
        '--aspect': `${(600 / 448) * 100}%`
      }
    }
  }
}
</script>

<style lang="scss" module>
  .container {
    position: relative;
    width: 100%;
    max-width: 44.8em;
    display: block;
    &:before {
      content: '';
      display: block;
      padding-bottom: var(--aspect);
    }
    @include down(md) {
      max-width: 31.1em;
      max-height: 33.7em;
    }
  }
  .image {
    z-index: 2;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    mask: url("~/assets/images/shape2.svg") center / contain no-repeat;

    @include down(md) {
      mask-image: url("~/assets/images/shape2-mob.svg");
      height: 33.7em;
    }
  }
  .decor {
    z-index: 1;
    &Top {
      position: absolute;
      top: 0;
      left: 5.1em;
      width: 7.4em;
      @include down(md) {
        width: 5.2em;
        left: 3.5em;
      }
    }
    &Bottom {
      position: absolute;
      bottom: 0;
      right: 7.6em;
      width: 4.5em;
      @include down(md) {
        width: 3.2em;
        right: 5.2em;
      }
    }
  }
</style>
