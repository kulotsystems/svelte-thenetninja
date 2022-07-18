<script>
    // import {onMount, onDestroy} from 'svelte';
    import {fade, slide, scale} from 'svelte/transition';
    import {flip} from 'svelte/animate';
    import PollStore   from '../stores/PollStore.js'
    import PollDetails from './PollDetails.svelte';

    export let polls = [];

    // const unsub = PollStore.subscribe((data) => {
    //     polls = data;
    // });

    // // lifecycle hooks
    // onMount(() => {
    //     // maybe get data from the database
    //     console.log('component mounted');
    // });
    // onDestroy(() => {
    //     // unsubscribe from the store
    //     console.log('component destroyed');
    //     unsub();
    // });
</script>


<div class="container">
    <div class="poll-list">
        {#each $PollStore as poll (poll.id)}
            <div in:fade out:scale|local animate:flip={{duration: 500}}>
                <PollDetails {poll} on:vote/>
            </div>
        {/each}
    </div>
</div>


<style>
    .container {
        padding-left: 15px;
        padding-right: 15px;
    }

    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>