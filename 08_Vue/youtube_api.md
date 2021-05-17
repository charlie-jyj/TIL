## 준비

- notion

https://www.notion.so/Youtube-API-key-031e096d383b4350a361527ee8420e84

- API key

```
AIzaSyAxMFWcJQCAB3X1zHYLMJ5nHcvup8z561g
```



- API Guide
- https://developers.google.com/youtube/v3/guides/implementation/search

## app

```vue
<template>
  <div class="container">
    <div class="row mt-5 mb-5">
      <div class="col-1"><img width="100%" :src="logo" alt=""></div>
      <div class="col-10 d-flex align-items-end"><SearchBar @fetch-videos="onFetchVideos"/></div>
      <div class="col-1"></div>
    </div>
   
   
    <div class="row">
      <div class="col-12 col-md-8">
          <VideoDetail :video="video"/>
      </div>
      <div class="col-12 col-md-4">
         <VideoList :videos="videos" @click-video="onClickVideo"/>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from '@/components/SearchBar'
import VideoList from '@/components/VideoList'
import VideoDetail from '@/components/VideoDetail'

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      videos: [],
      video: {},
      logo: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTtJF7SUTRrMxFZ_umQeGvLBQrqA4VI_pRrTQ&usqp=CAU',
    }
  },
  methods: {
    onFetchVideos(videos) {
      this.videos = videos
    },

    onClickVideo(video) {
      console.log(video)
      this.video = video
    }
  },
}
</script>

<style>

</style>
```

- emit 된 event 를 받아 prop 으로 다시 내려보낼 것



## main

```javascript
import Vue from 'vue'  // 위치명시 X : 내 위치의 vue 파일 찾기 => 없음 => node_modules 탐색
import App from './App.vue' // 위치명시 O : 내 위치에서 찾기

// h (vue render method) hyperscript = createElement
new Vue({
  // el: '#app', mount 하는 것과 같은데 시점이 다를 뿐
  render: h => h(App)
}).$mount('#app')  // index.html 의 div#app 에 붙이기 위함
```

- import 구문
  - 주소 명시하면 그 주소를 탐색한다
  - 주소 대신 이름을 명시하면 일치하는 파일을 찾아 위로 올라간다.
- Vue instance를 생성할 때 render 함수
  - `createElement`  함수가 인자로 들어온다
  - 콜백함수에 객체를 넘긴다.
  - h 는 상징성을 가진 문자일 뿐 의미하는 바는 createElement 함수
- `el` 과 mount 의 차이는 시점의 차이
  - 연결할 객체를 인지하는 시점이 el 은 객체가 생성될 때, 
  - mount 는 객체 생성 후 인 것

https://v3.vuejs.org/guide/render-function.html#h-arguments



## searchBar



### axios

```
$ npm install axios
```

- import 해서 사용해야 한다

```vue
<script>
import axios from 'axios'
const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
const URL = 'https://www.googleapis.com/youtube/v3/search'

export default {
  name: 'SearchBar',
  data() {
    return {
      query: '',
    }
  },
  methods: {
    onClick() {
      axios.get(URL, {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: this.query,
        }
      })
        .then(res => {
          this.$emit('fetch-videos', res.data.items)
        })
        .catch(err => console.log(err))
    },
    onInput(event) {
      this.query = event.target.value
    }
  }
}
</script>
```





### API KEY 숨기기

- `.env.local`
  - 접두사 `VUE_APP_` 가 붙어야 인지할 수 있다.

```
VUE_APP_YOUTUBE_API_KEY=AIzaSyCL4MW47NluIqx8OM2RDB-HJglVoWZch4w
```



```
const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
```



https://cli.vuejs.org/guide/mode-and-env.html#modes





## Video List



### v-for 의 v-bind: key 

`:key` 사용하기

- v-for 가 즉각 반응하며 재정렬하는 상황에서
- vue 가 순서를 기억하기 위해서
- 가능하면 언제나 key를 추가한다
- 가장 unique 한 값을 key로 삼고 순서를 기억하게 한다.
- PK 와 유사하다

![image-20210511144247451](youtube_api.assets/image-20210511144247451.png)



- component 도 `v-for` 를 가질 수 있다.
  - **반복문을 통해 접근한 각 item을 bind하여 prop으로 넘길 수 있다.**

```vue
<template>
  <ul class="list-group">
    <VideoListItem v-for="video in videos" :key="video.etag" :video="video" @click-video="onClickVideo"/>
  </ul>
</template>
```



- VideoListItem은 `li` 로 감싼다.

```vue
<template>
  <li class="list-group-item video-item list-group-item-action" @click="onClickItem">
    <img class="me-3" :src="videoImgUrl" alt="video-thumbnail">
    <p class="media-body overflow-ellipsis">
      {{ video.snippet.title }}
    </p>
  </li>
</template>
```





## Bootstrap

> cdn 을 넣어도 좋다



```
npm install bootstrap
```



![image-20210511151059300](youtube_api.assets/image-20210511151059300.png)



### ratio

- `iframe` 관련한 class 도 존재한다.
  - 비율을 쉽게 조정할 수 있다.

```html
<div class="ratio ratio-16x9">
  <iframe src="https://www.youtube.com/embed/zpOULjyy-n8?rel=0" title="YouTube video" allowfullscreen></iframe>
</div>
```







## VideoDetail

- 객체의 isEmpty 확인하기
  - 최초에 load 했을 때는 prop이 {} 빈객체 이기 때문에
  - 빈 객체에서 속성값을 get 하려 할 때 오류가 발생한다
  - 따라서 prop 이 아직 전달되지 않았을 때, 처리가 필요하다.



```vue
<div v-if="isVideoEmpty">  
    <p v-text="video.snippet.title" class="h4 mb-3"></p>
    <div class="mt-4 border" v-text="video.snippet.description">
    </div>
  </div>
```



```javascript
 computed: {
    isVideoEmpty() {
    return !!Object.keys(this.video).length
    }
  }
```

- length의 반환값이 숫자이므로 !(not) 하면 boolean 으로 형변환하면서 값을 반전시키므로 ! 를 한 번 더 붙인다.



### lodash

```
$ npm i -g npm
$ npm i --save lodash
```

- import 해서 사용한다.
- `_.unescape`
  - escape 문자 구현을 위한 함수

```javascript
 videoTitle() {
      return _.unescape(this.video.snippet.title)
    }
```

![image-20210512004838509](youtube_api.assets/image-20210512004838509.png)





## 배포

```
npm run build
```

- dist 폴더의 내용을 
- github.io에 push 했더니 배포가 끝