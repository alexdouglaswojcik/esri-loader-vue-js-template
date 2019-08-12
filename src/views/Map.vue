<template>
  <div>
    <b-card no-body class="overflow-hidden">
      <b-row no-gutters>
        <b-col md="8">
          <b-card-text id="viewDiv"></b-card-text>
        </b-col>
        <b-col md="4">
          <b-card-body title="Horizontal Card">
            <b-card-text>
              This is a wider card with supporting text as a natural lead-in to additional content.
              This content is a little bit longer.
            </b-card-text>
          </b-card-body>
        </b-col>
      </b-row>
    </b-card>
  </div>
</template>


<script>
// @ is an alias to /src
import { loadModules } from "esri-loader";
import { loadCss } from "esri-loader";

export default {
  name: "about",
  components: {},
  mounted() {
    console.log("map: mounted");

    loadCss();

    loadModules(["esri/views/MapView", "esri/widgets/LayerList", "esri/Map"])
      .then(([MapView, LayerList, Map]) => {
        
        // create new map
        var webmap = new Map({
            basemap: 'topo-vector'
        });
        
        
        // and we show that map in a container w/ id #viewDiv
        var view = new MapView({
          map: webmap,
          container: "viewDiv",
          center: [-63.737, 45.126],
          zoom: 7
        });

      })
      .catch(err => {
        // handle any errors
        console.error(err);
      });
  }
};
</script>

<style scoped>
#viewDiv {
  padding: 0;
  margin: 0;
  height: 750px;
}
</style>

