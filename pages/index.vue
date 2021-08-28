<template>
  <div class="page home">
    <div class="container">
      <div class="holder">
        <div class="draggable" draggable="true"></div>
        <div class="column left">
          <h1>Artist 1</h1>
          <p class="typewriter left">
            This is a small demo for a storytelling concept
          </p>
        </div>
        <div class="column right">
          <h1>Artist 2</h1>
          <p class="typewriter right">
            You can match with an artist bij dragging the LP
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
// Typewriter effects
// https://css-tricks.com/snippets/css/typewriter-effect/
import Vue from "vue";

export default Vue.extend({
  computed: {},
  methods: {},
  mounted() {
    const columns = document.querySelectorAll('.column');

    columns.forEach(column => {
      column.addEventListener('dragenter', () => {
        column.classList.add('hover')
      })

      column.addEventListener('dragleave', () => {
        column.classList.remove('hover')
      })
    })
  }
});
</script>

<style lang="scss" scoped>
.home {
  height: 100vh;
  background-color: #cecece;
}

.container {
  height: 100%;
}

.holder {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  color: #efefef;

  @media (min-width: 0px) and (max-width: 1024px) {
    flex-direction: column;
  }

  .draggable {
    position: absolute;
    width: 100px;
    height: 100px;
    background-image: url('@/assets/images/vinyl.png');
    background-repeat: no-repeat;
    background-position: center;
    background-size: contain;
    opacity: 1 !important;
    z-index: 999;
    cursor: pointer;
  }

  .column {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
    height: 100%;
    font-family: "Lato";
    opacity: 0.6;
    transition: all 0.2s ease-in-out;
    user-select: none;

    &.hover {
      opacity: 1;
    }

    &:hover {
      opacity: 1;
    }

    &.left {
      background-color: #3b185f;
    }

    &.right {
      background-color: #a12568;
    }

    h1 {
      pointer-events: none;
    }

    .typewriter {
      pointer-events: none;
      white-space: nowrap;
      overflow: hidden;
      border-right: 2px solid white;

      &.left {
        width: 20.5em;
        opacity: 0;
        animation: type 5s steps(48, end),
          blink 0.5s step-end infinite alternate;
        animation-fill-mode: forwards;
      }

      &.right {
        width: 21.3em;
        opacity: 0;
        animation: type 5s steps(48, end),
          blink 0.5s step-end infinite alternate;
        animation-fill-mode: forwards;
      }
    }
  }
}

@keyframes type {
  0% {
    width: 0;
  }
  1% {
    opacity: 1;
  }
  100% {
    opacity: 1;
  }
}

@keyframes blink {
  50% {
    border-color: transparent;
  }
}
</style>>

</style>
