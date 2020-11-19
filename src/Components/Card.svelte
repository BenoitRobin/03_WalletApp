<script>
    export let name;
    export let price
</script>

<!-- MON STYLE -->

<style type='text/scss'>

// MES VARIABLES
@import '../styles/variables.scss';

// ----

.card {
    width:80%;
    background-color: #fff;
    border: 2px solid $alt-color;
    border-radius: 5px;
    padding: 1em;
    margin: 1em auto;

    display: flex;
    justify-content: space-between;
    align-items: center;

    &-info {
        width: 55%;
        display: flex;
        justify-content: space-between;

        &--title {
            font-weight: 700;
        }

        &--amount {
            font-weight: 300;
        }
    }

    &-picto {
        width: 1em;
    }
}

</style>

<div class="card">
    <div class="card-info">
        <h2 class="card-info--title">
            {name}
        </h2>
        <p class="card-info--amount">$ {price}</p>
    </div>
    <div class="card-picto">
        <img src="assets/trash-solid.svg" alt="trash">
    </div>
</div>