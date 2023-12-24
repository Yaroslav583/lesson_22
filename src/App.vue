<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col">
        <h2>Characteristics: ({{ totalPoints }}/20)</h2>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <ul class="list-group list-group-flush">
          <character-setting v-for="character in characteristics" :key="character.id" :character="character"
                             :total-points="totalPoints" @increment="incrementCount" @decrement="decrementCount"
          />
        </ul>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <pre>{{ characteristics }}</pre>
      </div>
    </div>
  </div>
</template>

<script>
import CharacterSetting from './CharacterSetting.vue'

export default {
  components: {
    'character-setting': CharacterSetting,
  },
  data() {
    return {
      characteristics: [
        {
          id: 1,
          title: 'Health',
          count: 0,
        },
        {
          id: 2,
          title: 'Strength',
          count: 0,
        },
        {
          id: 3,
          title: 'Intelligence',
          count: 0,
        },
        {
          id: 4,
          title: 'Endurance',
          count: 0,
        },
        {
          id: 5,
          title: 'Mana',
          count: 0,
        },
        {
          id: 6,
          title: 'Armor',
          count: 0,
        },
        {
          id: 7,
          title: 'Speed',
          count: 0,
        },
      ],
      totalPoints: 20,
    };
  },
  methods: {
    incrementCount(character) {
      if (this.totalPoints > 0) {
        character.count += 1
        this.totalPoints -= 1;
      }
    },
    decrementCount(character) {
      if (character.count > 0) {
        character.count -= 1
        this.totalPoints += 1;
      }
    },
  },
};
</script>