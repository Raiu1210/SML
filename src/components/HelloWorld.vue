<template>
  <div>
    <div>
      {{latitude}}、{{longitude}}
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      latitude: 0.0,
      longitude: 0.0,
    }
  },
  mounted() {
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(
        function(position){
          let coords = position.coords;
          // 緯度経度だけ取得
          this.latitude = coords.latitude;
          this.longitude = coords.longitude;
        }.bind(this),
        function(error) {
          // エラー処理を書く
          alert("位置情報取れんかったー")
        }
      );
    } else {
      // エラー処理を書く
      alert("デバイス変えたほうがいいかも")
    }
  }
}
</script>