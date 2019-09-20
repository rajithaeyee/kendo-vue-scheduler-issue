<template>
  <div>
    <a-button type="primary" @click="backToCalender">Back</a-button>
      <h1>I'm the edit window</h1>
      <span>I have some other data here which are fetched from server</span>
 </div>

</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component({})
export default class CalenderEditFormComponent extends Vue {
@Prop({})
backToCalender!:Function;
}
</script>

<style lang="scss">

</style>
