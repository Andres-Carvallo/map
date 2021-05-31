<style>

body{
  font-family: Roboto;
  height: 760px;
  background-color: #e6e6fa;
  position: relative;
}

  .markers{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 30px;
  }
  .form-control{
    font-family: Roboto;
    color: rgb(126, 126, 126);
    width: 246px;
    height: 40px;
    left: 84px;
    top: 65px;
    mix-blend-mode: multiply;
    box-sizing: border-box;
    text-align: center;
    margin-top: 10px;
    
  }

    .form-control:focus{
      mix-blend-mode:normal;
    }

  .iconSearch { 
    margin-left: 10px;
    color: rgb(126, 126, 126);
    cursor: pointer;
    margin-top: 10px;
  }
  .iconBack{
    margin-right: 15px;
    color: rgb(126, 126, 126);
    cursor: pointer;
    margin-top: 10px;
  }

  .iconClose {
    margin-right: 20px;
    color: rgb(126, 126, 126);
    cursor: pointer;
  }
  .map{
    height: 760px;
    display: flex;
    justify-content: center;
    align-items: flex-end;
  }
  .over-map-div{
    display:block;
  }
  .over-map{
    position: relative;
    z-index: 1;
    background: #4F4F4F;
    border-radius: 30px;
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 22px;
    letter-spacing: 0em;
    color: #ffff;
    width:350px;
    height: 130px;

    -webkit-transition: height 1s ease-out;
    -moz-transition: height 1s ease-out;
    -o-transition: height 1s ease-out;
    transition: height 1s ease-out;


  }
  .over-map-detail{


    position: relative; 
    z-index: 1;
    background: #4F4F4F;
    border-radius: 30px;
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 22px;
    letter-spacing: 0em;
    color: #ffff;
    width:350px;
    height: 245px;
    
  }

    .over-map-info{
      margin-top: 5%;
      text-align: left;
      padding-left: 15px;
      display: flex;
      width: 300px;
    }
    .over-map-text-name{
      font-size: 14px;
    }
    .over-map-text-address{
      font-size: 10px;
    }
    .over-map-text-detail{
      text-decoration: underline;
      font-size: 10px;
      cursor: pointer;
      color: #FB8EFD;
    }
  .vue-map-hidden{
    display: block;
  }

  .pins{
    text-align: center;
    padding-bottom: 40px;
    background-color: #e6e6fa;
  }
  .places-title{
    margin-top: 105px;
    color: rgb(126, 126, 126);
    font-weight: bolder;
    
  }
  .places-distance{
    color: rgb(126, 126, 126);
    font-weight: bold;
    font-size: 12px;
  }
  .places-div{
    align-items: center;
    border-bottom: 20px;
    border-bottom-color: rgb(126, 126, 126);
    padding: 20px 0;
  }
    .places-div:hover{
      background-color: #ffff;
    }
    .places{
      display: flex;
      justify-content: left;
      align-items: center;
      align-self: center;
      color: rgb(126, 126, 126);
      font-weight: bold;
      font-size: 12px;
    }
    .line{
      border: 1.5px solid #333333;
      background-color:  #333333;
      width: 60px;
      margin-left: 155px;
      margin-top: 14px;
      align-items: center;
      align-self: center;
      cursor: pointer;
      
    }
    .circular{
      border-radius: 50%;
      width: 80px;
      height: 80px;
      margin-left: 15px;

    }

    .card-detail{
      background-color: lavender;
      color: rgb(126, 126, 126);
      width: 332px;
      margin-left: 10px;
      margin-top: 10px;
      border-radius: 30px;
      height: 110px;

    }
      .upper-card-detail{
        display: flex;
        margin-right: 15px;
      }
      .flower-div{
        margin-top: 10px;
        margin-left: 5px;
        display: flex;
        flex: 1;
      }
      .upper-card-icon{
        margin-left: 5px;
        margin-right: 5px;
        width: 10%;
      }
      .upper-card-text{
        background-color: #FFD189;
        padding: 3px 3px;
        align-items: center;
        vertical-align: middle;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 35px;
        font-size: 10px;

      }

      .upper-card-text2{
        background-color: lightpink;
        padding: 3px 3px;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 35px;
        font-size: 10px;
      }

      .upper-card-text3{
        background-color: lightgreen;
        padding: 3px 3px;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 35px;
        font-size: 10px;
      }

      .upper-card-text4{
        background-color: lightblue;
        padding: 3px 3px;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 35px;
        font-size: 10px;
      }
    .lower-card-detail{
      margin-top: 20px;
      display: flex;
      align-items: center;
    }
      .lower-card-text{
        margin-left: 12px;
        font-size: 18;
        padding: 5px 5px;
      }
        .lower-card-text:hover{
          background-color: white;
        }
      .lower-card-text2{
        margin-left: 20px;
        font-size: 18;
        padding: 5px 5px;
      }
        .lower-card-text2:hover{
          background-color: white;
        }



</style>

