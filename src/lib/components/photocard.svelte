<script lang="ts">
  const mouseEnter = (e: MouseEvent) => {
    const card = document.getElementById("card");
    if (card) {
      card.style.transform = "scaleY(1.1)";
    }
    console.log("enter");
  };

  const mouseLeave = (e: MouseEvent) => {
    const card = document.getElementById("card");
    if (card) {
      card.style.transform = "scaleY(1)";
    }
    console.log("leaving");
  };
</script>

<html lang="en">
    <body>
        <div class="step"></div>
    </body>
</html>

<style>
 html, body {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.step {
  position: relative;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  height: 80px;
  width: 80px;
  border: 8px solid #0460CC;
 
  background: #FFFFFF;
  box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.25);
}
.step span {
  position: relative;
  font-size: 72px;
  top: 5px;
  left: -5px;
}
.step::after {
  opacity: 0;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  content: "";
  height: 100%;
  width: 100%;
  background: #0460CC;
  -webkit-animation-name: ripple;
          animation-name: ripple;
  -webkit-animation-duration: 3s;
          animation-duration: 3s;
  -webkit-animation-delay: 0s;
          animation-delay: 0s;
  -webkit-animation-iteration-count: infinite;
          animation-iteration-count: infinite;
  -webkit-animation-timing-function: cubic-bezier(0.65, 0, 0.34, 1);
          animation-timing-function: cubic-bezier(0.65, 0, 0.34, 1);
  z-index: -1;
}

@-webkit-keyframes ripple {
  from {
    opacity: 1;
    transform: scaleY(0.75);
  }
  to {
    opacity: 0;
    transform: scaleY(2);
  }
}

@keyframes ripple {
  from {
    opacity: 1;
    transform: scaleY(0.75);
  }
  to {
    opacity: 0;
    transform: scaleY(2);
  }
}
</style>
