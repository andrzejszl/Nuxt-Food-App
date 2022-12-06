<template>
    <section class="masthead" role="img" aria-label="Image Description">
    <h1>
        Nuxt Food App
    </h1>
        <button>
        See restaurants >
        </button>
    </section>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>
.masthead {
  width: 100%;
  height: 80vh;
  padding: 40px;
  overflow: hidden;
  background-size: cover !important;
  background: radial-gradient(ellipse at center, rgba(0,0,0,0) 0%, rgba(0,0,0,0) 48%, rgba(0,0,0,0.65) 100%), url(~assets/headerimg.jpg) no-repeat center center scroll;
}

h1 {
  font-style: normal;
  font-weight: bold;
  color: #eee;
  font-size: 8vmin;
  letter-spacing: 0.03em;
  line-height: 1;
  text-shadow: 1px 2px 4px rgba(0, 0, 0, 0.8);
  margin-bottom: 62px;
}
    
      
button {
  background: #098191;
  transition: background ease .25s;
  border-radius: 17px;
  display: inline-block;
  border: none;
  padding: 0.75rem 1.5rem;
  margin: 0;
  text-decoration: none;
  color: #ffffff;
  font-size: 1.2rem;
  cursor: pointer;
  text-align: center;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}
button:hover {
  background: #63b6b8
}
button:focus {
  outline: 1px solid #fff;
  outline-offset: -4px;
}
</style>