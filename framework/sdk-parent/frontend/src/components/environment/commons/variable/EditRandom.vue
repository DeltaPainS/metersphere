<template>
  <el-form :model="editData" label-position="right" label-width="80px" size="small" ref="form5" :rules="rules">
    <el-form-item :label="$t('api_test.variable_name')" prop="name">
      <el-input v-model="editData.name" :placeholder="$t('api_test.variable_name')"></el-input>
    </el-form-item>

    <el-form-item :label="$t('commons.description')" prop="description">
      <el-input class="ms-http-textarea"
                v-model="editData.description"
                type="textarea"
                :disabled="disabled"
                :autosize="{ minRows: 2, maxRows: 10}"
                :rows="2" size="small"/>
    </el-form-item>

    <el-form-item :label="$t('schema.minimum')" prop="minNumber">
      <el-input :disabled="disabled" size="small" v-model="editData.minNumber" placeholder="0"/>
    </el-form-item>
    <el-form-item :label="$t('schema.maximum')" prop="maxNumber">
      <el-input :disabled="disabled" size="small" v-model="editData.maxNumber" placeholder="10"/>
    </el-form-item>
    <el-form-item :label="$t('variables.format')" prop="value">
      <el-input :disabled="disabled" v-model="editData.value" :placeholder="$t('variables.counter_info')"></el-input>
    </el-form-item>
  </el-form>
</template>

<script>

export default {
  name: "MsEditRandom",
  components: {},
  props: {
    editData: {},
  },
  computed: {
    disabled() {
      return !(this.editData.name && this.editData.name !== "");
    }
  },
  data() {
    return {
      rules: {
        name: [
          {required: true, message: this.$t('test_track.variable_name'), trigger: 'blur'},
        ],
      },
    }
  },
}
</script>

<style scoped>

</style>
