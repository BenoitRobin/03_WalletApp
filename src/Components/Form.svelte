<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let newArticle = {
        name: '',
        price: ''
    }

    function newExpense() {
        // console.log(newArticle)
        dispatch('newEntryArticle', {name: newArticle.name, price: newArticle.price})
        newArticle= {};
    }
</script>

<!-- MON STYLE -->

<style type='text/scss'>

// MES VARIABLES
@import '../styles/variables.scss';

// ----
.form {
    width: 100%;
    &-group {
        display: flex;
        flex-direction: column;
        margin: .5em 0;
    
        &--expenses {
            font-size:1.5rem;
            font-weight: 500;
            margin-bottom: .5em;
        }

        &--input {
            padding: .5em;
            color: $myblack;
            border-radius: 5px;
            font-size: 1.3rem;
        }

        &--input:hover {
            background-color: $mywhite;
        }
    } 
}

input:focus {
    outline: none;
    
}

// Button

.btn {
    width: fit-content;
    font-size: 1.3rem;
    padding: .3em 1em;
    margin: 1em 0 1.5em 0;

    background-color: $button-color;
    border-radius: 5px;
    border: 2px solid $button-color;
    cursor: pointer;
    transition: background-color .2s ease-in-out;

    &:hover {
        background-color: $back-color;
        color: $button-color;
    }
}

</style>

<form class="form" on:submit|preventDefault={newExpense}>
    <div class="form-group">
        <label for="expenses" class="form-group--expenses">
            Expense name
        </label>
        <input bind:value="{newArticle.name}" type="text" id='expenses' class="form-group--input" placeholder="Name a new expense...">
    </div>

    <div class="form-group">
        <label for="amount" class="form-group--expenses">
            Amount
        </label>
        <input bind:value="{newArticle.price}"  type="number" id='amount' class="form-group--input" placeholder="Expense amount...">
    </div>

    <button type="submit" class="btn">Add amount</button>
</form>