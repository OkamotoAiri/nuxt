<template>
  <div class="menu-list" v-cloak>
        <div class="sp-menu" @click="showMenu()">
          <span class="material-icons" id="open" v-show="!activeBtn">menu
          <p class="m-logo">MENU</p></span>
          <span class="material-icons" id="close" v-show="activeBtn">close
            <p class="c-logo">CLOSE</p>
          </span>
        </div>
    
      <transition name="menu" >
        <div class="menu" v-show="activeBtn">
          <ul>
            <!-- <ul @click="activeBtn = false"> -->
              <li><nuxt-link to="/task">TOP</nuxt-link></li>
              <li><nuxt-link to="/task/form">顧客登録</nuxt-link></li>
              <li><nuxt-link to="/task/list">顧客一覧</nuxt-link></li>
            </ul>
        </div>
      </transition>
    </div>
</template>

<script>

export default {
    data(){
      return{
        activeBtn:false,
        showMenu() {
          this.activeBtn = !this.activeBtn
        }
    }
}
}

</script>

<style>

#open,
#close {
  position: fixed;
  right: 25px;
  z-index: 3;
  color:#fff;
  font-size:36px;
  line-height:20px;
  cursor: pointer;
  transition: 0.4s ease;
}

.m-logo,
.c-logo {
  font-size: 11px;
  position: fixed;
  top:39px;
  right:25px;
}

.c-logo {
  font-size: 10px;
}

#close {
  color: black;
}


.menu{
  position: fixed;
  top: 0;
  right:0px;
  z-index: 2;
  width: 160px;
  height: 100%;
  padding: 64px 0;
  text-align: center;
  background: rgba(255,255,255,0.8);
}

.menu li {
  margin-top:24px;
  transform: translateY(16px);
  transition: opacity .3s, transform .3s;
  font-weight: bold;
}

.menu li > a {
  display: block;
  line-height: 50px;
  text-decoration: none;
  transition: all .2s;
  color: black;
}

.menu li > a:hover {
  color: white;
  font-size: 18px;
  transition: all .2s;
  background-color: rgb(99, 133, 247);
}

.menu-enter-active,
.menu-leave-active 
{
  transition: opacity 0.4s;
}

.menu-enter, .menu-leave-to {
  opacity: 0;
}

.menu-leave, .menu-enter-to {
  opacity: 1;
}

</style>
