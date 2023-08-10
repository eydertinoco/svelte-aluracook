<script lang="ts">
    export let tag: 'h1' | 'h2' | 'h3' | 'h4' | 'h5' | 'h6';
</script>

<svelte:element this={tag} class="titulo tag-{tag}">
    <slot></slot>
</svelte:element>

<style>
    .titulo {
        color: var(--verde);
        text-transform: uppercase;
        line-height: 2rem;
        margin-bottom: 1rem;
    }

    .tag-h1 {
        font-size: 1.5rem;
        font-weight: 700;
    }
    .tag-h2 {
        font-size: 1.4rem;
        font-weight: 700;
    }
    .tag-h3 {
        font-size: 1.3rem;
        font-weight: 700;
    }
    .tag-h4 {
        font-size: 1.2rem;
        font-weight: 600;
    }
    .tag-h5 {
        font-size: 1.1rem;
        font-weight: 600;
    }
    .tag-h6 {
        font-size: 1rem;
        font-weight: 600;
    }
</style>