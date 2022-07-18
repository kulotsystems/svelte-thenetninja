<script>
    import Header from './lib/Header.svelte';
    import Footer from './lib/Footer.svelte';
    import Tabs   from './shared/Tabs.svelte';
    import CreatePollForm from './lib/CreatePollForm.svelte';

    // tabs
    let items = [
        'Current Polls',
        'Add New Poll'
    ];
    let activeItem = 'Current Polls';

    const tabChange = (e) => {
        activeItem = e.detail;
    }
</script>

<Header/>
<main>
    <Tabs {items} {activeItem} on:tabChanged={tabChange}/>
    {#if activeItem === 'Current Polls'}
        <p>Poll list component goes here</p>
    {:else if activeItem === 'Add New Poll'}
        <CreatePollForm/>
    {/if}
</main>
<Footer/>


<style>
    main {
        max-width: 960px;
        margin: 40px auto;
    }
</style>