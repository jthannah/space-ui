<script>
    export let menuActive = false;
</script>

<div id="nav-sidebar" class:active="{menuActive}">
  <button id="menu-icon" on:click={() => menuActive = !menuActive} href="#">
    <span class="line line-1"></span>
    <span class="line line-2"></span>
    <span class="line line-3"></span>
  </button>
  <p>MENU</p>
  <div id="sidebar"></div>
</div>

<style lang="stylus">
  #nav-sidebar {
    align-items: center;
    box-shadow: 2px 0 8px -1px rgba(0,0,0,0.7);
    display: flex;
    flex-direction: column;
    height: 100vh;
    flex: 1 1 50px;
    position: fixed;
		z-index: 5;

    &.active {
      box-shadow: none;

      #sidebar {
          filter: opacity(0);
      }
    }

    p {
      color: #ffffff;
      font-size: 0.75rem;
      margin: 0;
      z-index: 1;
    }
  }

  #sidebar {
		background: linear-gradient(to bottom right, rgba(186, 30, 104, 0.9), rgba(86, 67, 253, 0.9));
    filter: opacity(1);
    transition: filter 0.3s;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
  }

  background = #3d566e;
  color = #ecf0f1;

  height-icon = 20px;
  width-line = 40px;
  height-line = 5px;

  transition-time = 0.4s;
  rotation = 45deg;
  translateY = (height-icon / 2);
  translateX = 0;

  #menu-icon {
    background: none;
    border: none;
    outline: none;
    width: width-line;
    height: height-icon;
    display: block;
    position: relative;
    margin: 1rem 0.5rem 0.5rem;
    top: 0;
    z-index: 2;

    &:hover {
      cursor: pointer;
    }

    .line {
      display:block;
      background:color;
      width: width-line;
      height: height-line;
      position:absolute;
      left:0;
      border-radius:(height-line / 2);
      transition: all transition-time;
      -webkit-transition: all transition-time;
      -moz-transition: all transition-time;

      &.line-1 {
        top:0;
      }
      &.line-2 {
        top:50%;
      }
      &.line-3 {
        top:100%;
      }
    }
    &:hover, &:focus {
       .line-1 {
          transform: translateY(height-line / 2 * -1);
          -webkit-transform: translateY(height-line / 2 * -1);
          -moz-transform: translateY(height-line / 2 * -1);
       }
      .line-3 {
          transform: translateY(height-line / 2);
          -webkit-transform: translateY(height-line / 2);
          -moz-transform: translateY(height-line / 2);
      }
    }
  }

  #nav-sidebar.active #menu-icon {
    .line-1 {
      transform: translateY(translateY) translateX(translateX) rotate(rotation);
      -webkit-transform: translateY(translateY) translateX(translateX) rotate(rotation);
      -moz-transform: translateY(translateY) translateX(translateX) rotate(rotation);
    }
    .line-2 {
      opacity:0;
    }
    .line-3 {
      transform: translateY(translateY * -1) translateX(translateX) rotate(rotation * -1);
      -webkit-transform: translateY(translateY * -1) translateX(translateX) rotate(rotation * -1);
      -moz-transform: translateY(translateY * -1) translateX(translateX) rotate(rotation * -1);
    }
  }
</style>