
<template>
    <div class="container">
        <div class="card-panel teal lighten-2">
            <strong>RAPPORT DE STOCK</strong>
        </div>

        <p></p>




        <div>
                    <div id="button" @click="show">
            <a class="dropdown-trigger btn" href="#" data-target="menu">
                <i class="medium material-icons">menu</i>
            </a>
        </div>

        <div class="row">
            <form v-if="this.set">
                <div id="menu">
                    <p>
                        <label>
                            <input class="with-gap" name="group1" type="radio" />
                            <span class="black-text text-darken-2">Journalier</span>
                        </label>
                    </p>
                    <p>
                        <label>
                            <input class="with-gap" name="group1" type="radio" />
                            <span class="black-text text-darken-2">Hebdomadaire</span>
                        </label>
                    </p>
                    <p>
                        <label>
                            <input class="with-gap" name="group1" type="radio" />
                            <span class="black-text text-darken-2">Mensuel</span>
                        </label>
                    </p>
                    <p>
                        <label>
                            <input class="with-gap" name="group1" type="radio" />
                            <span class="black-text text-darken-2">Annuel</span>
                        </label>
                    </p>
                </div>
            </form>
        </div>

        </div>
        <br>
        <br>
        <div class="ruban">
            <strong>Réception</strong>
        </div>

        <table class="highlight striped">
            
            <thead>
                <tr>
                    <th id="al">Produits</th>

                    <th id="il">Quantité</th>

                    <th id="ol">Date</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(article, index) in articles" :key="index">
                    <td>{{ article.name }}</td>
                    <td>{{ article.value }}</td>
                    <td>{{ article.date }}</td>
                    <td></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>


export default {

    data() {
        return {
            set: false,
            showForm: false,
            product: "",
            quantity: 0,
            articles: [
                {
                    name: "Produit1",
                    value: 10,
                    date: "11/02/2020"
                },
                {
                    name: "Produit2",
                    value: 20,
                    date: "11/02/2020"
                },
                {
                    name: "Produit3",
                    value: 30,
                    date: "11/02/2020"
                },
            ]
        }
    },
    methods: {
        show() {
            this.set = !this.set
            this.showForm = !this.showForm;
        },

    }
} 
</script>


<style>
.card-panel {
    text-align: center;
    color: white;
    font-family: "Times New Roman", Times, serif;
    font-size: 20px;
}
#button {
    float: right;
    border-radius: 50%;
}
.row {
    float: right;
    padding-block: 1px;
    align-items: right;
}
.ruban {
    text-align: center;
    font-size: "Times New Roman", Times, serif;
    font-size: 20px;
    background-color: silver;
    width: 100%;
    display: flex;
    justify-content: center;
    margin-top: 10px;
}
</style>
