<script>
import * as types from '@editor/types'
import * as _ from 'lodash-es'
import Seeder from '@editor/seeder'
import defaults from '../../mixins/defaults'
import sectionMedia from '../../mixins/sectionMedia'

const GROUP_NAME = 'FirstScreen'
const NAME = 'FirstScreenFantasy01'
const BG_SECTION = 'url(https://cdn.ptah.pro/prod/5ee8d62d480c4e00018c404d/8d8511f3-770d-431e-9864-f217f2db8cae.jpg)'

const COMPONENTS_2 = [
  {
    name: 'Logo',
    element: types.Logo,
    type: 'image',
    class: 'b-logo-fs',
    label: 'logo'
  },
  {
    name: 'TextElement',
    element: types.Text,
    type: 'text',
    class: 'b-text-fs',
    label: 'text'
  },
  {
    name: 'Button',
    element: types.Button,
    type: 'button',
    class: 'b-button-fs',
    label: 'button'
  }
]

const C_CUSTOM_2 = [
  {
    element: {
      styles: {
        'background-image': 'url("https://cdn.ptah.pro/tst/5ef4948bf835ea00018fb774/be57acdb-9c29-4b1e-8aaa-361e1a8df27b.svg")',
        'background-color': 'rgba(0, 0, 0, 0)',
        'background-repeat': 'no-repeat',
        'background-size': 'contain',
        'width': '500px',
        'height': '121px',
        'margin-top': '25px',
        'margin-bottom': '20px',
        'margin-left': '13px'
      },
      media: {
        'is-mobile': {
          width: '270px',
          height: '100px',
          'margin-top': '25px',
          'margin-rihgt': '0',
          'margin-bottom': '0',
          'margin-left': '0'
        }
      }
    }
  },
  {
    element: {
      text: '<h1>HERE SHOULD BE A LITTLE TEXT ABOUT YOURE GAME</h1>',
      styles: {
        'font-size': '5.6rem',
        'line-height': '1.2',
        'color': '#ffffff',
        'text-align': 'left',
        'margin-top': '25px',
        'margin-bottom': '20px',
        'margin-left': '13px',
        'padding-left': '13px'
      },
      media: {
        'is-mobile': {
          'font-size': '2rem',
          'line-height': '1.4',
          'text-align': 'right',
          'margin-top': '16px',
          'margin-bottom': '16px',
          'margin-left': '20px',
          'margin-right': '8px',
          'padding-left': '80px'
        }
      }
    }
  },
  {
    element: {
      text: '<b>Call to Action</b>',
      styles: {
        'background-color': '#AF2E12',
        'color': '#ffffff',
        'font-size': '2rem',
        'text-align': 'center',
        'width': '240px',
        'height': '64px',
        'border-width': '1px',
        'border-style': 'solid',
        'border-color': '#000000',
        'margin-top': '25px',
        'margin-bottom': '70px',
        'margin-left': '38px'
      },
      pseudo: {
        'hover': {
          'background-color': '#333333 !important',
          'border-width': '1px',
          'border-style': 'solid',
          'border-color': '#000000'
        }
      }
    }
  }
]

const COMPONENTS_3 = [
  {
    name: 'SocialNetworks',
    element: types.SocialNetworks,
    type: 'networks',
    class: 'b-social-networks-fs',
    label: 'Social Networks'
  }
]

const C_CUSTOM_3 = [
  {
    element: {
      styles: {
        'margin-top': '20px'
      },
      socialNetworks: {
        'facebook': {
          name: 'Facebook',
          expand: false,
          visible: true,
          url: ''
        },
        'instagram': {
          name: 'Instagram',
          expand: false,
          visible: true,
          url: ''
        },
        'twitter': {
          name: 'Twitter',
          expand: false,
          visible: true,
          url: ''
        },
        'youtube': {
          name: 'Youtube',
          expand: false,
          visible: true,
          url: ''
        }
      },
      colorFill: {
        color: '#C53314'
      },
      sizeIcons: {
        width: 30
      },
      media: {
        'is-mobile': {
          'margin-top': '20px',
          'margin-left': '13px'
        },
        sizeIcons: {
          width: 20
        }
      }
    }
  }
]

const SCHEMA_CUSTOM = {
  mainStyle: {
    styles: {
      'background-image': BG_SECTION,
      'background-size': 'cover',
      'background-color': '#4A4A4A',
      'background-repeat': 'no-repeat',
      'background-attachment': 'scroll',
      'background-position': '50% 0%',
      'height': '100vh'
    },
    media: {
      'is-mobile': {
        'background-position': '50% 50%'
      }
    }
  },
  container: {
    width: 5,
    minWidth: 2,
    maxWidth: 10,
    grow: ['$sectionData.container2'],
    selfName: '$sectionData.container'
  },
  components2: _.merge({}, C_CUSTOM_2),
  container2: {
    width: 7,
    minWidth: 2,
    maxWidth: 10,
    grow: ['$sectionData.container'],
    selfName: '$sectionData.container2',
    styles: {
      'align-items': 'flex-start'
    },
    media: {
      'is-mobile': {
        'align-items': 'flex-end'
      }
    }
  },
  container3: {
    width: 12,
    media: {
      'is-mobile': {
        'align-items': 'flex-end'
      }
    }
  },
  components3: _.merge({}, C_CUSTOM_3),
  edited: true
}

