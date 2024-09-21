<template>
  <div>
    <button @click="showForm">Show Registration Form</button>
    <button @click="showFriends">Show Friend List</button>

    <registration-form v-if="isFormVisible"></registration-form>
    <friend-list v-if="!isFormVisible"></friend-list>
  </div>
</template>

<script>
import RegistrationForm from '../components/pages/RegistrationForm.vue';
import FriendList from '../components/pages/FriendList.vue';

export default {
  components: {
    RegistrationForm,
    FriendList,
  },
  data() {
    return {
      isFormVisible: true, // Initially show the Registration Form
    };
  },
  methods: {
    showForm() {
      this.isFormVisible = true;
    },
    showFriends() {
      this.isFormVisible = false;
    },
  },
};
</script>

/****Sidebar Nav ****/
/*

//Sidebar.vue
<template>
  <div class="sidebar">
    <h2>Navigation</h2>
    <button @click="showForm">Registration Form</button>
    <button @click="showFriends">Friend List</button>
  </div>
</template>

<script>
export default {
  methods: {
    showForm() {
      this.$emit('change-view', 'form');
    },
    showFriends() {
      this.$emit('change-view', 'friends');
    },
  },
};
</script>

<style>
.sidebar {
  width: 200px;
  background-color: #f8f9fa;
  padding: 15px;
  box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
}
</style>


//HomePage.vue

<template>
  <div class="home-view">
    <sidebar @change-view="changeView"></sidebar>
    <div class="content">
      <registration-form v-if="currentView === 'form'"></registration-form>
      <friend-list v-if="currentView === 'friends'"></friend-list>
    </div>
  </div>
</template>

<script>
import Sidebar from '../components/Sidebar.vue';
import RegistrationForm from '../components/pages/RegistrationForm.vue';
import FriendList from '../components/pages/FriendList.vue';

export default {
  components: {
    Sidebar,
    RegistrationForm,
    FriendList,
  },
  data() {
    return {
      currentView: 'form', // Default view is the Registration Form
    };
  },
  methods: {
    changeView(view) {
      this.currentView = view;
    },
  },
};
</script>

<style>
.home-view {
  display: flex;
}
.content {
  margin-left: 20px; /* Space between sidebar and content */
  flex: 1; /* Allow the content to take remaining space */
}
</style>

*/