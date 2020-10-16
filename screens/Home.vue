<template>
  <view class="container">
    <view class="statusbar" />

    <view class="efe">
      <button title="camaraaa" @press="tomarFoto"></button>
      <image class="test" :source="{ uri: fotomeme }" />
    </view>

    <view class="efe">
      <button title="videooo" @press="tomarVideo"></button>
      <video class="test" :source="{ uri: videomeme }" useNativeControls resizeMode="contain" />
    </view>
  </view>
</template>

<script>
import { Video } from "expo-av";
export default {
  data() {
    return {
      fotomeme:
        "https://i.pinimg.com/originals/d6/fe/9b/d6fe9baa42405280bb6c6b8f2a2f8b03.jpg",
      videomeme:
        "https://drive.google.com/uc?id=159pweJhwB1Uv_awFpS4IFFEJdMUr-3w0&export=download"
    };
  },
  props: {
    navigation: {
      type: Object
    }
  },
  methods: {
    tomarFoto() {
      this.navigation.navigate("Camara", {
        onGoBack: this.refresh,
        tipo: "Foto"
      });
    },
    tomarVideo() {
      this.navigation.navigate("Camara", {
        onGoBack: this.refresh,
        tipo: "Video"
      });
    },
    refresh(data, tipo) {
      tipo == "Foto" ? (this.fotomeme = data) : (this.videomeme = data);
    }
  },
  components: { Video }
};
</script>

<style>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
}
.statusbar {
  background-color: white;
  /* height: 110; */
  height: 20;
}
.efe {
  padding: 10;
  
}
.test {
  width: 300;
  height: 300;
}
</style>
