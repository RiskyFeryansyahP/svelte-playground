<script lang="ts">
    export let message: string = "Default value"

    const isShowModal = true
    export let isPromo: boolean = false
</script>

{#if isShowModal}
    <div class="backdrop" class:promo={isPromo}> <!-- class:promo is conditional style, where promo is name of class css -->
        <div class="modal">
            <p> {message} </p>
        </div>
    </div>
{/if}

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);
    }

    .modal {
        padding: 10px;
        border-radius: 10px;
        max-width: 400px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }

    .promo .modal {
        background: crimson;
        color: white;
    }
</style>