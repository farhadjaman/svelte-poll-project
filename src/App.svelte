<script>
import Header from "./components/Header.svelte";
import Footer from "./components/Footer.svelte";
import CreatePollForm from "./components/CreatePollForm.svelte";
import PollList from "./components/PollList.svelte"
import Tabs from "./shared/Tabs.svelte";
let items=['Current Polls','Add New Poll']
let activeItem='Current Polls'
const tabChange=(e)=>{
	activeItem=e.detail
}

//polls
let polls=[
	{
		id:1,
		question:'Python or Javascript?',
		answerA:'Python',
		answerB:'Javascript',
		votesA:9,
		votesB:15
	}
]

const handleAddPoll=(e)=>{
	console.log("comming ere")
   polls=[...polls,e.detail]
	 console.log(polls)
}
</script>
<Header />
<main>
	<Tabs {items} {activeItem} on:tabChange={tabChange}/>
	{#if activeItem==='Current Polls'}
	<PollList {polls} />
	{:else}
		<CreatePollForm on:addPoll={handleAddPoll}/>
	{/if}
</main>
<Footer />


<style>
	main{
		max-width: 960px;
		margin:40px auto;
	}
</style>