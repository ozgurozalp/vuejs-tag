<template>
    <div class="tag-container">
        <tag 
            v-for="(tag, index) in tags" 
            :tag="tag" 
            :index="index" 
            :key="index"
            :tagColor="color"
            @removeOneTagEvent="clicktToRemove($event)"
        />
        <input 
            type="text" 
            @keydown.enter="addTag" 
            @keydown.backspace="removeTag" 
            placeholder="Anahtar Kelime Giriniz"
        />
        <transition name="fade">
            <p class="error" v-if="error">Bu etiket daha önceden eklenmiş</p>
        </transition>
    </div>
</template>

<script>
import tag from './Tag';
export default {
    name: 'tags',
    props : {
        value : {
            required : false
        },
        color : {
            type : String,
            required : false,
            default : 'primary'
        }
    },
    data () {
        return {
            tags : [],
            error : false
        }
    },
    methods : {
        addTag(event){
            let data = event.target;
            let matchedTag = false;

            if (data.value.length > 0) {
                this.tags.forEach(tag => {
                    if (tag.toLowerCase() === data.value.toLowerCase()) {
                    matchedTag = true;
                    }
                });

                if(!matchedTag){
                    this.tags.push(data.value);
                    data.value = null;
                }else{
                    this.error = true;
                    setTimeout(() => {
                        this.error = false; 
                    }, 1500);
                }
            }     
        },
        removeTag(event){
            if (event.target.value.length <= 0) {
                this.tags.splice(this.tags.length - 1, 1); 
            }
        },
        clicktToRemove(index){
            this.tags.splice(index, 1); 
        }
    },
    components : {
        tag
    },
    created(){
        if(this.value){
            if(this.value.length > 0){
                this.tags = this.value.split(',');
            }
        }
    },
    watch : {
        tags(){
            this.$emit('input', this.tags.join(','));
        }
    }
}
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.tag-container {
    border: 1px solid #cccccc;
    padding: 20px;
    margin-bottom: 10px;
}
input {
    outline: none;
    height: 40px;
    width: 160px;
    border: 1px solid #cccccc;
    border-radius: 5px;
    padding: 12px 12px;
    box-sizing: border-box;
}
.error {
    font-size: 12px;
    color: red;
    margin-top: 5px;
}
</style>
