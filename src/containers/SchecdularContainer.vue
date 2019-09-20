<template>
  <div>
    <kendo-scheduler
      v-if="!editWindowProperties.visible"
      id="kendoScheduler"
      class="Scheduler"
      :data-source="eventList"
      :footer="false"
      :selectable="true"
      @add="onAdd"
      @edit="onEdit"
      :snap="true"
    >
      <kendo-scheduler-view :type="'day'" :editable-destroy="false" :event-template="templateDay"></kendo-scheduler-view>
    </kendo-scheduler>
    <schedular-dialog-component :modalProperties="modalProperties" />
    <calender-edit-form-component
      v-if="editWindowProperties.visible"
      :backToCalender="backToCalenderHandler"
    />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import AgEventTemplateComponent from "@/components/templates/AgEventTemplateComponent.vue";
import SchedularDialogComponent from "@/components/dialogs/SchedularDialogComponent.vue";
import CalenderEditFormComponent from "@/components/forms/CalenderEditFormComponent.vue";

@Component({
  components: {
    SchedularDialogComponent,
    CalenderEditFormComponent
  }
})
export default class SchecdularContainer extends Vue {
  modalProperties = {
    visible: false
  };
  editWindowProperties = {
    visible: false
  };

  /**
   * sample event list
   */
  eventList = [
    {
      Id: "1",
      start: new Date(new Date().setHours(1, 30)),
      end: new Date(new Date().setHours(2, 30)),
      title: "appointment 1"
    },
    {
      Id: "2",
      start: new Date(new Date().setHours(2, 30)),
      end: new Date(new Date().setHours(3, 30)),
      title: "appointment 2"
    },
    {
      Id: "3",
      start: new Date(new Date().setHours(3, 30)),
      end: new Date(new Date().setHours(4, 30)),
      title: "appointment 3"
    },
    {
      Id: "4",
      start: new Date(new Date().setHours(4, 30)),
      end: new Date(new Date().setHours(5, 30)),
      title: "appointment 4"
    },
    {
      Id: "5",
      start: new Date(new Date().setHours(6, 30)),
      end: new Date(new Date().setHours(8, 30)),
      title: "appointment 5"
    },
    {
      Id: "6",
      start: new Date(new Date().setHours(8, 30)),
      end: new Date(new Date().setHours(10, 30)),
      title: "appointment 6"
    }
  ];

  /**
   * kendo onadd hanlder
   * @param e
   */
  onAdd(e: any) {
    e.preventDefault();
    this.modalProperties.visible = true;
  }

  /**
   * Kendo onEdit Hanlder
   * @param e
   */
  onEdit(e: any) {
    e.preventDefault();
    this.editWindowProperties.visible = true;
  }

  /**
   * get custom template
   * @param data
   */
  templateDay(data: any) {
    return {
      template: Vue.component(
        AgEventTemplateComponent.name,
        AgEventTemplateComponent
      ),
      templateArgs: data
    };
  }

  backToCalenderHandler() {
    this.editWindowProperties.visible = false;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
