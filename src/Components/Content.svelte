<script>
    import Form from "./Form.svelte"
    import Card from "./Card.svelte"
    import { v4 as uuidv4 } from 'uuid';


    let articleArray = [
        {
            id: uuidv4(),
            name: 'Car',
            price: 3500
        },
        {
            id: uuidv4(),
            name: 'Svelte course',
            price: 90
        },
        {
            id: uuidv4(),
            name: 'xBox Series X',
            price: 500
        },
        {
            id: uuidv4(),
            name: 'Ticket for \'MEUTE\'',
            price: 40.5
        },
    ]

    $:total = articleArray.reduce((acc, curr)=>{
        return acc += curr.price;
    }, 0)

    function addArticle(event) {
        // console.log(event.detail)
        let newEntry= { id: uuidv4(), name: event.detail.name, price: event.detail.price};
        articleArray= [newEntry, ...articleArray];
        
        // console.log('new Array : ',articleArray);
    }

    function removeArticle(event) {
        // console.log(event.detail.id)
        articleArray = articleArray.filter(item => item.id != event.detail.id)
    }

    
</script>

<!-- MON STYLE -->

<style type='text/scss'>

// MES VARIABLES
@import '../styles/variables.scss';

// ----

.container {
    width: 80%;
    margin: 2em auto;
    padding: 1em;
    background-color: $mywhite;
    font-size: 2rem;
    border: 1px solid $back-color;
    border-radius: 5px;

    &-title {
        font-weight: 700;
    }
    &-amount {
        font-weight: 300;
    }

}

</style>


<div class="container">
    <Form on:newEntryArticle={addArticle} />

    <h2 class="container-title">
        Total expenses : <span class="container-amount">$ {total}</span>
    </h2>
    <hr>

    {#each articleArray as article (article.id)}
    
    <Card 
        id={article.id}
        name={article.name}
        price={article.price}
        on:deleteItem={removeArticle}
    />

    {/each}
</div>