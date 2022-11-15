<template>
  <v-card
    flat
    class="pa-3 mt-2"
  >

    <v-card-text>
      <v-form class="multi-col-validation mt-6">
        <v-row>
          <v-col
            cols="12"
          >
            <v-text-field
              v-model="noticeDataLocale.title"
              label="제목"
              dense
              outlined
            ></v-text-field>
          </v-col>

      
          <v-col
            cols="12"
          >
            <v-select
              v-model="noticeDataLocale.status"
              dense
              outlined
              label="카테고리"
              :items="status"
            ></v-select>
          </v-col>


          <v-col cols="12">
            <v-textarea
              v-model="noticeDataLocale.content"
              outlined
              rows="7"
              label="내용"
            ></v-textarea>
          </v-col>

          <v-col cols="12">
            <v-btn
              color="primary"
              class="me-3 mt-4"
            >
              작성 요청
            </v-btn>
            <v-btn
              color="secondary"
              outlined
              class="mt-4"
              type="reset"
              @click.prevent="resetForm"
            >
              취소
            </v-btn>
          </v-col>
        </v-row>
      </v-form>
    </v-card-text>
  </v-card>
</template>

<script>
import { mdiAlertOutline, mdiCloudUploadOutline } from '@mdi/js'
import { ref } from '@vue/composition-api'

export default {
  props: {
    noticeData: {
      type: Object,
      default: () => {},
    },
  },
  setup(props) {
    const status = ['공지사항', '점검예정', '오류수정']
    const noticeDataLocale = ref(JSON.parse(JSON.stringify(props.noticeData)))


    const resetForm = () => {
      noticeDataLocale.value = JSON.parse(JSON.stringify(props.noticeData))
    }

    return {
      status,
      noticeDataLocale,
      resetForm,
      icons: {
        mdiAlertOutline,
        mdiCloudUploadOutline,
      },
    }
  },
}
</script>
