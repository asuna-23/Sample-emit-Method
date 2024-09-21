<template>
  <div>
    <h1>Form</h1>
    <form @submit.prevent="handleSubmit">
      <div class="mb-3">
        <label for="name" class="form-label">Name</label>
        <input v-model="name" type="text" class="form-control" id="name" required />
      </div>
      <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <input v-model="email" type="email" class="form-control" id="email" required />
      </div>
      <div class="mb-3">
        <label for="phone" class="form-label">Phone</label>
        <input v-model="phone" type="text" class="form-control" id="phone" required />
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return {
      name: '',
      email: '',
      phone: '',
    };
  },
  methods: {
    handleSubmit() {
      const newFriend = {
        name: this.name,
        email: this.email,
        phone: this.phone,
        showDetails: false,
        favorite: false,
      };
      this.$emit('add-friend', newFriend); // Emit the new friend
      this.name = '';
      this.email = '';
      this.phone = '';
    },
  },
};
</script>
