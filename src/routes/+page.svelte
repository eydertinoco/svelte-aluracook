<script lang="ts">
    import '../app.css';

    import MinhaLista from "$components/MinhaLista.svelte";
    import Titulo from "$components/Titulo.svelte";
    import Categoria from "$components/Categoria.svelte";
    import Tag from "$components/Tag.svelte";

    import categorias from "$json/categorias.json";

    import { minhaLista } from "$stores/minhaLista.js";

    function adicionarIngrediente(evento: CustomEvent<string>) {
        const ingrediente = evento.detail;
        $minhaLista = [...$minhaLista, ingrediente];
        console.log(minhaLista);
    }
    function removerIngrediente(evento: CustomEvent<string>) {
        const ingrediente = evento.detail;
        $minhaLista = $minhaLista.filter(
            (item) => item !== ingrediente
        );
    }
</script>

<svelte:head>
    <title>Alura Cook</title>
</svelte:head>

{#if $minhaLista.length}
    <div class="minha-lista-container">
        <MinhaLista ingredientes={$minhaLista}/>

        <div class="divisoria"/>
    </div>
{/if}

<main>
    <Titulo tag="h1">Ingredientes</Titulo>

    <div class="info">
        <p>
            Texto 1
        </p>
        <p>
            Texto 2
        </p>
    </div>

    <ul class="categorias">
        {#each categorias as categoria (categoria.nome)}
            <li>
                <Categoria
                        {categoria}
                        on:adicionarIngrediente={adicionarIngrediente}
                        on:removerIngrediente={removerIngrediente}
                />
            </li>
        {/each}
    </ul>

    <div class="buscar-receitas">
        <a href="/receitas">
            <Tag ative={true} tamanho="lg">Buscar Receitas</Tag>
        </a>
    </div>
</main>

<style>
    .minha-lista-container {
        margin-bottom: 2rem;
    }

    .info {
        margin-bottom: 3.375rem;
    }
    .info > p {
        line-height: 2rem;
    }

    .categorias {
        margin-bottom: 4.6875rem;

        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 1.5rem;
    }

    .buscar-receitas {
        display: flex;
        justify-content: center;
    }
</style>