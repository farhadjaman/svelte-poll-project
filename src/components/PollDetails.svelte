<script>
  import Card from "../shared/Card.svelte";
  import {createEventDispatcher} from 'svelte';
  
  export let poll;
  const dispatch=createEventDispatcher();

    //reactive poll
    $: totalVotes=poll.votesA+poll.votesB;
    $: percentA=Math.floor((poll.votesA/totalVotes)*100);
    $: percentB=Math.floor((poll.votesB/totalVotes)*100);
    const handleVote=(option,id)=>{
         dispatch('vote',{
           option,
           id
         })
   }
    

</script>
<Card>
<div class="poll">
  <h3>{poll.question}</h3>
  <p>Total votes: {totalVotes}</p>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div class="answer" on:click={()=>handleVote('a',poll.id)}>
    <div class="percent percent-a" style="width:{percentA}%"/>
    <span>{poll.answerA} ({poll.votesA})</span>
  </div>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div class="answer"  on:click={()=>handleVote('b',poll.id)}>
    <div class="percent percent-b" style="width:{percentB}%"></div>
    <span>{poll.answerB} ({poll.votesB})</span>
  </div>
</div>
</Card>

<style>
  h3{
    margin: 0;
    color: #555;
  }
  p{
    margin-top:6px;
    font-size: 14px;
    color: #aaa;
    margin-bottom: 30px;
  }
  .answer{
    background-color: #fafafa;
    cursor: pointer;
    margin: 10px auto;
    position: relative;
  }
  .answer:hover{
    cursor: pointer;
    opacity: 0.6;
  }
  span{
    display: inline-block;
    padding: 10px 20px;
  }

  .percent{
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;

  }
  .percent-a{
    background-color: #e4411930;
    border-left: 4px solid #e44119;
  }
  .percent-b{
    background-color: #21f36730;
    border-left: 4px solid #21f367;
  }
</style>