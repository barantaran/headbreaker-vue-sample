<template>
    <div id="puzzle"></div>
</template>

<script>
import headbreaker from 'headbreaker';
let appWidth = 900;

const drawPuzzle = () => {
  let puzzleImage = new Image();
  puzzleImage.src = '/photorealistic_face_of_ancient_daemon.png';
  puzzleImage.onload = () => {

    const autogen = new headbreaker.Canvas('puzzle', {
      width: appWidth,
      height: 900,
      pieceSize: 150,
      proximity: 20,
      borderFill: 15,
      strokeWidth: 5,
      lineSoftness: 0.18,
      painter: new headbreaker.painters.Konva(),
      image: puzzleImage
    });
    
    autogen.adjustImagesToPuzzleHeight();
    autogen.autogenerate({
      horizontalPiecesCount: 4,
      verticalPiecesCount: 4
    });
    
    autogen.shuffleGrid();
    autogen.draw();
  }
};

export default {
  mounted() {
    drawPuzzle()
  }
};
</script>
<style>
#app
{
  width: 900px;
  background-color: black;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  margin: auto;
  transform: translateY(-50%);
  border-radius: 50px;
}
</style>