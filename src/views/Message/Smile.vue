<template>
  <div class="row">
    <div class="slime"
         :class='{active:isactive}'
         ref="slime">
      <svg x="0px"
           y="0px"
           width="125px"
           height="100px"
           viewBox="0 0 126.75 103.25"
           enable-background="new 0 0 126.75 103.25">
        <g class="crops"
           ref="crops">
          <path d="
          M126.153,71.798
          c0,35.275-30.128,31.452-65.403,31.452
          S0.411,107.073,0.411,71.798
          S34,0.927,63.282,0.927
          C92,0.927,126.153,36.523,126.153,71.798z" />
        </g>
        <g class="ombre">
          <path opacity="0.1"
                d="
          M98.583,98.968
          c0,5.085-4.708,4.313-37.833,4.313
          c-29.563,0-32.769,0.771-32.769-4.313
          c0-8.718,18.86-10.218,35.301-10.218
          C79.407,88.75,98.583,91.125,98.583,98.968z
          " />
        </g>
        <g class="reflet">
          <ellipse transform="matrix(
            0.5486 -0.8361
            0.8361 0.5486
            20.2905 77.5842)"
                   opacity="0.5"
                   fill="#fff"
                   cx="82"
                   cy="20"
                   rx="7.75"
                   ry="13.75" />
        </g>
        <g class="yeux">
          <g>
            <path d="
              M36.833,66.583
              c-3.359,0-6.083,2.724-6.083,6.083
              c0,3.359,2.724,6.083,6.083,6.083
              c3.36,0,6.083-2.724,6.083-6.083
              C42.917,69.307,40.193,66.583,36.833,66.583
              z
              M39.5,71.25
              c-0.874,0-1.583-0.709-1.583-1.583
              c0-0.875,0.709-1.583,1.583-1.583
              c0.875,0,1.583,0.709,1.583,1.583
              C41.083,70.541,40.375,71.25,39.5,71.25
              z" />
            <circle fill="#FFFFFF"
                    cx="39.5"
                    cy="69.667"
                    r="1.583" />
            <path d="
              M88.833,66.583
              c-3.359,0-6.083,2.724-6.083,6.083
              c0,3.359,2.724,6.083,6.083,6.083
              c3.36,0,6.083-2.724,6.083-6.083
              C94.917,69.307,92.193,66.583,88.833,66.583
              z 
              M91.5,71.25c-0.874,0-1.583-0.709-1.583-1.583
              c0-0.875,0.709-1.583,1.583-1.583
              c0.875,0,1.583,0.709,1.583,1.583
              C93.083,70.541,92.375,71.25,91.5,71.25
              z" />
            <circle fill="#FFFFFF"
                    cx="91.5"
                    cy="69.667"
                    r="1.583" />
          </g>
        </g>
        <g class="bouche">
          <g>
            <path fill="#A862A6">
              <animate id="animBouche"
                       attributeName="d"
                       dur="3s"
                       repeatCount="indefinite"
                       values="
              M49.9,78
              c0,3.151,1.885,5.435,4.528,7
              c3.228-1.911,7.589-2.749,11.072-2.749
              S73.344,83.089,76.572,85
              c2.643-1.565,4.528-3.849,4.528-7
              H49.9
              z; 
              M49.9,73
              c0,3.151,1.885,10.435,4.528,12
              c3.228-1.911,7.589-2.749,11.072-2.749
              S73.344,83.089,76.572,85
              c2.643-1.565,4.528-8.849,4.528-12
              H49.9
              z;
              M49.9,78
              c0,3.151,1.885,5.435,4.528,7
              c3.228-1.911,7.589-2.749,11.072-2.749
              S73.344,83.089,76.572,85
              c2.643-1.565,4.528-3.849,4.528-7
              H49.9
              z" />
            </path>
            <path fill="#E0B7E5"
                  d="
            M52.678,84.25
            c7.116,3.558,15.028,3.558,22.144,0
            C68.463,80.485,59.037,80.485,52.678,84.25
            C52.679,84.25,52.656,84.25,52.678,84.25z">

            </path>
          </g>
        </g>
      </svg>
    </div>
  </div>
</template>

<script>
import { Toast } from "vant";
export default {
  data() {
    return {
      isactive: false,
      numSlime: Math.floor(Math.random() * 10 + 1),
      colors: [
        "#1abc9c",
        "#2ecc71",
        "#3498db",
        "#9b59b6",
        "#34495e",
        "#f1c40f",
        "#e67e22",
        "#e74c3c",
        "#ecf0f1",
        "#95a5a6"
      ]
    };
  },
  mounted() {
    this.changecolor();
  },
  methods: {
    changecolor() {
      if (this.isactive) {
        Toast({
          duration: 1000,
          position: "top",
          message: "请不要点太快"
        });
        return;
      }
      this.numSlime++;
      this.numSlime = this.numSlime >= 10 ? 0 : this.numSlime;
      this.$refs.crops.style.fill = this.colors[this.numSlime];
      if (timer) {
        clearTimeout(timer);
      }
      this.isactive = true;
      const timer = setTimeout(() => {
        this.isactive = false;
      }, 1000);
    }
  }
};
</script>

<style  lang="scss" scoped>
.row {
  margin-top: px2rem(50px);
  display: flex;
  align-items: center;
  justify-content: center;
}
.slime {
  display: inline-block;
  width: px2rem(175px);
  height: 100px;
  margin: auto;
  padding: 5px 20px;
  -webkit-animation: respire 3s infinite ease;
  animation: respire 3s infinite ease;
}

@keyframes respire {
  0% {
    transform-origin: 50% 100%;
    transform: scaleX(1) scaleY(1);
  }
  50% {
    transform-origin: 50% 100%;
    transform: scaleX(1.05) scaleY(0.95);
  }
  100% {
    transform-origin: 50% 100%;
    transform: scaleX(1) scaleY(1);
  }
}

.slime.active {
  -webkit-animation: changeForme 1s ease-in-out;
  animation: changeForme 1s ease-in-out;
}

@keyframes changeForme {
  0% {
    transform-origin: 50% 100%;
    transform: scaleX(1) scaleY(1);
  }
  40% {
    transform-origin: 50% 100%;
    transform: scaleX(0.8) scaleY(1.2);
  }
  50% {
    transform-origin: 50% 100%;
    transform: scaleX(1.2) scaleY(0.8);
  }
  60% {
    transform-origin: 50% 100%;
    transform: scaleX(0.9) scaleY(1.1);
  }
  70% {
    transform-origin: 50% 100%;
    transform: scaleX(1.2) scaleY(0.8);
  }
  80% {
    transform-origin: 50% 100%;
    transform: scaleX(0.9) scaleY(1.1);
  }
  90% {
    transform-origin: 50% 100%;
    transform: scaleX(1.2) scaleY(0.8);
  }
  100% {
    transform-origin: 50% 100%;
    transform: scaleX(1) scaleY(1);
  }
}

.slime .yeux {
  -webkit-animation: cligneYeux 3s infinite ease-in-out;
  animation: cligneYeux 3s infinite ease-in-out;
}

@keyframes cligneYeux {
  0% {
    transform-origin: 62.5px 80px;
    transform: scaleY(1);
  }
  70% {
    transform-origin: 62.5px 80px;
    transform: scaleY(1);
  }
  80% {
    transform-origin: 62.5px 80px;
    transform: scaleY(0.2);
  }
  90% {
    transform-origin: 62.5px 80px;
    transform: scaleY(1);
  }
  100% {
    transform-origin: 62.5px 80px;
    transform: scaleY(1);
  }
}
</style>
