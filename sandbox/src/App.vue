<script setup lang="ts">
export defaults {
  data() {
          return {
            count: 10,
            counterTitle: 'Counter Standard',
            incrementAmount: 8,
            message: 'Hello it works',
            listOfNumbers: [
              {
                name: 1,
                id: '6a887cd2-f0bf-4321-b192-92016f82a883',
                list: [1, 2, 3]
              },
              {
                name: 2,
                id: '8d14d90b-2d47-473e-8293-d5c324111d0d',
                list: [1, 2, 3]
              },
              {
                name: 3,
                id: 'cd806d65-2309-4625-9104-dcd636cd79b5',
                list: [1, 2, 3]
              },
              {
                name: 4,
                id: '00c939cd-fbf4-46d0-8e61-0bc2ce8a5332',
                list: [1, 2, 3]
              },
              {
                name: 5,
                id: '295a8170-59c1-4462-9de1-3c9cd41cedab',
                list: [1, 2, 3]
              }
            ]
          }
        },
        computed: {
          displayTitle() {
            if (this.count > 20) {
              return 'Counter Standard - Very Long'
            } else {
              return 'Counter Standard'
            }
          },
          optimizedIncrementAmount() {
            return this.displayTitle.length * this.incrementAmount
          }
        },
        methods: {
          incrementCount(newAmount, event) {
            console.log(newAmount)
            console.log(event)
            this.count += this.optimizedIncrementAmount
          }
        },
        watch: {
          count(newValue) {
            if (newValue > 20) {
              this.counterTitle += ' Very Long'
            }
          }
        }
      }
}
</script>

<template>
  <p v-if="characterList.length === 0">There are no characters</p>
      <ul v-else-if="characterList.length % 2 === 0">
        <li v-for="character in characterList">
          <p>{{ character.name }}</p>
          <button @click="favoriteCharacter(character)">⭐ Favorite</button>
        </li>
      </ul>
      <h2>Favorite Characters</h2>
      <ul v-if="favoriteList.length > 0">
        <li v-for="character in favoriteList">{{ character }}</li>
        <p v-else>No favorite characters yet!</p>
      </ul>

      <h2>New Character</h2>
      <pre>{{ newCharacter }}</pre>
      <label for="character-name">Name</label>
      <input
        type="text"
        v-model="newCharacter.name"
        @keyup.enter="addNewCharacter"
      />
      <p>
        <span v-for="(character, index) in characterList"
          >{{ character.name }}{{ index === characterList.length - 1 ? '' : ', '
          }}
        </span>
      </p>
      <!-- <p v-else>There are odd characters!</p> -->
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
