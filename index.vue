<script>
export default {
  props: ['link', 'fast', 'onlyTop'],
  methods: {
    top() {
      global.scrollTo({top: 0, behavior: this.fast ? 'instant' : 'smooth'});
      this.$emit('top');
    },
    next() {
      this.$emit('next');
      this.top();
    },
    reload() {
      this.$emit('reload');
      this.top();
    },
    reset() {
      this.$emit('reset');
      this.top();
    },
  },
};
</script>

<template>
  <nav class="level is-mobile pagination-widget">
    <div class="level-left" v-if="!onlyTop">
      <div class="field has-addons">
        <div class="control">
          <button v-if="!link" class="button" @click="next()">
            {{ $t('main.next') }}
          </button>
          <nuxt-link
            v-else
            :to="localePath(link)"
            class="button"
            @click.native="next()"
          >
            {{ $t('main.next') }}
          </nuxt-link>
        </div>
        <p class="control">
          <button class="button" @click="reload()">
            <i class="material-icons">replay</i>
          </button>
        </p>
        <p class="control">
          <button class="button" @click="reset()">
            <i class="material-icons">chevron_left</i>
          </button>
        </p>
      </div>
    </div>
    <div v-else></div>

    <div class="level-right">
      <div class="field">
        <p class="control">
          <button class="button" @click="top()">
            <i class="material-icons">keyboard_arrow_up</i>
          </button>
        </p>
      </div>
    </div>
  </nav>
</template>

<style lang="less">
.pagination-widget {
  position: relative;
  padding: @indent-sm;
  z-index: 0;
}
</style>
