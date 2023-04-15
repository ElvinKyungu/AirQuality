<script>
export default {
   
  data() {
    return {
      airQualityData: [],
    };
  },
  mounted() {
    fetch("http://api.airvisual.com/v2/nearest_city?key=3ec25430-b9b1-47cb-b1ec-8cd7ab1f0415")
      .then(response => response.json())
      .then(data => {
        this.airQualityData.push({
          city: data.data.city,
          pm25: data.data.current.pollution.pm25,
          pm10: data.data.current.pollution.pm10,
        });
      })
      .catch(error => console.error(error));
  },
}
</script>
<template>
   <div class="app-container">
      <div class="card">
         <h1>Air Quality App</h1>
         <div class="information-block">
            <div class="loader active">
               <img src="./icons/biodegradable.svg" class="loader-logo" alt="loader" srcset="">
            </div>
            <img src="./icons/magnifying-glass.svg" alt="feeling image" class="emoji-logo" srcset="">
            <p class="user-information">Your city information</p>
            <table>
               <tr>
                  <th>City</th>
                  <td>...</td>
               </tr>
               <tr>
                  <th>Pollution info</th>
                  <td>...</td>
               </tr>
               <tr>
                  <th>Air Quality</th>
                  <td>...</td>
               </tr>
            </table>
            <p class="scale-bar-text">Pollution scale :</p>
            <div class="scale-bar">
               <img src="./icon/location.svg" alt="" srcset="">
               <div class="scale-section"></div>
               <div class="scale-section"></div>
               <div class="scale-section"></div>
               <div class="scale-section"></div>
               <div class="scale-section"></div>
               <div class="scale-section"></div>
            </div>
         </div>
      </div>
   </div>
</template>
<style scoped>

</style>