export default {
  name: NAME,

  group: GROUP_NAME,

  description: 'Fantasy title Maximum main screen',

  mixins: [defaults, sectionMedia],

  cover: '/img/covers/first-screen-fantasy-01.jpg',

  $schema: {
    mainStyle: types.StyleObject,
    container: types.StyleObject,
    container2: types.StyleObject,
    container3: types.StyleObject,
    components: [],
    components2: COMPONENTS_2,
    components3: COMPONENTS_3
  },

  created () {
    if (this.$sectionData.edited === undefined) {
      Seeder.seed(_.merge(this.$sectionData, SCHEMA_CUSTOM))
    }
  }
}
</script>

<template>
  <section
    class="b-first-screen-fantasy-01"
    :class="$sectionData.mainStyle.classes"
    :style="[$sectionData.mainStyle.styles, $sectionData.objVarsMedia]"
    v-styler:section="$sectionData.mainStyle"
  >
    <slot name="menu"/>
    <slot name="video"/>
    <slot name="overlay"/>
    <div class="b-grid">
      <div class="b-grid__row">
        <div class="b-grid__col-m-12" :class="`b-grid__col-${$sectionData.container.width}`">
          <sandbox
            container-path="$sectionData.container"
            components-path="$sectionData.components"
            class="b-sandbox">

            <draggable v-model="$sectionData.components" class="b-draggable-slot b-draggable-slot_100" :style="$sectionData.container.styles" @start="$_drag('components')" @change="$_dragStop">
              <div v-for="(component, index) in $sectionData.components" v-if="$sectionData.components.length !== 0" :key="index">
                <component
                  v-styler:for="{ el: $sectionData.components[index].element, path: `$sectionData.components[${index}].element`, type: $sectionData.components[index].type, label: component.label }"
                  :is="component.name"
                  :href="$sectionData.components[index].element.link.href"
                  :target="$sectionData.components[index].element.link.target"
                  :path="`components[${index}].element`"
                  :style="$sectionData.components[index].element.styles"
                  :class="[$sectionData.components[index].element.classes, $sectionData.components[index].class]"
                  >
                  <div v-html="$sectionData.components[index].element.text"></div>
                </component>
              </div>
            </draggable>
          </sandbox>
        </div>
        <div class="b-grid__col-m-12" :class="`b-grid__col-${$sectionData.container2.width}`">
          <sandbox
              container-path="$sectionData.container2"
              components-path="$sectionData.components2"
               class="b-sandbox">

            <draggable v-model="$sectionData.components2" class="b-draggable-slot b-draggable-slot_100" :style="$sectionData.container2.styles" @start="$_drag('components2')" @change="$_dragStop">
              <div v-for="(component, index) in $sectionData.components2" v-if="$sectionData.components2.length !== 0" :key="index">
                <component
                  v-styler:for="{ el: $sectionData.components2[index].element, path: `$sectionData.components2[${index}].element`, type: $sectionData.components2[index].type, label: component.label }"
                  :is="component.name"
                  :href="$sectionData.components2[index].element.link.href"
                  :target="$sectionData.components2[index].element.link.target"
                  :path="`components2[${index}].element`"
                  :style="$sectionData.components2[index].element.styles"
                  :class="[$sectionData.components2[index].element.classes, $sectionData.components2[index].class]"
                  >
                  <div v-html="$sectionData.components2[index].element.text"></div>
                </component>
              </div>
            </draggable>
          </sandbox>
        </div>
      </div>
      <div class="b-grid__row">
        <div class="b-grid__col-m-12" :class="`b-grid__col-${$sectionData.container3.width}`">
          <sandbox
            container-path="$sectionData.container3"
            components-path="$sectionData.components3"
            class="b-sandbox">

            <draggable v-model="$sectionData.components3" class="b-draggable-slot b-draggable-slot_100" :style="$sectionData.container3.styles" @start="$_drag('components3')" @change="$_dragStop">
              <div v-for="(component, index) in $sectionData.components3" v-if="$sectionData.components3.length !== 0" :key="index">
                <component
                  v-styler:for="{ el: $sectionData.components3[index].element, path: `$sectionData.components3[${index}].element`, type: $sectionData.components3[index].type, label: component.label }"
                  :is="component.name"
                  :href="$sectionData.components3[index].element.link.href"
                  :target="$sectionData.components3[index].element.link.target"
                  :path="`components3[${index}].element`"
                  :style="$sectionData.components3[index].element.styles"
                  :class="[$sectionData.components3[index].element.classes, $sectionData.components3[index].class]"
                  >
                  <div v-html="$sectionData.components3[index].element.text"></div>
                </component>
              </div>
            </draggable>
          </sandbox>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="sass" scoped>
</style>
