<template>
  <div id="app">
  <b-container class="bv-example-row">
    <b-row class="text-center">
        <b-col md="4">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Voluptates deleniti consectetur culpa ut repellat ea dolorum sed enim. Vero magnam quo, rem velit beatae corrupti exercitationem commodi nostrum!</b-col>
        <b-col md="4">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quis similique voluptate ex repudiandae consequuntur provident nobis eveniet maiores ipsam nesciunt?</b-col>
        <b-col md="4">Lorem ipsum dolor sit amet consectetur adipisicing elit. Optio, enim!</b-col>
    </b-row>
    <hr>
    <b-row class="text-center">
        <b-col>1 of 3</b-col>
        <b-col cols="5">2 of 3 (wider)</b-col>
        <b-col>3 of 3</b-col>
    </b-row>
    <hr>
    <b-row align-h="center">
      <b-col cols="4">
        <b-button size="lg" variant="success" @click="handleClick">
          My button
        </b-button>
      </b-col>
      <b-col cols="4">
        <b-alert variant="danger"
             dismissible
             :show="showDismissibleAlert"
             @dismissed="showDismissibleAlert=false">
               Dismissible Alert!
        </b-alert>
      </b-col>
    </b-row>

    <hr>

    <b-row>
      <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group id="exampleInputGroup1"
                    label="Email address:"
                    label-for="exampleInput1"
                    description="We'll never share your email with anyone else.">
        <b-form-input id="exampleInput1"
                      type="email"
                      v-model="form.email"
                      required
                      placeholder="Enter email">
        </b-form-input>
      </b-form-group>
      <b-form-group id="exampleInputGroup2"
                    label="Your Name:"
                    label-for="exampleInput2">
        <b-form-input id="exampleInput2"
                      type="text"
                      v-model="form.name"
                      required
                      placeholder="Enter name">
        </b-form-input>
      </b-form-group>
      <b-form-group id="exampleInputGroup3"
                    label="Food:"
                    label-for="exampleInput3">
        <b-form-select id="exampleInput3"
                      :options="foods"
                      required
                      v-model="form.food">
        </b-form-select>
      </b-form-group>
      <b-form-group id="exampleGroup4">
        <b-form-checkbox-group v-model="form.checked" id="exampleChecks">
          <b-form-checkbox value="me">Check me out</b-form-checkbox>
          <b-form-checkbox value="that">Check that out</b-form-checkbox>
        </b-form-checkbox-group>
      </b-form-group>
      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    </b-row>
    <hr>
    <b-row>
      <b-btn v-b-modal.modal1>Launch demo modal</b-btn>
    </b-row>
    
</b-container>
  <b-modal id="modal1" title="Bootstrap-Vue">
    <p class="my-4">Hello from modal!</p>
  </b-modal>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      showDismissibleAlert: false,
       form: {
        email: '',
        name: '',
        food: null,
        checked: []
      },
      foods: [
        { text: 'Select One', value: null },
        'Carrots', 'Beans', 'Tomatoes', 'Corn'
      ],
      show: true
    }
  },
  methods:{
    handleClick(){
      this.showDismissibleAlert = true
    },
    onSubmit (evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset (evt) {
      evt.preventDefault();
      /* Reset our form values */
      this.form.email = '';
      this.form.name = '';
      this.form.food = null;
      this.form.checked = [];
      /* Trick to reset/clear native browser form validation state */
      this.show = false;
      this.$nextTick(() => { this.show = true });
    }
  }
}
</script>

<style lang="scss">

</style>
