<template>
  <div ref="wrapper" :class=wrapperClass>
    <HiddenFields />
    <Control ref="control" />
    <MenuPortal v-if="appendToBody" ref="portal" />
    <Menu v-else ref="menu" />
  </div>
</template>

<script>
  import treeselectMixin from '@/mixins/treeselectMixin.js'
  import HiddenFields from '@/components/HiddenFields.vue'
  import Control from '@/components/Control.vue'
  import Menu from '@/components/Menu.vue'
  import MenuPortal from '@/components/MenuPortal.vue'

  import {defineComponent} from 'vue';
  export default defineComponent({
    name: 'vue-treeselect',
    mixins: [ treeselectMixin ],
    components:{
      HiddenFields,Control,Menu,MenuPortal
    },

    computed: {
      wrapperClass() {
        return {
          'vue-treeselect': true,
          'vue-treeselect--single': this.single,
          'vue-treeselect--multi': this.multiple,
          'vue-treeselect--searchable': this.searchable,
          'vue-treeselect--disabled': this.disabled,
          'vue-treeselect--focused': this.trigger.isFocused,
          'vue-treeselect--has-value': this.hasValue,
          'vue-treeselect--open': this.menu.isOpen,
          'vue-treeselect--open-above': this.menu.placement === 'top',
          'vue-treeselect--open-below': this.menu.placement === 'bottom',
          'vue-treeselect--branch-nodes-disabled': this.disableBranchNodes,
          'vue-treeselect--append-to-body': this.appendToBody,
        }
      },
    },

    // render() {
    //   return (
    //     <div ref="wrapper" class={this.wrapperClass}>
    //       <HiddenFields />
    //       <Control ref="control" />
    //       {this.appendToBody ? <MenuPortal ref="portal" /> : <Menu ref="menu" />}
    //     </div>
    //   )
    // },
  })
</script>
