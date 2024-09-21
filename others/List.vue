<template>
  <div class="friend-list">
    <h2>List</h2>
    <div v-if="friends.length === 0" class="no-friends">
      <p>No friends added yet. Please add some friends!</p>
    </div>
    <div v-for="(friend, index) in friends" :key="index" class="friend-container">
      <div class="friend-header">
        <span class="friend-name">
          {{ friend.name }} 
          <span v-if="friend.favorite" class="favorite-icon">
            <i class="bi bi-star-fill"></i>(Favorite)
          </span>
        </span>
        <div>
          <button class="toggle-details-btn" @click="toggleDetails(index)">
            <i :class="friend.showDetails ? 'bi bi-eye-slash' : 'bi bi-eye'"></i>
          </button>
          <button class="favorite-btn" @click="toggleFavorite(index)">
            <i :class="friend.favorite ? 'bi bi-star-fill' : 'bi bi-star'"></i>
          </button>
          <button class="remove-btn" @click="removeFriend(index)">
            <i class="bi bi-trash"></i>
          </button>
        </div>
      </div>
      <div v-if="friend.showDetails" class="friend-details">
        <p><strong>Email:</strong> {{ friend.email }}</p>
        <p><strong>Phone:</strong> {{ friend.phone }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'List',
  props: {
    friends: {
      type: Array,
      required: true,
    },
  },
  methods: {
    toggleDetails(index) {
      this.friends[index].showDetails = !this.friends[index].showDetails;
    },
    removeFriend(index) {
      this.$emit('remove-friend', index);
    },
    toggleFavorite(index) {
      this.friends[index].favorite = !this.friends[index].favorite;
    },
  },
};
</script>

<style scoped>
.friend-list {
  padding: 20px;
}

.no-friends {
  color: #888; /* Optional styling for the no friends message */
  text-align: center;
  margin: 20px 0;
}

.friend-container {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 10px;
  margin-bottom: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.friend-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.friend-name {
  font-weight: bold;
}

.favorite-icon {
  color: gold;
  margin-left: 5px;
}

.toggle-details-btn, .favorite-btn, .remove-btn {
  margin-left: 5px;
  background: none;
  border: none;
  cursor: pointer;
  font-size: 18px; /* Adjust size as needed */
}

.toggle-details-btn:hover, .favorite-btn:hover, .remove-btn:hover {
  color: #007bff; /* Change color on hover if desired */
}

.friend-details {
  margin-top: 10px;
  padding-left: 10px;
  color: #555;
}
</style>
