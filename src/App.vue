<template>
  <div class="parent-container">
    <h1>Parent Component</h1>
    <p>Komponen ini berada di parent komponen, dimana komponen ini mencangkup semua komponen lainnya.<br>
    disini saya membuat tentang berbagai info game yang saya buat</p>
    <ChildComponent @data-updated="handleDataUpdated" />
    <SlotComponent :backgroundImage="gameBackground">
      <!-- Display game information -->
      <template v-if="gameInfo">
        <u><h2>{{ gameInfo.name }}</h2>
        <p>Genre: {{ gameInfo.genre }}</p>
        <p>Developer: {{ gameInfo.developer }}</p>
        <p>Release Year: {{ gameInfo.releaseYear }}</p>
        <p>Platform: {{ gameInfo.platform }}</p>
        <p>Rating: {{ gameInfo.rating }}/10</p>
        <p>Info: {{ gameInfo.info }}</p></u>
      </template>
      
    </SlotComponent>
  </div>
</template>

<script>
import SlotComponent from './components/SlotComponent.vue';
import ChildComponent from './components/ChildComponent.vue';

import SuperMarioImage from './assets/SuperMario.jpg';
import TheLegendofZeldaImage from './assets/TheLegendofZelda.jpg';
import MinecraftImage from './assets/Minecraft.jpg';
import PokemonImage from './assets/Pokémon.jpg';
import GrandTheftAutoImage from './assets/GrandTheftAuto.jpg';
import FortniteImage from './assets/Fortnite.jpg';
import LeagueofLegendsImage from './assets/LeagueofLegends.jpg';
import CallofDutyImage from './assets/CallofDuty.jpg';
import FIFAImage from './assets/FIFA.jpg';

