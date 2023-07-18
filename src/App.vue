<template>
  <div id="app">
    <div>Headbreaker from Vue</div>
    <div id="puzzle"></div>
  </div>
</template>

<script>
import headbreaker from 'headbreaker';

const drawPuzzle = () => {
  const autogen = new headbreaker.Canvas('puzzle', {
    width: 800,
    height: 650,
    pieceSize: 100,
    proximity: 20,
    borderFill: 10,
    strokeWidth: 2,
    lineSoftness: 0.18,
    painter: new headbreaker.painters.Konva(),
  });

  autogen.autogenerate({
    horizontalPiecesCount: 2,
    verticalPiecesCount: 2,
    metadata: [
      { color: '#B83361' },
      { color: '#B87D32' },
      { color: '#A4C234' },
      { color: '#37AB8C' },
    ],
  });

  autogen.draw();
};

export default {
  mounted() {
    drawPuzzle()
  },
};
</script>