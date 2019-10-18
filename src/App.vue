<template>
  <div id="app">
    <filterTag :dataArray='dataArray' :tag='targetCategory' v-on:childToParent="onChildClick" />
    <ul class="list">
      <li v-for="el in data" :key="el.id" class="list__item"><span>{{el.Car}}</span> <span>{{el.car_model}}</span><span>{{el.model_year}}</span></li>
    </ul>
  </div>
</template>

<script>
import filterTag from "./components/filter-tag";

export default {
  name: "App",
  components: {
    filterTag
  },
  data() {
    return {
      dataArray: [
        {"id":1,"Car":"Honda","car_model":"Element","model_year":2009},
        {"id":2,"Car":"Geo","car_model":"Metro","model_year":1995},
        {"id":3,"Car":"Lotus","car_model":"Exige","model_year":2012},
        {"id":4,"Car":"Pontiac","car_model":"GTO","model_year":1967},
        {"id":5,"Car":"Chrysler","car_model":"300","model_year":2012},
        {"id":6,"Car":"Porsche","car_model":"Cayenne","model_year":2010},
        {"id":7,"Car":"Isuzu","car_model":"i-350","model_year":2006},
        {"id":8,"Car":"Audi","car_model":"A4","model_year":2006},
        {"id":9,"Car":"Mercury","car_model":"Monterey","model_year":2007},
        {"id":10,"Car":"Mitsubishi","car_model":"Cordia","model_year":1985},
        {"id":11,"Car":"BMW","car_model":"M3","model_year":1996},
        {"id":12,"Car":"Chevrolet","car_model":"Camaro","model_year":1971},
        {"id":13,"Car":"Subaru","car_model":"Legacy","model_year":2000},
        {"id":14,"Car":"Honda","car_model":"Element","model_year":2006},
        {"id":15,"Car":"Porsche","car_model":"Cayman","model_year":2006},
        {"id":16,"Car":"Buick","car_model":"Rendezvous","model_year":2003},
        {"id":17,"Car":"BMW","car_model":"7 Series","model_year":1997},
        {"id":18,"Car":"GMC","car_model":"Savana 2500","model_year":1999},
        {"id":19,"Car":"Suzuki","car_model":"X-90","model_year":1997},
        {"id":20,"Car":"Pontiac","car_model":"Grand Prix Turbo","model_year":1990},
        {"id":21,"Car":"Subaru","car_model":"Legacy","model_year":2010},
        {"id":22,"Car":"Volkswagen","car_model":"CC","model_year":2009},
        {"id":23,"Car":"Honda","car_model":"Insight","model_year":2006},
        {"id":24,"Car":"Saab","car_model":"9-5","model_year":2007},
        {"id":25,"Car":"Toyota","car_model":"Ipsum","model_year":2000},
        {"id":26,"Car":"Audi","car_model":"A8","model_year":2009},
        {"id":27,"Car":"Nissan","car_model":"Sentra","model_year":1999},
        {"id":28,"Car":"BMW","car_model":"M3","model_year":2006},
        {"id":29,"Car":"Ford","car_model":"F-Series Super Duty","model_year":2012},
        {"id":30,"Car":"Mazda","car_model":"B-Series Plus","model_year":1996},
        {"id":31,"Car":"Audi","car_model":"A4","model_year":1997},
        {"id":32,"Car":"Chevrolet","car_model":"Silverado 1500","model_year":2002},
        {"id":33,"Car":"Saturn","car_model":"Astra","model_year":2009},
        {"id":34,"Car":"Volvo","car_model":"V50","model_year":2008},
        {"id":35,"Car":"Ford","car_model":"Windstar","model_year":2000},
        {"id":36,"Car":"Saturn","car_model":"Ion","model_year":2005},
        {"id":37,"Car":"Toyota","car_model":"RAV4","model_year":1997},
        {"id":38,"Car":"Mitsubishi","car_model":"Starion","model_year":1985},
        {"id":39,"Car":"Cadillac","car_model":"DeVille","model_year":2003},
        {"id":40,"Car":"Volvo","car_model":"240","model_year":1993},
        {"id":41,"Car":"Scion","car_model":"tC","model_year":2013},
        {"id":42,"Car":"Daewoo","car_model":"Nubira","model_year":2000},
        {"id":43,"Car":"Mitsubishi","car_model":"Pajero","model_year":2004},
        {"id":44,"Car":"Honda","car_model":"Accord","model_year":2000},
        {"id":45,"Car":"Volvo","car_model":"V70","model_year":2003},
        {"id":46,"Car":"Chevrolet","car_model":"3500","model_year":1996},
        {"id":47,"Car":"Volkswagen","car_model":"rio","model_year":1996},
        {"id":48,"Car":"Dodge","car_model":"Stratus","model_year":1997},
        {"id":49,"Car":"Chrysler","car_model":"300","model_year":2006},
        {"id":50,"Car":"Chevrolet","car_model":"Corvette","model_year":2010},
        {"id":51,"Car":"Mercedes-Benz","car_model":"SLK-Class","model_year":1997},
        {"id":52,"Car":"Mazda","car_model":"CX-7","model_year":2011},
        {"id":53,"Car":"Chevrolet","car_model":"Camaro","model_year":2010},
        {"id":54,"Car":"Dodge","car_model":"Stealth","model_year":1996},
        {"id":55,"Car":"Pontiac","car_model":"Grand Prix","model_year":2004},
        {"id":56,"Car":"Maybach","car_model":"57","model_year":2007},
        {"id":57,"Car":"Daewoo","car_model":"Leganza","model_year":1999},
        {"id":58,"Car":"GMC","car_model":"Yukon","model_year":1998},
        {"id":59,"Car":"Land Rover","car_model":"LR2","model_year":2010},
        {"id":60,"Car":"Audi","car_model":"A6","model_year":2012},
        {"id":61,"Car":"Volkswagen","car_model":"Jetta","model_year":1985},
        {"id":62,"Car":"Mazda","car_model":"626","model_year":1997},
        {"id":63,"Car":"Mercedes-Benz","car_model":"SLK-Class","model_year":2001},
        {"id":64,"Car":"Toyota","car_model":"Prius","model_year":2011},
        {"id":65,"Car":"Mercury","car_model":"Villager","model_year":1993},
        {"id":66,"Car":"Lincoln","car_model":"MKZ","model_year":2011},
        {"id":67,"Car":"GMC","car_model":"Savana 1500","model_year":2006},
        {"id":68,"Car":"Pontiac","car_model":"GTO","model_year":1973},
        {"id":69,"Car":"Pontiac","car_model":"1000","model_year":1985},
        {"id":70,"Car":"Honda","car_model":"Accord","model_year":2012},
        {"id":71,"Car":"Buick","car_model":"Electra","model_year":1985},
        {"id":72,"Car":"Volkswagen","car_model":"riolet","model_year":1993},
        {"id":73,"Car":"GMC","car_model":"Sonoma","model_year":1993},
        {"id":74,"Car":"Toyota","car_model":"Corolla","model_year":2001},
        {"id":75,"Car":"GMC","car_model":"Savana 2500","model_year":2008},
        {"id":76,"Car":"Ford","car_model":"Explorer","model_year":1995},
        {"id":77,"Car":"Honda","car_model":"Civic","model_year":1995},
        {"id":78,"Car":"Land Rover","car_model":"Defender 90","model_year":1995},
        {"id":79,"Car":"Chevrolet","car_model":"Corvette","model_year":1966},
        {"id":80,"Car":"Suzuki","car_model":"Swift","model_year":1994},
        {"id":81,"Car":"Nissan","car_model":"Frontier","model_year":2011},
        {"id":82,"Car":"Mazda","car_model":"MX-5","model_year":1999},
        {"id":83,"Car":"Audi","car_model":"200","model_year":1989},
        {"id":84,"Car":"Mitsubishi","car_model":"Eclipse","model_year":1998},
        {"id":85,"Car":"Cadillac","car_model":"Eldorado","model_year":1992},
        {"id":86,"Car":"Corbin","car_model":"Sparrow","model_year":1999},
        {"id":87,"Car":"Mercury","car_model":"Mountaineer","model_year":2008},
        {"id":88,"Car":"Porsche","car_model":"928","model_year":1988},
        {"id":89,"Car":"Chevrolet","car_model":"Silverado 3500","model_year":2007},
        {"id":90,"Car":"Porsche","car_model":"Boxster","model_year":2003},
        {"id":91,"Car":"Nissan","car_model":"Maxima","model_year":1994},
        {"id":92,"Car":"Volkswagen","car_model":"Routan","model_year":2009},
        {"id":93,"Car":"Lincoln","car_model":"Town Car","model_year":1984},
        {"id":94,"Car":"Toyota","car_model":"Yaris","model_year":2012},
        {"id":95,"Car":"Plymouth","car_model":"Acclaim","model_year":1992},
        {"id":96,"Car":"Dodge","car_model":"Intrepid","model_year":1997},
        {"id":97,"Car":"Suzuki","car_model":"Swift","model_year":1996},
        {"id":98,"Car":"Alfa Romeo","car_model":"164","model_year":1992},
        {"id":99,"Car":"BMW","car_model":"3 Series","model_year":1997},
        {"id":100,"Car":"Mercedes-Benz","car_model":"E-Class","model_year":2005}
      ],
      targetCategory: 'Car',
      selectedTag: '',
    };
  },
  computed: {
    data() {
      if(this.selectedTag) {
        return this.dataArray.filter(el => el.Car === this.selectedTag);
      }
      return this.dataArray;
    }
  },
  methods: {
    onChildClick(value) {
      this.selectedTag = value
    }
  }
};
</script>

<style lang='scss'>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.list {
  list-style: none;
  padding: 0;

  &__item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    border-bottom: 1px solid gray;
    margin-bottom: 8px;
  }
}
</style>
