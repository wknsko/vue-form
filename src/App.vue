<template>
  <div class="container">
    <form class="card" @submit.prevent="submitHandler">
      <h1>Surver for Vue Dev</h1>
      <!-- <div class="form-control" :class="{ invalid: errors.name }">
        <label for="name">What's your name?</label>
        <input type="text" v-model.trim="name" id="name" placeholder="enter your name">
        <small v-if="errors.name">{{ errors.name }}</small>
      </div> -->
      <app-input
      placeholder="enter your name"
      :errors="errors.name"
      label="Whats's your name?"
      v-model:value="name"></app-input>

    <div class="form-control">
      <label for="age">Choose your age</label>
      <input type="number" v-model.number="age" id="age">
    </div>

    <div class="form-control">
      <label for="city">Your city</label>
      <select id="city" v-model="city">
        <option value="spb"> Saint Shitersburg</option>
        <option value="msk">Moskal'yovo</option>
        <option value="nsk">Nososeberyl'sk</option>
      </select>
    </div>

    <div class="form-checkbox">
      <span class="label" >Ready to move outside of Parussia?</span>
      <div class="checkbox">
        <label><input type="radio" v-model="relocate" name="trip" value="yes"/> Fuck Yeah</label>
      </div>
      <div class="checkbox">
        <label><input type="radio" v-model="relocate" name="trip" value="no"/> No, I am dipshit</label>
      </div>
    </div>

    <div class="form-checkbox">
      <span class="label">What do you know?</span>
      <div class="checkbox">
        <label><input type="checkbox" name="skills" v-model="skills" value="vuex"/> Vuex</label>
      </div>
      <div class="checkbox">
        <label><input type="checkbox" name="skills" v-model="skills" value="vue-cli"/> Vue CLI</label>
      </div>
      <div class="checkbox">
        <label><input type="checkbox" name="skills" v-model="skills" value="router"/> Vue Router</label>
      </div>
    </div>

    <div class="form-checkbox">
      <span>Rules of our Company</span>
      <div class="checkbox">
        <label><input type="checkbox" name="agree" v-model="agree">I do agree with the rules</label>
      </div>

    </div>

    <button type="submit" class="btn primary">Send</button>

  </form>
</div>
</template>

<script>
import AppInput from './components/AppInput.vue';
  export default {
    data() {
      return {
        name: '',
        age: 20,
        city: 'nsk',
        relocate: 'yes',
        skills: [],
        agree: false,
        errors: {
          name: null
        }
      }
    },
    methods: {
      formValid() {
        let isValid = true;
        if(this.name.length === 0) {
          this.errors.name = `Name can't be empty`;
          isValid = false;
        } else {
          this.errors.name = null
        }
        return isValid;
      },
      submitHandler(){
        if(this.formValid()) {
        //event.preventDefault()
        console.group('Form Data');
        console.log('Name: ' + this.name);
        console.log('Age: ' + this.age);
        console.log('City: ' + this.city);
        console.log('Escape to Freedom: ' + this.relocate);
        console.log('Skills: ' + this.skills);
        console.log('Rules: ' + this.agree)
        console.groupEnd()
      }
      }
    }, components: {
      AppInput
    }

  }
</script>

<style >
.form-control small {
  color: darkred;
}
.form-control.invalid input {
  border-color: darkred
}

</style>
