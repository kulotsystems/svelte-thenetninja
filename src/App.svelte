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


    const tabChange = (e) => {
        activeItem = e.detail;
    };

    const addPoll = (e) => {
        // const poll = e.detail;
        // polls = [poll, ...polls];
        // console.log(polls);
        activeItem = 'Current Polls';
    };

    // const handleVote = (e) => {
    //     const {id, option} = e.detail;
    //
    //     let copiedPolls = [...polls];
    //     let upvotedPoll = copiedPolls.find((poll) => poll.id === id);
    //     if(option === 'a') {
    //         upvotedPoll.votesA += 1;
    //     }
    //     else if(option === 'b') {
    //         upvotedPoll.votesB += 1;
    //     }
    //
    //     polls = copiedPolls;
    // };
</script>

<Header/>
<main>
    <Tabs {items} {activeItem} on:tabChanged={tabChange}/>
    {#if activeItem === 'Current Polls'}
        <!--<PollList on:vote={handleVote}/>-->
        <PollList/>
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