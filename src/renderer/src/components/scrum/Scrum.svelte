<script>
  import { questions } from './questions.js'
  let currentQuestion = 0
  let score = 0
  let showExplanation = false
  let userAnswer = null

  // Initialize the visibility state
  let isVisible = true
  let isCorrect = false

  // Function to toggle the visibility
  function toggleVisibility() {
    isVisible = !isVisible
  }

  function submitAnswer() {
    if (userAnswer === questions[currentQuestion].answer) {
      score += 1
      isCorrect = true
    } else {
      isCorrect = false
    }
    showExplanation = true
  }

  function nextQuestion() {
    showExplanation = false
    userAnswer = null
    currentQuestion += 1
  }
</script>

<div class="grid-flow-row bg-white text-black p-1 rounded">
  <div class=" p-5 bg-slate-300 rounded">
    {#if currentQuestion < questions.length}
      <div>
        <h2 class="text-2xl my-4 font-bold">Question {currentQuestion + 1} :</h2>
        <p class="text-2xl my-2 font-semibold">{questions[currentQuestion].question}</p>
        {#each questions[currentQuestion].choices as choice, index}
          <label class="text-xl my-2 p-2">
            <input class="my-4" type="radio" bind:group={userAnswer} value={index} />
            {choice} <br />
          </label>
        {/each}

        <button
          class:hidden={!isVisible}
          class:show={isVisible}
          class="flex mx-auto w-full my-4 text-2xl border-8 bg-white border-blue-700 font-extrabold rounded p-2"
          on:click={() => {
            submitAnswer()
            toggleVisibility()
          }}
          disabled={userAnswer === null}
        >
          Soumettre La Réponse
        </button>

        {#if showExplanation}
          <p
            class:customresgreen={isCorrect}
            class:customresred={!isCorrect}
            class=" font-bold text-xl my-2"
          >
            {questions[currentQuestion].explanation}
          </p>
          <button
            class:customquestiongreen={isCorrect}
            class:customquestionred={!isCorrect}
            class="text-center flex mx-auto my-4 text-2xl border-8 bg-white font-extrabold rounded p-2"
            on:click={() => {
              nextQuestion()
              toggleVisibility()
            }}>Question Suivante</button
          >
        {/if}
      </div>
    {:else}
      <div>
        <h1 class="text-3xl font-semibold my-2">Quiz Complete!</h1>
        <p class="text-2xl font-bold text-center my-2">Your score: {score} / {questions.length}</p>
      </div>
    {/if}
  </div>
</div>

<style>
  /* Define the hidden and show classes */
  .hidden {
    display: none;
  }
  .show {
    display: inline-block;
  }

  .customresgreen {
    color: green;
  }

  .customresred {
    color: red;
  }

  .customquestiongreen {
    border-color: greenyellow;
  }

  .customquestionred {
    border-color: red;
  }
</style>
