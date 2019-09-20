<template>
  <a-modal
    v-model="modalProperties.visible"
    onOk="okHandler"
    :maskClosable="true"
    :width="450"
  >
 <p>Hello Im new appointment window</p>
  </a-modal>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import moment from 'moment';

@Component({})
export default class SchedularDialogComponent extends Vue {
@Prop({})
modalProperties!:any;

okHandler(){
    console.log("Ok...");
}
}
</script>
<style lang="scss">

</style>
