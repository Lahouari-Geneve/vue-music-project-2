<template>
<div class="container-fluid py-10 px-10" style="background-color:black;">
  <div class="row video-player">
    <div class="col-md-7 video-container embed-responsive embed-responsive-4by3">
      <iframe width="720" height="600" class="embed-responsive-item" :src="this.activeVideo.youtubeURL" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>  
    <div class="col-md-4 video-list" style="background-color:white;">
      <div @click="chooseVideo(video)" :key="video.id" v-for="video in videos" class="thumbnail">
        <div class="thumbnail-img shadow p-3 mb-5 bg-white rounded">
          <img :src="video.thumbnail" classe="shadow-2-strong" />
          <br />
        </div>
        <div class="thumbnail-info" >
          <h3>{{video.title}}</h3>
          <p>{{video.creator}}</p>
          <p class="thumbnail-views">{{video.views}} Views</p>
          <button class="fa fa-play crimson"></button>
        </div>
      </div>
    </div>
  </div>
  <div>
    <div class="col-md-12">
        <h3>{{this.activeVideo.title}}</h3>
        <p>{{this.activeVideo.views}} views</p>
        <p><button class="fa fa-thumbs-up" @click="addLike"></button>   {{this.activeVideo.likes}}
        <button class="fa fa-thumbs-down" @click="removeLike"></button>   {{this.activeVideo.dislikes}} </p>
        <br />
        <br />
        <br />
        <br />
        <br />
    </div>
  </div>
</div>
</template>

<script>
let videos = [
  {
    id: 1,
    title: "GNAT (Directed by Cole Bennett)",
    thumbnail: "https://i2.wp.com/nobetterlane.com/wp-content/uploads/2020/12/eminem-gnat-video.jpg?resize=1035%2C425&ssl=1",
    youtubeURL: "https://www.youtube.com/embed/EosMazKaPbU?list=PLyORnIW1xT6waC0PNjAMj33FdK2ngL_ik",
    creator: "Eminem",
    likes: 2200,
    dislikes: 220,
    views: 22000
  },
  {
    id: 2,
    title: "GIRL LIKE ME (Official Music Video)",
    thumbnail: "https://s3.amazonaws.com/images.imvdb.com/video/302288359725-black-eyed-peas-girl-like-me_music_video_ov.jpg?v=2",
    youtubeURL: "https://www.youtube.com/embed/vMLk_T0PPbk?list=PLyORnIW1xT6waC0PNjAMj33FdK2ngL_ik",
    creator: "Black Eyed Peas, Shakira",
    songlength: "3:54",
    likes: 1100,
    dislikes: 110,
    views: 11000
  },
  {
    id: 3,
    title: "AVEC TA ZOUZ (Clip Officiel)",
    thumbnail: "https://i.ytimg.com/vi/CPgS_VcLKT8/maxresdefault.jpg",
    youtubeURL: "https://www.youtube.com/embed/CPgS_VcLKT8",
    creator: "Therapie TAXI",
    likes: 3300,
    dislikes: 330,
    views: 33000
  },
  {
    id: 4,
    title: "Bohemian Rhapsody (Official Video Remastered)",
    thumbnail: "https://lescultivores.com/wp-content/uploads/2020/10/bohemian-rhapsody-intro.jpg",
    youtubeURL: "https://www.youtube.com/embed/fJ9rUzIMcZQ",
    creator: "Queen",
    likes: 4400,
    dislikes: 440,
    views: 44000
  },
  {
    id: 5,
    title: "Sweet Dreams (Are Made Of This) (Official Video)",
    thumbnail: "https://stack.com.au/wp-content/uploads/2020/03/Eurythmics_DavidMontgomery.jpg",
    youtubeURL: "https://www.youtube.com/embed/qeMFqkcPYcg",
    creator: "Eurythmics, Annie Lennox, Dave Stewart",
    likes: 5500,
    dislikes: 550,
    views: 55000
  }
];

export default {
  name: 'VideoPlayer',
  data () {
    return {
      videos,
      activeVideo: videos[0]
    }
  },
  methods:{
  chooseVideo(video){
      //SET VIDEO AS ACTIVE VIDEO
      this.activeVideo = video;
      //INCREASE THE VIDEOS VIEWS BY 1
      video.views += 1;
  },
  addLike(){
      //INCREASE THE LIKES BY 1
      this.activeVideo.likes += 1;
},
  removeLike(){
      //INCREASE THE DISLIKES BY 1
      this.activeVideo.dislikes += 1;
}
}
}
</script>

<style scoped>
  .thumbnail{
    display:flex;
  }
  .thumbnail img{
    width:250px;
}

.thumbnail-info{
    margin-left:20px;
}

.thumbnail h3{
    font-size:16px;
}

h3,
p{
    margin:0;
    padding:0;
    color: crimson;
}

.thumbnail-views{
    font-size:14px;
}

.video-container{
    margin-right:40px;
}

.row{
    display:flex;
    justify-content:space-between;
}

button{
    background:crimson;
    color:white;
    border:none;
    padding:10px 20px;
}

</style>