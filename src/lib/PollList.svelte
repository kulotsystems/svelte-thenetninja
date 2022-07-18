<script>
    import PollDetails from './PollDetails.svelte';

    export let polls = [];
</script>


<div class="container">
    <div class="poll-list">
        {#each polls as poll (poll.id)}
            <div>
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