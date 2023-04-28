<script setup>
import axios from '@/http/axios-instance'
import {onMounted, reactive} from 'vue'

  let Data = reactive({ malumotlar: []})
  async function getDataFromApi() {
    try {
      const response = await axios.$http.get(`users`);
      Data.malumotlar = response.data.slice(0, 1)
    } catch (error) {
      console.error(error);
    }
  }

  let Posts = reactive([])
  async function getPostsFromApi(){
    const res = await axios.$http.get(`posts`);
        console.log(res.data.slice(0, 2));
    // if(Posts.malumotlar === []){
    //   try {
    //     const res = await axios.$http.get(`posts`);
    //     console.log(res.data.slice(0, 2));
    //     Posts.malumotlar = res.data.slice(0, 2)
    //   } catch (error) {
    //     console.error(error)
    //   }
    // }
  }


  let Language = 'English'
  function changeLang(){
    console.log('asiudg')
  }

  onMounted(() => {
    getDataFromApi()
  })

</script>

<template>
  <header>
    <nav class="navbar navbar-expand-lg bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Link</a>
            </li>
          </ul>

          

          <form class="d-flex">

          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle btn btn-outline-success"
                href="#" role="button"
                data-bs-toggle="dropdown"
                aria-expanded="false"
                style="margin-right: 7px;"
                >
                {{Language}}
              </a>
              <ul class="dropdown-menu">
                <li><a class="dropdown-item" href="#" value="uzb">O'zbekcha</a></li>
                <li><a class="dropdown-item" href="#" value="rus">Русский</a></li>
                <li><a class="dropdown-item" href="#" value="eng">English</a></li>
              </ul>
            </li>
          </ul><img type="button" src="./assets/icons/icons8-incoming-call-67.png" alt=""
          style="width: 40px; height: 40px; margin: 3px;">
          <img type="button" src="./assets/icons/icons8-telegram-94.png" alt=""
          style="width: 45px; height: 45px;">
          <img type="button" src="./assets/icons/icons8-instagram-48.png" alt=""
          style="width: 45px; height: 45px;">
          </form>
        </div>
      </div>
    </nav>

    <button type="button" class="btn btn-primary">button</button>
    <button type="button" class="btn btn-primary">button</button>
      <div v-for="(item, id) in Data.malumotlar" :key="id">
        <div>id: {{item.id}}</div>
        <div>name: {{item.name}}</div>
        <div>username: {{item.username}}</div>
        <div>email: {{item.email}}</div>
        <div>address: {{item.address.street}}</div>
        <div>phone: {{item.phone}}</div>
        <div>company: {{item.company.name}}</div>
      </div>
    <button type="button" class="btn btn-secondary" data-toggle="modal" data-target="#exampleModalCenter" @click.prevent="getPostsFromApi">
      hello world
    </button>

    <!-- Button trigger modal -->
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#staticBackdrop">
      Launch static backdrop modal
    </button>

    <!-- Modal -->
    <div class="modal fade" id="staticBackdrop" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="staticBackdropLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h1 class="modal-title fs-5" id="staticBackdropLabel">Modal title</h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            ...
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary">Understood</button>
          </div>
        </div>
      </div>
    </div>


    <div v-for = "(item, id) in Posts" :key="id">
      <div>id: {{item.id}}</div>
      <div>title: {{item.title}}</div>
      <div>body: {{item.body}}</div>
    </div>
  </header>
  <main>
    
  </main>
</template>

