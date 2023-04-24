<template>
  <div>
    <button @click="getPerson" class="btn btn-primary">Get Person</button>
    <div v-if="set" class="person mt-3">
      <img :src="newPerson.pfp" alt="profile">
      <p>{{newPerson.username}}</p>
    </div>
    <div class="users-container">
      <h2>Users</h2>
      <div class="users-grid">
        <div v-for="user in users" :key="user.username">
          <img :src="user.pfp" alt="profile">
          <p>{{user.username}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    import { ref } from "vue";
    export default {
        setup() {
            const newPerson = ref({
                username: null,
                pfp: null
            })
            const set = ref(false)
            const users = ref([])

            const getPerson = async() => {
                fetch('https://randomuser.me/api')
                .then(res => res.json())
                .then(res => {
                    const person = {
                        username: res.results[0].login.username,
                        pfp: res.results[0].picture.large,
                    };
                    newPerson.value.username = person.username;
                    newPerson.value.pfp = person.pfp;
                    set.value = true;
                    users.value.push(person);
                    console.log(users.value);
                })
                .catch(err => console.log(err))
            }            

            return {users, set, newPerson, getPerson}
        }
    }
</script>

<style scoped>
  .users-container {
    margin-top: 2rem;
    width: 50%;
    margin: auto;
    margin-top: 20px;
  }
  .users-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-gap: 1rem;
  }
  .users-grid > div {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .users-grid img {
    max-width: 100%;
  }
  .users-grid p {
    margin-top: 0.5rem;
  }
</style>