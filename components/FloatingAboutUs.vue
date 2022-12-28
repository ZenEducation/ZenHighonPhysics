<template>
  <div class="styling">
    <div>
      <div class="container">
        <div class="avatar">
          <a href="https://codepen.io/MarioDesigns/">
            <img
              id="img1"
              src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/751678/skytsunami.png"
              alt="Skytsunami"
            />
          </a>
        </div>
        <div class="content">
          <h1>Floating CSS animation</h1>
          <p>Follow me on:</p>
          <p id="spana">
            <span
              ><a
                href="https://twitter.com/MDesignsuk"
                id="imgcol"
                target="_blank"
                ><font-awesome-icon icon="fa-brands fa-twitter"
              /></a>
            </span>
            <span
              ><a
                href="https://github.com/Mario-Duarte/"
                id="imgcol"
                target="_blank"
                ><font-awesome-icon
                  icon="fa-brands fa-github"
                ></font-awesome-icon></a
            ></span>
            <span
              ><a
                href="https://bitbucket.org/Mario_Duarte/"
                id="imgcol"
                target="_blank"
                ><font-awesome-icon
                  icon="fa-brands fa-bitbucket"
                ></font-awesome-icon></a
            ></span>
            <span
              ><a
                href="https://codepen.io/MarioDesigns/"
                id="imgcol"
                target="_blank"
                ><font-awesome-icon
                  icon="fa-brands fa-codepen"
                ></font-awesome-icon></a
            ></span>
          </p>
          <p>BY: Mario Duarte</p>
        </div>
      </div>

      <a
        class="suppoprt-me"
        href="https://www.buymeacoffee.com/marioduarte"
        target="_blank"
        ><img
          id="img1"
          src="https://img.buymeacoffee.com/button-api/?text=Buy me a Coffee&nbsp&emoji=&slug=marioduarte&button_colour=FF5F5F&font_colour=ffffff&font_family=Cookie&outline_colour=000000&coffee_colour=FFDD00"
      /></a>
    </div>
  </div>
</template>

<script>
export default {
  name: "FloatingAboutUs",
};
</script>

<style scoped>
.styling {
  height: 100vh;
  margin: 0px;
  padding: 20px;
  font-family: "Helvetica", sans-serif;
  background: rgb(26, 188, 156);
  background: -moz-linear-gradient(
    -45deg,
    rgba(26, 188, 156, 1) 0%,
    rgba(142, 68, 173, 1) 100%
  );
  background: -webkit-linear-gradient(
    -45deg,
    rgba(26, 188, 156, 1) 0%,
    rgba(142, 68, 173, 1) 100%
  );
  background: linear-gradient(
    135deg,
    rgba(26, 188, 156, 1) 0%,
    rgba(142, 68, 173, 1) 100%
  );
}
h1 {
  font-size: 24px;
  margin: 10px 0 0 0;
  font-weight: lighter;
  text-transform: uppercase;
  color: #eeeeee;
}

#imgcol {
  color: #cccccc;
}

p {
  font-size: 12px;
  font-weight: light;
  color: #333333;
}

@keyframes float {
  0% {
    box-shadow: 0 5px 15px 0px rgba(0, 0, 0, 0.6);
    transform: translatey(0px);
  }
  50% {
    box-shadow: 0 25px 15px 0px rgba(0, 0, 0, 0.2);
    transform: translatey(-20px);
  }
  100% {
    box-shadow: 0 5px 15px 0px rgba(0, 0, 0, 0.6);
    transform: translatey(0px);
  }
}

.container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.avatar {
  width: 150px;
  height: 150px;
  box-sizing: border-box;
  border: 5px white solid;
  border-radius: 50%;
  overflow: hidden;
  box-shadow: 0 5px 15px 0px rgba(0, 0, 0, 0.6);
  transform: translatey(0px);
  animation: float 6s ease-in-out infinite;
}

#img1 {
  width: 100%;
  height: auto;
}

span a {
  font-size: 18px;
  color: #cccccc;
  text-decoration: none;
  margin: 0 10px;
  transition: all 0.4s ease-in-out;
}
span a :hover {
  color: #ffffff;
}
.content {
  width: 100%;
  max-width: 600px;
  padding: 20px 40px;
  box-sizing: border-box;
  text-align: center;
}

.suppoprt-me {
  display: inline-block;
  position: fixed;
  bottom: 10px;
  left: 10px;
  width: 20vw;
  max-width: 250px;
  min-width: 200px;
  z-index: 9;
}
</style>
