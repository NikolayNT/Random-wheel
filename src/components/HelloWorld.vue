<template>
  <!--<svg viewBox="0 0 200 200" class="pie">
    <path id="first"></path>
    <path id="second"></path>
  </svg>-->
  <div class="parent-canvas" :style="{ 'width': canvasObj.width + 'px', 'height': canvasObj.height + 'px' }">
    <canvas id="canvas" :width="this.canvasObj.width" :height="this.canvasObj.height" class="canvas"></canvas>
    <img src="../../src/img/blue-arrow-23.png" class="arrow">
    <p class="result-text">Рекомендовано развить: {{ result }}</p>
    <div class="parameters">
      <h1 class="title__text">Компетенции для развития</h1>
      <div class="slider-blok">
        <input id="first" type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="firstMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="first" />
        <p class="slider-mean">{{ firstMean }}</p>
      </div>
      <div class="slider-blok">
        <input id="second" type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="secondMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="second" />
        <p class="slider-mean">{{ secondMean }}</p>
      </div>
      <div class="slider-blok">
        <input id="three" type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="threeMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="three" />
        <p class="slider-mean">{{ threeMean }}</p>
      </div>
      <div class="slider-blok">
        <input type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="threeMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="three" />
        <p class="slider-mean">{{ threeMean }}</p>
      </div>
      <div class="slider-blok">
        <input type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="threeMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="three" />
        <p class="slider-mean">{{ threeMean }}</p>
      </div>
      <div class="slider-blok">
        <input type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="threeMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="three" />
        <p class="slider-mean">{{ threeMean }}</p>
      </div>
      <div class="slider-blok">
        <input type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="threeMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="three" />
        <p class="slider-mean">{{ threeMean }}</p>
      </div>
      <div class="slider-blok">
        <input type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="threeMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="three" />
        <p class="slider-mean">{{ threeMean }}</p>
      </div>
      <div class="slider-blok">
        <input type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="threeMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="three" />
        <p class="slider-mean">{{ threeMean }}</p>
      </div>
      <div class="slider-blok">
        <input type="text" class="slider-input" />
        <input @mousemove="changeAll(), draw()" @click="changeAll(), draw()" v-model="threeMean" type="range"
          :min="minWeight" :max="maxWeight" step="1" class="three" />
        <p class="slider-mean">{{ threeMean }}</p>
      </div>
      <button @click="twist()" class="button">Получить рекомендацию</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data() {
    return {
      sliderValue: '',
      secondValue: '',
      threeValue: '',
      firstMean: 50,
      secondMean: 50,
      threeMean: 50,
      rotate: 0,
      canvasObj: {
        "width": 470,
        "height": 470,
      },
      maxWeight: 100,
      minWeight: 0,
      result: '',
    }
  },
  mounted() {
    this.$nextTick(function () {
      
      this.sliderValue = 50;
      this.secondValue = 50;
      this.threeValue = 50;

      this.changeAll();
      this.draw();
    })
  },
  methods: {

    /*getCoordinateEndPoint(persent) {
      const degrees = persent * 3.6;
      console.log(degrees);
      console.log(Math.cos(degrees * Math.PI / 180));
      const coordinatOne = 100 - (Math.cos(degrees * Math.PI / 180) * 90)
      const coordinatTwo = 100 - (Math.sin(degrees * Math.PI / 180) * 90)
      console.log({ "one": coordinatOne.toFixed(3), "two": coordinatTwo.toFixed(3) });
      return { "one": coordinatOne.toFixed(3), "two": coordinatTwo.toFixed(3) };
    },

    setCoordinates(sectorId, sectorPen) {
      const sector = document.getElementById(sectorId);
      console.log(sectorId)
      console.log(sector)
      sector.setAttribute('d', sectorPen);
    },*/

    /*changeArea(sectorId, persent) {
      console.log("процент первый" + persent);
      const coordinateObj = this.getCoordinateEndPoint(persent);
      let typeArc = 0;
      if (persent > 49)
        typeArc = 1;

      const coordinatString = "M100,100 L10,100 A90,90 0 " + typeArc + ",1 " + coordinateObj.one + "," + coordinateObj.two + " Z"
      this.setCoordinates(sectorId, coordinatString)
    },

    changeAreaTwo(sectorId, persent, startPoint, startPersent) {
      console.log("процент секонд" + persent);
      console.log(Number(startPersent) + Number(persent));
      const coordinateObj = this.getCoordinateEndPoint(Number(startPersent) + Number(persent));
      let typeArc = 0;
      if (persent > 49)
        typeArc = 1;

      const coordinatString = "M100,100 L" + startPoint.one + "," + startPoint.two + " A90,90 0 " + typeArc + ",1 " + coordinateObj.one + "," + coordinateObj.two + " Z"
      this.setCoordinates(sectorId, coordinatString)
    },*/

    changeAll() {
      const sumWeight = Number(this.firstMean) + Number(this.secondMean) + Number(this.threeMean);
      this.sliderValue = this.firstMean * 100 / sumWeight;
      this.secondValue = this.secondMean * 100 / sumWeight;
      this.threeValue = this.threeMean * 100 / sumWeight;
    },

    draw() {
      const circle = {
        "centerX": this.canvasObj.height / 2,
        "centerY": this.canvasObj.width / 2,
        "radius": this.canvasObj.width / 2 - 5,
        "border": 3,
      }

      const startPoint = Number(this.sliderValue);
      const endPoint = startPoint + Number(this.secondValue);
      const endPointThree = endPoint + Number(this.threeValue);

      const canvas = document.getElementById('canvas');
      const ctx = canvas.getContext('2d');
      ctx.clearRect(0, 0, this.canvasObj.width, this.canvasObj.height);

      ctx.beginPath();
      ctx.lineWidth = circle.border;
      ctx.moveTo(circle.centerX, circle.centerY);
      ctx.arc(circle.centerX, circle.centerY, circle.radius, 0, startPoint * 3.6 * Math.PI / 180, false);
      ctx.lineTo(circle.centerX, circle.centerY);
      ctx.fillStyle = 'rgb(0,255,0)';
      ctx.fill();
      ctx.stroke();


      ctx.beginPath();
      ctx.lineWidth = circle.border;
      ctx.moveTo(circle.centerX, circle.centerY);
      ctx.arc(circle.centerX, circle.centerY, circle.radius, startPoint * 3.6 * Math.PI / 180, (endPoint) * 3.6 * Math.PI / 180, false);
      ctx.lineTo(circle.centerX, circle.centerY);
      ctx.fillStyle = '#ff0000';
      ctx.fill();
      ctx.stroke();

      ctx.beginPath();
      ctx.lineWidth = circle.border;
      ctx.moveTo(circle.centerX, circle.centerY);
      ctx.arc(circle.centerX, circle.centerY, circle.radius, endPoint * 3.6 * Math.PI / 180, endPointThree * 3.6 * Math.PI / 180, false);
      ctx.lineTo(circle.centerX, circle.centerY);
      ctx.fillStyle = '#0000ff';
      ctx.fill();
      ctx.stroke();

    },

    mouseMove(e) {
      const getCursorPosition = (canvas, event) => {
        const rect = canvas.getBoundingClientRect()
        const x = event.clientX - rect.left
        const y = event.clientY - rect.top
        console.log("x: " + x + " y: " + y)
      }
      const canvas = document.querySelector('canvas')
      getCursorPosition(canvas, e);
    },

    getRGBcanvas(x, y) {
      const canvas = document.querySelector('.canvas')
      const ctx = canvas.getContext('2d');
      let ctxGet = ctx.getImageData(x, y, 1, 1);
      let red = ctxGet.data[0];
      let green = ctxGet.data[1];
      let blue = ctxGet.data[2];
      //let alpha = ctxGet.data[3];
      return red + " " + green + " " + blue;
    },

    win() {
      console.log('Координата')
      const startY = this.canvasObj.height / 2;
      const startX = this.canvasObj.width / 2 + this.canvasObj.width / 2 - 5;
      console.log(startX)
      console.log(startY)
      console.log(this.getRGBcanvas(startX - 5, startY + 5));

      let ooo = Number(this.canvasObj.width) / 2 - 5 - 7
      console.log('Радиус: ' + ooo);
      console.log('x: ' + this.canvasObj.width / 2);
      console.log('y: ' + this.canvasObj.width / 2);

      let x = ooo * Math.cos(14 * 3.6 * Math.PI / 180) + this.canvasObj.width / 2;
      let y = ooo * Math.sin(14 * 3.6 * Math.PI / 180) + this.canvasObj.width / 2;

      console.log('xnew: ' + x);
      console.log('ynew: ' + y);

      /*ctx.beginPath();
      ctx.lineWidth = 1;
      ctx.moveTo(x, y);
      ctx.arc(x, y, this.canvasObj.width  / 2 - 5 - 7, 0, 14 * 3.6 * Math.PI / 180, false);
      ctx.lineTo(x, y);
      ctx.fillStyle = 'rgb(0,255,0)';
      ctx.fill();
      ctx.stroke();*/

      console.log(this.getRGBcanvas(x, y));

      console.log((this.rotate - Math.floor(this.rotate / 360, 0) * 360))

      let xooo = ooo * Math.cos(((14 * 3.6) - ((this.rotate - Math.floor(this.rotate / 360, 0) * 360))) * Math.PI / 180) + this.canvasObj.width / 2;
      let yooo = ooo * Math.sin(((14 * 3.6) - ((this.rotate - Math.floor(this.rotate / 360, 0) * 360))) * Math.PI / 180) + this.canvasObj.width / 2;


      console.log('xnewooo: ' + xooo);
      console.log('ynewooo: ' + yooo);

      console.log(this.getRGBcanvas(xooo, yooo));

      if (this.getRGBcanvas(xooo, yooo) === '0 255 0') {
        this.result = document.getElementById("first").value
        //alert(document.getElementById("first").value)
      }
      if (this.getRGBcanvas(xooo, yooo) === '255 0 0') {
        this.result = document.getElementById("second").value
        //alert(document.getElementById("second").value)
      }
      if (this.getRGBcanvas(xooo, yooo) === '0 0 255') {
        this.result = document.getElementById("three").value
        //alert(document.getElementById("three").value)
      }
    },

    twist() {
      function getRandomArbitrary(min, max) {
        return Math.random() * (max - min) + min;
      }
      let start = this.rotate
      let finish = start + getRandomArbitrary(3000, 5000);
      this.rotate = finish;

      document.getElementById("canvas").animate(
        [
          { transform: 'rotate(' + start + 'deg)' },
          { transform: 'rotate(' + finish + 'deg)' },
        ],
        {
          duration: 10000,
          easing: "cubic-bezier(.64,-0.32,.58,1.62)",
          fill: "both",
        },
      );

      setTimeout(() => {
        this.win()
      }, 10000);
    }
  },

}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

