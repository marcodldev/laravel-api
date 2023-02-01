<template>
	<div>

    <WorkInProgress />

    <div>
        <ul>
            <li v-for="elem in posts" :key="elem.id">{{ elem.title }}</li>
        </ul>
    </div>
	</div>
</template>

<script>

import WorkInProgress from "../components/WorkInProgress.vue"

export default{
	name: "App",
	components: {

        WorkInProgress
	//inserire futuri componenti
	},
    data(){
        return{
            posts: []
        }
    },
    mounted(){
        this.getPosts();
    },
    methods : {
        getPosts(){
            axios.get('http://localhost:8000/api/posts')
                .then((res) => {
                    this.posts = res.data
                })
        }
    }
}
</script>
