<template>
  <div class="col-md-8">
    <div class="card">
      <div class="card-header">
        <strong>{{ Comments.length }}</strong> 已評論餐廳
      </div>
      <div class="card-body">
        <a
          href="/restaurants/48"
          v-for="Comment in Comments"
          :key="Comment.RestaurantId"
        >
          <img
            :src="Comment.Restaurant.image"
            width="60"
            height="60"
            class="avatar"
          />
        </a>
      </div>
    </div>
    <br />
    <div class="card">
      <div class="card-header">
        <strong>{{ FavoritedRestaurants.length }}</strong> 收藏的餐廳
      </div>
      <div class="card-body">
        <a
          href="/restaurants/48"
          v-for="FavoritedRestaurant in FavoritedRestaurants"
          :key="FavoritedRestaurant.id"
        >
          <img
            :src="FavoritedRestaurant.image"
            width="60"
            height="60"
            class="avatar"
          />
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    initialComments: {
      type: Array,
      required: true,
    },
    initialFavoritedrestaurants: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      Comments: this.initialComments,
      FavoritedRestaurants: this.initialFavoritedrestaurants,
    };
  },
};
</script>