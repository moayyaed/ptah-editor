<template>
  <div class="b-control-panel" @click.stop="">
    <button class="b-control-panel__close" @click="setControlPanel(false)">
      <icon-base color="#c4c4c4" width="10" height="10" name="close"/>
    </button>
    <component :is="panelName" :builder="builder"/>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

import ThePanelSection from './ThePanelSection'
import ThePanelSlot from './ThePanelSlot'
import ThePanelButton from './ThePanelButton'
import ThePanelSocialSettings from './ThePanelSocialSettings'
import ThePanelSocialStyle from './ThePanelSocialStyle'
import ThePanelText from './ThePanelText'
import ThePanelTimerSettings from './ThePanelTimerSettings'
import ThePanelTimerStyle from './ThePanelTimerStyle'
import ThePanelImage from './ThePanelImage'
import ThePanelAvailablePlatforms from './ThePanelAvailablePlatforms'
import ThePanelRestrictions from './ThePanelRestrictions'
import ThePanelInlineText from './ThePanelInlineText'

export default {
  name: 'TheControlPanel',

  props: {
    builder: {
      type: Object,
      required: true
    }
  },

  computed: {
    ...mapState('Sidebar', [
      'settingObjectType',
      'controlPanel'
    ]),

    panelName () {
      return `ThePanel${this.controlPanel.name}`
    }
  },

  methods: {
    ...mapActions('Sidebar', ['setControlPanel'])
  },

  components: {
    ThePanelSection,
    ThePanelButton,
    ThePanelSocialSettings,
    ThePanelSocialStyle,
    ThePanelText,
    ThePanelTimerSettings,
    ThePanelTimerStyle,
    ThePanelSlot,
    ThePanelAvailablePlatforms,
    ThePanelRestrictions,
    ThePanelInlineText,
    ThePanelImage
  }
}
</script>

<style lang="sass" scoped>
@import '../../../assets/sass/_colors.sass'
@import '../../../assets/sass/_variables.sass'

.b-control-panel
  position: relative
  width: $size-step*9
  height: 100%
  padding: 2.4rem 1.7rem 2.4rem

  display: flex
  flex-direction: column

  background: $white
  box-shadow: 0px 0.4rem 1rem rgba($black, 0.35)

  color: $dark-grey
  font-size: 1.4rem
  letter-spacing: -0.01em

  &__title
    color: $black
    font-size: 2rem
    font-weight: bold

    min-width: 28rem
    margin: 0 0 2.8rem 0
    padding: 0
    &:first-letter
      text-transform: uppercase

  &__close
    position: absolute
    right: 1rem
    top: 2.1rem
    z-index: 10

    padding: 0.6rem 1rem

    border: 0
    background: transparent
    cursor: pointer
</style>