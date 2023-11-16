<script setup>
import {ref, onMounted} from 'vue'
  
import CloseIcon from './icons/IconClose.vue'
import MenuIcon from './icons/IconMenu.vue'

const menu = ref(false)

const toggleMenu = () => {
  menu.value = !menu.value
}


 

  onMounted(() => {
    const header = document.querySelector('.header')
    const scrollWatcher = document.createElement('div')

    scrollWatcher.setAttribute('data-scroll-watcher', '')
    header.before(scrollWatcher)

    const navObserver = new IntersectionObserver((entries) => {
      header.classList.toggle('sticking', !entries[0].isIntersecting)
      console.log(entries)
    })
    navObserver.observe(scrollWatcher)

  })

</script>


<template>
  <header class="header" id="header">
    
    <nav class="nav container">
      <a href="#" class="nav__logo">
        <img src="../assets/logo.png" alt="" /> Fruit
      </a>

      <div class="nav__menu" :class="{show: menu}" id="nav-menu">
        <ul class="nav__list">
          <li class="nav__item">
            <a href=#home class="nav__link" >Home</a>
          </li>
          <li class="nav__item">
            <a href=#about class="nav__link">About Us</a>
          </li>
          <li class="nav__item">
            <a href=#popular class="nav__link">Popular</a>
          </li>
          <li class="nav__item">
            <a href=#join class="nav__link">Join Us</a>
          </li>
        </ul>

        <!-- Close button -->
        <div class="nav__close" id="nav-close" @click='toggleMenu'>
          <CloseIcon/>
        </div>

       
      <img src="../assets/branch-2.png" alt="" class="nav__img-1"/>
      <img src="../assets/fruit-line-1.png" alt="" class="nav__img-2"/>

      </div>

      <!-- Toggle  button -->
      <div class="nav__toggle"   id="nav-toggle" @click='toggleMenu'>
          <MenuIcon/>
      </div>
     
    </nav>
    
  </header>
</template>

