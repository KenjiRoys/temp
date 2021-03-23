<template>
    <div id="app">
      <nav>
        <p><b>SOMECOMPANY</b></p>
        <div>
          <button @click='lang = "En"'>ENG</button>
          <button @click='lang = "Ru"'>RU</button>
          <button @click='lang = "Uz"'>UZB</button>
        </div>
      </nav>
      <hr>
      <h1>{{ translated.header }}</h1>
      <p>{{ translated.text }}</p>
      <div class="slider">
        <button @click='prevImage()'>next</button>
        <button @click='nextImage()'>prev</button>
        <br>
        <img v-if="imageIndex == 0" src="https://bigpicture.ru/wp-content/uploads/2015/11/nophotoshop29-800x532.jpg" alt="">
        <img v-if="imageIndex == 1" src="https://news.liga.net/images/general/2019/09/11/20190911155211-5324.jpg?v=1568211567" alt="">
        <img v-if="imageIndex == 2" src="https://filedn.com/ltOdFv1aqz1YIFhf4gTY8D7/ingus-info/BLOGS/Photography-stocks3/stock-photography-slider.jpg" alt="">
      </div>
    </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return{
      lang: 'En',
      imageIndex: 0,
      responce: {
        header: {
          En: "We are SOMECOMPANY",
          Ru: "Мы - SOMECOMPANY",
          Uz: "Biz - SOMECOMPANY"
        },
        text:{
          En: "And we dome crazy stuff little managment or smth.",
          Ru: "И мы делаем нереальные вещи по типу менеджмента или что то там еще.",
          Uz: "Va biz tasavurga sig'maydigan narsalar bilan shug'ulanamiz, masalan menedjment."
        }
      }
    }
  },
  methods:{
    nextImage(){
      if(this.imageIndex < 2)
        this.imageIndex++;
      else
        this.imageIndex = 0;
    },
    prevImage(){
      if(this.imageIndex > 0)
        this.imageIndex--;
      else
        this.imageIndex = 2;
    }
  },
  computed: {
    translated(){
      let temp = Object.assign({}, this.responce);
      temp.header = temp.header[this.lang];
      temp.text = temp.text[this.lang];  
      return temp;
    }
  }
}
</script>

<style>
.slider > img{
  width: 500px;
  height: 500px;
}
#app{
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  color:#2c3e50;
}
nav{
  display: flex;
  justify-content: space-around;
  align-items: center;
}
</style>
