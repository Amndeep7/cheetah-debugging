/*
  When you click on a header in order to do a 'check' event, sometimes the other headers aren't
  updated as well.  The most reproducible case I can come up with is below.  This example generates
  a single column of data with three headers consisting of the title, the sum of the data, and the
  minimum of the data.  When you click on the title header, the min header is not updated until you
  hover over either the sum or min headers.  Furthermore, when you click on the min header and then
  click on the title header, the min header is not updated until you hover over the sum or
  min headers.  Scrolling also causes the updates to occur.
  */
<template>
  <div>
    <div>Cheetah header test</div>
    <div class="wrapper">
      <c-grid ref="grid" :data="data">
        <template slot="layout-header">
          <c-grid-layout-row>
            <c-grid-header :width="200" :header-field="'asdf'" :header-action="'check'" @changed-header-value="onChange">
              {{'title ' + 'asdf'}}
            </c-grid-header>
          </c-grid-layout-row>
          <c-grid-layout-row>
            <c-grid-header :width="200" :header-field="'asdf'" :header-action="'check'" @changed-header-value="onChange">
              {{'sum ' + data.reduce((acc,cur) => acc + cur['asdf'], 0)}}
            </c-grid-header>
          </c-grid-layout-row>
          <c-grid-layout-row>
            <c-grid-header :width="200" :header-field="'asdf'" :header-action="'check'" @changed-header-value="onChange">
              {{'min ' + Math.min(...(data.map(d=>d.asdf)))}}
            </c-grid-header>
          </c-grid-layout-row>
        </template>
        <template slot="layout-body">
          <c-grid-layout-row>
            <c-grid-column :field="'asdf'" :width="200"/>
          </c-grid-layout-row>
        </template>
      </c-grid>
    </div>
  </div>
</template>

<script>
// eslint-disable
import * as cGridAll from 'vue-cheetah-grid'

export default {
  name: 'App',
  components: {
    ...cGridAll,
  },
  data() {
    return {
      data: (new Array(10)).fill(0).map(i => ({ 'asdf': Math.random() })),
    }
  },
  methods: {
    onChange() {
      this.data = (new Array(10)).fill(0).map(i => ({ 'asdf': Math.random() }));
    },
  },
}
</script>

<style>
.wrapper {
  width: 250px;
  height: 350px;
}
</style>
