<template>
  <div class="col-md-4">
    <div class="card">
      <div class="card-header">
        <strong>{{ Followers.length }}</strong> followings (追蹤者)
      </div>
      <div class="card-body">
        <router-link
          v-for="Follower in Followers"
          :key="Follower.id"
          :to="{ name: 'UserFollower', params: { id: Follower.id } }"
        >
          <img :src="Follower.image" width="60" height="60" class="mr-1 mb-1" />
        </router-link>
      </div>
    </div>
    <br />
    <div class="card">
      <div class="card-header">
        <strong>{{ Followings.length }}</strong> followers (追隨者)
      </div>
      <div class="card-body">
        <router-link
          :to="{
            name: 'UserFollower',
            params: { id: Following.Followship.followingId },
          }"
          v-for="Following in Followings"
          :key="Following.id"
        >
          <img
            :src="Following.image"
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
    initialFollowers: {
      type: Array,
      required: true,
    },
    initialFollowings: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      Followers: this.initialFollowers,
      Followings: this.initialFollowings,
    };
  },
};
</script>