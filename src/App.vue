<template>
  <el-config-provider :locale="elLocale">
  <div id="app">
    <VFormDesigner ref="vfDesignerRef" :global-dsv="globalDsv">
      <!--
      <template #customToolButtons>
        <el-button type="text" @click="doTest">测试btn</el-button>
      </template>
      -->
    </VFormDesigner>
  </div>
  </el-config-provider>
</template>

<script>
import VFormDesigner from './components/form-designer/index.vue'
import enUSLang from 'element-plus/lib/locale/lang/en'

export default {
  name: 'App',
  components: {
    VFormDesigner,
  },
  data() {
    return {
      elLocaleMap: {
        'en-US': enUSLang,
      },

      globalDsv: {
        testApiHost: 'http://www.test.com/api',
        testPort: 8080,
      },

    }
  },
  computed: {
    elLocale() {
      let curLocale = localStorage.getItem('v_form_locale') || 'en-US'
      return this.elLocaleMap[curLocale]
    },

  },
  methods: {
    doTest() {
      let fieldList = this.$refs.vfDesignerRef.getFieldWidgets(null, true)
      console.log('test', fieldList)
    }

  }
}
</script>

<style lang="scss">
  #app {
    height: 100%;
  }
</style>
