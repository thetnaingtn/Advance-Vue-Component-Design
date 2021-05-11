<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="text-center p-8 my-8">
      <primary-button>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
          <path d="M13 8V2H7v6H2l8 8 8-8h-5zM0 18h20v2H0v-2z" />
        </svg>
        Download
      </primary-button>
      <div class="max-w-xs mx-auto mb-8">
        <media-card>
          <img
            slot="image"
            src="https://images.unsplash.com/photo-1495835788122-ca48931258be?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=acc48b0187b28f7a221362b843f15755&auto=format&fit=crop&w=3450&q=80"
            alt=""
          />
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Officia
            eos accusantium minima architecto natus sequi quisquam incidunt
            dolorem, adipisci accusamus facere dicta magni, qui consectetur,
            omnis quis, voluptas tempore quo!
          </p>
          <template slot="heading"> </template>
        </media-card>
      </div>
    </div>
  </div>
</template>

<script>
import PrimaryButton from "./components/PrimaryButton";
import MediaCard from "./components/MediaCard";
export default {
  name: "App",
  components: {
    PrimaryButton,
    MediaCard,
  },
};
</script>

<style>
@import "./assets/css/app.css";
</style>
