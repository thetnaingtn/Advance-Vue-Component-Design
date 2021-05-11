<template>
  <div>
    <div class="min-h-screen bg-grey-darker p-8">
      <div class="max-w-sm mx-auto">
        <user-settings-form :account-id="accountId"></user-settings-form>
      </div>
    </div>

    <announcement-modal
      @close="showAnnouncement = false"
      :show="showAnnouncement"
    />

    <portal-target name="modals"></portal-target>
  </div>
</template>

<script>
/* eslint-diable */
import UserSettingsForm from "./components/UserSettingsForm.vue"
import AnnouncementModal from "./components/AnnouncementModal"
export default {
  components: {
    UserSettingsForm,
    AnnouncementModal
  },
  data() {
    return {
      accountId: 7,
      showAnnouncement: true
    }
  }
}
</script>

<style src="./assets/css/app.css"/>
