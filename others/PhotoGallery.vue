<template>
  <div class="photo-gallery">
    <h2>Photo Gallery</h2>
    <input type="file" @change="uploadFiles" multiple />

    <!-- Display when there are no images -->
    <div v-if="images.length === 0" class="empty-message">
      <p>No photos uploaded yet. Add some memories by clicking the upload button above!</p>
    </div>

    <!-- Display the gallery grid when images are available -->
    <div v-else class="gallery-grid">
      <div v-for="(image, index) in images" :key="index" class="gallery-item">
        <img :src="image" alt="Uploaded photo" />
        <button @click="removeImage(index)">Remove</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const images = ref([]);

// Handle file upload
const uploadFiles = (event) => {
  const files = Array.from(event.target.files);
  files.forEach((file) => {
    // Create a FileReader instance using Vue reactivity
    const reader = new FileReader();
    reader.onload = (e) => {
      images.value.push(e.target.result);
    };
    reader.readAsDataURL(file);
  });
};

// Remove an image from the gallery
const removeImage = (index) => {
  images.value.splice(index, 1);
};
</script>

<style scoped>
.photo-gallery {
  padding: 20px;
}

.empty-message {
  margin-top: 20px;
  text-align: center;
  color: #777;
  font-size: 16px;
  font-style: italic;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 10px;
  margin-top: 20px;
}

.gallery-item {
  position: relative;
  border: 2px solid #ccc;
  border-radius: 8px;
  overflow: hidden;
}

.gallery-item img {
  width: 100%;
  height: auto;
  display: block;
}

.gallery-item button {
  position: absolute;
  top: 5px;
  right: 5px;
  background-color: rgba(255, 0, 0, 0.7);
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>

/*

<template>
  <div class="photo-gallery">
    <h2>Photo Gallery</h2>
    <input type="file" @change="handleFileUpload" multiple />
    
    <!-- Display when there are no images -->
    <div v-if="images.length === 0" class="empty-message">
      <p>No photos uploaded yet. Add some memories by clicking the upload button above!</p>
    </div>
    
    <!-- Display the gallery grid when images are available -->
    <div v-else class="gallery-grid">
      <div v-for="(image, index) in images" :key="index" class="gallery-item">
        <img :src="image" alt="Uploaded photo" />
        <button @click="removeImage(index)">Remove</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PhotoGallery',
  data() {
    return {
      images: [], // Array to store image URLs
    };
  },
  methods: {
    handleFileUpload(event) {
      const files = event.target.files;
      for (let i = 0; i < files.length; i++) {
        const reader = new FileReader();
        reader.onload = (e) => {
          this.images.push(e.target.result);
        };
        reader.readAsDataURL(files[i]);
      }
    },
    removeImage(index) {
      this.images.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.photo-gallery {
  padding: 20px;
}

.empty-message {
  margin-top: 20px;
  text-align: center;
  color: #777;
  font-size: 16px;
  font-style: italic;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 10px;
  margin-top: 20px;
}

.gallery-item {
  position: relative;
  border: 2px solid #ccc;
  border-radius: 8px;
  overflow: hidden;
}

.gallery-item img {
  width: 100%;
  height: auto;
  display: block;
}

.gallery-item button {
  position: absolute;
  top: 5px;
  right: 5px;
  background-color: rgba(255, 0, 0, 0.7);
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>


*/