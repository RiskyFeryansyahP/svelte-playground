<script lang="ts">
    export let isShowModal: boolean = false
    export let isPromo: boolean = false
</script>

{#if isShowModal}
    <!-- 
        class:promo is conditional style, where promo is name of class css 
        if we need to use handleToogle from app component we only just type on:click
    -->
    <div class="backdrop" class:promo={isPromo} on:click|self>
        <div class="modal">
            <slot name="title"></slot> <!-- call slot using specific name -->
            <slot></slot>
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