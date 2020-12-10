<template>
  <div class="card mb-3">
    <div class="row no-gutters">
      <div class="col-md-4">
        <img :src="User.image" width="300px" height="300px" />
      </div>
      <div class="col-md-8">
        <div class="card-body">
          <h5 class="card-title">{{ User.name }}</h5>
          <p class="card-text">{{ User.email }}</p>
          <ul class="list-unstyled list-inline">
            <li>
              <strong>{{ Comments.length }}</strong> 已評論餐廳
            </li>
            <li>
              <strong>{{ FavoritedRestaurants.length }}</strong>
              收藏的餐廳
            </li>
            <li>
              <strong>{{ Followers.length }}</strong> followings (追蹤者)
            </li>
            <li>
              <strong>{{ Followings.length }}</strong> followers (追隨者)
            </li>
          </ul>
          <p>
            <a href="/users/1/edit"
              ><button
                type="submit"
                class="btn btn-primary"
                v-if="initialisfollowed"
              >
                edit
              </button></a
            >
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    initialUser: {
      type: Object,
      required: true,
    },
    initialComments: {
      type: Array,
      required: true,
    },
    initialFavoritedrestaurants: {
      type: Array,
      required: true,
    },
    initialFollowers: {
      type: Array,
      required: true,
    },
    initialFollowings: {
      type: Array,
      required: true,
    },
    initialIsfollowed: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      User: this.initialUser,
      Comments: this.initialComments,
      FavoritedRestaurants: this.initialFavoritedrestaurants,
      Followers: this.initialFollowers,
      Followings: this.initialFollowings,
      initialisfollowed: this.initialIsfollowed,
    };
  },
  methods: {
    addFollowing() {
      this.User = {
        ...this.Followings, // 保留餐廳內原有資料
        isFavorited: true,
      };
    },
    deleteFollowing() {
      this.restaurant = {
        ...this.Followings, // 保留餐廳內原有資料
        isFavorited: false,
      };
    },
  },
};
</script>