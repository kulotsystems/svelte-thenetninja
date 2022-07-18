<script>
    import Header from './lib/Header.svelte';
    import Footer from './lib/Footer.svelte';
    import Tabs   from './shared/Tabs.svelte';
    import CreatePollForm from './lib/CreatePollForm.svelte';
    import PollList       from './lib/PollList.svelte';

    // tabs
    let items = [
        'Current Polls',
        'Add New Poll'
    ];
    let activeItem = 'Current Polls';

    let polls = [
        {
            id      : 1,
            question: 'Python or JavaScript?',
            answerA : 'Python',
            answerB : 'JavaScript',
            votesA  : 9,
            votesB  : 15
        }
    ];

    const tabChange = (e) => {
        activeItem = e.detail;
    }

    const addPoll = (e) => {
        const poll = e.detail;
        polls = [poll, ...polls];
        console.log(polls);
        activeItem = 'Current Polls';
    }
</script>

<Header/>
<main>
    <Tabs {items} {activeItem} on:tabChanged={tabChange}/>
    {#if activeItem === 'Current Polls'}
        <PollList {polls}/>
    {:else if activeItem === 'Add New Poll'}
        <CreatePollForm on:pollAdded={addPoll}/>
    {/if}
</main>
<Footer/>


<style>
    main {
        max-width: 960px;
        margin: 40px auto;
    }
</style>