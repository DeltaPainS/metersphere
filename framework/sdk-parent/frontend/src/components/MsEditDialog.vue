<template>
  <el-dialog :close-on-click-modal="closeOnClickModal"
             :title="title"
             :width="width"
             :visible="visible"
             destroy-on-close
             :fullscreen="fullScreen"
             :append-to-body="appendToBody"
             @close="handleClose">

    <slot name="header"></slot>

    <slot></slot>

    <template v-slot:footer>
      <slot name="footer">
        <div v-if="withFooter" class="dialog-footer">
          <ms-dialog-footer
            @cancel="handleCancel"
            @confirm="handleConfirm"/>
        </div>
      </slot>
    </template>

  </el-dialog>
</template>

<script>
import MsDialogFooter from "./MsDialogFooter";
export default {
  name: "MsEditDialog",
  components: {MsDialogFooter},
  props: {
    title: {
      type: String,
      default() {
        return 'title';
      }
    },
    visible: {
      type: Boolean,
      default() {
        return false;
      }
    },
    appendToBody: {
      type: Boolean,
      default() {
        return false;
      }
    },
    width: {
      type: String,
      default() {
        return "50%";
      }
    },
    withFooter: {
      type: Boolean,
      default() {
        return true;
      }
    },
    closeOnClickModal: {
      type: Boolean,
      default: false
    },
    fullScreen: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleConfirm() {
      this.$emit('confirm');
    },
    handleCancel() {
      this.handleClose();
      this.$emit('cancel');
    },
    handleClose() {
      this.$emit('update:visible', false);
      this.$emit('close');
    },
  }
};
</script>

<style scoped>

</style>
