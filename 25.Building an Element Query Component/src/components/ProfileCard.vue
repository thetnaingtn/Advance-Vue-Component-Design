<template>
  <with-dimension>
    <div
      slot-scope="{ width }"
      class="profile-card"
      :class="{ 'profile-card--horizontal': width >= 400 }"
    >
      <img
        class="profile-card-image"
        src="https://cdn4.iconfinder.com/data/icons/avatars-xmas-giveaway/128/batman_hero_avatar_comics-512.png"
        alt=""
      />
      <div class="profile-card-meta">
        <div class="mb-4">
          <p class="text-xl leading-tight">Toby Flenderson</p>
          <p class="text-sm leading-tight text-grey-dark">
            Human Resources at Dunder Mifflin
          </p>
        </div>
        <div>
          <button class="btn btn-sm btn-pill btn-indigo-outline">
            Message
          </button>
        </div>
      </div>
    </div>
  </with-dimension>
</template>

<script>
import WithDimension from "./WithDimension";

export default {
  components: {
    WithDimension,
  },
};
</script>

<style scoped>
</style>