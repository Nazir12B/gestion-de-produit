<template>
 <div class="container"> 

   <div class="card-panel teal lighten-2">RECEPTION DE PRODUITS</div>

    <div class="row">
    <form class="col s12">

      <div class="row">
        <div class="file-field input-field col s6">
            <div class="btn">
            <span>Doc</span>
            <input type="file" multiple>
      </div>

      <div class="file-path-wrapper">
        <input class="file-path validate" type="text" placeholder="Document justificatif">
      </div>

        </div>

        <div class="input-field col s6">
          <input id="icon_date_range" type="date" class="validate" >
        </div>
      </div>
    </form>
  </div>

  <div>
    <table class="highlight centered striped">
      <thead>
        <tr>
            <th>Produits</th>
            <th>Quantité</th>
            <th>Supprimer</th>
            <th> <i class="small material-icons" @click="show">add_circle_outline</i></th>
           
        </tr>
      </thead>
      
      <tbody>
        <tr v-for="(article,index) in articles" :key="index">
          <td>{{article.name}}</td>
          <td>{{article.value}}</td>
          <td>
            <i class="material-icons" @click="removeThis(index)">delete</i>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
 
 <div class="row">
    <form class="col s12"> 
      
      <div v-if="showForm">
        <div class="input-field col s12 m6">
          Produit: <input type="text" v-model="product"/>
        </div>

        <div class="input-field col s12 m6"> 
            Quantité:<input type="number" v-model="quantity"/> 
        </div>    
       </div>
    </form>
     
 </div>
  
  <div class="centre">
    <button @click="save" class="button button1">Enregistrer</button>
    <button @click="show" class="button button2">Annuler</button>
  </div>
</div>
</template>

<script>
export default {
  data(){
    return{
      showForm:false,
      product:"",
      quantity: 0,
      articles : [
        {
          name: "Produit1",
          value:10,
        },
        {
          name: "Produit2",
          value:20,
        },
        {
          name: "Produit3",
          value:30,
        },
      ]
    }
  },
  methods:{
    show(){
      this.showForm=!this.showForm;
    },
    removeThis(index){
      this.articles.splice(index,1);
    },
    save(){
      this.articles.push(
        {
          name:this.product,
          value:this.quantity
        }
      );
      this.showForm=!this.showForm;
    },
  }

}
</script>


<style>
html,
body {
	height: 100%;
}

body {
	margin: 0;
	background: white;
	font-family: Arial;
	font-weight: 100;
}

.container {
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}

.card-panel{
  text-align: center;
  color: white;
  font-family: 'Times New Roman', Times, serif;
  font-size: 35px;
  border-radius: 10px;
} 


.highlight {
	border-collapse: collapse;
	overflow: hidden;
  border-radius: 10px;
	
}

th {
  font-family: Georgia;
  font-size: 20px;
  height: 10px;
	background-color:silver;
	color:black;
	
}

td {
  font-size: 13px;
	padding: 15px;
	color:black;
}

.button {
  border: none;
  color: white;
  padding: 10px 25px;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 20px 10px;
  transition-duration: 0.4s;
  cursor: pointer;
  border-radius: 25px;
}

.centre{
  text-align: center;
  
}


.button1 {
  background-color: teal; 
  color: black; 
  border: 1px solid rgba(14, 139, 143, 0.522);
}

.button1:hover {
  background-color:rgba(14, 139, 143, 0.522);
  color: white;
}

.button2 {
  background-color: white; 
  color: black; 
  border: 1px solid silver;
}

.button2:hover {
  background-color:silver;
  color: white;
}

</style>
