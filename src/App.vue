<template>
  <div id="app">
    <div class="form-group">
      <input v-model="experience" class="input" type="text" placeholder="Deneyim ekleyin..." />
      <button class="btn" @click="addExperience">Ekle</button>
    </div>
    <TimeLine :timelineData="timelineData" />
  </div>
</template>

<script>
import TimeLine from "./components/TimeLine";

export default {
  name: "App",
  components: {
    TimeLine,
  },
  data() {
    return {
      experience: "",
      timelineData: []
    }
  },
  methods: {
    addExperience() {
      const payload = {
        id: this.timelineData.length + 1,
        date: new Date(),
        desc: this.experience
      };

      this.timelineData.push(payload);
    }
  }
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #000;
  color: #fff;
  height: 100vh;
  width: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
}
.form-group {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 30px;
  & .input {
    height: 40px;
    width: 100%;
    padding: 3px 5px;
  }
  & .btn {
    height: 40px;
    width: 80px;
    border: none;
    border-radius: 5px;
  }
}
</style>
