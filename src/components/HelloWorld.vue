<template>
  <div class="hello">
      <div class="title">
        <h1>It's Our Journey</h1>
        <p>Cannavaro Yogi & Ajeng Kiasti</p>
      </div>
      <div class="timeline">
        <div class="checkpoint">
          <div>
            <h2>13 April 2023 - First Chat On IG</h2>
            <img :src="image1" alt="Yogi">
            <!-- <p>
              Lorem ipsum doler sit amet, asdsadsa
            </p> -->
          </div>
        </div>
        <div class="checkpoint">
          <div>
            <h2>15 April : First Time Our Meet</h2>
            <img :src="image2" alt="Yogi">
          </div>
        </div>
        <div class="checkpoint">
          <div>
            <h2>30 April - Taman Mini Indonesia Indah</h2>
            <img :src="image3" alt="Yogi">
          </div>
        </div>
        <div class="checkpoint">
          <div>
            <h2>24 Juni: Grand Indonesia</h2>
            <img :src="image4" alt="Yogi">
          </div>
        </div>
        <div class="checkpoint">
          <div>
            <h2>24 Juni: Grand Indonesia (2)</h2>
            <video autoplay muted loop>
              <source :src="video1" type="video/mp4">
            </video>
          </div>
        </div>
      </div>
      <div class="footer">
        <h1>"Akan terus berlanjut untuk hari-hari selanjutnya"</h1>
      </div>
      <div class="audio">
        {{ currentAudioName || audioList[0].name }}
        <audio-player autoplay
          ref="audioPlayer"
          :audio-list="audioList.map(elm => elm.url)"
          :before-play="handleBeforePlay"
          theme-color="#ffff"
        />
      </div>
  </div>
</template>

<script>
import AudioPlayer from '@liripeng/vue-audio-player'


export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    AudioPlayer
  },
  data(){
    return{
      sumber: require('@/assets/sample-3s.mp3'),
      currentAudioName: '',
      audioList: [
        {
          name: 'The 1975 - About You',
          url: require('@/assets/about-you.mp3')
        }
      ],
      image1: require('@/assets/first.jpeg'),
      image2: require('@/assets/second.jpeg'),
      image3: require('@/assets/third.jpeg'),
      image4: require('@/assets/fourth.jpeg'),
      video1: require('@/assets/givideo.mp4'),
      bg: require('@/assets/yogi.jpeg'),
    }
  },
  methods: {
    // Something to do before playing
    handleBeforePlay(next) {
      // There are a few things you can do here...
      this.currentAudioName = this.audioList[this.$refs.audioPlayer.currentPlayIndex].name

      next() // Start playing
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
body {
  margin: 0;
  font-family: sans-serif;
  background:
    no-repeat center fixed
    /* url(https://drive.google.com/uc?export=view&id=1UVpsPa4-xbOrXopXCVTy65TkEzZ4etnZ); */
    url(http://localhost:8080/bg2.jpeg);
  color: #fff;
  padding: 2em;
  background-size: cover;
}

body::before {
  content: '';
  background: rgba(0, 0, 0, .6);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  position: fixed;
}

* {
  margin: 0;
  padding: 0;
}

.footer {
  text-align: center;
  font-family: 'Pacifico';
  font-size: small;
}
h1 {
  margin: 0.3em;
  font-size: 3em;
}

h2 {
  margin-bottom: 0.5em;
  font-family: 'Pacifico';
}

.timeline img {
  border-radius: 5%;
  align-content: center;
  width: 100%;
  margin-bottom: 15px;
}

.timeline video {
  border-radius: 5%;
  align-content: center;
  width: 100%;
  height: 600px;
  margin-bottom: 15px;
}

.title {
  text-align: center;
  font-family: 'Pacifico';
  font-size: 18px;
}

.audio {
  max-width: 34em;
  margin: 5em auto;
}

.timeline {
  margin: 5em auto;
  max-width: 30em;
}

.checkpoint {
  max-width: 25em;
  padding-top: 2em;
  padding-bottom: 2em;
  position: relative;
}

.checkpoint div {
  border: 2px solid #888;
  border-radius: 1em;
  padding: 1.5em;
}

.checkpoint p {
  line-height: 27px;
  color: #ccc;
}

.checkpoint:nth-child(odd) {
  border-left: 3px solid #888;
  padding-left: 3em;
  transform: translateX(15em);
}

.checkpoint:nth-child(even) {
  border-right: 3px solid #888;
  padding-right: 3em;
  transform: translateX(-13em);
}

.checkpoint:nth-child(odd)::before,
.checkpoint:nth-child(even)::before {
  content: '';
  background: #888;
  width: 3em;
  height: 3px;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}

.checkpoint:nth-child(odd)::before {
  left: 0;
}

.checkpoint:nth-child(even)::before {
  right: 0;
}

.checkpoint:nth-child(odd) div::before,
.checkpoint:nth-child(even) div::before {
  content: '';
  background: #fff;
  box-shadow: 0 0 0.5em #0d71fc;
  width: 0.8em;
  height: 0.8em;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  border-radius: 50%;
}

.checkpoint:nth-child(odd) div::before {
  left: -0.5em;
}

.checkpoint:nth-child(even) div::before {
  right: -0.5em;
}

@media screen and (max-width: 1150px) {
  .timeline {
    width: 80vw;
  }
  .timeline .checkpoint {
    width: 100%;
    transform: none;
    padding-left: 0 ;
    padding-right: 0;
    border: none;
  }

  .timeline .checkpoint::before {
    width: 3px;
    height: 4em;
    top: -2em;
    left: 50%;
    transform: translateX(-50%);
  }

  .timeline .checkpoint div::before {
    top: -0.5em;
    left: 50%;
    transform: translateX(-50%);
  }
}
</style>
