<script>
  import PollDetails from "./PollDetails.svelte";
  export let polls=[];
  const handleVote=(e)=>{

    const {option,id}=e.detail;
    const poll=polls.find(p=>p.id===id);
    poll.votesA+=option==='a'?1:0;
    poll.votesB+=option==='b'?1:0;
    polls=[...polls];


  }
</script>
  
 <div class="poll-list">
    {#each polls as poll (poll.id)}
    <PollDetails {poll} on:vote={handleVote}/>
    {/each}
 </div>

 <style>
    .poll-list{
      display:grid;
      grid-template-columns: repeat(2,1fr);
      grid-gap:20px;
    }
   </style>