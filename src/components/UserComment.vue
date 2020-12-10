<template>
  <div class="col-md-8">
    <div class="card">
      <div class="card-header">
        <strong>{{ Comments.length }}</strong> 已評論餐廳
      </div>
      <div class="card-body">
        <router-link
          v-for="Comment in Comments"
          :key="Comment.id"
          :to="{ name: 'UserComment', params: { id: Comment.Restaurant.id } }"
        >
          <img
            :src="Comment.Restaurant.image"
            width="60"
            height="60"
            class="mr-1 mb-1"
          />
        </router-link>
      </div>
    </div>
    <br />
    <div class="card">
      <div class="card-header">
        <strong>{{ FavoritedRestaurants.length }}</strong> 收藏的餐廳
      </div>
      <div class="card-body">
        <router-link
          v-for="FavoritedRestaurant in FavoritedRestaurants"
          :key="FavoritedRestaurant.id"
          :to="{
            name: 'UserComment',
            params: { id: FavoritedRestaurant.Favorite.RestaurantId },
          }"
        >
          <img
            :src="FavoritedRestaurant.image"
            width="60"
            height="60"
            class="mr-1 mb-1"
          />
        </router-link>
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