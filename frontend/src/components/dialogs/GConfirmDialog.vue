<!--
SPDX-FileCopyrightText: 2023 SAP SE or an SAP affiliate company and Gardener contributors

SPDX-License-Identifier: Apache-2.0
 -->

<template>
  <g-dialog
    ref="gDialog"
    :confirm-button-text="confirmButtonText"
    :cancel-button-text="cancelButtonText"
    :width="width"
    :confirm-value="confirmValue"
  >
    <template #caption>
      {{ captionText }}
    </template>
    <template #message>
      <!-- eslint-disable-next-line vue/no-v-html -->
      <div v-html="messageHtml" />
    </template>
  </g-dialog>
</template>

<script>
import GDialog from './GDialog.vue'

export default {
  components: {
    GDialog,
  },
  data () {
    return {
      confirmButtonText: undefined,
      cancelButtonText: undefined,
      captionText: undefined,
      messageHtml: undefined,
      width: undefined,
      confirmValue: undefined,
    }
  },
  methods: {
    waitForConfirmation ({ confirmButtonText, cancelButtonText, captionText, messageHtml, width, confirmValue } = {}) {
      this.confirmButtonText = confirmButtonText || 'Confirm'
      this.cancelButtonText = cancelButtonText || 'Cancel'
      this.captionText = captionText || 'Confirm'
      this.messageHtml = messageHtml
      this.width = width || '500'
      this.confirmValue = confirmValue

      return this.$refs.gDialog.confirmWithDialog()
    },
  },
}
</script>