<template>
  <div>
    <div class="markers">
      <span @click='refresh' class="material-icons md-36 iconBack">arrow_back</span>
      <GmapAutocomplete
        class="form-control"
        @place_changed='setPlace'
        placeholder="Ingresa una dirección"
      />
      <span  @click='addMarker' class="material-icons md-36 iconSearch">search</span>
      
    </div>
    <br>
    <GmapMap
      class="map"
      :center='center'
      :zoom='15'
      
    >
      <GmapMarker
        :key="index"
        v-for="(m, index) in markers"
        :position="m.position"
        @click="showCard(m)"
        :icon="markerOptions"

      />
      <div class="over-map"  :class=" detail ?  'over-map-detail' : 'over-map'" :style="showInfo ? 'display:flex;' : 'display:none;'" v-bind="placeSelected">
        <div class="over-map-div">
          <div class="line" @click="showDetail"></div>
          <div class="over-map-info" v-show="places.length >= 1" >
            <div>
              <div class="over-map-text-name">
                {{placeSelected.name}}
              </div>
              <div class="over-map-text-address">
                {{placeSelected.formatted_address}}
              </div>
              <div class="over-map-text-detail">
                <div  @click="showDetail" >Ver perfil de colegio</div>
              </div>
            </div>
            <div v-show="placeSelected.photos">
              <img class="circular" :src="`${placeSelected? imgUrl : ''}`" alt="">
            </div>
          </div>
          <div class="card-detail"  v-show="detail">
            <div v-show="cardInfo">
              <div class="upper-card-detail">
                <div class="flower-div">
                  <img class="upper-card-icon" src="../assets/flower.png" alt="">
                  <div class="upper-card-text">1 2 3 4</div>
                  <img class="upper-card-icon" src="../assets/house.png" alt="">
                  <div class="upper-card-text2">1 2 3 4</div>
                  <img class="upper-card-icon" src="../assets/grass.png" alt="">
                  <div class="upper-card-text3">1 2 3 4</div>
                  <img class="upper-card-icon" src="../assets/building.png" alt="">
                  <div class="upper-card-text4">1 2 3 4</div>
                </div>
              </div>
              <div class="lower-card-detail">
                <div class="lower-card-text">Particular Subvencionado</div>
                <div class="lower-card-text2">Pre Kinder a IV°</div>
              </div>
            </div>
  
          </div>
        </div>
      </div>
    </GmapMap>
    <div class="pins" v-show="places.length >= 1 ">
      <h2 class="places-title">Tus pins</h2>
      <div v-show="places.length == 2" class="places-distance" :dist="places.length >= 2 ? getDistance(places[0], places[1]) : ''">
        Distancia entre primer pin y segundo pin {{distInbetween}} kms.
      </div>
      <div class="places-div">
        <div class="places" v-for="(place, index) in places " :key="index">
          <span  @click='deleteMarker(place)' class="material-icons md-36 iconClose">close</span>
          {{place.formatted_address}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'GoogleMap',
  data() {
    return {
      center: { lat: 45.508, lng: -73.587 },
      currentPlace: null,
      markers: [],
      places: [],
      markerOptions: {
        url: require('../assets/dot.png'),
        size: {width: 60, height: 60, f: 'px', b: 'px',},
        scaledSize: {width: 50, height: 50, f: 'px', b: 'px',},

      },
      showInfo: false,
      placeSelected: "",
      imgUrl: "",
      detail: false,
      distInbetween: "",
      cardInfo: false,

    }
  },
  mounted() {
    this.geolocate();
  },
  methods: {
    setPlace(place) {
      this.currentPlace = place;
    },
    addMarker() {
      if (this.currentPlace) {
        const marker = {
          lat: this.currentPlace.geometry.location.lat(),
          lng: this.currentPlace.geometry.location.lng(),
        };
        this.markers.push({ position: marker });
        this.places.push(this.currentPlace);
        this.center = marker;
        this.currentPlace = null;

      }
    },
    deleteMarker(placeSelect){
      var newPlaces = [];
      var newMarkers = [];
      var app = this;

      this.places.forEach(function(place){
        if(placeSelect.place_id != place.place_id){
          newPlaces.push(place)
        }else{
          if(placeSelect.place_id == app.placeSelected.place_id){
            app.showInfo = false;
          }
          app.markers.forEach(function(mark){
            if(mark.position.lat != place.geometry.location.lat() && mark.position.lng != place.geometry.location.lng()){
              newMarkers.push(mark);
            }
            
          });
        }
      });
      this.places = newPlaces;
      this.markers = newMarkers;
      this.distInbetween = "";

    },

    geolocate: function() {
      navigator.geolocation.getCurrentPosition(position => {
        this.center = {
          lat: position.coords.latitude,
          lng: position.coords.longitude,
        };
      });
    },

    refresh:function(){
      var place ="";
      this.setPlace(place);
    },

    showCard:function(marker){
      var app = this;
      this.places.forEach(function(place){
        if(marker.position.lat == place.geometry.location.lat() && marker.position.lng == place.geometry.location.lng()){
          app.placeSelected = place;
          if(place.photos){
            app.imgUrl = place.photos[0].getUrl()

          }
          
        }
      });
      if(this.showInfo){
        this.showInfo = false;
      }else{
        this.showInfo = true;
      }
    },

    showDetail:function(){
      var app = this;
      if(this.detail == false){
        this.detail = true;
        setTimeout(function(){ app.cardInfo = true; }, 1000);
      }else{
        this.detail = false;
        this.cardInfo = false;

      }
    },

    getDistance:function(p1, p2){
      if(p1 && p2){
        var rad = function(x) {
          return x * Math.PI / 180;
        };
        var R = 6378137; // Earth’s mean radius in meter
        var dLat = rad(p2.geometry.location.lat() - p1.geometry.location.lat());
        var dLong = rad(p2.geometry.location.lng() - p1.geometry.location.lng());
        var a = Math.sin(dLat / 2) * Math.sin(dLat / 2) +
          Math.cos(rad(p1.geometry.location.lat())) * Math.cos(rad(p2.geometry.location.lat())) *
          Math.sin(dLong / 2) * Math.sin(dLong / 2);
        var c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
        var d = R * c;
        this.distInbetween = (d/1000).toFixed(2); // returns the distance in meter
      }


    }


  },
};
</script>