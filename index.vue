<script>
export default {
  props: ['fast'],
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
    <div class="level-left">
      <div class="field has-addons">
        <p class="control">
          <button class="button" @click="next()">Следующие</button>
        </p>
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
  padding: 0 @indent-sm;
  position: relative;
}
</style>
