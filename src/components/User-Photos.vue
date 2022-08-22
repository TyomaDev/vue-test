<template>

  <div class="MainPhotos">
    <!-- loader -->
      <loader v-if="loading"/>
    <!-- /loader -->
    <!-- show -->
    <div v-else>
      <!-- gallery -->
      <div v-if="ImgisOpen === null" class="PhotosBlock">
        <div class="OnePhotoBlock" v-for="Photo in addedPhotos" v-on:click="openPhoto(Photo.id)">
          <img v-bind:src="Photo.url" alt="Photo">
          <h3>id: {{Photo.id}}</h3>
        </div>
      </div>
      <!-- one photo -->
      <div v-else class="OnePhotoOpen">
          <img v-bind:src="openedPhoto.url" alt="Photo">
          <h1 v-on:click="closePhoto()">&#10006;</h1>
          <div>
            <h3>Comment</h3>
            <textarea v-model="textAreaPhoto"></textarea>
            <p>Write a few sentences about the photo.</p>
          </div>
          <button v-on:click="sendCom">Save</button>
      </div>
      <!-- /show -->
    </div>
  </div>

</template>
<script>

import axios from 'axios'
import loader from '@/components/loader.vue'
const url = 'https://boiling-refuge-66454.herokuapp.com/images'

export default {
  data(){
    return{
      ImgisOpen: null,
      addedPhotos: [],
      openedPhoto:  [],
      textAreaPhoto: '',
      loading: true

    }
  },
  components:{
    loader
  },
  mounted(){
    axios.get(url).then(response => this.addedPhotos = response.data).then(setTimeout(() => {this.loading = false}, "500"))
  },
  
  methods: {
    openPhoto(id){
      this.loading = true
      
      this.ImgisOpen = id,
      axios.get(url + '/' + this.ImgisOpen).then(response => this.openedPhoto = response.data).then(setTimeout(() => {this.loading = false}, "300"))
      
    },
    closePhoto(){
      this.ImgisOpen = null,
      axios.get(url + '/').then(response => this.openedPhoto = response.data)
    },
    sendCom(){
      axios.post((url + '/' + this.ImgisOpen + '/comments'), {id: 1, text: this.textAreaPhoto, data: 2}).catch((e)=>{console.log(e)}),
      // axios.post((url + '/' + this.ImgisOpen), { text: this.textAreaPhoto}),
      this.textAreaPhoto = ''

    }
  }
   
  }

</script>

<style scope>

.PhotosBlock{
  width: 100%;
  margin-top: 2.5rem;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 330px);
  justify-items: center;
}
.OnePhotoBlock{
  width: 430px;
}
.OnePhotoBlock>img{
  width: 100%;
  border-radius: 6px;
  cursor: pointer;
  object-fit: cover;	
}
.OnePhotoBlock>img:hover{
  opacity: 0.9;
  transition:opacity 0.3s;
}
h3{
  margin: 0.5rem 0;
  font-weight: 600;
  font-size: 14px;
}
p{
  font-weight: 400;
  font-size: 14px;
  color: #6B7280;
  margin-top: 0.5rem;
}
.OnePhotoOpen{
  display: flex;
  flex-flow: column;
  justify-content: center;
  background-color: #fff;
  margin: 3rem auto;
  border-radius: 8px;
  width: 80%;
  position: relative;
}
h1{
  position: absolute;
  top: 20px;
  right: 35px;
  cursor: pointer;
  font-size: 36px;
  color: rgb(0, 0, 0);
  transition: color 0.3s;
}
h1:hover{
  color: #6B7280;
  transition: color 0.3s;
}
.OnePhotoOpen>img{
  width: 405px;
  height: 405px;
  object-fit: cover;	
  box-shadow: 0px 25px 50px -12px rgba(0, 0, 0, 0.25);
  border-radius: 24px;
  margin: 2rem auto;
}
.OnePhotoOpen>div{
  width: 50%;
  margin: auto;
  margin-bottom: 2rem;
}
.OnePhotoOpen>div>textarea{
  max-width: 100%; 
  min-width: 100%;
  min-height: 105px;
  border: 1px solid#D1D5DB;
  outline:none;
  border-radius: 6px;
  padding: 10px;
}
.OnePhotoOpen>div>textarea:focus-visible{
  border: 1px solid rgb(186, 190, 195)
}
.OnePhotoOpen>button{
  padding: 10px 15px;
  background-color: #4F46E5;
  box-shadow: 0px 20px 25px -5px rgba(0, 0, 0, 0.1), 0px 10px 10px -5px rgba(0, 0, 0, 0.04);
  color: #fff;
  border-radius: 6px;
  border: none;
  cursor: pointer;
  margin:0 auto;
  margin-bottom: 2rem;
  transition:background-color 0.3s;
}
.OnePhotoOpen>button:hover{
  background-color: rgb(95, 95, 95);
  transition:background-color 0.3s;
}

/* media */
@media screen and (max-width: 1440px){
    .InfoBlock{
        width: 80%;
    }
    .InfoBlock>img{
      width: 80%;
      margin: 0 auto;
    }
    .InfoBlock__User>div{
      margin-left: 15rem !important;
    }
    /*  */
    .PhotosBlock{
        width: 100%;
        margin-top: 2.5rem;
        display: flex;
        flex-wrap: wrap;

        justify-content: center;
    }
    .OnePhotoBlock{
        margin: 1rem 2rem;
    }
    
}
@media screen and (max-width: 1200px){
    .InfoBlock{
        width: 100%;
    }
    .InfoBlock>img{
      width: 100%;
      margin: 0 auto;
    }
    .InfoBlock__User>div{
      margin-left: 5rem !important;
    }  
}
@media screen and (max-width: 768px){
    .InfoBlock{
        width: 100%;
    }
    .InfoBlock>img{
      object-fit: cover;	
      width: 100%;
      height: 150px;

      margin: 0 auto;
    }
    .InfoBlock__User{
      width: 100%;
      margin-top: 1rem;
      display: flex !important;
      flex-flow: column !important;
      justify-content: center !important;
      align-items: center !important;
    }
    .InfoBlock__User>img{
      width: 7rem; 
      margin-top: -5rem;
    }
    .InfoBlock__User>h2{
      margin-left: 0 !important;
    }
    .InfoBlock__User>div{
      margin-left: 0 !important;
    }  
    .OnePhotoBlock {
    width: 60%;
    margin: 1rem auto;
    }
    .OnePhotoOpen>img{
    width: 15rem;
    height: 15rem;
    margin: 1rem auto;
    border-radius: 6px;
    }
    .OnePhotoOpen>div {
    width: 80%;
    margin: auto;
    margin-bottom: 2rem;
    }
    h1{
      top: auto;
      bottom: 15px !important;
      right: 15px;
    }
}
</style>
