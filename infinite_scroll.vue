<template>
  <div id="scrollInfinite">
    <v-progress-circular
      v-if="loading"
      :width="3"
      :size="32"
      color="primary"
      indeterminate
    ></v-progress-circular>
  </div>
</template>

<script>
export default {
  props: {
    loading: Boolean,
  },
  methods: {
    endOfScroll() {
      const observer = new IntersectionObserver(
        (entries) => {
          if (entries[0].isIntersecting === true) {
            this.$emit("endOfScroll");
          }
        },
        { threshold: 0.5 },
      );

      // eslint-disable-next-line no-undef
      observer.observe(scrollInfinite);
    },
  },
  mounted() {
    this.endOfScroll();
  },
};
</script>

<style lang="scss">
#scrollInfinite {
  display: flex;
  justify-content: center;
  padding-bottom: 8px;
  padding-top: 8px;
}
</style>
