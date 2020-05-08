<template>
  <div id="app">
    <b-container>
      <b-row align-h="center" class="mt-5">
        <b-col cols="5">
         <b-card class="p-3">
           <h4 class="mb-4">Chcete Cityvizor i ve vaši obci?</h4>
           <h5 class="mb-4">Dejte nám vědet a my to s vedením obce vyřídíme za vás.</h5>
            <b-form @submit="onSubmit" @reset="onReset" v-if="show">

      <b-form-group
        id="input-group-1"
        label="Email"
        label-for="input-1"
      
        
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          required
          placeholder="vas email"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Jmeno" label-for="input-2" description="Vaše jméno mužeme uvést v seznamu zájemcu o Cityvizor při jednání se vedením obce.">
        <b-form-input
          id="input-2"
          type="jmeno"
          v-model="form.jmeno"
          required
          placeholder="vase jmeno"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Obec" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.obec"
          :options="obec"
          required
          placeholder="nazev obce"
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-4">
        <b-form-checkbox-group v-model="form.checked" id="checkboxes-4">
          <b-form-checkbox value="me">Chci dostávat informace o přepojení moji obce a Cityvizoru</b-form-checkbox>
          <b-form-checkbox value="that">Souhlasím se spracovaním osobních údajů a jejich poskytnutím obci</b-form-checkbox>
        </b-form-checkbox-group>
      </b-form-group>

      <b-button type="submit" variant="primary">Chci Cityvizor</b-button>
      
    </b-form>
         </b-card> 
        </b-col>  
      </b-row>
    </b-container>

  

  </div>
</template>

<script>

export default {
  data() {
    return {
      showDismissableAlert: false,
      form: {
          email: '',
          jmeno: '',
          obec: null,
          checked: []
        },
        obec : [{ text: 'vybrat', value: null }, 'Praha 1', 'Praha 2', 'Praha 3', 'Praha 4','Praha 5'],
        show: true
    }
  },
  methods: {
    handleClick() {
      this.showDismissableAlert = true
    },
    onSubmit (evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset (evt) {
      evt.preventDefault();
      this.form.email = '';
      this.form.name = '';
      this.form.obec = null;
      this.form.checked = []
      this.show = false;
      this.$nextTick (() => {this.show = true});
    }
    
    
  }

}

</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Lato:400,700');
  
    body {
      background: rgb(104, 106, 109);
      font-family: 'Lato', sans-serif;

    }


</style>
