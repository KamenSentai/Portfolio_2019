<template lang="pug">
.grid
  .grid_card(v-for="(card, index) in cards" :key="index")
    .grid_frame
      a(
        data-mouse="is-reduced"
        :title="card.name"
        :href="card.demo !== '' ? card.demo : card.code"
        target="_blank"
        rel="noopener"
      )
        img.grid_image(
          data-mouse="is-reduced"
          :src="require(`../assets/images/${card.slug}/0.png`)"
          :alt="card.name"
        )
      .grid_mask.grid_mask-top(:data-theme="$store.state.theme.color")
      .grid_mask.grid_mask-bottom(:data-theme="$store.state.theme.color")
      .grid_mask.grid_mask-left(:data-theme="$store.state.theme.color")
      .grid_mask.grid_mask-right(:data-theme="$store.state.theme.color")
    h2.grid_title {{ card.name }}
    .grid_links
      push.grid_link(
        v-if="card.code !== ''"
        :isExternal="true"
        :isTexted="true"
        title="View code"
        :href="card.code"
        target="_blank"
      )
      push.grid_link(
        v-if="card.demo !== ''"
        :isExternal="true"
        :isTexted="true"
        title="View demo"
        :href="card.demo"
        target="_blank"
      )
</template>

<script>
import Push from './push'

export default {
  props: [
    'url',
    'cards'
  ],
  components: {
    'push': Push
  }
}
</script>

<style lang="stylus" scoped>
@import '~assets/styles/tools/app'

.grid
  display flex
  justify-content space-between
  flex-wrap wrap
  margin 0 50px
  width 100%

  &_card
    display flex
    flex-direction column
    align-items center
    width calc(50% - 50px * 2)
    margin 50px
    margin-bottom 100px
    overflow hidden

    @media (max-width 750px)
      width 100%

  &_frame
    position relative
    display flex
    justify-content center
    align-items center
    width 100%
    height auto
    background-color $black
    overflow hidden

  &_mask
    position absolute
    width 100%
    height 100%
    pointer-events none
    transition background-color 1s $cubic 2s

    &[data-theme="black"]
      background-color $black

    &[data-theme="white"]
      background-color $white

    &-top
      bottom 100%
      border-bottom 2px solid $white

    &-bottom
      top 100%
      border-top 2px solid $white

    &-left
      right 100%

    &-right
      left 100%

  &_image
    width 100%
    height auto
    border 2px solid $white
    transition transform 1s $cubic
    will-change transform

    &:hover
      transform scale(.875)

  &_title
    margin 50px 0
    font-size 7.5rem
    font-weight 700
    text-align center

    @media (max-width 500px)
      font-size 5rem

  &_links
    display flex
    justify-content space-evenly
    width 100%

  &_link
    font-size 3.75rem
    text-transform uppercase
</style>