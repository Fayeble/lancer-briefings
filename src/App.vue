<template>
  <Header :header="this.header" />
  <div class="content-container">
    <section class="section-container" id="missions" style="width:435px; height:714px;">
      <div class="section-header clipped-medium-backward">
        <img src="/icons/mission-icon.svg" />
        <h1>Mission Log</h1>
      </div>
      <div class="section-content-container">
        <h3>Current Assignment</h3>
        <Markdown :source="current_md" class="markdown" />
        <h3>Mission List</h3>
        <div class="mission-list-container">
          <Mission
            v-for="item in this.missions"
            :key="item.slug"
            :mission="item"
            :selected="this.mission_slug"
            @click="selectMission(item)"
          />
        </div>
      </div>
    </section>
    <section class="section-container" id="events" style="width:435px; height:714px;">
      <div class="section-header clipped-medium-backward">
        <img src="/icons/events-icon.svg" />
        <h1>Events Log</h1>
      </div>
      <div class="section-content-container">
        <Markdown :source="events" class="markdown" />
      </div>
    </section>
    <section class="section-container" id="pilots" style="width:894px; height:714px;">
      <div style="height:52px; overflow:hidden;">
        <div class="section-header clipped-medium-backward-pilot">
          <img src="/icons/pilot-icon.svg" />
          <h1>Pilot Roster</h1>
        </div>
        <div class="rhombus-back">&nbsp;</div>
      </div>
      <div class="section-content-container">
        <div class="pilot-list-container">
          <Pilot v-for="item in this.pilots" :key="item.slug" :pilot="item" />
        </div>
      </div>
    </section>
  </div>
  <svg
    style="visibility: hidden; position: absolute;"
    width="0"
    height="0"
    xmlns="http://www.w3.org/2000/svg"
    version="1.1"
  >
    <defs>
      <filter id="round">
        <feGaussianBlur in="SourceGraphic" stdDeviation="5" result="blur" />
        <feColorMatrix
          in="blur"
          mode="matrix"
          values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -5"
          result="goo"
        />
        <feComposite in="SourceGraphic" in2="goo" operator="atop" />
      </filter>
    </defs>
  </svg>
  <audio autoplay>
    <source src="/startup.ogg" type="audio/ogg" />
  </audio>
  <Footer/>
</template>

<script>
import Header from './components/layout/Header.vue';
import Footer from './components/layout/Footer.vue';
import Mission from './components/Mission.vue';
import Pilot from './components/Pilot.vue';
import Markdown from 'vue3-markdown-it';

export default {
  components: {
    Header,
    Footer,
    Mission,
    Pilot,
    Markdown
  },

  data() {
    return {
      "mission_slug": "002",
      "current_md": "",
      "events": "",
      "missions": [
        {
          "slug": "011",
          "name": "Dreams-of-Reclamation",
          "status": "success"
        },
        {
          "slug": "012",
          "name": "Rustic-Ways",
          "status": "success"
        },
        {
          "slug": "013",
          "name": "Scrap-Heap",
          "status": "success"
        },
        {
          "slug": "021",
          "name": "Alpine-Hotline",
          "status": "success"
        },
        {
          "slug": "022",
          "name": "Radio-Static",
          "status": "success"
        },
        {
          "slug": "023",
          "name": "Anti-Air-Assault",
          "status": "success"
        },
        {
          "slug": "031",
          "name": "Deserted-Distress",
          "status": "success"
        },
        {
          "slug": "001",
          "name": "Treasure-Tussle",
          "status": "success"
        },
        {
          "slug": "101",
          "name": "Boat-Business",
          "status": "success"
        },
        {
          "slug": "002",
          "name": "Accelerating-Action",
          "status": "start"
        },
      ],
      "pilots": [
        /*{
          "callsign": "Claymore",
          "alias": "Lill Lefebvre",
          "code": "[DEFENDER/STRIKER] Defending, disruption, and melee combat. Struggles with overextension and synergy. Stops harm to allies.",
          "corpro": "GMS",
          "frame": "Sagarmatha",
          "mech": "ZWEIHÄNDER"
        },*/
		    {
          "callsign": "Tarot",
          "alias": "Mortimer Lindseth",
          "code": "[STRIKER/CONTROLLER] Debuffing, empowering, and mid-range. Struggles alone and hates action. Fast, social, magical, and emotional.",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "FØRECAST"
        },
		    /*{
          "callsign": "Spirit",
          "alias": "Spirit",
          "code": "[CONTROLLER/STRIKER] Hacking, set-up, and picking off. Struggles without team support. Is unable to be a pilot.",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "ROKO"
        },
		    {
          "callsign": "Recoil",
          "alias": "Aiko Fuyukayo",
          "code": "2VFEXU",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "BUYAN-M"
        },
        {
          "callsign": "Tsuchinoko",
          "alias": "[Classified]",
          "code": "[CQB] Striking from mid to close range, quick and hard. Struggles with long-range power. Rarely appears physically.",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "STEADY ED"
        },
		    {
          "callsign": "Clown",
          "alias": "Evelyn Mint",
          "code": "4TUHB4",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "CARNIVAL GAMES"
        },*/
		    {
          "callsign": "The Wall",
          "alias": "Phil Goodman",
          "code": "GCUDTH",
          "corpro": "GMS",
          "frame": "Sagarmatha",
          "mech": "BIG MECH"
        },
		    {
          "callsign": "Jestie",
          "alias": "Sylvie",
          "code": "ZQIOU8",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "PEQUOD"
        },
		    /*{
          "callsign": "Atlas",
          "alias": "Dante Cavazos",
          "code": "BDGOFX",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "GAEA"
        },
		    {
          "callsign": "Slick",
          "alias": "Chance",
          "code": "K6L773",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "RED RUSH"
        },*/
        {
          "callsign": "Tag",
          "alias": "Linnéa Aaberg",
          "code": "[ARTILLERY] Long range precision and damage, staying in cover. Struggles with loading and overcharging. A little too optimistic.",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "BRIDGES"
        },
      ],
      "header": {
        "planet": "Farivius",
        "year": "5014u",
        "system": "Xev'es",
        "gate": "Xev'es-Vortex",
        "ring": "Xev'es-Outer",
        "headerTitle": "SHARD",
        "headerSubtitle": "Mercenary Company",
        "subheaderTitle": "Fungal Discoveries ",
        "subheaderSubtitle": "The Shards TTJ",
      },
      "options":{
        "eventsMarkdownPerMission": true
      }
    }
  },

  created() {
    this.loadMissionMarkdown()
    this.loadEventsMarkdown()
  },

  computed: {

  },

  methods: {
    selectMission(mission) {
      this.mission_slug = mission.slug;
      this.loadMissionMarkdown()
      if(this.options.eventsMarkdownPerMission){
        this.loadEventsMarkdown();
      }
    },
    loadMissionMarkdown() {
      let self = this;
      let md = `/missions/${self.mission_slug}.md`
      var client = new XMLHttpRequest();
      client.open('GET', md);
      client.onreadystatechange = function () {
        self.current_md = client.responseText;
      }
      client.send();
    },
    loadEventsMarkdown() {
      let self = this;
      let md = "";

      if(self.options.eventsMarkdownPerMission){
        md = `/events/${self.mission_slug}.md`
      }
      else {
        md = "/events.md"
      }

      var client = new XMLHttpRequest();
      client.open('GET', md);
      client.onreadystatechange = function () {
        self.events = client.responseText;
      }
      client.send();
    }
  }

}
</script>


<style lang="scss">
#app {
  width: 1902px;
  height: 910px;
  overflow: hidden;
}
</style>
