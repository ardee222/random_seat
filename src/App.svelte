<script>
  import data from "./data/data.json"
  let student_data = data;
  let today = new Date();
  let year = today.getFullYear();
  let month = today.getMonth()+1;
  let date = today.getDate();
  let data_names

  function shuffle(){
    for(let i=20;i>1;i--){
      setTimeout(()=>{
      student_data = student_data.sort(() => {return Math.random() - 0.5})
      data_names = []
      student_data.forEach((element)=>{data_names.push(element.name)})
      },i*200)}
  }
  let row1,row2,row3,row4,row5,row6,row7
  $: row1 = student_data.slice(0,5);
  $: row2 = student_data.slice(5,10);
  $: row3 = student_data.slice(10,16);
  $: row4 = student_data.slice(16,22);
  $: row5 = student_data.slice(22,28);
  $: row6 = student_data.slice(28,33);
  $: row7 = student_data.slice(33,39);
  let clicked = false;
  function change_board(){
    clicked = !clicked;
    let board = clicked ? "其實我叫黑板" : "綠板"
    document.getElementsByName('black_board')[0].innerText = board;
  }

  let come_on;
  $:come_on = true;
  //debugging
</script>

<!--bg-slate-700-->
{#if come_on}
<div on:mouseup={()=>{come_on = false}} class="flex justify-center items-center max-w-md w-full max-h-screen h-screen bg-slate-700 mx-auto flex flex-col">
  <div class="text-4xl text-white">四校加油</div>
</div>
{/if}
<main class="max-w-md w-full max-h-screen h-screen bg-slate-700 mx-auto flex flex-col">
  <div class="relative m-4">
    <div class="absolute top-0 right-0 text-white font-serif text-xs">{year}年{month}月{date}日</div>
  </div>
  <div name="container" class="flex my-8 h-72 mx-auto font-serif border px-4 py-8 space-x-3">
    <div name="left_container" class="relative flex h-full">
      <div name="row1" class="flex flex-col">
        {#each row1 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div name="row2" class="flex flex-col">
        {#each row2 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>

      <div class="absolute w-full bottom-0 ">
        <div class="border text-center text-[#85A894]">門口</div>
      </div>
    </div>
    
    <div name="center_container"class="flex relative">
      <div name="row3" class="flex flex-col">
        {#each row3 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div name="row4" class="flex flex-col">
        {#each row4 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div name="row5" class="flex flex-col">
        {#each row5 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div class="absolute w-full bottom-0 ">
        <div name="black_board" class="border text-center text-[#85A894]"
        on:mouseup={change_board}
        class:text-green-300="{clicked === true}">綠板</div>
      </div>
    </div>

    <div name="right_container" class="flex relative">
      <div name="row6" class="flex flex-col">
        {#each row6 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div name="row7" class="flex flex-col">
        {#each row7 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div class="absolute w-full bottom-0 ">
        <div class="border text-center text-[#85A894]">教壇</div>
      </div>
    </div>
  
  </div>
  <div on:mouseup={shuffle} class="flex items-center justify-center space-x-2 mx-auto border max-w-sm w-full font-serif hover:bg-white active:bg-white active:text-yellow-500 text-white">
    <div class="text-[#85A894] font-bold">抽</div>
    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="white" class="w-4 h-4">
      <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 12c0-1.232-.046-2.453-.138-3.662a4.006 4.006 0 00-3.7-3.7 48.678 48.678 0 00-7.324 0 4.006 4.006 0 00-3.7 3.7c-.017.22-.032.441-.046.662M19.5 12l3-3m-3 3l-3-3m-12 3c0 1.232.046 2.453.138 3.662a4.006 4.006 0 003.7 3.7 48.656 48.656 0 007.324 0 4.006 4.006 0 003.7-3.7c.017-.22.032-.441.046-.662M4.5 12l3 3m-3-3l-3 3" />
    </svg>
  </div>
</main>

<style>

</style>