p {
  margin: 0;
  padding: 0;
}

.title__text {
  margin: 0 auto 15px;
  padding: 0;
  font-size: 23px;
}

.parent-canvas {
  position: relative;
}

.canvas {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 0;
}

.arrow {
  position: absolute;
  bottom: -49px;
  right: 30px;
  z-index: 1;
  height: 100px;
  transform: rotate(30deg);
}

.first {
  accent-color: #00ff00;
}

.second {
  accent-color: #ff0000;
}

.three {
  accent-color: #0000ff;
}

.slider-blok {
  display: flex;
  margin-bottom: 10px;
}

.result-text {
  position: absolute;
  left:115px;
  bottom: -90px;
  width: max-content;
  text-align: left;
  font-size: 18px;
  line-height: 20px;
}

.slider-input {
  height: 20px;
  width: 200px;
  margin-right: 10px;
  border-radius: 5px;
  display: block;
  width: 100%;
  padding: 16px 40px 15px 50px;
  background-color: #FFFFFF;
  border: 1px solid #ECECEC;
  box-sizing: border-box;
  border-radius: 10px;
  position: relative;
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  line-height: 17px;
  background-repeat: no-repeat;
  background-position: 19px 16px;
  background-size: 18px;
}

.slider-input:focus {
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  transition: 0.3s;
}

.slider-mean {
  width: 60px;
  margin-left: 10px;
  margin-top: 8px;
  text-align: left;
  font-size: 14px;
  line-height: 17px;
}

.parameters {
  position: absolute;
  top: 0;
  right: -500px;
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 3;
}

.button {
  margin-top: 15px;
  position: relative;
  display: inline-block;
  background-color: #0080c8;
  border: none;
  height: auto;
  font-size: 12px;
  font-weight: 800;
  line-height: 16px;
  text-align: center;
  white-space: normal;
  padding: 13px 25px;
  border-radius: 61px;
  cursor: pointer;
  transition: all .2s ease-in-out;
  box-shadow: none;
  color: #fff;
  text-transform: uppercase;
}
</style>
