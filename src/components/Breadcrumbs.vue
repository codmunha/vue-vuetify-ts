
<template>
  <v-row no-gutters>
    <v-col :sm="12" :lg="6">
      <h1 style="text-transform: capitalize;">
        <!-- {{ this.$route.name }} -->
        {{ $t(`message.${$route.name}`) }}
      </h1>
    </v-col>
    <v-col :sm="12" :lg="6">
      <v-breadcrumbs :items="breadcrumbs" class="breadcrumbs-main">
        <template v-slot:item="{ item }">
          <v-breadcrumbs-item
            :href="item.href"
            :disabled="item.disabled">
            <v-icon small left v-if="item.href == '/'">{{ 'mdi-home' }}</v-icon>
            <!-- eslint-disable vue/no-parsing-error -->
            {{ $t(`message.${item.text}`) }}
            <!-- {{ item.text.toUpperCase() }} -->
          </v-breadcrumbs-item>
        </template>
      </v-breadcrumbs>
    </v-col>
  </v-row>
</template>

<style lang="scss">
.breadcrumbs-main {
  float: right;
}
</style>

<script lang="ts">
import { Component, Vue, Watch } from 'vue-property-decorator'
@Component({
  name: 'Breadcrumbs'
})
export default class Breadcrumbs extends Vue {
  _breadcrumbs: Array<any>
  constructor() {
    super()
    this._breadcrumbs = []
  }
  get breadcrumbs() {
    this._breadcrumbs = this.$route.meta.breadcrumb
    return this._breadcrumbs
  }
}

</script>