export default {
  components: {
    SlotComponent,
    ChildComponent
  },
  data() {
    return {
      gameInfo: null,
      gameBackground: ''
    };
  },
  methods: {
    handleDataUpdated(data) {
      const genre = this.getGenre(data);
      if (genre !== 'Unknown') {
        this.gameInfo = {
          name: data,
          genre: genre,
          developer: this.getDeveloper(data),
          releaseYear: this.getReleaseYear(data),
          platform: this.getPlatform(data),
          rating: this.getRating(data),
          info: this.getInfo(data)
        };
        this.setGameBackground(data);
      } else {
        this.resetGameInfo();
        console.error("Game information not available for", data);
      }
    },
    setGameBackground(gameName) {
      const gameImages = {
        'Super Mario': SuperMarioImage,
        'The Legend of Zelda': TheLegendofZeldaImage,
        'Minecraft': MinecraftImage,
        'Pokémon': PokemonImage,
        'Grand Theft Auto': GrandTheftAutoImage,
        'Fortnite': FortniteImage,
        'League of Legends': LeagueofLegendsImage,
        'Call of Duty': CallofDutyImage,
        'FIFA': FIFAImage
      };
      this.gameBackground = gameImages[gameName] || '';
    },
    resetGameInfo() {
      this.gameInfo = null;
      this.gameBackground = '';
    },
    getGenre(gameName) {
      switch (gameName) {
        case 'Super Mario':
          return 'Platformer';
        case 'The Legend of Zelda':
          return 'Action-Adventure';
        case 'Minecraft':
          return 'Sandbox, Survival';
        case 'Pokémon':
          return 'Role-Playing, Adventure';
        case 'Grand Theft Auto':
          return 'Action-Adventure, Open World';
        case 'Fortnite':
          return 'Battle Royale, Survival';
        case 'League of Legends':
          return 'MOBA';
        case 'Call of Duty':
          return 'First-Person Shooter';
        case 'FIFA':
          return 'Sports';
        default:
          return 'Unknown';
      }
    },
    getDeveloper(gameName) {
      switch (gameName) {
        case 'Super Mario':
          return 'Nintendo';
        case 'The Legend of Zelda':
          return 'Nintendo';
        case 'Minecraft':
          return 'Mojang Studios';
        case 'Pokémon':
          return 'Game Freak';
        case 'Grand Theft Auto':
          return 'Rockstar North';
        case 'Fortnite':
          return 'Epic Games';
        case 'League of Legends':
          return 'Riot Games';
        case 'Call of Duty':
          return 'Various (Infinity Ward, Treyarch, Sledgehammer Games)';
        case 'FIFA':
          return 'EA Sports';
        default:
          return 'Unknown';
      }
    },
    getReleaseYear(gameName) {
      switch (gameName) {
        case 'Super Mario':
          return 1985;
        case 'The Legend of Zelda':
          return 1986;
        case 'Minecraft':
          return 2011;
        case 'Pokémon':
          return 1996;
        case 'Grand Theft Auto':
          return 1997;
        case 'Fortnite':
          return 2017;
        case 'League of Legends':
          return 2009;
        case 'Call of Duty':
          return 2003;
        case 'FIFA':
          return 1993;
        default:
          return null;
      }
    },
    getPlatform(gameName) {
      switch (gameName) {
        case 'Super Mario':
          return 'Nintendo (NES, SNES, Nintendo Switch)';
        case 'The Legend of Zelda':
          return 'Nintendo (NES, SNES, Nintendo Switch)';
        case 'Minecraft':
          return 'Various (PC, Console, Mobile)';
        case 'Pokémon':
          return 'Nintendo (Game Boy, Nintendo Switch)';
        case 'Grand Theft Auto':
          return 'Various (PlayStation, Xbox, PC)';
        case 'Fortnite':
          return 'Various (PlayStation, Xbox, PC,           Mobile)';
        case 'League of Legends':
          return 'PC';
        case 'Call of Duty':
          return 'Various (PlayStation, Xbox, PC)';
        case 'FIFA':
          return 'Various (PlayStation, Xbox, PC, Nintendo Switch)';
        default:
          return 'Unknown';
      }
    },
    getInfo(gameName) {
      switch (gameName) {
        case 'Super Mario':
          return 'Super Mario adalah salah satu game terpopuler di dunia. Game ini pertama kali dirilis pada tahun 1985 untuk Nintendo Entertainment System (NES). Game ini telah diadaptasi ke berbagai platform, termasuk Nintendo Switch.';
        case 'The Legend of Zelda':
          return 'The Legend of Zelda adalah salah satu game terpopuler di dunia. Game ini pertama kali dirilis pada tahun 1986 untuk Nintendo Entertainment System (NES). Game ini telah diadaptasi ke berbagai platform, termasuk Nintendo Switch.';
        case 'Minecraft':
          return 'Minecraft adalah salah satu game terpopuler di dunia. Game ini pertama kali dirilis pada tahun 2011 untuk PC. Game ini telah diadaptasi ke berbagai platform, termasuk PC, Console, dan Mobile.';
        case 'Pokémon':
          return 'Pokémon adalah salah satu game terpopuler di dunia. Game ini pertama kali dirilis pada tahun 1996 untuk Game Boy. Game ini telah diadaptasi ke berbagai platform, termasuk Nintendo Switch.';
        case 'Grand Theft Auto':
          return 'Grand Theft Auto adalah salah satu game terpopuler di dunia. Game ini pertama kali dirilis pada tahun 1997 untuk PlayStation. Game ini telah diadaptasi ke berbagai platform, termasuk PlayStation, Xbox, dan PC.';
        case 'Fortnite':
          return 'Fortnite adalah salah satu game terpopuler di dunia. Game ini pertama kali dirilis pada tahun 2017 untuk PC. Game ini telah diadaptasi ke berbagai platform, termasuk PlayStation, Xbox, PC, dan Mobile.';
        case 'League of Legends':
          return 'League of Legends adalah salah satu game terpopuler di dunia. Game ini pertama kali dirilis pada tahun 2009 untuk PC. Game ini telah diadaptasi ke berbagai platform, termasuk PC.';
        case 'Call of Duty':
          return 'Call of Duty adalah salah satu game terpopuler di dunia. Game ini pertama kali dirilis pada tahun 2003 untuk PlayStation. Game ini telah diadaptasi ke berbagai platform, termasuk PlayStation, Xbox, dan PC.';
        case 'FIFA':
          return 'FIFA adalah salah satu game terpopuler di dunia. Game ini pertama kali dirilis pada tahun 1993 untuk PC. Game ini telah diadaptasi ke berbagai platform, termasuk PlayStation, Xbox, PC, dan Nintendo Switch.';
        default:
          return 'Unknown';
      }
    },
    getRating(gameName) {
      switch (gameName) {
        case 'Super Mario':
          return 9;
        case 'The Legend of Zelda':
          return 10;
        case 'Minecraft':
          return 9.5;
        case 'Pokémon':
          return 9;
        case 'Grand Theft Auto':
          return 9.5;
        case 'Fortnite':
          return 8;
        case 'League of Legends':
          return 9;
        case 'Call of Duty':
          return 8.5;
        case 'FIFA':
          return 8.5;
        default:
          return 'Unknown';
      }
    }
  }
};
</script>

<style scoped>
.parent-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: rgba(0, 0, 0, 0.774);
  color: white;
}

</style>

