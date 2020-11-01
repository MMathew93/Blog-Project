<template>
  <div class="about">
    <HeaderComponent />
    <div>
      <section class="content">
        <img
          class="itsame"
          src="@/assets/itsame.jpg"
          alt="a sad man staring into the void"
        />
        <h2>
          "Alright after I finish learning Javascript I'm going to start
          learning Python, and maybe even a little Java!"
          <br />
          -Mathew McKinney Nov 2019
        </h2>
        <p class="aboutme">
          How naive I was...Hello, my name is Mathew Mckinney and I'm studying
          to be a Full stack Javascript Web developer/Software
          developer/Sometype of engineer, or honestly whatever a company needs
          to hire me for! I started my venture back in November of 2019 after
          having a real heart to heart with myself where I realized I needed to
          start making some changes.
        </p>
        <p class="aboutme">
          Before I got swept up into adulthood paying bills and rent I was
          previously studying for A+ certification and trying to find a position
          within the IT world. I started googling and asking Reddit what kind of
          work someone like me could learn without having to quite my full time
          job and just put forth the work, and programming popped up. Having
          many friends already in the field helped me make a decision and start
          my grind to a new opportunity, you could say the rest is history!
        </p>
        <p class="aboutme">
          If you have questions, want to hire me, or just hang out, reach out to
          me on any of my social media outlets. Thanks for stopping by!
        </p>
        <div class="social">
          <span class="icon has-text-info">
            <a class="links" href="https://www.facebook.com/mathew.mckinney">
              <i class="fab fa-facebook"></i>
            </a>
          </span>
          <span class="icon has-text-success">
            <a class="links" href="https://twitter.com/CallMeLyndexer">
              <i class="fab fa-twitter"></i>
            </a>
          </span>
          <span class="icon has-text-warning">
            <a class="links" href="https://github.com/MMathew93">
              <i class="fab fa-github-alt"></i>
            </a>
          </span>
          <span class="icon has-text-danger">
            <a class="links" href="mailto:mckinney.m93@gmail.com">
              <i class="fas fa-envelope"></i>
            </a>
          </span>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import HeaderComponent from "@/components/HeaderComponent";

export default {
  name: "About",
  components: {
    HeaderComponent
  }
};
</script>

<style>
.content {
  display: flex !important;
  flex-direction: column;
  align-items: center;
}

h2 {
  font-size: 1.4em !important;
  color: black !important;
  margin: 15px;
}

.itsame {
  border-radius: 50%;
  margin: 50px 50px 0px 50px;
}

.aboutme {
  max-width: 900px;
  font-size: 21px;
  margin: 5px;
}

.social {
  display: flex;
  justify-content: space-between;
  min-width: 400px;
  margin: 5px;
}

.icon {
  font-size: 35px;
}

.links {
  color: inherit !important;
}
</style>
