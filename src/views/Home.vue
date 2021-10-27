<template>
  <div class="home">
    <table v-if="list.length">
      <thead>
        <tr>
          <th style="width: 5%">#</th>
          <th style="width: 5%"></th>
          <th>Country</th>
          <th style="text-align: right">17/18</th>
          <th style="text-align: right">18/19</th>
          <th style="text-align: right">19/20</th>
          <th style="text-align: right">20/21</th>
          <th style="text-align: right">21/22</th>
          <th style="text-align: right">Ranking</th>
          <th>Teams</th>
        </tr>
      </thead>
      <tr v-for="item in list" :key="item.rank">
        <td style="text-align: right">{{ item.rank }}</td>
        <td>
          <img v-if="item.progress == 0" width="15" src="../assets/neutral.png" alt="status" />
          <img v-else-if="item.progress == 1" width="15" src="../assets/up.png" alt="status" />
          <img v-else width="15" src="../assets/down.png" alt="status" />
        </td>
        <td style="text-align: left">{{ item.country }}</td>
        <td style="text-align: right">{{ item.one }}</td>
        <td style="text-align: right">{{ item.two }}</td>
        <td style="text-align: right">{{ item.three }}</td>
        <td style="text-align: right">{{ item.four }}</td>
        <td style="text-align: right">{{ item.five }}</td>
        <td style="text-align: right">{{ item.total }}</td>
        <td style="text-align: center">
          <span class="remaining-teams" :style="getStyleTeams(item.currentTeams, item.totalTeams)">{{ item.currentTeams }} / {{ item.totalTeams }}</span>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import axios from "axios";

export default {
  name: "Home",
  components: {},
  data() {
    return {
      list: [],
    };
  },
  mounted() {
    axios
      .get("http://localhost:5000/api/rankings")
      .then((res) => {
        console.log(res);
        this.list = res.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
  methods: {
    getStyleTeams(current, total) {
      if (current == total) {
        return "background-color: green; color: white;";
      } else if (current != 0) {
        return "background-color: orange  ";
      } else {
        return "";
      }
    },
    getProgressImage(progress) {
      if (progress == 0) {
        return "../assets/neutral.png";
      } else if (progress == 1) {
        return "../assets/up.png";
      } else {
        return "../assets/down.png";
      }
    },
  },
};
</script>

<style scoped>
.home {
  margin-top: 25px;
  margin-bottom: 25px;
  margin-right: 35px;
  margin-left: 35px;
  font-family: Mukta, sans-serif;
}

.remaining-teams {
  padding-top: 5px;
  padding-right: 15px;
  padding-left: 15px;
  padding-bottom: 5px;
  border-radius: 5px;
  border: 0.5px solid #f1f2f6;
  font-weight: 600;
}
/* 
body {
  font-family: Mukta, sans-serif;
  height: 100vh;
  display: grid;
  justify-content: center;
  align-items: center;
  color: #4f546c;
  font-size: 0.9rem;
  background-color: #f9fbff;
} */

table {
  width: 100%;
  border-collapse: collapse;
  /* box-shadow: 0 5px 10px #e1e5ee; */
  box-shadow: 0 0 5px 2px #fffa65;
  /* box-shadow: 0 0 5px 2px #fff200; */

  background-color: white;
  text-align: left;
  overflow: hidden;
  border-radius: 15px;
}
thead {
  box-shadow: 0 5px 10px #e1e5ee;
}

th {
  padding: 1rem 2rem;
  text-transform: uppercase;
  letter-spacing: 0.1rem;
  font-size: 0.7rem;
  font-weight: 900;
  text-align: center;
}

td {
  padding: 1rem 2rem;
  font-size: 0.8rem;
}

tr:nth-child(even) {
  background: #f1f2f6;
}
</style>
